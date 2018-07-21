Avaliação Técnica Analista de Dados - MaxMilhas
================
Yara Barretto
7/18/2018

Análises propostas:
===================

### Análise 1: Tempos de Resposta das Buscas

1.  Qual é a análise:
    Analisar o tempo de resposta entre o início e fim da busca e entre fim da busca e recebimento.

2.  Motivação da análise:
    Verificar se as buscas demoram a trazer resultados.
    Identificar padrões de buscas que se mostram mais efetivos, identificar também quais padrões de buscas são menos efetivos.
    Identificar pontos onde a busca pode ser melhorada.

3.  Como executar:

-   Verificar outliers e seu volume, como tempo de respostas negativos ou muito longos.
-   Criar novo DataFrame com os dados, excluindo os outliers (caso seu volume seja baixo), para obtermos estatísticas descritivas mais corretas e realistas.
-   Realizar um summary na coluna 'qtd\_voos\_recebidos', para obtermos resumo simples dos dados, como Min., Max., 1st Qu. Mediana, Média, 3st Qu. e quantidade de NAs(dados não retornados).
-   Verificar quantidade de 'missing values', caso a quantidade for muito alta, procurar identificar porque o dado não foi armazenado.
-   Plotar gráficos para verificar correlações entre as variáveis disponíveis para análise e o tempo de resposta entre o início e o fim da busca e entre o fim da busca e o recebimento, exemplos:
    -   Tempo de resposta x Qtd de voos recebidos
    -   Tempo de resposta x Tipo de Voo
    -   Tempo de resposta x Número de passageiros
    -   Tempo de resposta x Dias da semana
    -   Tempo de resposta x Dias da semana + Horário
    -   Tempo de resposta x Usuário com id identificado
    -   Tempo de resposta x Usuário com id não identificado
-   Verificar quais variáveis afetam mais o tempo de resposta da busca.
-   Aprofundar a análise em alguns pontos mais relevantes.
-   Buscar e propor soluções para a melhoria do tempo de resposta.
-   Propor novos dados a serem guardados nas buscas para que possa auxiliar em análises futuras.

### Análise 2: Quantidade de Voos Retornados nas Buscas

1.  Qual é a análise:
    Analisar a quantidade de voos que são retornados nas buscas mais realizadas, analisar também se há padrão de buscas que retornam poucos resultado.

2.  Motivação da análise:
    Verificar se as buscas mais realizadas trazem quantidade considerada como ideal para o cliente que está realizando a pesquisa.
    Identificar padrões de buscas que retornam mais resultados e padrões de buscas que retornam menos resultados.

3.  Como executar:

-   Verificar outliers e seu volume, como volume de voos retornados negativos ou &gt; 400.
-   Criar novo DataFrame com os dados, excluindo os outliers (caso seu volume seja baixo), para obtermos estatísticas descritivas mais corretas e realistas.
-   Realizar um summary na coluna 'qtd\_voos\_recebidos', para obtermos resumo simples dos dados, como Min., Max., 1st Qu. Mediana, Média, 3st Qu. e quantidade de NAs(dados não retornados).
-   Verificar quantidade de 'missing values', caso a quantidade for muito alta, verificar porque o dado não está sendo armazenado.
-   Plotar gráficos para verificar correlação entre as variáveis disponíveis para análise e a quantidade de voos recebidos, exemplos:
    -   Qtd de Voos Recebidos x Tipo de Voo
    -   Qtd de Voos Recebidos x Classe
    -   Qtd de Voos Recebidos x Direção
    -   Qtd de Voos Recebidos x Número de passageiros
    -   Qtd de Voos Recebidos x Dias da semana
    -   Qtd de Voos Recebidos x Dias da semana + Horário
    -   Qtd de Voos Recebidos x Usuário com id identificado
    -   Qtd de Voos Recebidos x Usuário com id não identificado
    -   Qtd de Voos Recebidos x Tempo de resposta
-   Verificar quais variáveis mostram afetar o número de voos recebidos.
-   Aprofundar a análise nos pontos relevantes.
-   Buscar e propor soluções para retornar mais voos onde a quantidade é considerada pequena. Uma solução que pode ser buscada é a adição de novos fornecesores de voos.
-   Dentro dessa análise, pode-se verificar as quantidade de melhores preços na MaxMilhas, verificando se tem ou não relação com o número de voos retornados.
-   Propor novos dados a serem guardados nas buscas para que possa auxiliar em análises futuras.

### Análise 3: Análise de Perfil do Buscador

1.  Qual é a análise:
    Usar os dados para encontrar um perfil dominante de buscador, e também perfis específicos. Exemplo de Perfil: 'Voos nacionais, que saem de SP, com duração de 3 a 7 dias, 1 adulto de classe econômica com usuário não identificado'.

2.  Motivação da análise:
    Priorizar correções e demandas das buscas relacionadas aos Perfis de busca dominantes. Criação de Campanhas para Perfis específicos, com a possibilidade de análise clara dos resultados.

3.  Como executar:

-   Verificar quais dados podem ser usados para montagem do perfil.
-   Transformar dados que possíveis de serem transformados em fator, para facilitar a visualização dos dados no R.
-   Analisar com summary as variáveis escolhidas e plotar alguns resultados para que possam ser visualizados de forma mais clara.
-   Montagem do Perfil com os resultados análisados no passo anterior.
-   Montagem de Perfil diferente do dominante geral.
-   Propor novos dados a serem guardados nas buscas para que possa auxiliar em análises futuras.

A análise escolhida para ser realizada é a Análise 3
----------------------------------------------------

Preparando os dados para serem analisados:

### Analisando Variáveis

##### Usuários Identificados

Apenas 12% dos usuários que realizam buscam são identificados:

| Buscas com Idusers | Buscas sem Idusers |
|--------------------|--------------------|
| *12%*              | *88%*              |

#### Companhias Aéreas

As companhias aéreas Azul, Gol e Tam retornam volumes semelhantes, já a Avianca retorna menos resultados: ![](Search_mm_YaraBarretto_files/figure-markdown_github/ciasaeras-1.png)

#### Tipos de Voo

Nos tipos de Voos buscados, Ida e Volta apresenta volume 6% maior: ![](Search_mm_YaraBarretto_files/figure-markdown_github/tipo-1.png)

#### Dias Entre Viagens

A média de dias entre viagens é 5, porém viagens muito compridas puxam a média para cima, a mediana nos apresenta um resultado mais relista, no caso a mediana é 1 e 75% das viagens se concentram em até 6 dias.

    ##      Min.   1st Qu.    Median      Mean   3rd Qu.      Max. 
    ##       0.0       0.0       1.0       4.9       6.0 2191460.0

![](Search_mm_YaraBarretto_files/figure-markdown_github/dias-1.png)

#### Quantidade de Adultos

82% dos clientes buscam passagens para apenas uma pessoa, 15% para duas pessoas e apenas 3% para 3 pessoas ou mais.
![](Search_mm_YaraBarretto_files/figure-markdown_github/qtdadult-1.png)

#### Quantidade de Crianças e Bebês

Apenas 6% dos clientes buscam passagens para crianças, sendo que 4% delas buscam passagem para apenas uma criança. Apenas 2% dos clientes buscam passagens incluindo bebês. Podemos ver nos histogramas abaixo que a maioria pesquisa passagem para apenas uma criança ou bebê.
![](Search_mm_YaraBarretto_files/figure-markdown_github/qtdcb-1.png)![](Search_mm_YaraBarretto_files/figure-markdown_github/qtdcb-2.png)

#### Voo Internacional x Voo Nacional

89% dos clientes buscam voos nacionais, 11% buscam voos internacionais. ![](Search_mm_YaraBarretto_files/figure-markdown_github/vooint-1.png)

#### Direção dos Voos

89% dos clientes buscam voos nacionais, os outros 11% dividem em 9% saindo do Brasil e 2% voltando para o Brasil. ![](Search_mm_YaraBarretto_files/figure-markdown_github/dir-1.png)

#### Classe

99,7% dos clientes buscam voos de classe econômica. ![](Search_mm_YaraBarretto_files/figure-markdown_github/classe-1.png)

### Perfil Encontrado

Podemos dizer que o Perfil dominante do buscador é:
Usuários não identificados buscando por passagens de ida e volta nacionais para apenas uma pessoa adulta com duração de 1 dia e para viajar de classe econômica.

### Perfil 2 - Clientes que buscam passagens internacionais

Podemos criar um novo Data Frame contendo somente as buscas internacionais e realizar a mesma análise.

##### Usuários Identificados

Apenas 12% dos usuários que realizam buscam são identificados, mesmo resultado apresentado no perfil dominante geral:

| Buscas com Idusers | Buscas sem Idusers |
|--------------------|--------------------|
| *12%*              | *88%*              |

#### Companhias Aéreas

As companhias aéreas Tam, Gol e Azul, retornam volumes semelhantes, já a Avianca retorna menos resultados: ![](Search_mm_YaraBarretto_files/figure-markdown_github/ciasaerasi-1.png)

#### Tipos de Voo

Nos tipos de Voos buscados para viagens internacionais, Ida e Volta apresenta volume de 62%: ![](Search_mm_YaraBarretto_files/figure-markdown_github/tipoi-1.png)

#### Dias Entre Viagens

A média de dias entre viagens internacionais é 11, porém viagens muito compridas puxam a média para cima, a mediana nos apresenta um resultado mais relista, no caso a mediana é 5 e 75% das viagens se concentram em até 11 dias. Temos muitos 0 na base, é um ponto que deve ser verificado.

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##     0.0     0.0     5.0    10.9    11.0   396.0

![](Search_mm_YaraBarretto_files/figure-markdown_github/diasi-1.png)

#### Quantidade de Adultos

77% dos clientes que buscam passagens internacionais buscam para apenas uma pessoa, 19% para duas pessoas e apenas 3% para 3 pessoas ou mais.
![](Search_mm_YaraBarretto_files/figure-markdown_github/qtdadulti-1.png)

#### Quantidade de Crianças e Bebês

Apenas 5% dos clientes buscam passagens para crianças, sendo que 4% delas buscam passagem para apenas uma criança. Apenas 1% dos clientes buscam passagens incluindo bebês. Podemos ver nos histogramas abaixo que a maioria pesquisa passagem para apenas uma criança ou bebê.
![](Search_mm_YaraBarretto_files/figure-markdown_github/qtdcbi-1.png)![](Search_mm_YaraBarretto_files/figure-markdown_github/qtdcbi-2.png)

#### Direção dos Voos

79% dos Clientes buscam Voos internacionais partindo do Brasil, 18% partindo de outros países para o Brasil e 3% bucam voos com partidas e destinos internacionais.
![](Search_mm_YaraBarretto_files/figure-markdown_github/diri-1.png)

#### Classe

97,3% dos clientes buscam voos de classe econômica. ![](Search_mm_YaraBarretto_files/figure-markdown_github/classei-1.png)

### Perfil Encontrado

Podemos dizer que o Perfil dominante do buscador de passagens internacional é:
Usuários não identificados buscando por passagens de ida e volta para apenas uma pessoa adulta com duração de média de 11 dias e para viajar de classe econômica.
