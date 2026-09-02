#  — Projeto: Análise de Rotatividade de Clientes da Model Fitness

## Sobre o projeto

Neste projeto, trabalhei com dados de clientes da rede de academias Model Fitness para analisar a rotatividade de usuários e entender quais características estão mais relacionadas ao cancelamento ou abandono da academia.

A ideia principal foi usar os dados disponíveis para identificar clientes com maior probabilidade de sair no mês seguinte, encontrar grupos de clientes com comportamentos parecidos e, a partir disso, propor algumas estratégias para melhorar a retenção.

## Objetivos

Neste projeto, meus principais objetivos foram:

* analisar os dados dos clientes e entender suas características;
* identificar padrões relacionados à rotatividade;
* construir modelos para prever a probabilidade de um cliente sair no mês seguinte;
* comparar regressão logística e floresta aleatória;
* criar agrupamentos de clientes usando técnicas de machine learning;
* identificar quais grupos apresentam maior e menor rotatividade;
* analisar os principais fatores relacionados à saída dos clientes;
* propor recomendações para melhorar a retenção.

# 1. Preparação e exploração inicial dos dados

Primeiramente, carreguei o arquivo `gym_churn_us.csv` e fiz uma análise inicial para entender a estrutura dos dados.

Verifiquei:

* quantidade de linhas e colunas;
* tipos de dados;
* existência de valores ausentes;
* possíveis inconsistências;
* estatísticas descritivas das variáveis.

Também utilizei o método `describe()` para analisar a média, o desvio padrão, os valores mínimos e máximos e os quartis das características dos clientes.

Depois, observei as características médias dos clientes que permaneceram e dos clientes que saíram, utilizando `groupby()` pela variável `Churn`.

# 2. Análise exploratória dos dados

Depois da preparação, comparei os dois grupos de clientes:

* clientes que permaneceram na academia;
* clientes que tiveram rotatividade.

Analisei características como idade, tempo de permanência, duração do contrato, frequência de visitas, participação em aulas em grupo e gastos adicionais.

Também construí histogramas e gráficos de distribuição para visualizar melhor as diferenças entre os clientes que permaneceram e os que saíram.

Além disso, criei uma matriz de correlação para entender quais variáveis possuem maior relação entre si e quais características podem estar mais associadas à rotatividade.

Essa etapa foi importante para conseguir identificar alguns padrões antes de construir os modelos de previsão.

# 3. Modelo para prever a rotatividade

Na próxima etapa, construí modelos de classificação binária para prever se um cliente teria rotatividade no mês seguinte.

Primeiramente, separei as variáveis preditoras da variável objetivo `Churn` e dividi os dados em conjuntos de treinamento e validação utilizando `train_test_split()`.

Defini um `random_state` para conseguir reproduzir os resultados.

## Regressão logística

O primeiro modelo que utilizei foi a regressão logística.

Treinei o modelo com os dados de treinamento e depois fiz as previsões utilizando o conjunto de validação.

Para avaliar o desempenho, analisei:

* acurácia;
* precisão;
* sensibilidade.

## Floresta aleatória

Depois, utilizei o algoritmo de floresta aleatória para fazer a mesma previsão.

Também treinei o modelo com os dados de treinamento e avaliei suas previsões no conjunto de validação usando as mesmas métricas.

## Comparação dos modelos

Por fim, comparei os resultados dos dois modelos para identificar qual apresentou melhor desempenho na previsão da rotatividade.

A escolha do modelo foi baseada principalmente nas métricas calculadas no notebook, considerando que, para esse problema, é importante conseguir identificar corretamente os clientes que apresentam risco de sair.

# 4. Agrupamento dos clientes

Depois da parte de previsão, passei para a análise de agrupamentos.

O objetivo foi encontrar grupos de clientes com características e comportamentos semelhantes.

Primeiramente, padronizei as características dos clientes para que as variáveis com escalas diferentes não tivessem um peso desproporcional no agrupamento.

Em seguida, utilizei a função `linkage()` para calcular as distâncias entre os clientes e construí um dendrograma.

Com o dendrograma, analisei visualmente a quantidade de grupos que poderia ser utilizada. Para manter a comparação com os demais projetos, utilizei **5 agrupamentos** no K-means.

# 5. Análise dos agrupamentos

Depois de aplicar o K-means, atribuí cada cliente a um dos cinco grupos.

Em seguida, analisei os valores médios das características de cada agrupamento para entender o perfil dos clientes de cada grupo.

Comparei características como:

* idade;
* tempo de permanência;
* duração do contrato;
* frequência de visitas;
* participação em aulas em grupo;
* meses restantes do contrato;
* gastos adicionais;
* outras características disponíveis no conjunto de dados.

Também construí distribuições para visualizar melhor as diferenças entre os agrupamentos.

Essa análise ajudou a identificar quais grupos possuem comportamentos mais semelhantes e quais apresentam características que podem indicar maior risco de rotatividade.

# 6. Taxa de rotatividade por agrupamento

Depois de criar os grupos, calculei a taxa de rotatividade de cada agrupamento utilizando `groupby()`.

Comparei os grupos para identificar quais apresentavam maior proporção de clientes que saíram e quais apresentavam maior retenção.

A partir dessa análise, consegui identificar os grupos mais propensos à rotatividade e os grupos que apresentavam um comportamento mais fiel
