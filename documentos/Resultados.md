# Documentação de proposta de uma nova modelagem

## Introdução
[Texto falando sobre a sprint com os objetivos]

## Metodologia
[introdução às metricas e hiperparametros e como será a escolha do melhor modelo]
### Metricas

- Acúracia
  - A acurácia é uma métrica simples que utiliza a razão entre todos os acertos do modelo (Verdadeiros Positivos e Verdadeiros Negativos) sobre a quantidade total de elementos usados na predição, ou seja, VP somado com VN, FP e FN.

[mudar imagem para fórmula]

  ![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/a137bb75-f2af-4fc6-bad8-696d75bd671d)
  
- Revocação
  - A revocação  é uma métrica que avalia a capacidade de um modelo em identificar corretamente os exemplos positivos em relação ao total de exemplos positivos presentes nos dados,
ela é calculada dividindo o número de verdadeiros positivos (VP) pela soma dos verdadeiros positivos (VP) com os falsos negativos (FN). 

[mudar imagem para fórmula]

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/dfdf8dad-37ee-4de4-bef2-7dd8fcc5245c)

- matriz de confusão

[colocar imagem exemplo]

  - Após a classificação dos elementos pela modelagem preditiva, os resultados da predição são colocados em diferentes quadrantes. Na diagonal principal  estão os valores corretamente preditos. Fora dessa diagonal se encontram os erros cometidos.

## Resultados


### Matrizes de confusão

- Matriz de confusão do NaiveBayes com BOW:

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/985374b8-8793-436c-a488-95a67c7dc01d)

[Acurácia e revocação do modelo]

- Matriz de confusão do Naive Bayes com Word2Vec:

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/f258a39a-8056-4cb0-8ebf-87221dc15c5e)

[Acurácia e revocação do modelo]

- Matriz de confusão SVM: 

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/f51b85cd-289c-47d5-ae8b-fb3561210849)

[Acurácia e revocação do modelo]

- Matriz de confusão transformers:

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/a113ab4d-0cbc-4374-942b-5a6fcb9cbfa2)

[Acurácia e revocação do modelo]

[Indicar que pela acurácia alta do modelo RN com T, foi feito um gráfico da curvatura da acurácia para avaliar overfitting]

[Imagem do gráfico]

[Explicar gráfico]



## Conslusão

### Comparação entre os modelos

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/bb1c5e00-5624-4854-89e9-765e9c0671f2)
[Talvez não precise mostrar o resultado de sprint anterior, apenas se for usado pra reforçar na conclusão a escolha do modelo]
- Matriz de confusão da Rede Neural com Word2Vec: 

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99202408/66ff0ebc-523e-4cdf-86fa-b7354d529e2f)

# Modelo escholido :

## Referências
