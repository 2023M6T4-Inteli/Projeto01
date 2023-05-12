# Inteli - Instituto de Tecnologia e Liderança 

<p align="center">
<a href= "https://www.inteli.edu.br/"><img src="https://s3.amazonaws.com/gupy5/production/companies/26702/career/63484/images/2022-04-28_16-56_logo.png" alt="Inteli - Instituto de Tecnologia e Liderança" border="0" width="200"></a>
</p>

# Sprint-2
## Introdução:
Bag of wordss

## Modelo BoW
O modelo de bag of words (ou, em tradução literal, saco de palavras) é uma representação que transforma texto em vetores de tamanho fixo para contar a quantidade de vezes que as palavras aparecem nas frases em questão, sem considerar sua ordem ou o contexto. Esse método é comumente chamado de vetorização.

## Análise Descritiva do Corpus:

##  Método/Resultados:
## Tratamento de dados para o modelo

### Remoção de todas as linhas que não possuem a coluna texto
Todas as tuplas que não aprensenta nem um texto nós descartamos do dataframe.

### Remoção de acentos
Para garantir que um texto seja processado de forma consistente, é importante realizar a normalização dos seus componentes, e para isso, utilizamos como pré-processamento a remoção de acentos. Ela é uma etapa fundamental, já que isso ajuda o algoritmo a compreender com mais precisão o que o texto está dizendo. Além disso, a ausência de acentos reduz o risco de que o algoritmo interprete de maneira diferente duas palavras idênticas, mas que tenham sido acentuadas de formas distintas ou incorretas. Em resumo, a remoção de acentos foi utilizada pois é uma prática essencial no pré-processamento de textos para aprimorar a qualidade e a eficácia da análise de dados em linguagem natural.

### Tratamento letras maiusculas
O tratamento de letras maiúsculas é importante porque, muitas vezes, a diferença entre letras maiúsculas e minúsculas pode impactar negativamente a análise do algoritmo, tendo em vista que ele pode interpretar as palavras como diferentes em determinadas situações. Esse problema pode levar a resultados imprecisos, considerando que, diante do objetivo de contar a frequência de palavras, essas diferenças garantem que as palavras sejam contadas de maneira distinta.  Além disso, é muito importante considerar que letras maiúsculas são usadas em diferentes contextos, como por exemplo, no início de nomes próprios, início de frases, entre outros, o que pode mudar o sentido das frases. E também padronizar o Bag Of Words.  Por isso, a necessidade de aplicar conversão de todas as letras minúsculas, ou tratar a diferença entre maiúsculas e minúsculas com devida atenção. 

### Tokenização
A tokenização é um processo de pré-processamento utilizado para dividir os valores de uma coluna em pedaços menores, como palavras ou frases. Cada pedaço, conhecido como token, recebe um valor específico para identificação. Esse processo torna o texto mais gerenciável e facilita a análise e os processamentos subsequentes dos dados. Utilizamos esse pré-processamento pois além de reduzir a complexidade na comparação de palavras, por meio dele, é possível construir um vocabulário a partir de uma normalização e redução de ruídos, sendo fundamental para a classificação de texto e análise de sentimento.

### Remoção de Stop Words
A remoção dos Stop Words é um pré-processamento importante pois elimina palavras irrelevantes que podem prejudicar a precisão do modelo final, como artigos, preposições, conjunções, entre outros conectores. Esse tratamento ajuda na eficácia da classificação de texto e na redução tanto do vocabulário quanto de ruídos (palavras que não têm um valor semântico significativo)

### Tratamento de abreviações

### Remoção de todos comentarios criados pelo btgpactual

### Remoção de colunas irrelevantes para o modelo

## Conclusão

