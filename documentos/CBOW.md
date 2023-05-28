

# Modelos utilizados para processamento de Linguagem Natural

[Escrever texto introdutório sobre o uso de dois modelos Word2Vec pré-treinado e com embedding layer]

## Modelo Word2Vec

O modelo word2Vec é um algoritmo de Machine Learning utilizado em linguagem natural para gerar representações vetoriais de palavras e capturar relações semânticas. Esse modelo mapeia palavras em vetores, de forma que as palavras semanticamente similares fiquem próximas umas das outras.
Para uma melhor obtenção e precisão de representações vetoriais de palavras, optamos por utilizar o modelo Word2vec pré-treinado. 
A partir de um treinamento extensivo, o modelo captura relações semânticas com base em suas ocorrências e contextos dentro de um corpus de treinamento. Isso permite um melhor desempenho no conhecimento prévio adquirido e um aumento da precisão das aplicações em PLN. 

### Método escolhido
O Método escolhido foi o CBOW por ter como objetivo a previsão de uma palavra alvo com base em seu contexto. Ele considera várias palavras para combiná-las e assim, faz a previsão de uma única palavra de destino.
Geralmente, ele produz representações vetoriais mais densas e por lidar com as palavras mais frequentes, é capaz de evitar seus ruídos e garantir seus contextos.
Por possuirmos relativamente um conjunto de dados de treinamento pequeno, o modelo CBOW é mais favorável e eficiente para capturar as informações contextuais mais próximas. 

### Construção e execução do modelo
Para o nosso modelo, utilizamos um modelo pré treinado retirado do Núcleo Interinstitucional de Linguística Computacional, pois eles já possuíam um modelo treinado com palavras em português, sendo assim, o mais adequado a ser aplicado à nossa base de dados, que está em portugues também.

Para construção do modelo, primeiramente passamos todos os textos do nosso dataframe por nossa pipeline de processamento. Para cada frase no dataset foi utilizado nosso modelo pré treinado para gerar os vetores das palavras presente nas frases do dataset, sendo gerado um vetor para cada palavra das frases.

E por fim, foi realizado a soma desses vetores, gerando um vetor referente a cada frase inserida no modelo

## Modelo Word2Vec utilizando Embedding Layer

O método Embedding Layer é utilizado para a representação vetorial em dados categóricos. Esse uso em conjunto traz alguns benefícios como lidar com a dimensionalidade variável dos dados, convertendo palavras de um vocabulário maior em vetores densos de comprimento fixo, menores que os vetores de entrada, o que facilita o processamento e análise. Além disso, essa combinação melhora a generalização para palavras não vistas durante o treinamento, pois o modelo aprende a extrair informações contextuais e considerar as relações entre as palavras. Dessa forma, mesmo palavras ausentes no conjunto de treinamento podem ser inseridas com base em palavras semanticamente similares (Qi, et al, 2018).


### Método escolhido

O vetor de embedding pode ser utilizado para diversas finalidades, a depender de como o Word2vec é treinado e com as camadas aprendidas. 

O Word2vec é treinado para predição de palavras e o seu contexto, em comparação às outras palavras, como dito por John Rpert Firth, "Você conhecerá uma palavra pela sua companheira". Assim o Word2Vec aprende o conjunto em que a palavra pode aparecer, usando a similaridade entre os vetores.

No caso de embeddings aprendidos, o modelo pode ser treinado para prever sentimentos, com base nas palavras utilizadas nas frases, como palavras que frequentemente aparecem em frases positivas, ou mais comuns em frases negativas.

Considerando os tratamentos realizados no pré-processamento dos dados e a tokenização, é possível criar um vocabulário mapeando cada palavra única, dando sequência para o treinamento de um modelo Word2Vec com embedding layers. Com isso, um DataFrame com os vetores das palavras é feito, e é possível exibr as palavras por similaridade, importante para a representação vetorial das palavras e palavras similares, e criando a relação semântica e contextual entre as palavras.


## Modelos de Classificação 
Os modelos de classificação são amplamente utilizados em PLN para categorizar textos em diferentes classes ou rótulos e diante disso, utilizamos duas abordagens: o uso de redes neurais e o algoritmo Naive Bayes.

### Rede Neural

O modelo de rede neural é uma abordagem de machine learning inspirada no funcionamento do cérebro humano. Ele é composto por vários neurônios que em conjunto, conseguem resolver determinado problema.
Cada neurônio recebe um conjunto de entradas que são multiplicadas por seus pesos associados, e são esses pesos que determinam a importância de cada entrada para cada saída do neurônio.

O treinamento desse modelo envolve a estimativa dos pesos dos neurônios com base no conjunto de dados de treinamento e sua maior vantagem é além de ter a capacidade de aprender automaticamente a partir dos dados sem projeção manual, ele lida com dados complexos e de alta dimensionalidade.

Na sprint atual, fizemos uma rede neural que incorpora uma camada de embedding utilizando o Word2Vec. A camada de embedding mapeia as palavras para vetores densos, capturando relações semânticas e o contexto da palavra dentro da frase.
Ao treinar a rede neural com a camada de embedding do Word2Vec, obtivemos os seguintes resultados. Alcançamos uma acurácia de 71% nos dados de teste após 30 épocas de treinamento com 50 camadas de entrada, 26 camadas oculta e uma camada de saída.
A utilização da camada de embedding Word2Vec proporcionou ao modelo a capacidade de capturar nuances semânticas e melhorar a representação das palavras nos comentários do Instagram do BTG. Essa abordagem ajudou a melhorar o desempenho do modelo em comparação com o uso do modelo Naive Bayes com BoW, demonstrando o potencial das técnicas de processamento de linguagem natural utilizadas nesta sprint.

[método escolhido para aplicar modelo]

[explicações com linha de raciocínio de aplicação]

[justificativa para uso de Rede Neural]

### Naive Bayes


O modelo Naive Bayes é um classificador que utiliza a probabilidade do Teorema de Bayes, que assume a independência condicional entre os recursos (palavras) dada a classe (sentimento positivo, negativo ou neutro). Nesta sprint, aplicamos o modelo Naive Bayes utilizando o Bag of Words (BoW) para classificar os comentários.

A escolha do modelo Naive Bayes com BoW é fundamentada na natureza estatística do Naive Bayes, no qual se enquadra bem o uso de BoW para mostrar a recorrência das palavras nos comentários. 

O modelo Naive Bayes, então, utiliza o conjunto de recursos construído para calcular as probabilidades condicionais de um comentário pertencer a cada uma das categorias de sentimento (positivo, negativo ou neutro). Com base nessas probabilidades, o modelo atribui uma classe ao comentário.

[método escolhido para aplicar modelo]

[explicações com linha de raciocínio de aplicação]

[justificativa para uso do Naive bayes]

## Métricas utilizadas para avaliação dos resultados

Para avaliar os modelos e comparar sua performance e desempenho, foram utilizadas duas métricas a partir dos resultados obtidos: Acurácia e a aplicação de uma matriz de confusão.
Um exemplo de matriz de confusão pode ser visto a seguir:
[imagem]
Após a classificação dos elementos pela modelagem preditiva, os resultados da predição são colocados em quatro diferentes quadrantes. Na diagonal principal (em azul escuro) estão os valores corretamente preditos, com Verdadeiros Positivos (VP) e Verdadeiros Negativos (VN). Fora dessa diagonal se encontram os erros cometidos, os Falsos Positivos (FN) e Falsos Negativos(FN) (Franceschi, 2019).

E a partir dos valores obtidos nos quadrantes, outras métricas podem ser extraídas, como a acurácia, com a seguinte fórmula:
[imegem]
A acurácia é uma métrica simples que utiliza a razão entre todos os acertos do modelo (Verdadeiros Positivos e Verdadeiros Negativos) sobre a quantidade total de elementos usados na predição, ou seja, VP somado com VN, FP e FN. E como a fórmula não utiliza um peso aplicado, é importante ressaltar que apenas utilizando a acurácia não é possível avaliar o desempenho dos modelos (Chen, et al, 2020).

## Resultados obtidos

Desse três modelos: Naive Bayes utilizando Bag of Words (BoW), Naive Bayes com Word2Vec e uma Rede Neural com Word2Vec.

Os resultados foram os seguintes: o modelo Naive Bayes com Word2Vec obteve uma acurácia de 0.44. O modelo Naive Bayes com BoW, por sua vez, atingiu uma acurácia de 0.65. Por fim, a Rede Neural com Word2Vec alcançou uma acurácia de 0.63.
[Colocar resultados de acuaracia e matriz de confusao]

## Comparação com o modelo de Bag of Words (BoW)

Ambos os modelos de Bag of Words e Word2Vec são tecnicas para processamento de linguagem natural, mas o seu funcionamento é muito diferente. O modelo Bag of Words é uma técnica que converte cada palavra das frases em seu imput em um vocabulário, e as sentenças recebidas recebem uma classificação, caso a palavra apareça ou não, gerando uma matriz binária da ocorrência das palavras considerando a frequência das palavras. Já o modelo Word2Vec faz uso de vetores, considerando também um peso para as palavras, de acordo com palavras vizinhas desta, levando em conta assim o contexto em que a palavra foi utilizada.

Em geral, vetores de incorporação semântica levam a uma maior precisão nos resultados das modelagens. Isso também se deve pelo modelo Word2Vec ser pré-treinado, tendo acesso a uma base de dados maior do que o utilizado no modelo Bag of Words (Feng & Thuremella, 2018).

Também é importante ressaltar que o modelo Bag of Words é mais simples e por necessitar apenas da frequência das palavras, é mais eficiente. Mas por não considerar a ordem ou contexto das palavras, não possui tanta precisão, e quando o banco de dados é muito grande, ele gera um vocabulário que requer um processamento relevante para gerar seus resultados.

Em relação ao modelo Word2Vec, por considerar a semântica e o contexto, ele identifica mais facilmente palavras similares e analogias, reduzindo assim a dimensionalidade das representações das palavras no seu espaço vetorial, em comparação ao modelo Bag of Words.
Mas por ser um modelo mais complexo, necessita de um poder de processamento relevante, e tem dificuldade de lidar com palavras que aparecem poucas vezes.

[Apresentar resultados sprint anterior]

[comparar resultados sprint anterior com essa sprint]


## Conclusão 
O modelo conseguiu fornecer com sucesso os vetores referentes a cada frase inserida no modelo. Como foi utilizado um modelo CBOW 50, como modelo pré-treinado, o output do modelo também foi um vetor de 50 dimensões para cada frase inserida nele.

Sendo assim, este vetor é gerado. Além de ser possível medir a similaridade entre as frases, com auxílio de um modelo de classificação, como Naive Bayes, e redes neurais, esses vetores podem ser utilizados como input de treinamento para o modelo, e para a classificação dos comentários.

[Colocar mais conclusao também as analises do cliente na apresentação]

## Referencias:
http://nilc.icmc.usp.br/nilc/index.php/repositorio-de-word-embeddings-do-nilc

CHEN, D., NIGRI, E., OLIVEIRA, G.,SEPULVENE, L., ALVES, T.: Métricas de Avaliação em Machine Learning: Classificação - Kunumi Blog, medium, 2020.

FRANCESCHI, P, R.: Modelagens Preditivas de Churn: O Caso do Banco do Brasil, Universidade do Vale do Rio dos Sinos, 2019.

Qi, Y., Sachan, D. S., Feliz, M., Padmanabhan, S. J., Neubig, G., When and Why asre Pre-trained Word Embeddings Useful for Neural Machine Translation?, Language Technologies Institute, Carnegie Mellon University, 2018.

Feng, B., Thuremella, D., A Tale of Two Encodings: Comparing Bag-of-Words and Word2vec for VQA, Princeton University, 2018.
