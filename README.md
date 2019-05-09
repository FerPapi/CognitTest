# CognitTest

a. Como foi a definição da sua estratégia de modelagem? 

Primeiramente, uma análise exploratória é feita e o dataset é limpo (havia colunas com inputs numéricos transformados em string, por exemplo). A análise exploratória revelou um dataset desbalanceado, com muitas saídas de valor 5 e 6 e poucas de outros valores. Além disso, as entradas do dataset revelaram ter muita pouca correlação com o valor de saída. Em geral isso pode ser contornado com um estimador universal (como uma Rede Neural), mas se nem combinações dos valores de entrada tiverem uma correlação suficiente com os de saída, então nem um estimador universal pode ter um bom desempenho.

A partir da análise inicial, tem-se uma avaliação inicial utilizando dois geradores aleatórios, um com uma distribuiço normal e outro com uma distribuição uniforme. Espera-se que um estimador seja ao menos melhor do que geradores aleatórios de valores de sada.

Então, dois modelos de estimadores são propostos: Uma regressão linear e Redes Neurais. Outra tentativa foi um modelo de Classificação por Rede Neural, onde as possíveis notas são consideradas como possíveis classes.

b. Como foi definida a função de custo utilizada?

As funções de custo utilizadas foram o Root Mean Square Error (RMSE), que é uma boa função de custo para comparações entre modelos propostos, penalizando mais fortemente erros maiores e o Mean Average Error (MAE), que dá uma boa percepção da precisão do modelo nos termos de suas variáveis originais.

c. Qual foi o critério utilizado na seleção do modelo final?

Deve-se escolher o modelo que obtenha melhor resultado de acordo com as métricas (MAE ou RMSE), mas que ao mesmo tempo não esteja com overfit dos dados, ou seja, 'viciado' para prever dados de um dataset em específico. Estratégias como o k-fold, mencionado abaixo, fazem a validação cruzada dos dados para evitar overfitting.

d. Qual foi o critério utilizado para validação do modelo? Por que escolheu utilizar este método?

Utilizou-se uma estratégia de k-fold, onde o dataset é separado em n (15) partes, n-1 partes são utilizadas para treinar o modelo e 1 parte é utilizada para avaliação. Repete-se o processo para cada uma das n partes sendo selecionadas como avaliação.

e. Quais evidências você possui de que seu modelo é suficientemente bom?

Os modelos finais, de regressão por Rede Neural e classificação por Rede Neural ainda não podem ser considerados como suficientemente bons.

Resultados

Modelo - RMSE - MAE:

Aleatório Uniforme - 3.30 - 2.75

Aleatório Normal - 1.37 - 1.04

Regressão Linear - 0.92 - 0.65

Regressão NN (Modelo 1 - SKLearn) - 1.12 - 0.83

Regressão NN (Modelo 2 - Keras) - 0.86 - 0.58

Classificação NN - 0.805 - 0.53

Os modelos apresentam resultados semelhantes, porém marginalmente superiores à uma Escolha Aleatória. O modelo de classificação apresentou o melhor resultado geral. O fato de que os modelos parecem convergir para um MAE de 0.5 (equivalente a todas as predições serem 5.5 e todos os outputs serem 5 ou 6), neste caso, pode indicar que o problema esteja mais no dataset e na escolha de features dos modelos do que dos modelos utilizados em si.

A partir disso, novas hiṕóteses podem ser geradas para posterior análise e avaliação:

1. O dataset é muito desbalanceado. Como a maioria dos valores de saída do dataset estão entre 5 e 6 (e não há valores abaixo de 3 e acima de 9), os modelos tendem a gerar predições entre estes 2 valores. Aumentar o dataset poderia ser um caminho válido de ser explorado.

2. Se obter novos dados não for possível, então deveria-se buscar um modelo de regressão ou classificação robusto o suficiente para datasets desbalanceados, utilizando de algumas técnica como undersampling.

3. Outros modelos de predição e/ou classificação poderiam ser usados em uma nova iteração sobre o problema. SVM ou K-Means poderiam ser boas escolhar

