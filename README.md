# Análise e Agrupamento de Dados de Mangás

### Desenvolvido por:
- Arthur de Araújo Leite,

- Pedro Henrique Carvalho de Paula,

- Roger Pelegrini Rampazo 

## Visão Geral do Projeto

Este projeto consiste em uma análise exploratória e aplicação de aprendizado de máquina não supervisionado (Clustering) em um dataset de mangás. O objetivo principal é limpar e reduzir a dimensionalidade dos dados de conteúdo e, em seguida, utilizar o algoritmo K-Means para agrupar os mangás em clusters com base em suas características de conteúdo e métricas de desempenho (como **score** e número de **membros**).

## Estrutura e Etapas

O projeto está dividido em dois principais *notebooks* que representam as fases de Pré-processamento e Agrupamento:

### 1\. `limpezaCSV.ipynb` (Pré-processamento e Redução de Features)

Este *notebook* é focado na preparação dos dados.

  * **Função:** Realiza a limpeza, transformação e, crucialmente, a redução de dimensionalidade nas *features* de conteúdo do dataset.
  * **Redução de Features:** As categorias de conteúdo de baixa frequência são agrupadas em uma única *feature* chamada `Content_Others`.
  * **Resultado Final:** O DataFrame final possui um conjunto reduzido de colunas, contendo 9 "Top features" de conteúdo mais a coluna `Content_Others`.
  * **Exportação:** O dataset processado e com features reduzidas é salvo no arquivo `manga_features_reduzidas.csv`.

### 2\. `agrupamento.ipynb` (Clustering K-Means)

Este *notebook* implementa a técnica de agrupamento para identificar padrões.

  * **Carregamento de Dados:** Carrega o arquivo `manga_minmaxt.csv` (assumido ser o dataset pré-processado ou uma variação deste).
  * **Metodologia:** Aplica o algoritmo **K-Means** para clustering.
  * **Dimensionalidade:** Utiliza **PCA (Análise de Componentes Principais)**.
  * **Análise de Clusters:** Os *clusters* gerados são sumarizados e analisados com base em:
      * **Score Médio** (`score`).
      * **Membros Médios** (`log_members`).
      * **Conteúdo Mais Frequente**.
  * **Interpretação Heurística:** O *notebook* tenta nomear os *clusters* com base em suas métricas, como por exemplo, classificando grupos com alto alcance e qualidade (score \> 7.5 e log\_members significativamente acima da média) como **"BLOCKBUSTER POPULAR"**.

## Requisitos para Execução

Para rodar os *notebooks* e replicar a análise, são necessárias as seguintes bibliotecas Python:

  * `pandas`
  * `numpy`
  * `matplotlib.pyplot`
  * `sklearn.cluster.KMeans` (scikit-learn)
  * `sklearn.decomposition.PCA` (scikit-learn)

Você pode instalá-las usando `pip`:

```bash
pip install pandas numpy matplotlib scikit-learn
```

## Como Executar

1.  **Download dos Arquivos:** Certifique-se de que todos os *notebooks* (`limpezaCSV.ipynb`, `agrupamento.ipynb`) e o arquivo de dados original (não fornecido, mas necessário para `limpezaCSV.ipynb`) e o arquivo de dados `manga_minmaxt.csv` (necessário para `agrupamento.ipynb`) estejam no mesmo diretório.
2.  **Executar `limpezaCSV.ipynb`:**
      * Abra o *notebook* em um ambiente Jupyter.
      * Execute todas as células para realizar o pré-processamento.
      * O arquivo `manga_features_reduzidas.csv` será gerado e salvo.
3.  **Executar `agrupamento.ipynb`:**
      * Abra este *notebook* (assumindo que o arquivo de entrada `manga_minmaxt.csv` ou o gerado na etapa 2 está disponível).
      * Execute as células para carregar os dados, aplicar K-Means e PCA, e visualizar os resultados dos *clusters*.
