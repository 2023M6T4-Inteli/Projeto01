# Inteli - Instituto de Tecnologia e Liderança 

<p align="center">
<a href= "https://www.inteli.edu.br/"><img src="https://s3.amazonaws.com/gupy5/production/companies/26702/career/63484/images/2022-04-28_16-56_logo.png" alt="Inteli - Instituto de Tecnologia e Liderança" border="0" width="200"></a>
</p>

# Sprint-2
## Introdução:
Dados são muito importantes para enriquecer tomadas de decisão das empresas, mas analisar os dados de forma manual demanda muito tempo, principalmente quando o profissional analisa esses dados diretamente em uma plataforma de rede social, por exemplo. Tendo isso em mente, nesta etapa do desenvolvimento do nosso modelo de machine learning para análise de sentimentos, vamos criar um modelo de bag of words. Esse modelo é uma técnica de processamento de linguagem natural que transforma textos em vetores de palavras, ignorando a estrutura gramatical e ordem das palavras, ranqueando cada palavra de acordo com a quantidade de ocorrências, neste caso, do banco de dados fornecido pelo parceiro de projeto.

Antes da criação do modelo, é preciso realizar a análise e entendimento dos dados, para então dar início no pré-processamento dos elementos da tabela, visando a criação do modelo de bag of words e sua natureza de vetorização das palavras. É importante ressaltar a importância do tratamento e pré-processamento dos dados, especialmente quando se trata de modelos de linguagens, que contém informações subjetivas, garantindo a qualidade dos dados para análise e obter resultados mais sólidos e robustos, evitando ruídos e viéses. 

## Metodologia:
A equipe de desenvolvimento recebeu o banco de dados no formato xlsx, em um excel, que contém 11 colunas e 12356 linhas, onde os dados foram extraídos do perfil do Instagram @btgpactual, pelo nosso parceiro de projeto BTG Pactual. Tendo dito isso, é importante destacar a confiança depositada na equipe de desenvolvimento pelo nosso parceiro, fundamental para o desenvolvimento e o sucesso deste projeto, e que a segurança e o sigilo das informações contidas no banco de dados são de extrema importância, e por isso, é preciso que a equipe se mantenha atenta à proteção desses dados e garanta que informações sensíveis não sejam divulgadas.



Após o recebimento dos dados, foi realizada uma análise para identificar features importantes para a criação de um modelo bag of words, com remoção de colunas irrelevantes antes do início da etapa de pré-processamento dos elementos da tabela.

### Análise Descritiva do Corpus:
A análise dos dados recebidos tem como objetivo obter uma melhor compreensão geral do corpus dos dados, identificando features necessárias, tratamentos e limpezas importantes para reduzir ruídos, etc. Aqui serão descritos os nome das colunas da tabela, os conteúdos contidos nos campos, e também quais colunas foram eliminadas, bem como a estratégia utilizada para a tomada dessas decisões. É importante ressantar que os nomes das colunas serão escritos exatamente como foram recebidos pela equipe, sendo alterados apenas utilizando algoritmos em python, e não manualmente na tabela excel, já que isso representa uma importante etapa no tratamento dos dados.

1. **Coluna: id:** A coluna id apresenta o index para visualização da planilha e pode ser usada como chave primária do comentário. No que diz respeito à utilização no modelo, essa coluna não confere relevância para a sua construção, visto que sua utilidade está atrelada apenas ao fato de garantir que cada linha possua um identificador único. Portanto, **essa coluna não será utilizada.**

2. **Coluna: "dataPublicada":** A coluna refere-se à data de publicação do comentário. Para a construção do modelo **bag of words**, essa coluna não apresenta relevância, portanto, **não será utilizada**. Posteriormente, sua utilização pode se fazer necessária para a averiguação dos períodos das campanhas.

3. **Coluna: "autor":** A coluna autor é referente à conta do instagram que realizou o comentário na postagem. Essa coluna **não será utilizada** pelo modelo bag of words, mas será importante para o agrupamento de comentários referente à empresa BTG, em outros modelos. 

4. **Coluna: "texto":** A coluna texto se refere ao texto presente no comentário realizado. Para a construção do modelo, essa é a **coluna com maior relevância**, visto que são justamente os conteúdos dos comentários que precisam ser analisados pelo modelo bag of words. 

5. **Coluna: "sentimento":** A coluna sentimento é, justamente, o target da classificação que precisamos fazer dos dados. Essa coluna será utilizada para o treinamento posterior do modelo, visto que apresenta o resultado esperado. Os comentários foram classificados como POSITIVE, NEGATIVE e NEUTRAL. Contudo, diante de uma análise manual das classificações, foi possível perceber que alguns comentários foram classificados de maneira errônea, dado que possuem um teor positivo mas foram classificados como negativos ou neutros. Tendo em vista o modelo de bag of words, essa coluna **não será utilizada**.

6. **Coluna: "tipoInteracao":** A coluna tipo interação informa o tipo de interação a qual aquele comentário pertence, como, por exemplo, uma resposta ou como marcação. Essa coluna, **não será utilizada** para a construção do modelo bag of words.

7. **Coluna: "anomalia":**  Utilizada para indicar ocorrências de links ou intenções maliciosos nos comentários, possui valores que variam de 0 (zero) para comentários que não se encaixam na condição descrita e 1 (um) para comentários que encaixam na condição. Por não apresentar ligação no sentimento expressado pelo usuário, esta coluna **não será utilizada**.

8. **Coluna: "probabilidadeAnomalia":**  Essa coluna indica a possibilidade de ocorrências de links ou intenções maliciosos nos comentários, possui valores que variam de 0 (zero) e 100 (cem) de acordo com a chance do comentário encaixar na condição. Por não apresentar ligação no sentimento expressado pelo usuário, esta coluna **não será utilizada**. Por não apresentar ligação no sentimento expressado pelo usuário, esta coluna **não será utilizada**.

9. **Coluna: "linkPost":** Essa coluna possui o link referente a postagem da qual foram retirados os comentários. Todos os comentários referentes à mesma postagem possuem o link igual. Pensando na análise de sentimento, essa coluna não apresenta relevância, portanto, **não será utilizada.** 

10. **Coluna: "processado":** Informa se o comentário foi analisado pelo algoritmo que a empresa parceira usa para classificar o sentimento do texto do usuário, definindo a sua classificação na coluna "sentimento". Por se tratar apenas por uma verificação extra, e todos os comentários da tabela terem sua classificação definida, por ora, essa coluna **não será utilizada.**

11. **Coluna: "contemHyperlink":** Não possuímos informações suficientes para definir qual é o significado dessa coluna. Portanto, ainda não pode-se definir se ela será utilizada ou não no decorrer do desenvolvimento do projeto. Por ora, essa coluna **não será utilizada.**



##  Métodos com seus respectivos resultados:
### Tratamento de dados para o modelo:
A partir da análise descritiva do corpus, para obter resultados significativos e precisos, selecionamos alguns pré-processamentos com o objetivo de tratar os dados e prepará-los para o nosso modelo Bag of Words. É essencial o uso desses pré-processamentos pois eles auxiliam na normalização do texto (consistência nos dados), na eliminação de ruídos, na padronização e no tratamento de ambiguidades. 

Segue abaixo todos os pré-processamentos selecionados:

- **Remoção de acentos:** Para garantir que um texto seja processado de forma consistente, é importante realizar a normalização dos seus componentes, e para isso, utilizamos como pré-processamento a remoção de acentos. Ela é uma etapa fundamental, já que isso ajuda o algoritmo a compreender com mais precisão o que o texto está dizendo. Além disso, a ausência de acentos reduz o risco de que o algoritmo interprete de maneira diferente duas palavras idênticas, mas que tenham sido acentuadas de formas distintas ou incorretas. Em resumo, a remoção de acentos foi utilizada pois é uma prática essencial no pré-processamento de textos para aprimorar a qualidade e a eficácia da análise de dados em linguagem natural.

- **Tratamento letras maiúsculas:** O tratamento de letras maiúsculas é importante porque, muitas vezes, a diferença entre letras maiúsculas e minúsculas pode impactar negativamente a análise do algoritmo, tendo em vista que ele pode interpretar as palavras como diferentes em determinadas situações. Esse problema pode levar a resultados imprecisos, considerando que, diante do objetivo de contar a frequência de palavras, essas diferenças garantem que as palavras sejam contadas de maneira distinta.  Além disso, é muito importante considerar que letras maiúsculas são usadas em diferentes contextos, como por exemplo, no início de nomes próprios, início de frases, entre outros, o que pode mudar o sentido das frases. E também padronizar o Bag Of Words.  Por isso, a necessidade de aplicar conversão de todas as letras minúsculas, ou tratar a diferença entre maiúsculas e minúsculas com devida atenção. 

- **Tokenização:** A tokenização é um processo de pré-processamento utilizado para dividir os valores de uma coluna em pedaços menores, como palavras ou frases. Cada pedaço, conhecido como token, recebe um valor específico para identificação. Esse processo torna o texto mais gerenciável e facilita a análise e os processamentos subsequentes dos dados. Utilizamos esse pré-processamento pois além de reduzir a complexidade na comparação de palavras, por meio dele, é possível construir um vocabulário a partir de uma normalização e redução de ruídos, sendo fundamental para a classificação de texto e análise de sentimento.

- **Remoção de Stop Words:** A remoção dos Stop Words é um pré-processamento importante pois elimina palavras irrelevantes que podem prejudicar a precisão do modelo final, como artigos, preposições, conjunções, entre outros conectores. Esse tratamento ajuda na eficácia da classificação de texto e na redução tanto do vocabulário quanto de ruídos (palavras que não têm um valor semântico significativo)

- **Tratamento de abreviações:** Dado que nosso trabalho envolve a manipulação de textos extraídos das redes sociais, onde uma quantidade significativa de comentários contém abreviações, não podemos simplesmente descartá-las. Para incorporá-las de forma eficaz em nosso modelo, precisamos realizar um tratamento adequado dessas abreviações, substituindo-as por suas versões completas. Isso permitirá que o modelo compreenda e processe melhor essas expressões.

- **Remoção de todas as linhas que não possuem a coluna texto:** Descartamos do dataframe todas as tuplas que não apresentam qualquer texto de comentário. Tal ação visa aumentar a velocidade de execução do nosso modelo e garantir que ele não seja de alguma forma influenciado por esses registros vazios.

- **Tratamento de emojis:** Emojis são muito utilizados por usuários de redes sociais, ajudando-os, assim, a expressar emoções e sentimentos. Portanto, para melhor entender o sentido de uma mensagem, o tratamento de emojis podem fornecer uma melhor precisão para a análise e uma classificação mais precisa dos sentimentos de uma mensagem.

## PIPELINE

Uma pipeline, é uma sequência de etapas ou operações que são aplicadas aos dados para prepará-lo para análises posteriores.

Em nossa pipeline específica, focada em pré-processamento de texto, implementamos várias etapas para otimizar a qualidade dos dados. Essas etapas incluem:

Remoção de acentos: Consiste em eliminar os acentos das palavras, evitando discrepâncias nas formas de escrita.

Remoção de letras maiúsculas: Transformação de todas as letras do texto em minúsculas, para evitar separar no BoW duas palavras iguais.

Tradução de emojis: Conversão de emojis presentes no texto para sua forma textual.

Tratamento de abreviação: Identificação e expansão de abreviações tornando o texto mais legível para análises posteriores.

Tokenização: Divisão do texto em unidades menores, como palavras ou subpalavras, conhecidas como tokens. Essa etapa facilita a análise e o processamento posterior do texto.

Remoção de stop words: Eliminação de palavras comuns, como artigos e preposições, que geralmente não contêm informações relevantes para as análises.

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99211976/a5084a02-42e6-495c-8605-30a211ca97d8)

Ao usar essa pipeline de pré-processamento, nosso objetivo é deixar o texto limpo, padronizado e pronto para análises de texto, como classificação, agrupamento ou extração de informações. Isso nos ajuda a obter resultados mais precisos para seguir com nossa solução.

## Resultados

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99211976/a81b6f13-80db-4848-8690-d2e4e1f3e143) ![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99211976/95352ad9-5583-48e1-a9a4-1c26c2ca7d9d)


A visualização de nuvem de palavras é uma forma de representar de maneira visual os principais resultados da análise de BoW. Ao analisar os dados, identificamos algumas palavras-chave recorrentes, tais como "btg", "banco", "limite", "conta", "cartão" e "ajudar". Essas palavras fornecem insights valiosos e nos permitem chegar a duas conclusões:

I - Nossa análise está caminhando na direção correta, visto que já podemos obter algumas percepções relevantes mesmo nessa fase inicial. Por exemplo, notamos que a demanda mais significativa dos clientes está relacionada a cartões de crédito.
Adicionalmente, embora sejam menos citadas, algumas palavras menos frequentes também desempenham um papel importante na análise. Um exemplo disso é o nome "Flávio", que se destaca devido à sua participação em uma campanha de marketing como atleta. Essa associação pode indicar sucesso em um nicho específico.

II - Considerando que esta fase de análise visa avaliar e definir o direcionamento das próximas etapas, uma das medidas que devemos adotar é a exclusão dos comentários relacionados ao BTG. Essa exclusão contribuirá para uma visualização mais clara e destacará apenas as informações verdadeiramente relevantes.

## Conclusão
Apartir dos resultados obtidos e com a avaliacao do cliente, podemos destacar que precisariamos fazer melhorias nos seguntes atributos: retirada da palavra btg e btgpactual no bagof words, ja que eh obvio que btg vai ser umas das palavras mais frequentes e isso nao gera nem um inghts relevantes; 

## Referências
Lee, J., Warner, E., Shaikhouni, S. et al. Unsupervised machine learning for identifying important visual features through bag-of-words using histopathology data from chronic kidney disease. Sci Rep 12, 4832 (2022). https://doi.org/10.1038/s41598-022-08974-8

