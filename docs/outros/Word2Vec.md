# Modelagem para processamento de Linguagem Natural usando Word2Vec

O Word2Vec é uma técnica poderosa que utiliza entradas de texto para treinar modelos e obter vetores de representação, abrangendo desde frases até parágrafos. Essa abordagem é altamente eficaz para o processamento de linguagem natural e classificação de texto. Neste trabalho, aplicamos um modelo Word2Vec pré-treinado à nossa base de dados, utilizando tanto a abordagem Bag of Words quanto um modelo com camada de incorporação (embedding layer).

Além disso, realizamos a comparação de dois modelos de classificação: Naive Bayes e Rede Neural. Os resultados foram avaliados por meio de métricas como matriz de confusão e acurácia. Ao final deste documento, apresentaremos uma discussão detalhada sobre os resultados obtidos.

## Modelo Word2Vec pré-treinado
O Word2Vec é um algoritmo de Machine Learning amplamente utilizado em processamento de linguagem natural para gerar representações vetoriais de palavras e capturar relações semânticas. Esse modelo mapeia palavras em vetores de tal forma que palavras semanticamente similares são posicionadas próximas umas das outras.

A fim de obter representações vetoriais de palavras mais precisas, optamos por utilizar um modelo Word2Vec pré-treinado. Através de um treinamento extensivo em grandes conjuntos de dados, o modelo é capaz de capturar relações semânticas com base nas ocorrências e contextos das palavras dentro do corpus de treinamento. Isso resulta em um conhecimento prévio rico e maior precisão nas aplicações de Processamento de Linguagem Natural (PLN).

## Modelo Word2Vec com Skipgram

Escolhemos testar o Modelo Word2Vec com SkipGram porque ele tem a capacidade de capturar relacionamentos contextuais entre palavras em um texto. Ele pode aprender a representar palavras com base em seu contexto, permitindo que palavras semanticamente e sintaticamente relacionadas sejam mapeadas para pontos próximos no espaço vetorial.

 A ideia do Skipgram é treinar uma rede neural para aprender vetores de palavras, onde cada palavra é representada por um vetor denso de valores reais. O tamanho desses vetores é conhecido como dimensão de embedding e é um hiperparâmetro definido pelo usuário.O objetivo é encontrar os melhores vetores de palavras que capturem as relações semânticas e sintáticas presentes no corpus de treinamento. 


### Método escolhido
O Método escolhido foi o Continuos Bag of Words (CBOW) por ter como objetivo a previsão de uma palavra alvo com base em seu contexto.Diferente do método Skip-gram, que prevê o contexto a partir de uma palavra-alvo, o CBOW considera múltiplas palavras em um contexto específico para fazer a previsão da palavra de destino.

Geralmente, ele produz representações vetoriais mais densas e, por lidar com as palavras mais frequentes, é capaz de evitar seus ruídos e garantir seus contextos. Além disso, por possuirmos um conjunto de dados de treinamento pequeno, o modelo CBOW é mais favorável e eficiente para capturar as informações contextuais mais próximas. 

### Construção e execução do modelo
Para o nosso modelo, utilizamos um modelo pré-treinado disponibilizado pelo Núcleo Interinstitucional de Linguística Computacional, que já possuía um modelo treinado com palavras em português. Esse modelo pré-treinado foi considerado o mais adequado para ser aplicado à nossa base de dados, uma vez que ela também está em português.

Para construir o nosso modelo, passamos todos os textos do dataframe por um processo de pré-processamento. Em seguida, utilizamos o modelo pré-treinado para gerar vetores para cada palavra presente nas frases do dataset. Dessa forma, obtemos um vetor para cada palavra nas frases.

Por fim, realizamos a soma desses vetores, o que nos permite gerar um vetor representativo para cada frase inserida no modelo.

### Resultados obtidos
Com a utilização desse modelo, foi possível obter a vetorização das palavras presentes nos comentários analisados, bem como a soma vetorial de palavras que possuem certa similaridade semântica. A utilização desse modelo no contexto de análise de sentimento pode trazer inúmeros benefícios e pretendemos explorá-los no decorrer da sprint 4. Dentre eles, é possível evidenciar a melhoria na representação de palavras, uma vez que esse modelo pode fornecer representações vetoriais mais ricas para as palavras, o que ajuda a capturar nuances e sutilezas nos sentimentos expressos por elas.
A inicialização eficaz desse modelo foi fundamental para a construção dos modelos de aprendizado de máquina que foram desenvolvidos nesse período, tendo em vista que foram capazes de fornecer uma compreensão prévia das associações emocionais entre as palavras.

## Modelo Word2Vec utilizando Embedding Layer
O método Embedding Layer é utilizado para a representação vetorial de dados categóricos. Ao ser utilizado em conjunto, ele traz diversos benefícios, como lidar com a dimensionalidade variável dos dados, convertendo palavras de um vocabulário maior em vetores densos de comprimento fixo, que são menores do que os vetores de entrada. Isso facilita o processamento e a análise dos dados.

Além disso, essa combinação melhora a generalização para palavras não vistas durante o treinamento. O modelo aprende a extrair informações contextuais e considerar as relações entre as palavras, o que permite inserir palavras ausentes no conjunto de treinamento com base em palavras semanticamente similares (Qi et al. 2018).

Dessa forma, mesmo palavras que não estão presentes no conjunto de treinamento podem ser representadas e utilizadas com base em palavras semelhantes, o que enriquece o modelo e sua capacidade de processar dados de linguagem natural.

### Método escolhido

O vetor de embedding tem diversas aplicações, dependendo de como o Word2Vec é treinado e das camadas aprendidas.

O Word2Vec é treinado para prever palavras e seu contexto em relação a outras palavras, como afirmado por John Rupert Firth: 'Você conhecerá uma palavra pela sua companheira'. Dessa forma, o Word2Vec aprende os conjuntos em que as palavras podem aparecer, utilizando a similaridade entre os vetores.

No caso de embeddings aprendidos, o modelo pode ser treinado para prever sentimentos com base nas palavras utilizadas nas frases, identificando palavras frequentemente presentes em frases positivas ou mais comuns em frases negativas.

Ao realizar o pré-processamento dos dados e a tokenização, é possível criar um vocabulário que mapeia cada palavra única, possibilitando o treinamento de um modelo Word2Vec com camadas de embedding. Isso resulta em um DataFrame com os vetores das palavras, permitindo a exibição de palavras por similaridade. Essa representação vetorial das palavras e a identificação de palavras similares criam relações semânticas e contextuais entre elas.

### Construção e execução do modelo

O raciocínio por trás do modelo Word2Vec baseia-se na ideia de que palavras com significados semelhantes aparecem em contextos semelhantes. O modelo aprende representações vetoriais (embeddings) para cada palavra, de modo que palavras semanticamente relacionadas fiquem próximas umas das outras no espaço vetorial.

Para treinar o modelo, normalmente é utilizado um grande corpus de texto. O algoritmo Word2Vec utiliza duas abordagens principais: o Skip-gram e o Continuous Bag of Words (CBOW).

No método Skip-gram, o objetivo é prever as palavras de contexto (as palavras ao redor de uma palavra-alvo) com base na palavra-alvo. Já no método CBOW, o objetivo é prever a palavra-alvo com base nas palavras de contexto. O modelo ajusta os pesos das conexões entre as palavras, de forma a maximizar a probabilidade de prever corretamente as palavras de contexto.

Uma vez treinado, o modelo Word2Vec produz vetores densos para cada palavra. Esses vetores podem ser usados para várias tarefas de processamento de linguagem natural, como classificação de sentimentos, agrupamento de documentos, identificação de tópicos, entre outros. Além disso, os vetores podem ser utilizados para calcular similaridade entre palavras, permitindo a realização de buscas semânticas e identificação de relações entre termos.

### Resultados obtidos
A construção desse modelo permitiu a obtenção de uma acurácia de 0.65 a partir de um treinamento realizado 50 vezes (definido pelo número de epochs do modelo). O números de epochs foi ajustado durante o treinamento para encontrar um equilíbrio entre o desempenho do modelo e o tempo de treinamento. 
Com essa abordagem, as palavras são representadas por vetores densos, capturando relações semânticas e sintáticas. Isso melhora a compreensão do significado e contexto das palavras. Os benefícios incluem a capacidade de calcular a similaridade entre palavras, agrupar palavras relacionadas, analisar sentimentos e recomendar palavras relacionadas. Além disso, esses vetores podem ser aplicados em tradução automática para melhorar a fluência das traduções.

## Modelos de Classificação 
Os modelos de classificação são amplamente utilizados no Processamento de Linguagem Natural (PLN) para categorizar textos em diferentes classes ou rótulos. Nesse sentido, utilizamos duas abordagens: redes neurais e o algoritmo Naive Bayes.

### Rede Neural

O modelo de rede neural é uma abordagem de aprendizado de máquina inspirada no funcionamento do cérebro humano. Ele é composto por vários neurônios que trabalham em conjunto para resolver um determinado problema.

Cada neurônio recebe um conjunto de entradas que são multiplicadas pelos seus pesos associados, e são esses pesos que determinam a importância de cada entrada para a saída do neurônio.

O treinamento desse modelo envolve a estimativa dos pesos dos neurônios com base no conjunto de dados de treinamento. Sua maior vantagem é a capacidade de aprender automaticamente a partir dos dados, sem necessidade de projeção manual. Além disso, ele lida de forma eficiente com dados complexos e de alta dimensionalidade.

Na atual sprint, desenvolvemos uma rede neural que incorpora uma camada de embedding utilizando o Word2Vec. Essa camada de embedding mapeia as palavras para vetores densos, capturando relações semânticas e o contexto das palavras dentro das frases.

As redes neurais são capazes de aprender representações complexas e não lineares a partir dos dados de treinamento, capturando as palavras e suas relações semânticas, o que justifica a sua aplicação neste projeto. Diferente do Naive Bayes, que depende de suposições prévias, as redes neurais possuem facilidade em aprender automaticamente, tornando também o processamento mais lento e complexo.

### Naive Bayes

O modelo Naive Bayes é um classificador que utiliza o Teorema de Bayes para calcular probabilidades. Ele assume a independência condicional entre os recursos (palavras) dadas as classes (sentimentos positivo, negativo ou neutro). Nesta sprint, aplicamos o modelo Naive Bayes utilizando a abordagem Bag of Words (BoW) para classificar os comentários.

A escolha do modelo Naive Bayes com BoW é baseada na natureza estatística do Naive Bayes, que se encaixa bem no uso de BoW para capturar a recorrência das palavras nos comentários.

O modelo Naive Bayes utiliza o conjunto de recursos construído para calcular as probabilidades condicionais de um comentário pertencer a cada uma das categorias de sentimento (positivo, negativo ou neutro). Com base nessas probabilidades, o modelo atribui uma classe ao comentário.

A aplicação do Naive Bayes se justifica pela capacidade do modelo em lidar com grandes conjuntos de dados, por ser um modelo mais simples e requerer menos recursos de processamento, comportando tanto a abordagem de Bag of Words, quanto o Word2Vec, facilitando a escalabilidade do algoritmo com inputs diferentes, em comparação a classificadores mais complexos, como as redes neurais.

## Métricas utilizadas para avaliação dos resultados

As métricas de avaliação são fundamentais para comparar a performance e o desempenho dos modelos utilizados. Nesse contexto, após obter os resultados dos modelos, foi gerada uma matriz de confusão para avaliar o desempenho (Franceschi, 2019).

A matriz de confusão é uma tabela que apresenta o desempenho de um modelo de classificação, dividindo as previsões em quatro categorias, como demonstrado a seguir:

<img src=  "https://github.com/2023M6T4-Inteli/Projeto01/blob/main/assets/imagens/matriz%20de%20confus%C3%A3o.png" alt = "matriz de confusão"  >

A acurácia é uma métrica simples que calcula a proporção de acertos do modelo, representada pela soma dos verdadeiros positivos e verdadeiros negativos, dividida pelo total de elementos utilizados na predição (verdadeiros positivos, verdadeiros negativos, falsos positivos e falsos negativos). No entanto, é importante destacar que a acurácia sozinha não é suficiente para avaliar completamente o desempenho dos modelos, pois não considera a distribuição das classes ou possíveis desequilíbrios no conjunto de dados (Chen, et al, 2020).

$$
\begin{align}
Acurácia={Verdadeiros Positivos \over Total}
\end{align}
$$

## Resultados obtidos

Matriz Rede Neural - Word2Vec
| **883** 	| 628 	|
|---	|---	|
| **451** 	| 1113 	|

Dentre os três modelos utilizados - Naive Bayes com Bag of Words (BoW), Naive Bayes com Word2Vec e Rede Neural com Word2Vec -, apresentamos a seguir os resultados obtidos em cada um deles.
O modelo Naive Bayes com Word2Vec obteve uma acurácia de 0.44, enquanto o modelo Naive Bayes com BoW alcançou uma acurácia de 0.71.

Por fim, a Rede Neural com Word2Vec obteve uma acurácia de 0.63. Ao treinar a rede neural com a camada de embedding do Word2Vec, foi possível alcançar uma acurácia de 71% nos dados de teste após 30 épocas de treinamento, utilizando 50 camadas de entrada, 26 camadas ocultas e uma camada de saída.
Essas informações fornecem uma visão geral dos resultados obtidos em cada modelo, permitindo uma comparação direta entre suas performances.

Comparação entre os desenvolvidos modelos:
<img src=  "https://github.com/2023M6T4-Inteli/Projeto01/blob/main/assets/imagens/comparacaoModelo.png" alt = "matriz de confusão">

## Comparação com o modelo de Bag of Words (BoW)

Ambos os modelos de Bag of Words e Word2Vec são técnicas utilizadas no processamento de linguagem natural, porém, seus funcionamentos são bastante distintos. O modelo Bag of Words é uma abordagem que converte cada palavra das frases em um vocabulário específico, e as sentenças recebidas são classificadas com base na presença ou ausência das palavras, resultando em uma matriz binária que representa a ocorrência das palavras considerando suas frequências. Por outro lado, o modelo Word2Vec utiliza vetores para representar as palavras, levando em consideração o contexto em que cada palavra é utilizada, além de atribuir pesos com base em palavras vizinhas.

Em geral, o uso de vetores de incorporação semântica, como no caso do Word2Vec, tende a resultar em maior precisão nos resultados de modelagem. Isso se deve, em parte, ao fato de o Word2Vec ser pré-treinado e ter acesso a uma base de dados mais extensa do que o modelo Bag of Words (Feng & Thuremella, 2018).

Também é importante ressaltar que o modelo Bag of Words é mais simples e eficiente, pois requer apenas informações sobre a frequência das palavras. No entanto, devido à sua natureza de não considerar a ordem ou contexto das palavras, ele pode não ser tão preciso. Além disso, quando lidando com bancos de dados muito grandes, o modelo Bag of Words pode gerar um vocabulário extenso que demanda um processamento significativo para produzir resultados.

Em contrapartida, o  modelo Word2Vec, ao considerar a semântica e o contexto das palavras, tem maior facilidade em identificar palavras similares e estabelecer relações de analogia. Isso resulta em uma redução na dimensionalidade das representações das palavras em seu espaço vetorial, em comparação com o modelo Bag of Words. No entanto, por ser um modelo mais complexo, o Word2Vec requer mais poder de processamento e pode enfrentar dificuldades ao lidar com palavras que aparecem em poucas ocasiões.

## Conclusão 
O modelo obteve sucesso ao fornecer os vetores correspondentes a cada frase inserida. Utilizou-se um modelo CBOW 50 pré-treinado, resultando em um vetor de 50 dimensões para cada frase.

Esses vetores gerados permitem medir a similaridade entre as frases, sendo possível utilizá-los como entrada de treinamento para modelos de classificação, como Naive Bayes e redes neurais, visando a classificação dos comentários.

A inclusão da camada de embedding Word2Vec proporcionou ao modelo a capacidade de capturar nuances semânticas e melhorar a representação das palavras presentes nos comentários do Instagram do BTG. Essa abordagem contribuiu para o aprimoramento do desempenho do modelo, em comparação com o uso do modelo Naive Bayes com BoW, evidenciando o potencial das técnicas de processamento de linguagem natural empregadas nesta etapa do projeto.

É importante destacar que outras métricas para avaliação que usam os valores obtidos na matriz de confusão, como precisão e revocação, também são importantes, pois a acurácia pode não apresentar o real desempenho, por si só, dos resultados obtidos pelos modelos.

Também é importante otimizar e ajustar os modelos de classificação utilizados, adicionando hiperparâmetros e separando também dados de treinamento e teste específicos para os modelos, evitando tornar os modelos enviesados, por exemplo, ou apresentando overfitting.

## Referencias:
http://nilc.icmc.usp.br/nilc/index.php/repositorio-de-word-embeddings-do-nilc

CHEN, D., NIGRI, E., OLIVEIRA, G.,SEPULVENE, L., ALVES, T.: Métricas de Avaliação em Machine Learning: Classificação - Kunumi Blog, medium, 2020.

FRANCESCHI, P, R.: Modelagens Preditivas de Churn: O Caso do Banco do Brasil, Universidade do Vale do Rio dos Sinos, 2019.

Qi, Y., Sachan, D. S., Feliz, M., Padmanabhan, S. J., Neubig, G., When and Why are Pre-trained Word Embeddings Useful for Neural Machine Translation?, Language Technologies Institute, Carnegie Mellon University, 2018.

Feng, B., Thuremella, D., A Tale of Two Encodings: Comparing Bag-of-Words and Word2vec for VQA, Princeton University, 2018.


