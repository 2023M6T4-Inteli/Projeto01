

# Modelos utilizados

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

[introdução]

### Método escolhido

[Explicação das etapas e decisões tomadas na construção do modelo]

## Modelo de Classificação Naive Bayes

[Introdução]
[método escolhido para aplicar modelo]
[explicações com linha de raciocínio de aplicação]
[justificativa para uso do Naive bayes]

## Métricas utilizadas para avaliação dos resultados
[acuracia e matriz de confusão]

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

## Referencias:
http://nilc.icmc.usp.br/nilc/index.php/repositorio-de-word-embeddings-do-nilc
