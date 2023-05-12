# Entendimento da experiência do usuário.
A fim de criar artefatos de planejamento estratégico capazes de nortear o entendimento da experiência do usuário da aplicação, desenvolvemos duas personas e cinco histórias dos usuários. Ambos artefatos estão dispostos abaixo.
## Personas
Personas são representações dos usuários ideais da nossa solução, criadas com base em dados reais, com o objetivo de ajudar a entender e atender às necessidades, desejos e comportamentos de forma mais efetiva.

<img src="https://github.com/2023M6T4-Inteli/Projeto01/blob/main/assets/imagens/persona%201.png" width = "200px" height="200px">

**Nome**: Gabriel Rodrigues

**Idade**: 29 anos

**Cargo**: Líder de operações automatizadas

**Gênero**: Masculino

**Cidade**: São Paulo - SP

**Renda média**: R$ 25.000,00 - R$26.000,00

**Personalidade**: Gabriel é um homem muito seguro de si, exigente, responsável e carismático. Ele se sente muito confortável  ao lidar com pressão e não se intimida facilmente, e por isso, sempre foi afeiçoado por situações desafiadoras. Por gostar mais desse dinamismo, não consegue se manter na mesma rotina, seja na sua vida pessoal ou profissional. Além disso, é um homem muito dedicado que busca realizar suas tarefas com excelência e responsabilidade.

**Interesses**: Gabriel se interessa muito por esportes, música e tecnologia. Ele costuma trabalhar muito e, quando está no seu tempo livre, gosta de estar com seus amigos e familiares.

**Dores com o problema**: Gabriel trabalha na área de Automação do Banco BTG Pactual. Atualmente desenvolve um novo projeto, no qual, se faz necessário que seu trabalho ocorra em parceria com um outro setor do BTG, o setor de marketing. Nesse projeto, ele recebeu a tarefa de desenvolver um algoritmo capaz de realizar análises de sentimentos a partir do processamento de linguagem natural. Contudo, o algoritmo que foi desenvolvido não se mostrou eficiente,  apresentando  erros que comprometem, de forma direta, a análise do time de marketing. 

**Objetivos com o problema**: Tendo isso em mente, Gabriel gostaria de ter acesso a ferramentas e códigos que consiga suprir as falhas apresentadas por seu desenvolvimento anterior.  Dessa forma, seu principal objetivo nesse momento é potencializar as análises realizadas pelo algoritmo, permitindo que o time de marketing atue de forma assertiva no desenvolvimento de outras campanhas para as redes sociais. De modo geral, essa melhoria permitirá que o banco tenha postagens mais bem estruturadas e direcionadas, o que resultará em  um lucro mais pungente.
#
<img src="https://github.com/2023M6T4-Inteli/Projeto01/blob/main/assets/imagens/persona%202.png" width = "200px" height="200px" >

**Nome**: Fernanda Soares

**Idade**: 26 anos

**Cargo**: Gerente de Marketing

**Gênero**: Feminino

**Cidade**: São Paulo - SP

**Renda média**: R$15.000,00 - R$16.000,00

**Personalidade**: Fernanda é uma mulher muito criativa, inteligente, ágil e esforçada. Ela busca sempre ser positiva e resiliente, tendo em vista que acredita que as pessoas ao seu redor merecem ter contato com a sua melhor versão. Além disso, Fernanda é muito dedicada, principalmente quando sabe que aquilo que ela desempenha terá um impacto positivo na realidade, ou seja, que está trabalhando em algo que acredita.

**Interesses**: Fernanda se interessa muito por design, música, arte e culinária. Ela ama visitar museus, teatros e galerias de arte no seu tempo livre e sempre fica impactada com o fato de que esse tipo de coisa tem o poder de gerar impressões nas pessoas e influenciar suas ações, mesmo que indiretamente. Além disso, ela se interessa muito por livros voltados para o entendimento da mente humana e para a compreensão da influência das propagandas na vida das pessoas.

**Dores com o problema**: No último mês, o banco BTG Pactual, empresa na qual Fernanda trabalha, solicitou uma análise de sentimento das campanhas de marketing veiculadas no instagram da empresa. O time de automação, a pedido do time de marketing, desenvolveu um algoritmo capaz de realizar essas análises. Porém, durante a sua utilização, Fernanda percebeu que é muito difícil compreender o funcionamento da solução, tendo em vista que a interface desenvolvida apresenta uma quantia excessiva de informações concentradas no mesmo lugar, o que sobrecarrega a visão dos usuários. Além disso, apesar de eficiente, Fernanda sente que ainda é possível potencializar os resultados obtidos, mediante um algoritmo ainda mais eficaz. 

**Objetivos com o problema**: Portanto, Fernanda gostaria de obter uma interface mais clara e intuitiva para o recebimento dos dados do algoritmo. Ela sente que, se conseguir compreender melhor todas as informações passadas, obterá resultados mais vantajosos. Ademais, com um algoritmo mais eficiente e com menos erros, é possível desenvolver estratégias mais certeiras e bem estruturadas, visando a melhoria da satisfação dos clientes do banco. 

## User stories
As histórias do usuário (ou user stories) representam uma técnica de gerenciamento de projetos que ajuda as equipes de desenvolvimento a compreender melhor as necessidades e expectativas do seu público alvo, no qual vão utilizar o sistema. Elas são escritas com base em três elementos: no papel do usuário, em sua necessidade e no valor que será agregado a ele. 
Para facilitar o entendimento do sistema, utilizamos  os critérios de aceitação e exemplos de teste de aceitação. 
Segue abaixo as user stories:

| **Número** 	| User story 1 	|
|---	|---	|
| **Épico** 	| Pré-processamento dos dados. 	|
| **Persona** 	| Gerente de marketing. 	|
| **História** 	| Eu, como gerente de marketing, quero que os dados sejam selecionados e filtrados sem perder o sentido do sentimento, garantindo a escolha dos comentários tratados para a análise e classificação posterior do sentimento. 	|
| **Critérios de aceitação** 	| - **Critério 1**: É necessário o algoritmo receber dados no formato de texto, extraídos de uma base de dados com nomes de colunas, e campos com as entradas de texto das postagens do Instagram, no formato .xlsx, para dar início ao pré-processamento de dados. <br><br>- **Critério 2**: É necessário a criação de um conhecimento estruturado, para a modelagem dos dados, utilizando técnicas de análise de sentimentos, para a extração da informação subjetiva em textos em linguagem natural (oponiões, sentimentos, comentários), sem a perda ou alteração do sentido do texto,  assim a polarização (positiva, negativa, ou neutra) permanece a mais coerente em relação ao sentido original do autor do texto. 	|
| **Testes de aceitação** 	| - **Teste 1  para o critério 1**:  O funcionário tenta alimentar o algoritmo com dados, utilizando um excel no formato indicado, sem alterar os nomes das colunas diretamente no excel:<br>    - Conseguiu: correto.<br>    - Não conseguiu: incorreto, é necessário que essa funcionalidade seja corrigida.<br><br>- **Teste 2 para o critério 1:** O funcionário tenta alimentar o algoritmo com dados, porém alterou o nome das colunas no banco de dados do excel antes: <br>    - Conseguiu: incorreto, é necessário que haja uma condicional que impeça a adição de dados que podem alterar a coluna a ser recebida e tratada.<br>    - Não conseguiu: correto.<br><br>- **Teste 1 para o critério 2**: O funcionário dá entrada no algoritmo utilizando dados com emojis:<br>    - Conseguiu: correto, foi possível converter o emoji em texto para a modelagem.<br>    - Não conseguiu: incorreto, é preciso verificar o tratamento de emojis no algoritmo, para não perder informações do sentimento do usuário. 	|

<br>
<br>

| **Número** 	| User story 2 	|
|---	|---	|
| **Épico** 	| Pré-processamento dos dados. 	|
| **Persona** 	| Líder da área de automação. 	|
| **História** 	| Eu, Como funcionário de automação, quero que os métodos de tratamento dos dados sejam escolhidos com foco na análise de sentimento. 	|
| **Critérios de aceitação** 	| **Critério 1:** É necessário que os tratamentos dos dados sejam escolhidos para criar um modelo de Bag of Words<br><br> **Critério 2:** É necessário que seja escolhido um número mínimo de parâmetros, sendo esse maior que 1.{retirada de acentos, retirada de artigos, tratamento emojs} <br><br> **Critério 3:** É necessário que haja uma indicação dos melhores métodos a serem utilizados para um resultado específico (isso pode estar estruturado em comentários no código). 	|
| **Testes de aceitação** 	| **Teste 1 para o critério 1 e para o critério 2:** O funcionário não escolhe nenhum método de tratamento de dados e tenta passar para a etapa de modelagem: <br> - Conseguiu: incorreto, é necessário que haja um pré processamento de dados antes de passar para a próxima etapa. Portanto, essa possibilidade deverá ser corrigida. <br> - Não conseguiu: correto. <br><br> **Teste 1 para o critério 3**: O funcionário utiliza os métodos indicados e consegue o melhor resultado após o pré-processamento de dados: <br> - Conseguiu: correto. <br> Não conseguiu: é preciso revisar os métodos indicados pelo código, a fim de apresentar as melhores opções para o usuário final. 	|
<br>
<br>

| Número | User story  3 |
|---|---|
| **Épico** | Modelagem do algoritmo. |
| **Persona** | Líder da área de automação. |
| **História** | Eu, como líder da área de automação, desejo separar os dados entre teste e treino para estruturar o modelo e receber os resultados da análise de sentimento.  |
| **Critérios de aceitação** | **Critério 1**:  Para que seja possível realizar a modelagem, é necessário utilizar os dados tratados anteriormente. <br><br> **Critério 2**: Os dados de teste e treino devem estar divididos de forma que o modelo receba 70% dos dados para treino e 30% para teste.<br><br> **Critério 3**: Os resultados não podem apresentar métricas perfeitas, tendo em vista que isso demonstra um vício do algoritmo aos dados fornecidos. |
| **Testes de aceitação** | **Teste 1 para o critério 1**: O funcionário de automação tenta utilizar os dados não tratados para treinar o modelo.  <br>- Conseguiu: incorreto, não deve ser possível treinar o modelo utilizando dados não tratados.<br>- Não conseguiu: correto.<br><br>**Teste 2 para critério 1**: O funcionário da área de automação tenta utilizar os dados anteriormente tratados para o treinamento do modelo.<br>- Conseguiu: correto.<br>- Não conseguiu: incorreto, não pode haver erros no processo de utilização dos dados tratados, essa funcionalidade precisa ser revisada e corrigida.<br><br>**Teste 1 para critério 2**: O funcionário de automação tenta treinar o modelo utilizando proporções de 50% e 50% ou com uma proporção de dados maior para teste do que para treino.<br>- Conseguiu: incorreto, é necessário que haja uma maior proporção de dados para treino do que para teste (baseado nas condições de construção de inteligências artificiais), visando um resultado relevante .<br>- Não conseguiu: correto<br><br>**Teste 2 para critério 2**: O funcionário de automação tenta treinar o modelo utilizando uma maior proporção de dados para treino quando comparada aos dados de teste (respeitando a proporção mínima de 30 e 70).<br>- Conseguiu: correto.<br>- Não conseguiu: incorreto, deve ser possível realizar a modelagem com essa proporção, portanto, essa funcionalidade precisa ser corrigida. <br><br>**Teste 1 para critério 3**: O modelo acerta todas as análises e apresenta métricas perfeitas.<br>- Incorreto: caso essa situação ocorra, é necessário revisar e corrigir o modelo preditivo, tendo em vista que ele se encontra viciado nos dados fornecidos.<br><br>**Teste 2 para critério 3**: O modelo erra a maioria das análises e apresenta métricas abaixo daquelas oferecidas pelo time de automação.<br>- Incorreto: diante dessa situação, é necessário que o modelo criado seja revisitado, tendo em vista que apresenta erros que não podem ser tolerados. |

<br>
<br>

| Número | User story 4. |
|---|---|
| **Épico** | Validação do algoritmo. |
| **Persona** | Líder da área de automação. |
| **História** | Eu, como líder da área de automação, quero que o modelo seja capaz de fornecer análises com base em métricas de avaliação para que seja possível gerar gráficos que possibilitem a visualização dos resultados. |
| **Critérios de aceitação** | **Critério 1**: A solução deve ser capaz de fornecer análises sobre os resultados dos diferentes modelos.<br><br>**Critério 2**: O modelo  deve ser capaz de gerar gráficos para analisar a performance de cada modelo.<br><br>**Critério 3**: As métricas utilizadas devem ser comuns para todos os modelos, visando a comparação dos resultados. |
| **Testes de aceitação** | **Teste 1 para o critério 1**:  O Líder da área de automação tenta executar as funções de análise do notebook:<br>- Conseguiu: correto.<br>- Não conseguiu: incorreto, essa funcionalidade precisa estar funcionando para que seja possível analisar os resultados.<br><br>**Teste 2 para o critério 1**:  O Líder da área de automação executa as funções de análise do notebook, sem executar previamente o modelo:<br>- Não gera análise: correto.<br>- Gera análise: Errado, uma vez que os dados não existem, não seria possível gerar a análise, sendo necessário revisar de onde estão vindo os dados da análise.<br><br>**Teste 1 para critério 2**: O Líder da área de automação tenta executar as funções de visualização de gráficos:<br>- Conseguiu: correto.<br>- Não conseguiu: Incorreto, provavelmente há um erro na geração do gráfico ou uma inconsistência na visualização, sendo necessário revisar os resultados obtidos ou o processo de geração do gráfico.<br><br>**Teste 1 para o critério 3**: O líder da área de automação tenta executar a comparação entre os diferentes modelos utilizando as mesmas métricas:<br>- Conseguiu: correto.<br>- Não conseguiu: Incorreto, essa funcionalidade precisa ser corrigida ou implementada.<br><br>**Teste 2 para o critério 3**: O líder da área de automação tenta executar a comparação entre os diferentes modelos utilizando métricas distintas:<br>- Conseguiu: Incorreto, não deve ser possível realizar comparações utilizando métricas distintas.<br>- Não conseguiu: correto. |

<br>
<br>

| Número | User story  5 |
|---|---|
| **Épico** | Visualização dos resultados da análise de sentimento. |
| **Persona** | Gerente de marketing; líder da área de automação. |
| **História** | Eu, como gerente de marketing, desejo visualizar a performance e repercussão de cada propaganda, para analisar o impacto das publicações na empresa. |
| **Critérios de aceitação** | **Critério 1**: O projeto deve ser capaz de fornecer, em uma interface, gráficos com base nos dados de desempenho de cada propaganda analisada. |
| **Testes de aceitação** | **Teste 1 para o critério 1**:  O gerente de marketing tenta visualizar as informações na interface, após a execução do modelo.<br>- Sucesso na visualização gráfica do desempenho das propagandas: correto.<br>- Os gráficos não foram exibidos na interface: Incorreto, o processo de geração dos gráficos ou de exibição precisam ser revisados<br><br>**Teste 2 para o critério 1**: O gerente de marketing tenta visualizar as informações na interface sem executar o modelo <br>- Sucesso na visualização gráfica do desempenho das propagandas: Incorreto, pois não deveriam existir dados para gerar a visualização<br>- Aviso que o modelo não foi executado:Correto<br>- Erro do serviço de visualização: Errado, pois o cliente deveria ficar ciente que o modelo não rodou ainda. |
