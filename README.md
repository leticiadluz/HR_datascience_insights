# Ciência de Dados em Recursos Humanos

**Este repositório é dedicado à análise e compreensão das altas taxas de rotatividade de funcionários enfrentadas por uma empresa de tecnologia, especificamente uma software house.**
- A empresa tem experimentado uma rotatividade significativa de funcionários, chegando a 30% em alguns semestres. 
- Essa alta taxa de rotatividade tem custos substanciais e impactos no negócio.
- Utilizando técnicas de ciência de dados, como análise exploratória, modelos preditivos e clusterização, desenvolvemos estratégias mais eficazes de retenção e identificar fatores críticos que contribuem para o turnover.

-  Este projeto faz parte do desafio da [Data Viking](https://www.dataviking.com.br/), onde foram disponibilizados dados reais de uma software house para os participantes interessados.
-  **Qualquer análise e estudo baseados em dados podem ser realizados, como: Modelo de Turnover, Cluster de Funcionários, Perfil de Risco, Ciclos de Rotatividade, entre outros.**


## 1 -  Análise Exploratória de Dados
- **Na análise exploratória dos dados relacionados à rotatividade de funcionários, encontramos os seguintes resultados, apoiados por testes estatísticos:**
  - Data de Contratação: Novembro foi o mês com o maior número de contratações (70 novos funcionários). Fevereiro e setembro também tiveram alta demanda, com 67 contratações cada. Abril registrou o menor número de contratações, com apenas 35.
  - Data de Desligamento: Todos os 144 registros de desligamento possuem a mesma data (14 de maio de 2024), sugerindo que esses dados podem ser sintéticos e que a coluna 'Meses_de_Serviço' pode estar inconsistente.
  - Meses de Serviço: A análise indica que os meses de serviço não são um fator determinante para o desligamento, pois as distribuições e medidas centrais são semelhantes entre funcionários desligados e ativos.
  - Idade: A idade também não parece ser um fator significativo para o desligamento, com distribuições semelhantes entre os dois grupos.
  - Pontuação de Desempenho: Funcionários desligados tendem a ter pontuações de desempenho mais altas em comparação com funcionários ativos, sugerindo que funcionários de alto desempenho podem estar mais propensos a se desligarem.
  - Satisfação com o Trabalho: Não houve uma diferença significativa na satisfação com o trabalho entre funcionários desligados e ativos, indicando que esta variável pode não ser um fator crítico para o desligamento.
  - Nível de Cargo: A distribuição de desligamentos é uniforme entre os diferentes níveis de cargo (Júnior, Pleno, Sênior), sugerindo que o nível de cargo não influencia significativamente a taxa de desligamento.
  - Salário: Não houve uma diferença significativa nos salários entre funcionários desligados e ativos, indicando que o salário pode não ser um fator determinante para o desligamento.
  - Horas Extras: Funcionários desligados tendem a realizar mais horas extras do que funcionários ativos, mostrando uma diferença significativa entre os dois grupos. Isso indica que a carga de trabalho adicional pode estar associada ao desligamento.
  - **Em resumo, entre as variáveis analisadas, Pontuação de Desempenho e Horas Extras mostraram uma relação significativa com a taxa de desligamento. Funcionários com pontuações de desempenho mais altas e aqueles que realizam mais horas extras têm uma maior probabilidade de se desligarem da empresa.**

## 2 -  Aprendizado de máquina supervisionado (classificação)
- Construímos quatro modelos de Machine Learning utilizando três estimadores diferentes: KNN, SVC e XGBoost. Realizamos pré-processamento das variáveis, selecionando as mais adequadas para cada estimador e otimizando os hiperparâmetros. A métrica escolhida para a avaliação dos modelos foi o recall. Ao otimizar o recall, garantimos que estamos minimizando a quantidade de falsos negativos, ou seja, identificando o maior número possível de funcionários com risco de desligamento.
- Ao final, utilizamos uma abordagem de ensemble que combina as forças de dois algoritmos de machine learning (SVM e XGBoost) para melhorar o desempenho da classificação através de um VotingClassifier. O resultado final foi um recall de 0.62 nos dados de teste. Essa métrica, embora abaixo do desejado, deve-se ao fato de que as variáveis possuem baixa relação com o target. Apenas duas variáveis tinham uma relação média: Pontuação de Desempenho e Horas Extras. Algumas variáveis tiveram que ser excluídas, como Data de Desligamento e Meses de Serviço, que continham dados sintéticos e representavam dados futuros que não seriam vistos pelo modelo.
- Em resumo, os dados sugerem que o modelo de classificação tem um desempenho razoável, mas há espaço para melhorias. Ele é melhor do que um modelo aleatório, mas ainda não é excelente.

## 3 -  Aprendizado de máquina não supervisionado (clusterização)
- Para entender melhor os padrões entre os funcionários que deixam a empresa, utilizamos o algoritmo K-Means. O K-Means conseguiu segmentar os funcionários em dois clusters, permitindo-nos identificar alguns padrões de comportamento:
  - Cluster 0:
    - Funcionários mais jovens
    - Pontuação de desempenho ligeiramente menor
    - Média de satisfação no trabalho ligeiramente maior
    - Média de salário e de horas extras significativamente menor
    - Grupo formado quase que exclusivamente por funcionários de nível júnior a pleno
   
  - Cluster 1:
    - Funcionários mais velhos
    - Pontuação de desempenho ligeiramente maior
    - Média de satisfação no trabalho ligeiramente menor
    - Média de salário e de horas extras significativamente maior
    - Todos os funcionários são de nível sênior
    - 
- **Esses padrões podem ajudar a empresa a desenvolver estratégias específicas para melhorar a retenção de funcionários em cada grupo, abordando as necessidades e preocupações específicas de cada cluster.**

## Conclusões Gerais
- Entre as variáveis analisadas, a Pontuação de Desempenho e as Horas Extras mostraram uma relação significativa com a taxa de desligamento. Funcionários com pontuações de desempenho mais altas e aqueles que realizam mais horas extras tendem a ter uma maior probabilidade de se desligarem da empresa.
- Nosso modelo apresentou um desempenho razoável, com um recall de 62,16%. Isso indica que o modelo conseguiu identificar 62,16% de todas as instâncias positivas reais (funcionários propensos a sair). Embora o modelo ainda possa ser aprimorado, ele já é capaz de capturar uma parcela significativa dos funcionários em risco de desligamento.
- A análise de clusterização dos funcionários desligados revelou que o Cluster 1 é composto por funcionários de nível sênior que fazem mais horas extras e recebem um salário maior. Este perfil específico pode ser um bom indicativo para prever a saída de funcionários.
