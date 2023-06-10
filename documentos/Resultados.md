# Comparação de resultados e escolha do melhor modelo

## Metricas

- Acúracia
  - A acurácia é uma métrica simples que utiliza a razão entre todos os acertos do modelo (Verdadeiros Positivos e Verdadeiros Negativos) sobre a quantidade total de elementos usados na predição, ou seja, VP somado com VN, FP e FN.

  ![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/a137bb75-f2af-4fc6-bad8-696d75bd671d)
  
- Revocação
  - A revocação  é uma métrica que avalia a capacidade de um modelo em identificar corretamente os exemplos positivos em relação ao total de exemplos positivos presentes nos dados,
ela é calculada dividindo o número de verdadeiros positivos (VP) pela soma dos verdadeiros positivos (VP) com os falsos negativos (FN). 
- matriz de confusão

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/dfdf8dad-37ee-4de4-bef2-7dd8fcc5245c)

  - Após a classificação dos elementos pela modelagem preditiva, os resultados da predição são colocados em diferentes quadrantes. Na diagonal principal  estão os valores corretamente preditos. Fora dessa diagonal se encontram os erros cometidos.

## Resultados dos modelos

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/bb1c5e00-5624-4854-89e9-765e9c0671f2)


## Matrizes de confusão

- Matriz de confusão do NaiveBayes com BOW:

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/985374b8-8793-436c-a488-95a67c7dc01d)

- Matriz de confusão do Naive Bayes com Word2Vec:

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/f258a39a-8056-4cb0-8ebf-87221dc15c5e)

- Matriz de confusão da Rede Neural com Word2Vec: 

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/66ff0ebc-523e-4cdf-86fa-b7354d529e2f)

- Matriz de confusão transformers:

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/a113ab4d-0cbc-4374-942b-5a6fcb9cbfa2)

- Matriz de confusão SVM: 

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/f51b85cd-289c-47d5-ae8b-fb3561210849)

# Comparação dos resultados:

# Modelo escholido :
