## Trabalhando com dados no Google Sheets

[Dados para exemplo](https://docs.google.com/spreadsheets/d/1nrGBfid4YOf7M-kx0Mq9jSrA_Kao8IGNvqJJB5KTzGM/edit?usp=sharing)

Configure o formato (mundial ou norte-americano): `File -> Spreadsheet Settings -> Selecione o país`

### Tipos de valores no Google Sheets

* **Strings** - valores baseados em texto
* **Números** - valores numéricos
* **Datas** - valores temporais

### Maior segredo do Google Sheets

* Formatação condicional que faz zebra nas linhas
	* `Format -> Conditional Formatting -> Format cells if -> Custom Formula is -> =ISEVEN(ROW())`

### Principais fórmulas e funções

[Lista completa aqui](https://support.google.com/docs/table/25273?hl=pt)

Mais usadas:

* Concatenar: `=CONCATENATE(D1, ", ",E1 )` e `CONCAT`
* Dividir: `=SPLIT(F1, ", ")`
* Localizar e substituir: `Find and Replace`  
* Substituir: `=SUBSTITUTE(H2, ",", "")`
* Multiplicar: `=PRODUCT()`
* Média: `=AVERAGE()`
* Mediana:  `=MEDIAN()`
* Soma: (e outras operações)= `=SUM()`
* Importar tables: `IMPORTHTML(“http://link.com”, “table”, 2)
* Transpor linhas para colunas e vice-versa: `=TRANSPOSE('Copy of Dados brutos'!A2:A134)`
