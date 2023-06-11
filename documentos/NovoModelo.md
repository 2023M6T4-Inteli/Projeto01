# Documentação de proposta de uma nova modelagem

## Introdução
[Texto falando sobre a sprint com os objetivos]

## Metodologia
Nesta seção do documento serão abordados os principais tópicos relacionados ao desenvolvimento e métricas de avaliação dos modelos preditivos, bem como a introdução do modelo escolhido para confrontar os modelos desenvolvidos em sprints anteriores, sendo este o Support Vector Machine.
Também serão exploradas as otimizações realizadas nos modelos, sejam por hiperparâmetros ou outros tipos de vetorização de palavras para o processamento de linguagem natural.
Por fim, serão definidos os critérios de escolha do modelo, com base nas métricas relevantes, ressaltando a validação dos resultados para maior confiabilidade do desempenho do modelo a ser escolhido como mais adequado para o conjunto de dados utilizado neste projeto.

### Modelo Support Vector Machine (SVM)

O SVM é um algoritmo de aprendizado de máquina supervisionado que pode ser aplicado tanto a problemas de classificação quanto para de regressão. Ele busca uma linha de separação (hiperplano) entre duas classes distintas, baseando-se nos pontos mais próximos de cada classe. Este modelo foi escolhido pela sua performance com uma base de dados complexa e de alta dimensionalidade, em modelos de classificação, e pela facilitação em aplicar hiperparâmetros para ajustar o seu desempenho.

A partir de seu foco no treinamento e classificação de um dataset, seu objetivo principal é encontrar um hiperplano que melhor separe os pontos de dados em diferentes classes ou aproxime os pontos de dados com menor erro possível.

Uma das principais vantagens do SVM é sua capacidade de lidar com conjuntos de dados não lineares e possuir propriedades de regularização embutidas, o que ajuda a evitar o overfitting (sobreajuste) do modelo aos dados de treinamento.

### Método escolhido
Há dois tipos principais de SVM: o modelo rígido (hard margin) e o modelo com margem flexível (soft margin). O modelo rígido visa encontrar um hiperplano que separe os dados em duas classes assumindo que eles são linearmente separáveis e sem cometer erros de classificação. Já o modelo com margem flexível permite erros de classificação e além de encontrar um hiperplano que separe os dados da melhor maneira e que maximize a margem, ele busca minimizar esses erros de classificação também.

Em nosso modelo, utilizamos o SVM (Support Vector Machine) com margem flexível por permitir que o modelo seja mais flexível na adaptação dos dados e um certo grau de erro nos dados de treinamento. Isso evita o chamado "overfitting", onde o modelo se ajusta muito bem aos dados de treinamento, mas tem baixa capacidade de generalização para novos dados.


### Otimização da Modelagem


#### Hiperparâmetros
Para melhor configurar o desempenho da modelagem preditiva para classificação, os hiperparâmetros são ajustes definidos antes do treinamento do modelo, influenciando no seu aprendizado. A otimização desses hiperparâmetros se dá pela configuração e combinação desses parâmetros, que resultam no melhor desempenho do modelo, ressaltando a importância de evitar overfitting, melhorando a precisão dos resultados obtidos com a generalização do treinamento do modelo.

Uma técnica que pode ser utilizada para realizar a otimização de hiperparâmetros é a partir do Grid Search, que envolve a definição de um conjunto de valores possíveis para cada hiperparâmetro, que configura vários testes para a escolha dos ajustes ideais para o conjunto de dados utilizado, evitando overfitting e melhorando o desempenho do modelo.

É importante dizer que colocar um limite de configurações que o Grid Search realiza é importante para reduzir o tempo de execução do modelo, pois pode levar um tempo muito elevado e o desempenho não mudar, por algum problema na base de dados ou na pipeline dos dados, por exemplo, reduzindo a eficiência do Grid Search.


## Rede Neural com Vetorização por Transformers
[explicação do que é transformers]

### Método escolhido:
[explicação da criação/execução/hiperparametros do transformers]


## Métricas

### Acurácia

  - A acurácia é uma métrica simples que utiliza a razão entre todos os acertos do modelo (Verdadeiros Positivos e Verdadeiros Negativos) sobre a quantidade total de elementos usados na predição, ou seja, Verdadeiros Positivos somado com Verdadeiros Negativos, Falsos Positivos e Falsos Negativos.
 
<!-- ![formula acuracia](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/a137bb75-f2af-4fc6-bad8-696d75bd671d) -->

$$
\begin{align}
Acurácia={Verdadeiros Positivos + Verdadeiros Negativos \over Verdadeiros Positivos + Verdadeiros Negativos + Falsos Positivos + Falsos Negativos}
\end{align}
$$
  
### Revocação

  - A revocação  é uma métrica que avalia a capacidade de um modelo em identificar corretamente os exemplos positivos em relação ao total de exemplos positivos presentes nos dados,
ela é calculada dividindo o número de Verdadeiros Positivos pela soma dos Verdadeiros Positivos com os Falsos Negativos. 
<!-- 
<img src=  "https://github.com/2023M6T4-Inteli/Projeto01/assets/99538889/85c8486f-da84-4967-93db-98175782f866" alt = "formula revocacao">

![formula_revocacao](https://github.com/2023M6T4-Inteli/Projeto01/assets/99538889/85c8486f-da84-4967-93db-98175782f866) -->
$$
\begin{align}
Revocação={Verdadeiros Positivos \over Verdadeiros Positivos + Falsos Negativos}
\end{align}
$$


<!-- ![image](https://github.com/2023M6T4-Inteli/Projeto01/blob/main/assets/imagens/9#issue-1751518551) -->
<!-- 
[não usar essa imagem:]
![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/dfdf8dad-37ee-4de4-bef2-7dd8fcc5245c) -->


### Matriz de confusão

<img src=  "https://github.com/2023M6T4-Inteli/Projeto01/blob/main/assets/imagens/matriz%20de%20confus%C3%A3o.png" alt = "matriz de confusão"  width = "400px" height="400px" >
<!-- ![colocar imagem exemplo](https://github.com/2023M6T4-Inteli/Projeto01/issues/4#issue-1729946316) -->

Figura 1. Exemplo de Matriz de confusão.


A matriz de confusão é uma tabela que apresenta o desempenho de um modelo, que classifica os elementos pela modelagem preditiva. Os resultados da predição são colocados em diferentes quadrantes. Na diagonal principal  estão os valores corretamente preditos. Fora dessa diagonal se encontram os erros cometidos.


## Resultados
[Texto introdutório sobre os resultados]

### NaiveBayes com Bag of Words (${\color{blue}NB - BoW}$)

- Matriz de confusão:

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/985374b8-8793-436c-a488-95a67c7dc01d)

Figura 2. Matriz de confusão do modelo NaiveBayes com vetorização do tipo Bag of Words.

Legenda:

| **${\color{lightblue}Positivo}$** 	| ${\color{lightblue}0}$  	|
|---	|---	|
| **${\color{gold}Neutro}$** 	| ${\color{white}1}$ 	|
| **${\color{red}Negativo}$** 	| ${\color{red}2}$ 	|

-Métricas:

| **${\color{blue}Modelo}$** 	| ${\color{blue}NB - BoW}$  |
|---	|---	|
| **${\color{blue}Acurácia}$** 	| **72,3%**	|
| **${\color{blue}Revocação}$** 	| **71,3%**	|

### Naive Bayes com Word2Vec (${\color{blue}NB - W2V}$)
- Matriz de confusão:

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/f258a39a-8056-4cb0-8ebf-87221dc15c5e)

Figura 3. Matriz de confusão do modelo NaiveBayes com vetorização do tipo Word2Vec.

Legenda:

| **${\color{lightblue}Positivo}$** 	| ${\color{lightblue}0}$  	|
|---	|---	|
| **${\color{gold}Neutro}$** 	| ${\color{white}1}$ 	|
| **${\color{red}Negativo}$** 	| ${\color{red}2}$ 	|

-Métricas:

| **${\color{blue}Modelo}$** 	| ${\color{blue}NB - W2V}$  	|
|---	|---	|
| **${\color{blue}Acurácia}$** 	| **45,8%**	|
| **${\color{blue}Revocação}$** 	| **33,2%**	|

### Support Vector Machine com Word2Vec (${\color{Purple}SVM - W2V}$)
- Matriz de confusão: 

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/f51b85cd-289c-47d5-ae8b-fb3561210849)

Figura 4. Matriz de confusão do modelo Support Vector Machine com vetorização do tipo Word2Vec.

Legenda:

| **${\color{lightblue}Positivo}$** 	| ${\color{lightblue}0}$  	|
|---	|---	|
| **${\color{gold}Neutro}$** 	| ${\color{white}1}$ 	|
| **${\color{red}Negativo}$** 	| ${\color{red}2}$ 	|

-Métricas:

| **${\color{Purple}Modelo}$** 	| ${\color{Purple}SVM - W2V}$  	|
|---	|---	|
| **${\color{Purple}Acurácia}$** 	| **47,4%**	|
| **${\color{purple}Revocação}$** 	| **45,4%**	|

### Rede Neural com Transformers (${\color{greenyellow}RN - T}$)
- Matriz de confusão:

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/a113ab4d-0cbc-4374-942b-5a6fcb9cbfa2)

Figura 5. Matriz de confusão do modelo Rede Neural com vetorização do tipo Transformers.

Legenda:

| **${\color{lightblue}Positivo}$** 	| ${\color{lightblue}0}$  	|
|---	|---	|
| **${\color{gold}Neutro}$** 	| ${\color{white}1}$ 	|
| **${\color{red}Negativo}$** 	| ${\color{red}2}$ 	|

-Métricas:

| **${\color{greenyellow}Modelo}$** 	| ${\color{greenyellow}RN - T}$  	|
|---	|---	|
| **${\color{greenyellow}Acurácia}$** 	| **85,4%**|
| **${\color{greenyellow}Revocação}$** 	| **85,5%**	|

Tendo sido apresentados todos os resultados dos modelos utilizados neste projeto, o modelo de Rede Neural com vetorização por Transformers obteve a maior acurácia e revocação, 85.4% e 85.5% respectivamente. A fim de evitar o risco de overfitting, os resultados de treino e teste foram aplicados em um gráfico de curvatura de acurácia (Figura 6), para validar o desempenho desse modelo, para avaliar se o modelo está conseguindo generalizar a sua predição, e não apenas memorizando os dados de treino.

Este gráfico permite a visualização do desempenho do modelo à medida que o tamanho do conjunto de treinamento aumenta, em épocas (cada unidade de época representa a passagem do modelo em todo o conjunto de treinamento).

![Gráfico_Curvatura_RN_T](https://github.com/2023M6T4-Inteli/Projeto01/assets/99538889/5270c0d9-4867-4e5b-81e3-d66c442dadc2)

Figura 6. Gráfico de Curvatura do Modelo de Rede Neural com Vetorização do tipo Transformers.

Com base no gráfico, é visível que conforme o modelo passa por todo o conjunto de dados repetidamente, em cada época, a acurácia do treinamento aumenta rapidamente (curva azul), em relação à acurácia nos dados de teste (curva vermelha), que também apresenta um crescimento, porém mais discreto. 
Ao final de 20 épocas, a linha de treino (azul) chega a 100% de acurácia. Já a linha de teste (vermelha) atinge um valor de 85% de acurácia, aproximadamente, entre 12 e 13 épocas, enquanto a linha de treino (azul) ainda está com 95% de acurácia, aproximadamente.

Por estar com uma média de 10% a mais na acurácia de treinamento, em relação à acurácia do teste, 95% e 85%, respectivamente, entre a época 12 e 13, o gráfico indica que não há um condicionamento por overfitting expressivo no modelo, mantendo um grau de generalização relevante, se as épocas forem limitadas neste valor.

## Conclusão
Com os resultados obtidos, os modelos serão confrontados a partir dos valores de acurácia e revocação, bem como foi destacado na definição de escolha dos critérios. Também serão levantados possíveis pontos fortes e limitações dos modelos e também do tipo de vetorização utilizada pelos mesmos.

A começar pelo modelo Naive Bayes, que apresentou uma acurácia muito maior utilizando a vetorização de Bag of Words que Word2Vec, 72,3% e 45,8% respectivamente, e uma diferença ainda maior levando em conta a revocação do modelo utilizando Bag of Words em comparação ao que utilizou o Word2Vec, 71,3% e 33,2% respectivamente, levanta algumas hipóteses. O modelo Naive Bayes, é um modelo de aprendizado de máquina relativamente simples, baseado no teorema de Bayes, e na suposição de independência condicional entre os atributos. Isso torna o modelo mais rápido de treinar, em relação a modelos mais complexos, como os de redes neurais por exemplo. Tendo isso em mente, ao analisar os resultados que utilizaram diferentes tipos de vetorização, pelo Naive Bayes ser baseado na suposição de independência condicional entre os atributos, no caso deste projeto, assumindo que as palavras no texto são independentes umas das outras, essa suposição pode ser mais adequada em cenários onde a relação semântica e contextual não são tão importantes.

A vetorização em Word2Vec captura essas relações semânticas entre as palavras, considerando a ordem e o contexto, diferente da vetorização em Bag of Words, que considera apenas a frequência em que as palavras ocorrem na base de dados do vocabulário criado. Isso pode justificar uma melhor performance da modelagem do Naive Bayes utilizando a vetorização em Bag of Words que o Word2Vec.

O modelo SVM apresentou uma acurácia e revocação de aproximadamente 45%, com a vetorização em Word2Vec, e apesar de ter hiperparâmetros ajustados com grid search, esse resultado indica que o modelo não conseguiu traçar um hiperplano eficaz para classificar os elementos do banco de dados, sugerindo que este modelo não conseguiu capturar as complexas relações semânticas da vetorização, tornando este um modelo ineficaz para análise de sentimentos deste banco de dados específico.

### Comparação entre os modelos
| **${\color{gold}Modelo}$** 	| ${\color{blue}NB - BoW}$  | ${\color{blue}NB - W2V}$  | ${\color{purple}SVM - W2V}$  	|  ${\color{greenyellow}RN - T}$  	| 
|---	|---	|---  |---  |---	|
| **${\color{gold}Acurácia}$** 	| **72,3%**| **45,8%**| **47,4%**| **85,4%**|
| **${\color{Gold}Revocação}$** 	| **71,3%**	| **33,2%**| **45,4%**| **85,5%**|

<!-- ![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/bb1c5e00-5624-4854-89e9-765e9c0671f2) -->


<!-- [Talvez não precise mostrar o resultado de sprint anterior, apenas se for usado pra reforçar na conclusão a escolha do modelo:]
- Matriz de confusão da Rede Neural com Word2Vec: 

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/66ff0ebc-523e-4cdf-86fa-b7354d529e2f)
 -->
# Modelo escolhido :

### Critérios para escolha do modelo de modelagem preditiva
É importante definir os critérios para a escolha do modelo mais adequado ao problema proposto neste projeto, e para isso, é necessário considerar o valor mais relevante das métricas utilizadas, ressaltando que a métrica mais relevante pode variar, de acordo com a classe mais importante a ser classificada de forma correta, levando em conta qual tipo de erro da predição pode ser mais prejudicial ao usuário que irá utilizar a solução desenvolvida neste projeto.

Dentre as três classes de categorias de sentimentos, Positivo, Neutro e Negativo, o sentimento mais importante de ser identificado de forma correta é o Negativo, pelo impacto que elementos dessa classe podem apresentar ao usuário do sistema desenvolvido. Sendo assim, o erro mais crítico é o de Falsos Negativos, que podem passar desapercebidos como sendo de outras classes, enquanto é na verdade da classe Negativo.

Analisar este cenário, é desejável utilizar o modelo que apresenta um alto índice de revocação, ou seja, que mais corretamente identificam elementos como sendo da classe Negativo, reduzindo assim o número de Falsos Negativos. Sendo essa a principal métrica de avaliação para o critério de escolha do modelo com base nos resultados obtidos.

Também é importante destacar que, ao confrontar os resultados dos modelos, seja levado em consideração o modelo com acurácia mais alta, além da revocação, e o tipo de vetorização que o modelo melhor se desempenhou. A combinação desses critérios indicará o modelo mais adequado para o projeto.

## Referências

https://www.inf.ufpr.br/dagoncalves/IA07.pdf

[https://medium.com/turing-talks/turing-talks-12-classificação-por-svm-f4598094a3f1](https://medium.com/turing-talks/turing-talks-12-classifica%C3%A7%C3%A3o-por-svm-f4598094a3f1)
