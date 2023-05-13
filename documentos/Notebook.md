# Inteli - Instituto de Tecnologia e Liderança 

<p align="center">
<a href= "https://www.inteli.edu.br/"><img src="https://s3.amazonaws.com/gupy5/production/companies/26702/career/63484/images/2022-04-28_16-56_logo.png" alt="Inteli - Instituto de Tecnologia e Liderança" border="0" width="200"></a>
</p>

# Sprint-2
## Introdução:
O modelo de bag of words (ou, em tradução literal, saco de palavras) é uma representação que transforma texto em vetores de tamanho fixo para contar a quantidade de vezes que as palavras aparecem nas frases em questão, sem considerar sua ordem ou o contexto. Esse método é comumente chamado de vetorização.

## Análise Descritiva do Corpus:
A análise descritiva do corpus é um processo que tem como objetivo principal descrever as características dos dados textuais de forma objetiva e clara. Essa análise permite uma visão geral e detalhada sobre os aspectos dos dados coletados do corpus.

Abaixo é possível visualizar a descrição do corpus referente ao nosso projeto:
1. **Coluna Id:** A coluna id apresenta o index para visualização da planilha e pode ser usada como chave primária do comentário. No que diz respeito à utilização no modelo, essa coluna não confere relevância para a sua construção, visto que sua utilidade está atrelada apenas ao fato de garantir que cada linha possua um identificador único. Portanto, *essa coluna não será utilizada.*

2. **Coluna dataPublicada:** A coluna data publicada refere-se a data de publicação do comentário. Para a construção do modelo **bag of words**, essa coluna não apresenta relevância, portanto, *não será utilizada*. Posteriormente, sua utilização pode se fazer necessária para a averiguação dos períodos das campanhas.

3. **Coluna autor:** A coluna autor é referente à conta do instagram que realizou o comentário na postagem. Essa coluna não será utilizada diretamente pelo modelo bag of words, mas será importante para o agrupamento de comentários referente à empresa BTG. 

4. **Coluna texto:** A coluna texto se refere ao texto presente no comentário realizado. Para a construção do modelo, essa é a coluna com maior relevância, visto que são justamente os conteúdos dos comentários que precisam ser analisados pelo modelo. 

5. **Coluna sentimento:** A coluna sentimento é, justamente, o target da classificação que precisamos fazer dos dados. Essa coluna será utilizada para o treinamento posterior do modelo, visto que apresenta o resultado esperado. Contudo, diante de uma análise manual das classificações, foi possível perceber que alguns comentários foram classificados de maneira errônea, dado que possuem um teor positivo mas foram classificados como negativos ou neutros.

6. **Coluna tipoInteracao:** A coluna tipo interação informa o tipo de interação a qual aquele comentário pertence, como, por exemplo, uma resposta ou como marcação. Essa coluna, inicialmente, não será utilizada para a construção do modelo bag of words.

7. **Coluna anomalia:**  Não possuímos informações suficientes para definir qual é o significado dessa coluna. Portanto, ainda não pode-se definir se ela será utilizada ou não no decorrer do desenvolvimento do projeto. Por ora, essa coluna não será utilizada.

8. **Coluna probabilidadeAnomalia:**  Não possuímos informações suficientes para definir qual é o significado dessa coluna. Portanto, ainda não pode-se definir se ela será utilizada ou não no decorrer do desenvolvimento do projeto. Por ora, essa coluna não será utilizada.

9. **Coluna linkPost:** Essa coluna possui o link referente a postagem da qual foram retirados os comentários. Todos os comentários referentes à mesma postagem possuem o link igual. Pensando na análise de sentimento, essa coluna não apresenta relevância, portanto, não será utilizada. 

10. **Coluna processado:** Não possuímos informações suficientes para definir qual é o significado dessa coluna. Portanto, ainda não pode-se definir se ela será utilizada ou não no decorrer do desenvolvimento do projeto. Por ora, essa coluna não será utilizada.

11. **Coluna contemHyperlink:** Não possuímos informações suficientes para definir qual é o significado dessa coluna. Portanto, ainda não pode-se definir se ela será utilizada ou não no decorrer do desenvolvimento do projeto. Por ora, essa coluna não será utilizada.

##  Métodos com seus respectivos resultados:
### Tratamento de dados para o modelo:
A partir da análise descritiva do corpus, para obter resultados significativos e precisos, selecionamos alguns pré-processamentos com o objetivo de tratar os dados e prepará-los para o nosso modelo Bag of Words. É essencial o uso desses pré-processamentos pois eles auxiliam na normalização do texto (consistência nos dados), na eliminação de ruídos, na padronização e no tratamento de ambiguidades. 

Segue abaixo todos os pré-processamentos selecionados:

- **Remoção de acentos:** Para garantir que um texto seja processado de forma consistente, é importante realizar a normalização dos seus componentes, e para isso, utilizamos como pré-processamento a remoção de acentos. Ela é uma etapa fundamental, já que isso ajuda o algoritmo a compreender com mais precisão o que o texto está dizendo. Além disso, a ausência de acentos reduz o risco de que o algoritmo interprete de maneira diferente duas palavras idênticas, mas que tenham sido acentuadas de formas distintas ou incorretas. Em resumo, a remoção de acentos foi utilizada pois é uma prática essencial no pré-processamento de textos para aprimorar a qualidade e a eficácia da análise de dados em linguagem natural.

- **Tratamento letras maiusculas:** O tratamento de letras maiúsculas é importante porque, muitas vezes, a diferença entre letras maiúsculas e minúsculas pode impactar negativamente a análise do algoritmo, tendo em vista que ele pode interpretar as palavras como diferentes em determinadas situações. Esse problema pode levar a resultados imprecisos, considerando que, diante do objetivo de contar a frequência de palavras, essas diferenças garantem que as palavras sejam contadas de maneira distinta.  Além disso, é muito importante considerar que letras maiúsculas são usadas em diferentes contextos, como por exemplo, no início de nomes próprios, início de frases, entre outros, o que pode mudar o sentido das frases. E também padronizar o Bag Of Words.  Por isso, a necessidade de aplicar conversão de todas as letras minúsculas, ou tratar a diferença entre maiúsculas e minúsculas com devida atenção. 

- **Tokenização:** A tokenização é um processo de pré-processamento utilizado para dividir os valores de uma coluna em pedaços menores, como palavras ou frases. Cada pedaço, conhecido como token, recebe um valor específico para identificação. Esse processo torna o texto mais gerenciável e facilita a análise e os processamentos subsequentes dos dados. Utilizamos esse pré-processamento pois além de reduzir a complexidade na comparação de palavras, por meio dele, é possível construir um vocabulário a partir de uma normalização e redução de ruídos, sendo fundamental para a classificação de texto e análise de sentimento.

- **Remoção de Stop Words:** A remoção dos Stop Words é um pré-processamento importante pois elimina palavras irrelevantes que podem prejudicar a precisão do modelo final, como artigos, preposições, conjunções, entre outros conectores. Esse tratamento ajuda na eficácia da classificação de texto e na redução tanto do vocabulário quanto de ruídos (palavras que não têm um valor semântico significativo)

- **Tratamento de abreviações:** Dado que nosso trabalho envolve a manipulação de textos extraídos das redes sociais, onde uma quantidade significativa de comentários contém abreviações, não podemos simplesmente descartá-las. Para incorporá-las de forma eficaz em nosso modelo, precisamos realizar um tratamento adequado dessas abreviações, substituindo-as por suas versões completas. Isso permitirá que o modelo compreenda e processe melhor essas expressões.

- **Remoção de todas as linhas que não possuem a coluna texto:** Descartamos do dataframe todas as tuplas que não apresentam qualquer texto de comentário. Tal ação visa aumentar a velocidade de execução do nosso modelo e garantir que ele não seja de alguma forma influenciado por esses registros vazios.

### Remoção de todos comentarios criados pelo btgpactual

### Remoção de colunas irrelevantes para o modelo

## Conclusão


