# Documentação do modelo de bag of words
## Introdução
Dados são muito importantes para enriquecer as tomadas de decisão das empresas. Porém, analisar os dados de forma manual demanda muito tempo, principalmente quando o profissional analisa esses dados diretamente em uma plataforma de rede social, por exemplo. Nesta etapa do desenvolvimento do nosso modelo de machine learning para análise de sentimentos, criaremos um modelo de bag of words. Essa técnica de processamento de linguagem natural transforma textos em vetores de palavras, ignorando a estrutura gramatical e ordem das palavras. Cada palavra é ranqueada de acordo com a quantidade de ocorrências no banco de dados fornecido pelo parceiro de projeto.

Antes de criar o modelo de bag of words, é essencial analisar e compreender os dados para realizar o pré-processamento adequado. É importante ressaltar a relevância do tratamento e pré-processamento dos dados, especialmente quando se trata de modelos de linguagens - que contêm informações subjetivas - , garantindo a qualidade dos dados para análise e obtenção de resultados mais sólidos e robustos. Isso reduz a presença de ruídos e vieses. 

## Metodologia
A equipe de desenvolvimento recebeu o banco de dados no formato xlsx, em um excel, que contém 11 colunas e 12356 linhas. Os dados foram extraídos do perfil do Instagram @btgpactual pelo nosso parceiro de projeto, o banco BTG Pactual. É importante destacar a confiança depositada na equipe de desenvolvimento pelo nosso parceiro, que é fundamental para o desenvolvimento e o sucesso deste projeto. Além disso, a segurança e o sigilo das informações contidas no banco de dados são de extrema importância, por isso, a equipe deve se manter atenta à proteção desses dados e garantir que informações sensíveis não sejam divulgadas.

### Bag of Words
A técnica de "bag of words" identifica e classifica a frequência e ocorrência de "words" (palavras ou elementos) em cada "bag" ou "bolsa", que representa o conjunto do banco de dados utilizado. Cada modelo criado pode possuir diferentes conjuntos de elementos (Lee et al, 2022). A instância de cada palavra no modelo desconsidera a ordem e a gramática, separando adjetivos de substantivos, desconectando palavras compostas, por exemplo, e diferenciando variações de palavras, de acordo com sua escrita, como "água" e "agua", ou "Gato" e "gato". Isso ressalta a importância do tratamento dos dados para padronizar as palavras (Qader, Ameen, Ahmed, 2019).

O modelo "bag of words" pode ser utilizado para construir uma nuvem de palavras, facilitando a visualização e análise dos resultados obtidos e tornando os insights mais intuitivos (Powell et al, 2017).

### Análise Descritiva do Corpus
Após receber os dados, a equipe realizou uma análise para identificar as features importantes para criar um modelo bag of words, removendo as colunas irrelevantes antes do início da etapa de pré-processamento dos elementos da tabela.

O objetivo da análise foi compreender melhor o corpus dos dados, identificando features necessárias, tratamentos e limpezas importantes para reduzir ruídos, entre outros fatores. Serão apresentados aqui os nomes das colunas da tabela, os conteúdos dos campos e as colunas que foram eliminadas, bem como a estratégia utilizada para tomar essas decisões. É importante ressaltar que os nomes das colunas serão escritos exatamente como foram recebidos pela equipe, sendo alterados apenas por algoritmos em Python, e não manualmente na tabela do Excel, já que essa é uma etapa importante no tratamento dos dados.

1. **Coluna id:** A coluna id apresenta o index para visualização da planilha e pode ser usada como chave primária do comentário. No que diz respeito à utilização no modelo, essa coluna não confere relevância para a sua construção, visto que sua utilidade está atrelada apenas ao fato de garantir que cada linha possua um identificador único. Portanto, **essa coluna não será utilizada.**

2. **Coluna "dataPublicada":** A coluna refere-se à data de publicação do comentário. Para a construção do modelo **bag of words**, essa coluna não apresenta relevância, portanto, **não será utilizada**. Posteriormente, sua utilização pode se fazer necessária para a averiguação dos períodos das campanhas.

3. **Coluna "autor":** A coluna autor é referente à conta do instagram que realizou o comentário na postagem. Essa coluna **não será utilizada** pelo modelo bag of words, mas será importante para o agrupamento de comentários referente à empresa BTG, em outros modelos. 

4. **Coluna: "texto":** A coluna texto se refere ao texto presente no comentário realizado. Para a construção do modelo, essa é a coluna com **maior relevância**, visto que são justamente os conteúdos dos comentários que precisam ser analisados pelo modelo bag of words. 

5. **Coluna: "sentimento":** A coluna sentimento é, justamente, o target da classificação que precisamos fazer dos dados. Essa coluna será utilizada para o treinamento posterior do modelo, visto que apresenta o resultado esperado. Os comentários foram classificados como POSITIVE, NEGATIVE e NEUTRAL. Contudo, diante de uma análise manual das classificações, foi possível perceber que alguns comentários foram classificados de maneira errônea, dado que possuem um teor positivo mas foram classificados como negativos ou neutros. Tendo em vista o modelo de bag of words, essa coluna **não será utilizada**.

6. **Coluna: "tipoInteracao":** A coluna tipo interação informa o tipo de interação a qual aquele comentário pertence, como, por exemplo, uma resposta ou como marcação. Essa coluna, **não será utilizada** para a construção do modelo bag of words.

7. **Coluna: "anomalia":**  Utilizada para indicar ocorrências de links ou intenções maliciosas nos comentários, possui valores que variam de 0 (zero) para comentários que não se encaixam na condição descrita e 1 (um) para comentários que se encaixam na condição. Por não apresentar ligação no sentimento expressado pelo usuário, esta coluna **não será utilizada**.

8. **Coluna: "probabilidadeAnomalia":**  Essa coluna indica a possibilidade de ocorrência de links ou intenções maliciosas nos comentários, possui valores que variam de 0 (zero) e 100 (cem) de acordo com a chance do comentário encaixar na condição. Por não apresentar ligação no sentimento expressado pelo usuário, esta coluna **não será utilizada**. Por não apresentar ligação no sentimento expressado pelo usuário, esta coluna **não será utilizada**.

9. **Coluna: "linkPost":** Essa coluna possui o link referente a postagem da qual foram retirados os comentários. Todos os comentários referentes à mesma postagem possuem o link igual. Pensando na análise de sentimento, essa coluna não apresenta relevância, portanto, **não será utilizada.** 

10. **Coluna: "processado":** Informa se o comentário foi analisado pelo algoritmo que a empresa parceira usa para classificar o sentimento do texto do usuário, definindo a sua classificação na coluna "sentimento". Por se tratar apenas por uma verificação extra, e todos os comentários da tabela terem sua classificação definida, por ora, essa coluna **não será utilizada.**

11. **Coluna: "contemHyperlink":** Não possuímos informações suficientes para definir qual é o significado dessa coluna. Portanto, ainda não pode-se definir se ela será utilizada ou não no decorrer do desenvolvimento do projeto. Por ora, essa coluna **não será utilizada.**

A equipe utilizou o critério de funcionamento do modelo bag of words para decidir quais colunas excluir e quais manter. Nessa abordagem, cada palavra é tratada como uma unidade independente, o que torna irrelevante manter informações sobre a origem ou contexto, como as colunas "autor" e "dataPublicada". Se a estratégia fosse selecionar um conjunto de datas específicas, seria necessário destacá-lo e eliminar os elementos fora do período selecionado. As palavras-chave relevantes são provenientes dos textos escritos pelos usuários da rede social, e adicionar palavras não inseridas pelos usuários causaria muito ruído. Por isso, todas as colunas foram excluídas antes da criação do modelo, mantendo apenas o texto dos comentários para o pré-processamento.

No tópico de visualização gráfica dos dados, foram desenvolvidos métodos que possibilitaram a análise exploratória dos dados presentes na tabela fornecida pela empresa parceia. Por meio da visualização de valores nulos e do agrupamento por autores, foi possível perceber, e analisar melhor, como os dados se comportam e qual deveria ser a abordagem escolhida pelo grupo para lidar com eles. Diante disso, os critérios escolhidos para o desenvolvimento dessa parte estão voltados para os conhecimentos prévios dos integrantes do grupo, que sugeriram dois métodos de análise exploratória conhecidos.

### Pré-Processamento dos dados:
A etapa de pré-processamento é crucial para garantir a qualidade dos resultados obtidos, e sua extensão depende da qualidade dos dados brutos (Rudkowsky et al, 2018). Com base na análise descritiva do corpus, selecionamos alguns pré-processamentos essenciais para preparar os dados para nosso modelo Bag of Words. Essas etapas são fundamentais para normalizar o texto, eliminar ruídos, padronizar e tratar ambiguidades.

Segue abaixo todos os pré-processamentos selecionados:

- **Remoção de acentos:** Para garantir a consistência no processamento de um texto, é importante padronizar seus componentes, o que inclui a remoção de acentos. Além de evitar interpretações equivocadas, a ausência de acentos contribui para a identificação de palavras idênticas que foram acentuadas de maneiras diferentes. Em resumo, a remoção de acentos é uma prática essencial no pré-processamento de textos, pois aprimora a qualidade e a eficácia da análise de dados em linguagem natural.

- **Tratamento letras maiúsculas:** O tratamento de letras maiúsculas é importante porque, muitas vezes, a diferença entre letras maiúsculas e minúsculas pode impactar negativamente a análise do algoritmo, tendo em vista que ele pode interpretar as palavras como diferentes em determinadas situações. Esse problema pode levar a resultados imprecisos, considerando que, diante do objetivo de contar a frequência de palavras, essas diferenças garantem que as palavras sejam contadas de maneira distinta. Além disso, é muito importante considerar que letras maiúsculas são usadas em diferentes contextos, como, por exemplo, no início de nomes próprios, no início de frases, entre outros, o que pode mudar o sentido das sentenças e prejudicar o modelo bag of words.  Por isso, a necessidade de aplicar conversão de todas as letras minúsculas ou tratar a diferença entre maiúsculas e minúsculas com devida atenção. 

- **Tokenização:** Processo de pré-processamento utilizado para dividir os valores de uma coluna em pedaços menores, como palavras ou frases. Cada pedaço, conhecido como token, recebe um valor específico para identificação, o que permite que cada palavra seja tratada de forma independente. Esse processo torna o texto mais gerenciável e facilita a análise e os processamentos subsequentes dos dados. Esse tratamento reduz a complexidade na comparação de palavras e,  por meio dele, é possível construir um vocabulário a partir de uma normalização e de uma redução de ruídos, o que o torna fundamental para a classificação de texto e análise de sentimento.

- **Remoção de Stop Words:** A remoção dos Stopwords é um pré-processamento importante, pois elimina palavras irrelevantes que podem prejudicar a precisão do modelo final, como artigos, preposições, conjunções, entre outros conectores. Esse tratamento ajuda na eficácia da classificação de texto e na redução, tanto do vocabulário, quanto de ruídos (palavras que não têm um valor semântico significativo).

- **Tratamento de abreviações:** Dado que nosso trabalho envolve a manipulação de textos extraídos das redes sociais, em que uma quantidade significativa de comentários contêm abreviações, é necessário desenvolver um tratamento específico para esses casos. Para incorporar essa linguagem específica, de forma eficaz, em nosso modelo, é necessário realizar um tratamento adequado dessas abreviações, substituindo-as por suas versões completas. Isso permite que o modelo compreenda e processe melhor essas expressões.

- **Tratamento de emojis:** Emojis são muito utilizados por usuários de redes sociais, ajudando-os, assim, a expressar emoções e sentimentos. Portanto, para melhor entender o sentido de uma mensagem, o tratamento de emojis podem fornecer uma melhor precisão para a análise e uma classificação mais precisa dos sentimentos de uma mensagem.

Padronizar a variação de palavras é muito importante, já que o modelo bag of words contabiliza a ocorrência das palavras considerando variações na grafia como palavras diferentes. As palavras "água", "Água", "Agua", "AGUA", "agua", etc são escritas de forma diferente, mas representam os mesmos itens, por exemplo. Assim, os tratamentos de remoção de acentos, transformação de letras maiúsculas para minúsculas e a substituição de abreviações possuem o objetivo de reduzir as diferetes variações nas grafias de palavras que, apesar de estarem diferentes, possuem o mesmo sentido.

Os emojis são uma forma amplamente utilizada pelos usuários para expressar seus sentimentos e, por isso, são informações importantes para os algoritmos de análise de sentimento. Uma técnica utilizada para tratá-los é a conversão das figuras em texto, o que permite a inclusão desses dados no processamento de textos e na construção de modelos de análise de sentimento mais precisos.

A remoção de Stopwords é um processo fundamental para aprimorar a análise de dados em linguagem natural. Stopwords são palavras muito utilizadas, mas que não possuem significado por si só, como "o", "a" e "que". Quando incluídas em um modelo de bag of words, essas palavras causam ruído e podem prejudicar a análise. Portanto, eliminá-las é uma estratégia eficaz para melhorar a qualidade da análise de dados textuais.

Por fim, a tokenização é o princípio básico na criação de um modelo bag of words, que consiste na separação de frases em palavras isoladas. Esse processo possibilita a identificação de palavras-chave a partir da sua frequência em textos escritos por diferentes usuários, permitindo a identificação de tendências e padrões. O objetivo de todas as etapas descritas anteriormente é garantir um conjunto padronizado de palavras, criando um modelo bag of words com a menor quantidade de ruído possível.


## Pipeline
A utilização de uma pipeline é fundamental para organizar o fluxo de trabalho, garantindo coerência e eficiência na aplicação dos algoritmos. Ela permite a visualização clara das etapas do processo e facilita a identificação e correção de erros ou problemas em cada fase, melhorando significativamente a qualidade do resultado final. Além disso, a pipeline promove a comunicação efetiva entre os membros da equipe sobre os processos realizados. No contexto específico deste projeto, voltado para o pré-processamento de texto, a pipeline é essencial para demonstrar a sequência de etapas do tratamento dos dados, que ocorre da seguinte forma:

1. Entrada: Primeira etapa, com os dados em seu estado bruto, exatamente como constam na base de dados.
2. Remoção de acentos: Consiste em eliminar os acentos das palavras, evitando discrepâncias nas formas de escrita.
3. Conversão para minúsculas: Transformação de todas as letras do texto em minúsculas, para padronizar as palavras.
4. Tradução de emojis: Conversão de emojis presentes no texto para sua forma textual.
5. Tratamento de abreviações: Identificação e expansão de abreviações, tornando o texto mais legível para análises posteriores.
6. Tokenização: Divisão do texto em unidades menores, como palavras ou subpalavras, conhecidas como tokens, possibilitando a criação do modelo bag of words.
7. Remoção de stopwords: Eliminação de palavras comuns, como artigos e preposições, que não contêm informações relevantes para as análises.
8. Saída: Resultado final após os dados passarem por todas as etapas.

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99211976/a5084a02-42e6-495c-8605-30a211ca97d8)

*Figura 1. Pipeline desenvolvida com as etapas do pré-processamento dos dados, com uma frase utilizada como exemplo para demonstrar o resultado de cada etapa no texto.*

## Resultados
Os resultados obtidos podem ser observados na tabela com a frequência das dez palavras que tiveram mais ocorrências no banco de dados:


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

*Tabela 1.  Ocorrência das palavras que mais apareceram no banco de dados após criação do modelo bag of words.*

O resultado também pode ser verificado a partir da nuvem de palavras a seguir:
![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99211976/15065a90-69f7-4798-b013-2f17bbc9c45a)

*Figura 2. Nuvem de palavras do bag of words gerado. Quanto maior a palavra em relação às demais, maior foi a frequência no banco de dados. É importante ressaltar que palavras que estão próximas ou que apresentam a mesma cor não possuem nenhuma correlação, importando apenas no tamanho das palavras das demais*.

Também foi gerada uma nuvem de palavras utilizando a base de dados que apenas passou pelo processo de tokenização, sem nenhum outro pré-processamento, para ressaltar a diferença de uma nuvem de palavras que usa um bag of words com um conjunto totalmente bruto, sem remoção de stopwords, nem padronização de palavras.

![image](https://github.com/2023M6T4-Inteli/Projeto01/assets/99211976/0c6746f9-3670-4c41-ba26-a1024279ad40)

*Figura 3. Nuvem de palavras de um bag of words com um conjunto que passou apenas pelo pré-processamento de tokenização, sem remoção de nem modificação de nenhuma palavra*.

A visualização de nuvem de palavras é uma forma de representar de maneira visual os principais resultados da análise de bag of words. Ao analisar os dados,  algumas palavras-chave são recorrentes, tais como "btg", "banco", "limite", "conta", "cartão" e "ajudar".

Também foi possível perceber variações de palavras que não foram tratadas, mas que possuem o mesmo sentido, como plurais, e palavras com tempos verbais diferentes, bem como palavras que não representam nenhum insight importante, como "voces", "dia", "estamos", entre outras.

Outro ponto a destacar é palavras que estão diretamente ligadas ao nosso parceiro de projeto, como "btg", "banco", mas que não trazem nenhum insight, já que são naturalmente esperadas de aparecer em uma rede social de um banco, podendo ser utilizadas também como stop words.

## Conclusão
Após a análise nos tratamentos realizados e nos resultados obtidos, é possível chegar a dois tipos de conclusões:

I - O tratamento dos dados segue na direção correta, tendo sido possível obter percepções relevantes mesmo nesta fase inicial. Durante a análise manual da rede social em questão, foram encontrados comentários de clientes insatisfeitos com o limite do cartão, o que pode ser verificado na nuvem de palavras resultante de todo o pré-processamento. Além disso, palavras menos frequentes também desempenham um papel importante na análise. Por exemplo, o nome "Flávio" se destaca devido à sua participação em uma campanha de marketing como atleta, o que pode indicar sucesso em um nicho específico. Isso ressalta a importância de recortes nos conjuntos de dados com períodos de tempo específicos para avaliar o desempenho em campanhas, entre outros aspectos.

II - Nesta fase de análise, nosso objetivo é avaliar e definir o direcionamento das próximas etapas. Para atingir esse objetivo, é importante excluir os comentários relacionados ao BTG. Essa medida contribuirá para uma visualização mais clara e destacará apenas as informações verdadeiramente relevantes. Além disso, é preciso eliminar outras stop words que estão diretamente ligadas ao setor da empresa, mas não trazem insights, como "banco". Outra etapa crucial do pré-processamento é o tratamento de plurais, que podem diluir a frequência de palavras importantes, como "investimento" e "investimentos".

Para concluir, ao compararmos os resultados de uma nuvem de palavras de um conjunto de dados que passou por todos os tratamentos e outro conjunto com os dados brutos, fica evidente que as escolhas e tratamentos dos dados impactam diretamente na qualidade final do modelo bag of words. É fundamental reavaliar e aprimorar o modelo constantemente para obter resultados mais precisos e focados em palavras-chave relevantes, possibilitando insights valiosos para o nosso parceiro de projeto.

## Referências
Lee, J., Warner, E., Shaikhouni, S. et al. "Unsupervised machine learning for identifying important visual features through bag-of-words using histopathology data from chronic kidney disease", Scientific Reports, 2022. 

Qader, W. A., Ameen, M. M. and Ahmed, B. I. "An Overview of Bag of Words;Importance, Implementation, Applications, and Challenges", International Engineering Conference (IEC), 2019.

Rudkowsky, E., Haselmayer, M., Wastian, M., Jenny, M., Emrich, S., Sedlmair, M., "More than Bags of Words: Sentiment Analysis with WordEmbeddings", Communication Methods and Measures, 2018.

Powell, R. T., Olar, A., Narang, S., Rao, G., Sulman, E., Fuller, G. N., Rao, A. "Identification of Histological Correlates of Overall Survival in Lower Grade Gliomas Using a Bag-of-words Paradigm: A Preliminary Analysis Based on Hematoxylin & Eosin Stained Slides from the Lower Grade Glioma Cohort of The Cancer Genome Atlas", Journal of Pathology Informatics, 2017.
