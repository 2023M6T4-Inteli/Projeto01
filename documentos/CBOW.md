# Modelo Word2Vec

## Word2Vec
O modelo word2Vec é um algoritmo de Machine Learning utilizado em linguagem natural para gerar representações vetoriais de palavras e capturar relações semânticas. Esse modelo mapeia palavras em vetores, de forma que as palavras semanticamente similares fiquem próximas umas das outras.
Para uma melhor obtenção e precisão de representações vetoriais de palavras, optamos por utilizar o modelo Word2vec pré-treinado. 
A partir de um treinamento extensivo, o modelo captura relações semânticas com base em suas ocorrências e contextos dentro de um corpus de treinamento. Isso permite um melhor desempenho no conhecimento prévio adquirido e um aumento da precisão das aplicações em PLN. 

## Metodo escolhido
O Método escolhido foi o CBOW por ter como objetivo a previsão de uma palavra alvo com base em seu contexto. Ele considera várias palavras para combiná-las e assim, faz a previsão de uma única palavra de destino.
Geralmente, ele produz representações vetoriais mais densas e por lidar com as palavras mais frequentes, é capaz de evitar seus ruídos e garantir seus contextos.
Por possuirmos relativamente um conjunto de dados de treinamento pequeno, o modelo CBOW é mais favorável e eficiente para capturar as informações contextuais mais próximas. 
