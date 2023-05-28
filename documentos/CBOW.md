

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

[introduçao falando do udo de rede neural e naive bayes]

### Rede Neural

[Introdução]

[método escolhido para aplicar modelo]

[explicações com linha de raciocínio de aplicação]

[justificativa para uso de Rede Neural]

### Naive Bayes

[Introdução]

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

[Colocar resultados de acuaracia e matriz de confusao]

## Comparação com o modelo de Bag of Words (BoW)

[Diferença entre bag of words e esses modelos dessa sprint (introdução)]

[Apresentar resultados sprint anterior]

[comparar resultados sprint anterior com essa sprint]

[diferença entre os modelos com vantagens e desvantagens]

## Conclusão 
O modelo conseguiu fornecer com sucesso os vetores referentes a cada frase inserida no modelo. Como foi utilizado um modelo CBOW 50, como modelo pré-treinado, o output do modelo também foi um vetor de 50 dimensões para cada frase inserida nele.

Sendo assim, este vetor é gerado. Além de ser possível medir a similaridade entre as frases, com auxílio de um modelo de classificação, como Naive Bayes, e redes neurais, esses vetores podem ser utilizados como input de treinamento para o modelo, e para a classificação dos comentários.

[Colocar mais conclusao também as analises do cliente na apresentação]

## Referencias:
http://nilc.icmc.usp.br/nilc/index.php/repositorio-de-word-embeddings-do-nilc

CHEN, D., NIGRI, E., OLIVEIRA, G.,SEPULVENE, L., ALVES, T.: Métricas de Avaliação em Machine Learning: Classificação - Kunumi Blog, medium, 2020.

FRANCESCHI, P, R.: Modelagens Preditivas de Churn: O Caso do Banco do Brasil, Universidade do Vale do Rio dos Sinos, 2019.

Qi, Y., Sachan, D. S., Feliz, M., Padmanabhan, S. J., Neubig, G., When and Why asre Pre-trained Word Embeddings Useful for Neural Machine Translation?, Language Technologies Institute, Carnegie Mellon University, 2018.
