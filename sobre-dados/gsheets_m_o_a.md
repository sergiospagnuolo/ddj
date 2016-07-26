## Utilizando os dados em Google Sheets

*Este tutorial usa a versão em inglês do Google Sheets*

* Acesse o banco de dados da OCDE para baixarmos a tabela que utilizaremos aqui, sobre o índice de confiança empresarial em vários países e regiões.
	* **[Link para banco de dados](https://data.oecd.org/leadind/business-confidence-index-bci.htm)**  
___
* Acima do gráfico, clique no botão azul de *Download* e baixe o item *Full Indicator Data*. Isso vai carregar um arquivo .csv (ou seja, valores separados por vírgula).   
___
* Depois de baixar o arquivo, abra o seu [Google Sheets](https://docs.google.com/spreadsheets), e crie uma nova planilha, onde vamos subir esses dados.   
	* Não se esqueça de dar um nome para a planilha, como “Índice de Confiança Empresarial (BCI) - Fonte: OCDE”  
___
* Agora vamos carregar o arquivo.
	* `File -> Importar -> Upload`, depois disso, `Replace Current Sheet` ou até `Insert New Sheet`.
	* Mude o nome de sua aba/planilha, clicando na flechinha embaixo e escolhendo a opção `Rename`. Isso é particularmente importante para você não ficar perdido depois.
	* Seu arquivo deve ter quase **17 mil linhas** de dados!  
___
* Agora, nós vamos começar a extrair o que a gente precisa disso.
	* Duplique sua planilha. Isso é muito importante, porque se alguma der errado mais para frente, você terá facilmente os dados originais aí. Para isso, clique na flecha para baixo da aba e escola `Duplicate`.
	* Vamos selecionar apenas os países do BRIC (Brasil - BRA, Russia - RUS, Índia - IND e China - CHN).
	* Crie uma nova aba, desta vez vazia. Nela vamos colocar apenas os indicadores que vamos selecionar.
	* Copie apenas a primeira linha da planilha duplicada, com os cabeçalhos das colunas, e cole na mesma posição da nova aba.
	* Agora, utilizando `CTRL + F` ou `CMD + F`, vamos buscar pela sigla que designa cada país. No caso, comecemos pelo *BRA*. Você vai reparar que os resultados selecionados estão destacados. Agora, basta copiar e colar todas as linhas com *BRA* e colar na aba vazia.
	* Façamos o mesmo para os outros países.
	* De um nome para sua aba nova, como “BRIC data”.  
___
* Vamos limpar essa tabela, retirando e acrescentando informações para conseguirmos organizar melhor os dados.
	* Primeiro, apaguemos as colunas que não vamos utilizar, como *INDICATOR*	, *SUBJECT*, *MEASURE*, *FREQUENCY* e *Flag Codes*. Para isso, selecione toda a coluna e com o botão direito, clique `Delete`. 
	* Agora, vamos acrescentar o nome por extenso de cada país. Na coluna *Location*, clique na flechinha e então `Insert 1 right`, para inserir uma coluna à direita, onde colocaremos os valores. Depois, selecione a coluna *Location* inteiramente, copie e cole na coluna recém-criada.
	* Com a coluna inteiramente selecionada, vamos substituir esses valores. Vá em `Edit -> Find and Replace`, e substitua o valor *BRA* por *Brasil*. **CUIDADO: esse tipo de recurso é perigoso quando usado sem atenção, pois pode alterar valores em outras abas e colunas sem sua intenção. Certifique-se de que você está só com essa coluna selecionada**.
		* Faça o mesmo com os outros países.
	* Para nossa melhor compreensão, vamos mudar o nome das colunas. `*Location*(1) -> *Sigla*`, `*Location*(2) -> *pais*`, `*Time* -> *data*`, `*Value* -> *indice*`
	* Para deixar o índice mais compreensível, vamos delimitar o número casas decimais. Selecione apenas a coluna *indice* e vá em `Format -> Number -> 1,234,6`. Isso significa que vai sobrar apenas uma casa decimal depois da vírgula em vez das quatro casas anteriores.  
	* Por fim, vamos apagar linhas e colunas que apenas atrapalham. Atalho para o fim da planilha, aperte `CTRL + Seta para Baixo` ou `CMD + Seta para Baixo`, o mesmo vale para cima.
___

* Do jeito que o dado está agora, parece bacana. Mas esse formato, onde uma coluna possui várias categorias, pode ser conflitantes para diversos leitores de gráficos. A vantagem desse formato é que, por exemplo, quando não houver datas para alguns países e sim pra outros, isso não seria um grave problema. Ferramentas mais avançadas, como D3.js e Raw, reconhecem melhor esses dados, mas HighCharts e ChartBuilder, por exemplo (e muitos outros), têm problemas com esse formado. O jeito vai ser transformar os países em colunas - sem categorias, criando outra aba.
	* Crie uma nova aba vazia, dê nome a ela (como *BRIC por país*) e, como as das são iguais para todos os países, vamos criar a primeira coluna A como data. 
	* Conseguimos reparar que os dados temporais seguem um padrão, mês a mês, mas nem todos os países têm todos os meses. A Rússia, por exemplo, tem os dados mais antigos, desde 1992, e o Brasil, desde 1995. China e Índia começaram a ser averiguadas apenas a partir de 2000. A nova tabela tem que partir, então, a partir do dado número mais recente, da Índia, que data de maio de 2000 (5/1/2000) até novembro de 2015 (11/1/2015).    
	* Selecionemos, então, esse período para cada um dos países, e os copiemos para a nova aba sob a o cabeçalho de cada país.
	* Outra forma de fazer isso é copiar todos os dados, organizar por data em ordem crescente e cortar pelo topo.
	* Crie também uma nova aba da *BRIC Data* (pode chamar de *Para analise BRIC data*) removendo as linhas que não fazem parte da nossa análise, ou seja, tudo que não está entre maio 2000 (5/1/2000) até novembro de 2015 (11/1/2015). Por motivos óbvios, o comparativo deve ser feito no mesmo intervalo, e, como há mais dados de certos países do que para outros, o resultado sairá distorcido quando analisarmos.   
	* O ideal seria ter dados para todos para uma comparação mais longa, mas, como em dados tabulares cada coluna tem que corresponder a um número de linhas, e a gente não pode inventar dados, esse é o jeito que se dá. Mesmo assim, 15 anos de dados é bastante coisa.    
___
* Utilizando o [Chartbuilder](http://voltdatalab.github.io/chartbuilder-volt/build/index.html) a gente já consegue ver parte do resultado desejado - a evolução da confiança empresarial em cada país.  
___
* Agora, vamos analisar melhor esses números através da *Tabela Dinâmica* do Google Sheets, utilizando aquela aba *Para analise BRIC data*.
	* Selecione toda a planilha para se certificar que nenhum valor ficará de fora e vá em `Data -> Pivot Table`. 
	* O que queremos é saber qual o país teve o melhor desempenho geral ao longo de todo esse período.
	* Em `Rows`, agruparemos pela coluna `pais`.
	* Em `Values`, utilizaremos o `indice`. Por default, os valores para cada categoria serão somados. Mas não é isso que a gente quer, a gente quer a mediana do período. Selecionemos então `median`. Apenas por curiosidade, selecionemos também `average`. A mediana serve para evitar dados que fogem muito da realidade, como, por exemplo, durante a crise, que naturalmente afetou muito os países emergentes mais do que em outros anos. 
	* Podemos ver que, nos 15 anos em questão, no geral e nos dois cenários (média e mediana), o Brasil gozou de melhor confiança empresarial. Segundo a metodologia da OCDE, 100 é o estado normal das coisas.
	* Mudem o título dessa aba (como *Análise 1*).  
___
* No entanto, talvez essa não é a única análise a ser feita, embora nos dê algumas respostas. Uma outra análise, talvez melhor, é falar sobra a dispersão da confiança nesses países, ver qual o país oscilou menos no período sobre a normalidade (100) - afinal um país estável é mais confiável do que um país volátil. 
	* Para isso, temos que calcular o *desvio padrão* de cada um, ainda na *Análise 1*. A *variância* é a soma dos quadrados dos desvios dividida pelo número de ocorrências e nos diz o quanto os valores se afastaram da média, enquanto o *desvio padrão* faz a mesma coisa, mas na mesma unidade de medida que a variável.
	* Assim, vemos que a Índia é o país mais que menos oscilou, seguida do Brasil.  
___
* Para analisar como os países se saíram em relação um ao outro, e não em relação à normalidade, podemos calcular a oscilação deles um sobre os outros.  
	* Vamos criar duas únicas novas linhas ao fim de nossa aba *Para analise BRIC data*, e, embaixo do índice, calcula a média dos países. 
	* Criemos a uma nova coluna, chamada *variacao*, e acrescentemos a seguinte, e simples, fórmula: `=SUM(CELULA EM QUESTAO-COLUNA DA CELULAR + $ + CELULA COM A MEDIA)`. Apliquemos, assim, o valor a todas as outras células, arrastando o pequeno quadrado azul ao fim da célula a qual acabamos de acrescentar a fórmula.
	* Assim, saberemos quanto cada país oscilou sobre a média dos países em questão, não sobre a normalidade (100).
___

* Façam o mesmo processo só com os países OCDE em uma nova aba, para depois os compararmos, lembrando dos intervalos em questão, maio 2000 (5/1/2000) até novembro de 2015 (11/1/2015).

___

* Vamos criar, agora, ainda uma nova aba juntando OCDE e BRIC (chamada “BRIC + OCDE data”) e preparar os dados cruzar os resultados por ano, em vez de meses.
	* Copie os resultados da aba da OCDE para o da nova aba. 
	* Vamos acrescentar uma nova coluna para classificar uma *categoria*, discernindo o que são os BRIC e o que é a OCDE. 
	* Vamos criar ainda uma nova coluna, definindo os apenas os anos (sem os meses).
	* Acontece que há anos menores que os outros, como 2000 e 2015. Vamos então cortar fora 2000 e dar o perdão da nossa senhora da licença poética para 2015, já que só falta um mês pra completar esse ano. Mas, antes de cortar, duplique a tabela, você pode querer comparar OCDE e BRIC por mês. 
	* Faça uma tabela dinâmica simples comparando os dois períodos completos, e, inclusive, fazer aquele processo de transformar os países em colunas, mas dessa vez sem CTRL C + V, apenas na tabela dinâmica.
	* Faça uma tabela dinâmica comparando, agora, os anos.
