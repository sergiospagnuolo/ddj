## Formatos de dados

### Dados tabulares

método de organização de dados principalmente em colunas e linhas, onde tipicamente cada coluna tem um valor correspondente na linha. É o que você organiza num Excel, por exemplo. É utilizado para preparar visualização, analisar pequenos volumes de dados (com menos colunas) e organizar dados para "subir" em um banco de dados mais robustos, por exemplo.

   * [CSV](https://en.wikipedia.org/wiki/Comma-separated_values) - Comma-separated values - [Exemplo](https://raw.githubusercontent.com/voltdatalab/graficos/gh-pages/dados/Pedaladas%20fiscais%20na%20Caixa_fonte%20TCU%20com%20dados%20da%20Caixa.csv)
   * [TSV](https://en.wikipedia.org/wiki/Tab-separated_values) -  [Tab-separated values](https://raw.githubusercontent.com/voltdatalab/dados/master/meio-ambiente/dadosbarragensmineracao.tsv)
   * [Tabelas de HTML](http://www.w3schools.com/html/html_tables.asp)
   * [Tabelas em markdown](http://fletcher.github.io/MultiMarkdown-5/tables.html)

#### Ferramentas úteis - [Google Sheets](https://www.google.com/sheets/about/) / [Table Generator](http://www.tablesgenerator.com/) / [Excel](https://office.live.com/start/Excel.aspx) / [Conversor](http://www.convertcsv.com/csv-to-csv.htm)

#### Exemplo

| ano  | 1      | 2 | 3 | 4 | 5       | 6       |
|------|--------|---|---|---|---------|---------|
| 1974 | 0      | 0 | 0 | 0 | 818990  | 818990  |
| 1984 | 30847  | 0 | 0 | 0 | 936070  | 966917  |
| 1994 | 94126  | 0 | 0 | 0 | 763129  | 857255  |
| 2004 | 130527 | 0 | 0 | 0 | 806968  | 937495  |
| 2014 | 341181 | 0 | 0 | 0 | 1106440 | 1447621 |

---

### *Arrays*, objetos e *arrays* de objetos

* __*Array*__ é uma [forma específica](https://en.wikipedia.org/wiki/Array_data_structure) de organizar valores e variáveis em certa ordem correspondente a pelo menos um elemento principal e subelementos dentro de uma estrutura pré-concebida. A forma mais simples de um *array* é linear, ou seja, o dado é organizado cronologicamente, por exemplo. Ele é utilizado, muitas vezes, para montar visualizações de dados e estruturar dados em javascript.
    * Exemplo: Roubos em certa região de 2010 a 2015 podem ser armazenados assim: `[100, 150, 100, 80, 75, 75]`, sendo o primeiro valor atribuído a 2010 e o último, a 2015. 
* __Objetos__ são uma construção onde, dentro de uma elemento principal, você especifica seus subelementos. 
    * Exemplo: Roubos em certa região de 2010 a 2015 podem ser armazenados assim: `{"2010": 100}`.
* __*Array* de objetos__ é a junção de ambos.
    * Exemplo: Roubos em certa região de 2010 a 2015 podem ser armazenados assim: `[{"2010": 100}, {"2011": 150}, {"2012": 100}, {"2013": 80},  {"2014": 75},  {"2014": 75}`.
    * Um exemplo muito comum de __*Array* de objetos__ é o formato de [JSON](https://adobe.github.io/Spry/samples/data_region/JSONDataSetSample.html), que estrutura dados de uma forma que muitas ferramentas de visualização de dados e códigos (especialmente javascript) leem. - [Exemplo de JSON](https://raw.githubusercontent.com/voltdatalab/dados/master/economia/pedaladas.json)

#### Ferramentas úteis: [CSV to JSON](http://www.csvjson.com/csv2json) / [CSV to Array](http://www.speqmath.com/tutorials/csv2array/)

---

### Dados relacionais

Organizacão de dados utilizada em muitos bancos de dados, como formato SQL, que permite interação do usuário com os dados através de uma linguagem de busca específica. 

* A estrutura da organização continua em colunas e linhas
* É possível fazer buscas através de *Queries*, ou formulações do que se busca.
* Uma diferença para dados tabulares ou outro tipo de organização é que se pode trabalhar com um volume muito maior de dados e criar "inteligência" por trás deles, com cruzamento de dados.
   * Exemplo: Roubos em certa região de 2010 a 2015 podem ser filtrados por microregião, etnia de vítimas e outros dados mais granulares.
* Há ainda os dados chamados de não-relacionais, cuja estrutura basica são coleções de JSON, que permite mais flexibilidade de formatos de dados, mas também mais queries (é mais difícil). [A diferença é explicada aqui](https://www.pluralsight.com/blog/software-development/relational-non-relational-databases) 

#### Ferramentas úteis: [MYSql](https://www.mysql.com/) - [MongoDB](https://www.mongodb.com/)

#### Exemplo de banco de dados relacional: [Banco Mundial](http://data.worldbank.org/)
