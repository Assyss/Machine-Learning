# Projeto II: Implementação de Modelos de Regressão

**Projeto Integrador:** [Nome do Seu Projeto]
**Objetivo do ML:** Previsão de [Sua Variável Contínua, ex: Preço de Imóveis].
**Grupo:** [Nomes dos Membros]

---

## 1. Exploração e Geração dos Dados

### 1.1 Cenário e Justificativa (Geração de Dados Sintéticos)
[Descreva o cenário do seu Projeto Integrador (ex: Empresa de entregas, mercado imobiliário). Justifique por que foi necessário criar dados sintéticos (ex: "Não havia histórico de transações suficiente").]

O dataset sintético foi gerado com **5000 amostras**, baseado nas features: `Area`, `Quartos` e `Localizacao_Score`. O Target (`Preço`) foi criado com a adição de ruído.

### 1.2 Análise Exploratória
[Inclua as estatísticas e as visualizações geradas no notebook, como o Mapa de Calor de Correlação.]

---

## 2. Implementação dos Modelos (Seleção e Justificativa)

A tarefa é Regressão, logo, escolhemos modelos que abordam a complexidade dos dados de maneiras distintas.

| Algoritmo | Paradigma | Justificativa |
| :--- | :--- | :--- |
| **Regressão Linear** | Simples, Linear | Serve como **baseline** para determinar se a relação entre as variáveis é, primariamente, linear. |
| **Random Forest Regressor** | Ensemble (Não Linear) | Capaz de modelar interações complexas entre features sem a necessidade de pré-engenharia de features. |
| **SVR (RBF Kernel)** | Não Linear | Testa a capacidade de um modelo de vetor de suporte de encontrar um hiperplano ótimo em espaços de alta dimensão. |

### 2.1 Pré-processamento
Os dados foram escalados com `StandardScaler` para otimizar o desempenho do SVR e da Regressão Linear.

---

## 3. Avaliação e Comparação dos Resultados

Utilizamos o **RMSE (Root Mean Squared Error)** como métrica primária, pois ele fornece o erro médio na mesma unidade da variável `Preço`.

| Modelo | MAE | MSE | **RMSE** | $R^2$ Score |
| :--- | :--- | :--- | :--- | :--- |
| Regressão Linear | [Valor] | [Valor] | **[Valor]** | [Valor] |
| Random Forest | [Valor] | [Valor] | **[Valor]** | [Valor] |
| SVR | [Valor] | [Valor] | **[Valor]** | [Valor] |

### 3.1 Discussão

* **Melhor Modelo:** [Indique o modelo com o menor RMSE e maior $R^2$]. O [Melhor Modelo] performou melhor porque [justifique: ele capta não linearidades, ou a relação já era linear].
* **Performance da Baseline:** A Regressão Linear obteve um [Alto/Baixo] RMSE, indicando que [a maior parte da relação é linear, ou que o dataset requer modelos mais complexos].

---

## 4. Conclusão e Melhorias Futuras

O projeto demonstrou a aplicação de Machine Learning para a previsão de valores contínuos. O modelo [Melhor Modelo] é o mais indicado para implantação.

**Sugestões de Melhoria:**
1.  **Otimização:** Aplicar `GridSearchCV` para tunar os hiperparâmetros do Random Forest e SVR.
2.  **Engenharia de Features:** Criar features sintéticas (ex: interações) para alimentar os modelos lineares.
3.  **Outros Algoritmos:** Testar modelos de *boosting*, como o XGBoost ou LightGBM.