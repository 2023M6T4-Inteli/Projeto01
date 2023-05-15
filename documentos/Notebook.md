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

### Bag of Words:
Explicando o nome desta técnica, ela identifica e classifica a frequência e ocorrência de "words" (palavras ou elementos) em cada "bag", ou "bolsa" (que representa o conjunto do banco de dados utilizado), visto que cada modelo criado pode possuir diferentes conjuntos de elementos (Lee et al, 2022). A instância de cada palavra no modelo, desconsidera a ordem e a gramática, como separando adjetivos de substantivos e desconectando palavras compostas, por exemplo, e diferenciando variações de palavras, de acordo com sua escrita, como "água" e "agua", ou "Gato" e "gato", ressaltando a importância do tratamento dos dados para padronizar as palavras (Qader, Ameen, Ahmed, 2019).

O modelo bag of words pode ser utilizado para construir uma nuvem de palavras, para facilitar a visualização e a análise dos resultados obtidos, tornando mais intuitivo os insights obtidos (Powell et al, 2017). 

### Análise Descritiva do Corpus:
Após o recebimento dos dados, foi realizada uma análise para identificar features importantes para a criação de um modelo bag of words, com remoção de colunas irrelevantes antes do início da etapa de pré-processamento dos elementos da tabela.

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

O critério utilizado pela equipe para definir quais colunas seriam excluídas e quais seriam mantidas foi como base no funcionamento do modelo bag of words, que trata cada palavra como uma unidade independente. Como a estratégia do grupo foi criar um único conjunto com todas as palavras extraídas de todos os posts do banco de dados, independente da data ou autor do comentário, torna irrelevante manter informações sobre a origem ou contexto, como as colunas "autor", e "dataPublicada". Caso a estratégia do grupo fosse selecionar um conjunto de data específico, por exemplo, este conjunto deveria ser destacado, eliminando os elementos que estiverem fora do período selecionado. As palavras-chave relevantes são provenientes dos textos escritos pelos usuários da rede social, e sendo assim, adicionar palavras que não foram originalmente adicionadas pelos usuários causaria muito ruído, se fazendo necessário excluir todas as colunas antes da criação do modelo, mantendo apenas o texto dos comentários para o pré-processamento.

### Pré-Processamento dos dados:
Esta etapa impacta diretamente na qualidade dos resultados, porém a quantidade de pré-processamnento necessários também depende da qualidade dos dados brutos (Rudkowsky et al, 2018).
A partir da análise descritiva do corpus, para obter resultados significativos e precisos, selecionamos alguns pré-processamentos com o objetivo de tratar os dados e prepará-los para o nosso modelo Bag of Words. É essencial o uso desses pré-processamentos pois eles auxiliam na normalização do texto (consistência nos dados), na eliminação de ruídos, na padronização e no tratamento de ambiguidades. 

Segue abaixo todos os pré-processamentos selecionados:

- **Remoção de acentos:** Para garantir que um texto seja processado de forma consistente, é importante realizar a padronização dos seus componentes, foi aplicada a remoção de acentos. Além disso, a ausência de acentos reduz o risco de que o algoritmo interprete de maneira diferente duas palavras idênticas, mas que tenham sido acentuadas de formas distintas ou incorretas. Em resumo, a remoção de acentos foi utilizada pois é uma prática essencial no pré-processamento de textos para aprimorar a qualidade e a eficácia da análise de dados em linguagem natural.

- **Tratamento letras maiúsculas:** O tratamento de letras maiúsculas é importante porque, muitas vezes, a diferença entre letras maiúsculas e minúsculas pode impactar negativamente a análise do algoritmo, tendo em vista que ele pode interpretar as palavras como diferentes em determinadas situações. Esse problema pode levar a resultados imprecisos, considerando que, diante do objetivo de contar a frequência de palavras, essas diferenças garantem que as palavras sejam contadas de maneira distinta. Além disso, é muito importante considerar que letras maiúsculas são usadas em diferentes contextos, como por exemplo, no início de nomes próprios, início de frases, entre outros, o que pode mudar o sentido das frases. E também padronizar o bag of words.  Por isso, a necessidade de aplicar conversão de todas as letras minúsculas, ou tratar a diferença entre maiúsculas e minúsculas com devida atenção. 

- **Tokenização:** Processo de pré-processamento utilizado para dividir os valores de uma coluna em pedaços menores, como palavras ou frases. Cada pedaço, conhecido como token, recebe um valor específico para identificação, tornando cada palavra de forma independente. Esse processo torna o texto mais gerenciável e facilita a análise e os processamentos subsequentes dos dados. Esse tratamento reduz a complexidade na comparação de palavras, e por meio dele, é possível construir um vocabulário a partir de uma normalização e redução de ruídos, sendo fundamental para a classificação de texto e análise de sentimento.

- **Remoção de Stop Words:** A remoção dos Stop Words é um pré-processamento importante pois elimina palavras irrelevantes que podem prejudicar a precisão do modelo final, como artigos, preposições, conjunções, entre outros conectores. Esse tratamento ajuda na eficácia da classificação de texto e na redução tanto do vocabulário quanto de ruídos (palavras que não têm um valor semântico significativo).

- **Tratamento de abreviações:** Dado que nosso trabalho envolve a manipulação de textos extraídos das redes sociais, onde uma quantidade significativa de comentários contém abreviações, estes devem ser tratados. Para incorporá-las de forma eficaz em nosso modelo, é preciso realizar um tratamento adequado dessas abreviações, substituindo-as por suas versões completas. Isso permite que o modelo compreenda e processe melhor essas expressões.

- **Tratamento de emojis:** Emojis são muito utilizados por usuários de redes sociais, ajudando-os, assim, a expressar emoções e sentimentos. Portanto, para melhor entender o sentido de uma mensagem, o tratamento de emojis podem fornecer uma melhor precisão para a análise e uma classificação mais precisa dos sentimentos de uma mensagem.

Padronizar a variação de palavras é muito importante, já que o modelo bag of words contabiliza a ocorrência das palavras considerando variações na grafia como palavras diferentes. As palavras "água", "Água", "Agua", "AGUA", "agua", etc são escritas de forma diferente, mas representam a mesma coisa, por exemplo. Assim, os tratamentos de remoção de acentos, transformar letras maiúsculas em minúsculas e tratar abreviações possuem esse objetivo de reduzir a quantidade de palavras diferentes que possuem o mesmo sentido.

Emojis são utilizados por usuários para expressar seus sentimentos, informação muito importante para algoritmos de análise de sentimentos, e uma técnica para isso é com o tratamento de emojis, para converter figuras em texto.

Agora falando sobre a remoção de Stop Words, é essencial para eliminar palavras muito utilizadas, mas que não possuem nenhum significado, de forma independente. "O", "a", "que", entre outras são palavras utilizadas em linguagem natural, mas que para um modelo de bag of words apenas causaria ruídos.

Por fim, tokenizar palavras é o princípio básico da criação de um modelo bag of words, por separar frases em palavras isoladas, possibilitando posteriormente a identificação de palavras-chave a partir da sua frequência em textos escritos por usuários diferentes, podendo identificar tendências e padrões, onde o objetivo de todas as etapas descritas é garantir um conjunto de palavras padronizado, para criar um modelo bag of words, com a menor quantidade de ruídos.


## PIPELINE
Uma pipeline é importante para facilitar a visualização e análise na sequência de processos, definindo um fluxo de trabalho, de forma a estruturar a coerência e eficiência de algoritmos, por exemplo. Isso também permite corrigir erros ou problemas em cada etapa, melhorando a qualidade do resultado final, facilitando a comunicação sobre os processos entre os integrantes do time. No caso deste projeto, focada em pré-processamento de texto, a pipeline mostra a implementação das etapas do tratamento dos dados na seguinte sequência:

1. Entrada: Primeira etapa, com os dados em seu estado bruto, exatamente como constam na base de dados;
2. Remoção de acentos: Consiste em eliminar os acentos das palavras, evitando discrepâncias nas formas de escrita;
3. Remoção de letras maiúsculas: Transformação de todas as letras do texto em minúsculas, para padronizar palavras;
4. Tradução de emojis: Conversão de emojis presentes no texto para sua forma textual;
5. Tratamento de abreviação: Identificação e expansão de abreviações tornando o texto mais legível para análises posteriores;
6. Tokenização: Divisão do texto em unidades menores, como palavras ou subpalavras, conhecidas como tokens, possibilitando a criação do modelo bag of words;
7. Remoção de stop words: Eliminação de palavras comuns, como artigos e preposições, que não contêm informações relevantes para as análises;
8. Saída: Resultado final após os dados passarem por todas as etapas.

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99211976/a5084a02-42e6-495c-8605-30a211ca97d8)
Figura 1. Pipeline desenvolvida com as etapas do pré-processamento dos dados, com uma frase utilizada como exemplo para demonstrar o resultado de cada etapa no texto.

## Resultados
Os resultados obtidos poodem ser observados na tabela com a frequência das dez palavras que tiveram mais ocorrências no banco de dados:


| **Palavra** 	| Repetição 	|
|---	|---	|
| **btg** 	| 570 	|
| **banco** 	| 514 	|
| **limite** 	| 370 	|
| **conta** 	| 309 	|
| **cartao** 	| 263 	|
| **investimentos** 	| 233 	|
| **estamos** 	| 222 	|
| **dia** 	| 192 	|
| **ajudar** 	| 187 	|
| **melhor** 	| 185 	|

Tabela 1.  Ocorrência das palavras que mais apareceram no banco de dados após criação do modelo bag of words.

O resultado também pode ser verificado a partir da nuvem de palavras a seguir:
![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99211976/15065a90-69f7-4798-b013-2f17bbc9c45a)
Figura 2. Nuvem de palavras do bag of words gerado. Quanto maior a palavra em relação às demais, maior foi a frequência no banco de dados. É importante ressaltar que palavras que estão próximas ou que apresentam a mesma cor não possuem nenhuma correlação, importando apenas no tamanho das palavras das demais.

Também foi gerada uma nuvem de palavras utilizando a base de dados que apenas passou pelo processo de tokenização, sem nenhum outro pré-processamento, para ressaltar a diferença de uma nuvem de palavras que usa um bag of words com um conjunto totalmente bruto, sem remoção de stop words, nem podronização de palavras.
![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99211976/0c6746f9-3670-4c41-ba26-a1024279ad40)
Figura 3. Nuvem de palavras de um bag of words com um conjunto que passou apenas pelo pré-processamento de tokenização, sem remoção de nem modificação de nenhuma palavra.

A visualização de nuvem de palavras é uma forma de representar de maneira visual os principais resultados da análise de bag of words. Ao analisar os dados,  algumas palavras-chave são recorrentes, tais como "btg", "banco", "limite", "conta", "cartão" e "ajudar".
Também foi possível perceber variações de palavras que não foram tratadas, mas que possuem o mesmo sentido, como plurais, e palavras com tempos verbais diferentes, bem como palavras que não representam nenhum insight importante, como "voces", "dia", "estamos", entre outras.

Outro ponto a destacar é palavras que estão diretamente ligada ao nosso parceiro de projeto, como "btg", "banco", mas que não trazem nenhum insight, já que são naturalmente esperadas de aparecer em uma rede social de um banco, podendo ser utilizadas também como stop words.

## Conclusão
Após a análise nos tratamentos realizados e nos resultados obtidos, é possível chegar a dois tipos de conclusões:

I - O tratamento dos dados está na direção correta, visto que foi obter algumas percepções relevantes mesmo nessa fase inicial. Levando em conta a análise manual na rede social em questão, possuíam comentários sobre a insatisfação de clientes sobre o limite do cartão, e isso pôde ser verificado na nuvem de palavras que passou por todo o pré-procesamento. Adicionalmente, algumas palavras menos frequentes também desempenham um papel importante na análise. Um exemplo disso é o nome "Flávio", que se destaca devido à sua participação em uma campanha de marketing como atleta. Essa associação pode indicar sucesso em um nicho específico, levantando a importância de recortes nos conjuntos de dados, com períodos de tempo espoecíficos, para avaliar o desempenho em campanhas, por exemplo.

II - Considerando que esta fase de análise visa avaliar e definir o direcionamento das próximas etapas, uma das medidas que devemos adotar é a exclusão dos comentários relacionados ao BTG. Essa exclusão contribuirá para uma visualização mais clara e destacará apenas as informações verdadeiramente relevantes, bem como outras stop words que estão diretamente ligadas ao setor da empresa, mas não trazem insights, como "banco". Outro tratamento necessário é o de plurais, que podem dividir a frequência de palavras importantes, como "investimento" e "investimentos".

Para finalizar, a partir da comparação dos resultados de uma nuvem de palavras de um conjunto que passou por todos os tratamentos e um conjunto com os dados brutos, fica muito claro que a análise de escolhas e tratamentos dos dados impactam diretamente na qualidade final do modelo bag of words, sendo inclusive necessário reavaliar para incrementar o modelo para obter resultados melhores e mais focados em manter apenas palavras-chave, possibilitando assim, insights valiosos para o nosso parceiro de projeto.

## Referências
Lee, J., Warner, E., Shaikhouni, S. et al. "Unsupervised machine learning for identifying important visual features through bag-of-words using histopathology data from chronic kidney disease", Scientific Reports, 2022. 

Qader, W. A., Ameen, M. M. and Ahmed, B. I. "An Overview of Bag of Words;Importance, Implementation, Applications, and Challenges", International Engineering Conference (IEC), 2019.

Rudkowsky, E., Haselmayer, M., Wastian, M., Jenny, M., Emrich, S., Sedlmair, M., "More than Bags of Words: Sentiment Analysis with WordEmbeddings", Communication Methods and Measures, 2018.

Powell, R. T., Olar, A., Narang, S., Rao, G., Sulman, E., Fuller, G. N., Rao, A. "Identification of Histological Correlates of Overall Survival in Lower Grade Gliomas Using a Bag-of-words Paradigm: A Preliminary Analysis Based on Hematoxylin & Eosin Stained Slides from the Lower Grade Glioma Cohort of The Cancer Genome Atlas", Journal of Pathology Informatics, 2017.

