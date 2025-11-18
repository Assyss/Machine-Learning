# Implementação e Análise do Algoritmo PageRank

**Autor:** Bruno Assis

**Data:** 18 de Novembro de 2025

**Dataset:** Epinions Social Network (soc-Epinions1)

---

## 1. Introdução e Dataset

O objetivo deste projeto é implementar o algoritmo **PageRank** para identificar a importância de nós (usuários) em um grafo direcionado de confiança.

O conjunto de dados escolhido foi o **soc-Epinions1**, uma rede onde uma aresta $A \to B$ significa que o usuário $A$ "confia" no usuário $B$. O PageRank, neste contexto, mede a **reputação** ou **influência** do usuário.

- **Tipo:** Grafo Direcionado de Confiança.
- **Tamanho:** 75.879 nós e 508.837 arestas.

---

## 2. Metodologia e Implementação

O algoritmo PageRank foi implementado do zero em Python (célula 3) utilizando a **fórmula iterativa** padrão, conforme o enunciado:

$$PR(p_i) = \frac{1-d}{N} + d \sum_{p_j \in M(p_i)} \frac{PR(p_j)}{L(p_j)}$$

A convergência foi determinada por uma tolerância (`tol`) de $0.0001$. A alta correlação com a implementação do NetworkX (próxima de 1.0) validou a precisão do nosso código.

---

## 3. Análise dos Resultados

### 3.1 Os 10 Usuários Mais Influentes

Os 10 nós com maior PageRank são considerados os usuários mais influentes ou com maior reputação na rede. Eles recebem confiança de uma grande quantidade de fontes confiáveis. *(Os IDs exatos estão na saída do Notebook)*.

**Interpretação:** Nós com alto PageRank neste dataset são **influenciadores** de opinião na comunidade Epinions, pois recebem confiança indireta de toda a rede.

### 3.2 Impacto do Fator de Amortecimento ($d$)

O fator $d$ (probabilidade de continuar seguindo um link) foi variado para analisar seu impacto nos rankings.

![Impacto do Fator de Amortecimento (d)](main_files/variacao_damping.png)
*Figura 1: Impacto do fator 'd' nos 5 nós mais bem ranqueados.*

- **d = 0.50 (Mais Aleatório):** A pontuação de PageRank é distribuída de forma mais uniforme. As diferenças entre os nós de topo e os nós comuns diminuem, pois o algoritmo passa mais tempo "pulando" para páginas aleatórias.
- **d = 0.99 (Mais Estruturado):** As diferenças de pontuação aumentam drasticamente. O PageRank se concentra nos nós centrais. Isso amplifica a importância da estrutura de links, ou seja, a confiança depositada é quase sempre seguida.

---

## 4. Conclusão

A implementação do algoritmo PageRank foi bem-sucedida, fornecendo classificações de importância consistentes com a biblioteca NetworkX. A análise demonstrou que o PageRank é uma ferramenta robusta para medir a influência em redes sociais de confiança. O fator $d=0.85$ oferece o melhor equilíbrio, evitando que a pontuação se concentre demais em poucos hubs ($d=0.99$) ou que seja distribuída de forma muito plana ($d=0.50$).