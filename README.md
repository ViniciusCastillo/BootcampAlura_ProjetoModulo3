# BootcampAlura_ProjetoModulo3
## Criação de modelos de projeção de Covid para o Brasil

### Introdução
Neste projeto criei alguns modelos de projeção de óbitos Covid-19 e fiz comparações entre eles para avaliar qual traria uma maior aderência com a base de teste. 
Fiz o modelo projetando os dados do Brasil como um todo e depois por Região para ver se conseguiria uma aderência melhor com o que ocorreu no Brasil. 

### Tratamento dos Dados
O tratamento dos dados foram feitos em duas etapas, a primeira etapa eu reduzi a base coletada do [Brasil.io](https://brasil.io/dataset/covid19/caso_full/), mantendo apenas as cidades mais populosas e as informações consolidadas por estado. Também retirei as informações do mês de dezembro, por saber que tivemos problemas com os dados no Brasil, conforme esta [notícia do G1]( https://g1.globo.com/saude/coronavirus/noticia/2021/12/16/sem-dados-de-5-estados-brasil-registra-173-mortes-por-covid-em-24-horas-sistemas-seguem-com-problema-uma-semana-apos-ataque-hacker.ghtml). Esta primeira etapa foi realizada neste notebook: [TratandoBaseOriginal](https://github.com/ViniciusCastillo/BootcampAlura_ProjetoModulo3/blob/main/notebooks/TratandoBaseOriginal.ipynb).

A segunda parte foi separa esses dados em bases específicas e criar uma base consolidada do total do Brasil e outra consolidada por Região. Este tratamento foi feito neste notebook [Funcoes_Dados.ipynb](https://github.com/ViniciusCastillo/BootcampAlura_ProjetoModulo3/blob/main/notebooks/Funcoes_Dados.ipynb), junto com diversas funções que criei para facilitar na hora de avaliar os modelos.

### Projeções
As [projeções, comparações e análises](https://github.com/ViniciusCastillo/BootcampAlura_ProjetoModulo3/blob/main/notebooks/Comparacao_Projecoes.ipynb) foram feitas utilizando o [Facebook Prophet]( https://facebook.github.io/prophet/docs/quick_start.html#python-api) e depois comparadas utilizando as métricas de medição de erro MAE (Mean Absolute Error), RMSE (Root Mean Squared Error) e MAPE (Mean Absolute Percentage Error).

### Conclusões
Depois de alguns testes percebi que as projeções mais aderentes eram obtidas quando eu mesmo definia os changepoints e utilizando a sazonalidade anual que estava sendo desabilitada por padrão. Por exemplo, no caso do total do Brasil, ao utilizar a sazonalidade anual eu consegui reduzir o MAPE contra a base de teste de 58% para 33%.

Uma expectativa que eu tinha de ter uma maior precisão ao fazer as projeções por região e somar para ter uma visão do Brasil mais precisa, foi derrubada antes mesmo da comparação final quando não conseguir criar modelos aderentes por região. Retirando o Norte e o Nordeste que o modelo conseguiu ficar com um MAPE menor do que 40%, as demais regiões estavam com erros muito grandes no melhor modelo que consegui chegar.
Logo, quando comparei a soma desses modelos com a projeção do Brasil como um todo, ele apresentou um erro maior, um MAPE de 46% contra os 33% obtidos com o dado consolidado do Brasil.

Infelizmente não tive tempo de continuar as análises e projeções devido ao tempo para entrega do projeto estar perto do fim, porém ficam as ideais do que eu queria testar:
* A mesma análise da Região, mas fazendo por Unidade da Federação
* Fazer uma projeção das 10 cidades mais populosas e extrapolar para o Brasil e ver se teríamos uma boa aderência
* Repetir todas as análises utilizando a semana epidemiológica ao invés dos dados diários

Bom, é isso pessoal, espero que gostem das análises e até a próxima!
