# Ciência de Dados em Recursos Humanos

**Este repositório é dedicado à análise e compreensão das altas taxas de rotatividade de funcionários enfrentadas por uma empresa de tecnologia, especificamente uma software house.**
- A empresa tem experimentado uma rotatividade significativa de funcionários, chegando a 30% em alguns semestres. 
- Essa alta taxa de rotatividade tem custos substanciais e impactos no negócio.
- Utilizando técnicas de ciência de dados, como análise exploratória, modelos preditivos e clusterização, podemos desenvolver estratégias mais eficazes de retenção e identificar fatores críticos que contribuem para o turnover.

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

## 2 -  Aprendizado de máquina supervisionado (Classificação)
- Construímos quatro modelos de Machine Learning utilizando três estimadores diferentes: KNN, SVC e XGBoost. Realizamos pré-processamento das variáveis, selecionando as mais adequadas para cada estimador e otimizando os hiperparâmetros. A métrica escolhida para a avaliação dos modelos foi o recall. Ao otimizar o recall, garantimos que estamos minimizando a quantidade de falsos negativos, ou seja, identificando o maior número possível de funcionários com risco de desligamento.
- Ao final, utilizamos uma abordagem de ensemble que combina as forças de dois algoritmos de machine learning (SVM e XGBoost) para melhorar o desempenho da classificação através de um VotingClassifier. O resultado final foi um recall de 0.62 nos dados de teste. Essa métrica, embora abaixo do desejado, deve-se ao fato de que as variáveis possuem baixa relação com o target. Apenas duas variáveis tinham uma relação média: Pontuação de Desempenho e Horas Extras. Algumas variáveis tiveram que ser excluídas, como Data de Desligamento e Meses de Serviço, que continham dados sintéticos e representavam dados futuros que não seriam vistos pelo modelo.
- Em resumo, os dados sugerem que o modelo de classificação tem um desempenho razoável, mas há espaço para melhorias. Ele é melhor do que um modelo aleatório, mas ainda não é excelente.
