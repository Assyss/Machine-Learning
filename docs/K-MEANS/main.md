# Análise Visual do Agrupamento K-Means

A seguir, são apresentados os resultados visuais chave do processo de clusterização, desde a exploração inicial dos dados até a avaliação final do modelo.

---

### 1. Visualização Inicial dos Dados

Gráfico de dispersão do conjunto de dados antes da aplicação de qualquer algoritmo. A distribuição sugere a presença de agrupamentos naturais, que buscaremos identificar.

![Visualização Inicial dos Dados](main_files/visualizacao_inicial.png)

---

### 2. Determinação do Número de Clusters (Método do Cotovelo)

A curva de inércia (WCSS) foi plotada para diferentes valores de `k`. O "cotovelo" formado no gráfico aponta `k=4` como o número ótimo de clusters para este conjunto de dados.

![Método do Cotovelo](main_files/metodo_cotovelo.png)

---

### 3. Resultado Final do Agrupamento

Visualização dos 4 clusters identificados pelo algoritmo K-Means após o treinamento. Cada cor representa um cluster distinto, e os marcadores 'X' em vermelho indicam os centroides finais de cada grupo.

![Clusters Finais](main_files/clusters_finais.png)