# Projeto de Classificação com K-Nearest Neighbors: Tipos de Solo por Satélite
**Autor:** Bruno Assis

### Introdução
Este projeto tem como objetivo desenvolver um modelo de Machine Learning capaz de classificar tipos de solo com base em dados de observações de satélite. Para esta tarefa, foi utilizado o algoritmo **K-Nearest Neighbors (KNN)**, um modelo de aprendizado supervisionado baseado em instância, que classifica um novo dado com base na classe de seus "vizinhos" mais próximos no espaço de características.

O desenvolvimento seguiu as etapas de exploração, pré-processing, divisão dos dados, treinamento do modelo e avaliação de performance, utilizando as bibliotecas `pandas`, `numpy`, e `scikit-learn`.

### Etapa 1: Exploração dos dados
A primeira etapa consistiu em uma análise para entender a estrutura e as características do conjunto de dados Statlog (Landsat Satellite).

#### Natureza dos dados
O dataset é composto por **6435 amostras** (pixels de uma imagem de satélite), cada uma descrita por **36 características** (features). Essas características correspondem a valores de intensidade de luz em quatro bandas espectrais (duas visíveis e duas infravermelhas) para uma vizinhança de 3x3 pixels.

O objetivo é classificar cada amostra em uma das **6 classes de solo** possíveis:
* Classe 1: solo vermelho
* Classe 2: solo cinza
* Classe 3: solo com vegetação de restolho
* Classe 4: solo com vegetação de algodão
* Classe 5: mistura de solo e vegetação
* Classe 7: solo muito úmido

### Etapa 2: Pré-processamento
Nesta etapa, preparamos os dados para o treinamento do modelo, uma fase crítica para algoritmos baseados em distância como o KNN.

* **Limpeza e Tratamento de Valores Ausentes:** Uma verificação inicial confirmou que o dataset estava completo, sem valores nulos ou ausentes, não necessitando de técnicas de imputação.

* **Padronização dos Dados (Scaling):** O KNN calcula a "distância" (geralmente euclidiana) entre os pontos de dados para determinar seus vizinhos. Se as características estiverem em escalas diferentes, aquelas com maiores magnitudes dominarão o cálculo, distorcendo o resultado. Para evitar isso, foi **essencial realizar a padronização dos dados**. Utilizamos o `StandardScaler` do scikit-learn, que transforma cada característica para ter uma média de 0 e um desvio padrão de 1, garantindo que todas contribuam igualmente para o cálculo da distância.

### Etapa 3: Divisão dos dados
Para avaliar o modelo de forma justa, o conjunto de dados foi dividido em dois subconjuntos:

* **Conjunto de Treino (70% dos dados):** Usado para "apresentar" os dados ao modelo.
* **Conjunto de Teste (30% dos dados):** Usado para avaliar o desempenho do modelo em dados "novos".

A divisão resultou em:
* **Tamanho do conjunto de treino:** 4504 amostras
* **Tamanho do conjunto de teste:** 1931 amostras

### Etapa 4: Treinamento do modelo
O modelo escolhido foi o `KNeighborsClassifier` da biblioteca `scikit-learn`.

1.  **Instanciar o modelo:** Foi criado um classificador KNN com o hiperparâmetro `n_neighbors=5`.
2.  **Treinar o modelo:** O modelo foi treinado com o método `.fit()`, que recebeu os dados de treino padronizados (`X_train_scaled`, `y_train`).

### Etapa 5: Avaliação do modelo
Após o treinamento, o desempenho do modelo foi avaliado utilizando o conjunto de teste, também padronizado.

#### Métricas de desempenho
* **Acurácia:** O modelo atingiu uma **acurácia de aproximadamente 90.78%**.
* **Relatório de Classificação:**

| Classe | Precision | Recall | F1-Score | Support |
| :--- | :--- | :--- | :--- | :--- |
| 1 | 0.91 | 0.96 | 0.93 | 467 |
| 2 | 0.95 | 0.95 | 0.95 | 220 |
| 3 | 0.96 | 0.96 | 0.96 | 403 |
| 4 | 0.81 | 0.82 | 0.81 | 186 |
| 5 | 0.89 | 0.85 | 0.87 | 216 |
| 7 | 0.91 | 0.88 | 0.89 | 439 |

### Etapa 6: Relatório final e conclusão
O projeto demonstrou a eficácia do algoritmo KNN para um problema de classificação multiespectral. Com um pré-processamento adequado, notadamente a padronização dos dados, o modelo alcançou uma alta acurácia de **90.78%**.

#### Possíveis melhorias
* **Otimização de Hiperparâmetros:** Realizar uma busca em grade (`Grid Search`) para encontrar o valor ótimo de `K`.
* **Validação Cruzada (Cross-Validation):** Empregar a validação cruzada para obter uma estimativa mais confiável do desempenho.
* **Feature Engineering:** Explorar a criação de novas características para melhorar a separabilidade entre as classes.