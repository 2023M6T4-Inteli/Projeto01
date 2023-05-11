# Inteli - Instituto de Tecnologia e Liderança 

<p align="center">
<a href= "https://www.inteli.edu.br/"><img src="https://s3.amazonaws.com/gupy5/production/companies/26702/career/63484/images/2022-04-28_16-56_logo.png" alt="Inteli - Instituto de Tecnologia e Liderança" border="0" width="200"></a>
</p>

# Sprint-2

## Tratamento de dados para o modelo

### Remoção de todas as linhas que não possuem a coluna texto
Todas as tuplas que não aprensenta nem um texto nós descartamos do dataframe.

### Código para remoção dos acentos

### Tratamento letras maiusculas
O tratamento de letras maiúsculas é importante porque, muitas vezes, a diferença entre letras maiúsculas e minúsculas pode impactar negativamente a análise do algoritmo, tendo em vista que ele pode interpretar as palavras como diferentes em determinadas situações. Esse problema pode levar a resultados imprecisos, considerando que, diante do objetivo de contar a frequência de palavras, essas diferenças garantem que as palavras sejam contadas de maneira distinta.  Além disso, é muito importante considerar que letras maiúsculas são usadas em diferentes contextos, como por exemplo, no início de nomes próprios, início de frases, entre outros, o que pode mudar o sentido das frases. E também padronizar o Bag Of Words.  Por isso, a necessidade de aplicar conversão de todas as letras minúsculas, ou tratar a diferença entre maiúsculas e minúsculas com devida atenção. 

### Tokenização

### Remoção de Stop Words
A remoção dos Stop Words é um pré-processamento importante pois elimina palavras irrelevantes que podem prejudicar a precisão do modelo final, como artigos, preposições, conjunções, entre outros conectores. Esse tratamento ajuda na eficácia da classificação de texto e na redução tanto do vocabulário quanto de ruídos (palavras que não têm um valor semântico significativo)

### Tratamento de abreviações

### Remoção de todos comentarios criados pelo btgpactual

### Remoção de colunas irrelevantes para o modelo

## Modelo BoW
O modelo de bag of words (ou, em tradução literal, saco de palavras) é uma representação que transforma texto em vetores de tamanho fixo para contar quantas vezes as palavras aparecem nas frases em questão. Esse método é comumente chamado de vetorização.
