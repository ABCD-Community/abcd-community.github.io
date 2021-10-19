---
title: CISIS Linguagem de formato
description: If Standard, means that command/function has the same usage/result both in ISIS and CISIS. If CISIS is specified, means that it is available only in CISIS. Functions that are enhanced in CISIS, are presented with Standard/CISIS notation. (item always present)
lang: pt
lang-ref: cisis-formatting
---

# Linguagem de formato CISIS

A linguagem de formato CISIS é constituida de uma série de comandos e funcões que permitem a formatação do conteúdo dos campos de dados de bases de dados na tela.

É uma linguagem poderosíssima, e com ela, se torna possível a apresentação do conteúdo de cada registro de uma base de dados na ordem e aparência desejada, principalmente se mesclada com HTML e CSS.

É imprescindível que o bibliotecário domine esta linguagem para que possa criar qualquer tipo de relatório ou apresentações a partir de qualquer uma das bases de dados.

A formatação de registros, pressupõe do bibliotecário, o conhecimento do número de identificação de cada campo de dados que compõe cada registro da base de dados a ser formatada.

Veja abaixo os comandos e suas formas de usar.

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---


# A Linguagem de Formatação para apresentação de valores [REF](/pt/abcd-technology/cisis-formatting/#v---field--selector)

Esta é de longe a mais importante função da Linguagem de Formatação: especificando exatamente quais dados precisam ser tomados e como serão "exibidos" ou "impressos" (para a tela, para uma impressora, para um arquivo, para uma página da web ).
Existem documentos separados para lidar com esta linguagem extensa, por exemplo, o capítulo dedicado no Manual  de Referência ISIS, publicado pela UNESCO (Junho de 2004, capítulo 8, p. 94-122).

Basicamente, existem três tipos de declarações na LF ISIS:
    a) valores de campos, dados como: Vx, onde “V” representa o valor (ou "conteúdo") de um campo com a tag “x”, Vx^a é o valor de um subcampo (^a), do campo x e (Vx/) é o conjunto de todas as ocorrências do campo x separados por uma “nova linha” (/), desde que o parêntese abrace um “grupo repetitivo" de instruções para serem aplicadas a todas as ocorrências (campos repetitivos são uma característica forte e especial do ISIS).
    b) literais ou strings, que podem ser ‘incondicionais’ (aspas simples), |condicionais| (barras verticais – pipes - indicam que a string só será produzida se o campo relacionado está presente) e "repetitivo" (aspas duplas só irá produzir a string na primeira ocorrência de um campo repetitivo).
Aplicativos ISIS na web, como o ABCD, criam páginas web com tags HTML, utilizando este método de acrescentar literais aos valores dos campos, por exemplo,

```
    '<table><tr><td>' Vx '</td><td>' Vy '</td></tr></Table>'
```

Irá exibir respectivamente os campos X e Y em duas colunas de uma tabela em HTML. Note que todos os códigos HTML são cotados (como incondicionais) e os valores extraídos dos campos da base de dados são inseridos referindo-se a eles com a instrução V.

5.  comandos, que podem ser de diferentes tipos, por exemplo:

- comandos de Modo: mhl/u (modo cabeçalho em minúsculas/maiúsculas), mdl (modo de dados maiúsculas/minúsculas) ou mpl/u (modo de revisão maiúsculas/minúsculas);

- em ambientes Windows): comandos de definição de atributos de tela (cores, fontes, caixas) ou links (solicitando ao sistema operacional para abrir outros dados, por exemplo, dados multimídia referenciados em um registro), por exemplo:


LINK (‘clique aqui para o texto integral’, OPENFILE Vx) irá pedir - quando o usuário clica no texto de hiperlink, ‘clique aqui para o texto integral’ - ao Windows para abrir o arquivo cujo nome está em Vx, com o aplicativo Windows associado à extensão do arquivo;

-   o comando REF, que pode recuperar dados de outros registros (no mesmo ou em outra base de dados quando expressamente referenciada), permitindo implementar semi-relações em aplicações ISIS (mas com a vantagem de que a relação é estabelecida apenas em tempo de execução, quando requerida), por exemplo,

```REF(['users']) L(['users']V2),V1)``` 

recuperará o valor do campo 1 no banco de dados 'usuários' se a função L(ookup) tiver encontrado o valor do campo 2 (no banco de dados real) no índice do banco de dados de usuários, para que o MFN do registro possa ser identificado.

- declarações de roteamento condicional

```'IF...THEN... (ELSE....)FI'```

ou mesmo o 

```SELECT [case1 case2...] ELSE- CASE... ENDSEL``` 

podem ser usadas para aplicar declarações de formatação somente aos valores do banco de dados que atendam a determinadas condições.

-   no ambiente CISIS declarações extras da LF estão disponíveis, o mais importante é um comando que realmente irá processar um registro para alterar o conteúdo dos campos. A sintaxe geral é:
```
    proc(x|y...) 
```
onde x ou y pode ser qualquer um dos seguintes: ```'Dxxx' ```(para apagar o campo com tag xxx)

- ```|Axx#|value|#| ``` (para agregar o valor  xx ao campo)

-   As funções, principalmente para operações de “strings” (por exemplo, substr, tamanho, valor) ou numéricas (por exemplo, rmin rmax, rsum ...);




# Estrutura da Listagem de Referência


**Suporte:** 
Se Padrão, significa que comando/função tem o mesmo uso/resultado tanto no ISIS quanto no CISIS. Se CISIS for especificado, significa que está disponível somente em CISIS. As funções que são aprimoradas no CISIS, são apresentadas com a notação Standard/CISISIS. (item sempre presente)

**Tipo de função:**
Especifica o tipo do valor de retorno da função. Os possíveis valores são: Boolean, String e Numeric. (item só aplicável às funções)

**Sintaxe:**
Notação formal do uso do comando/função. (item sempre presente)

**Definição:**
Exposição do uso do comando/função.

**Componentes:**
Exposição de características adicionais do comando/função.

**Notas:**
Esclarece particularidades, restrições e/ou diferenças entre ISIS e CISIS.

**Exemplos:**
Provê um ou mais exemplos de uso do comando/função.

**Veja também:**
Lista comandos e funções relacionadas.


-------



# Caracteres % # '' "" || () / /* @ 




## # - nova linha incondicional

**Suporte:**   Standard

**Sintaxe:**   
`#`

**Definição:** 
Salta para a linha seguinte incondicionalmente.

**Exemplos:** 

```
#,("address:"v3(9,9)+|;  |#),
```

```
(|Name:  |v1^n,c20,|Surname:|v1^s/),###,
```

**Veja também:** 

**/** [conditional  newline]

**%** [reset  blank  line]


---

## % - cancela linha em branco

**Suporte:**  Standard
**Sintaxe:**   **%**
**Definition:** 

Cancela as linhas em branco prévias, se houver.

**Exemplos:** 
```
|Name: |v1^n,c20,|Surname:|v1^s,###,%,/,
```

```
v10/#,v20/#,v30/#,%#,
```

**Veja também:** 

**/** [conditional  newline]

**#** [unconditional  newline]

---

## "string"  - literal condicional

**Suporte:**  Standard

**Sintaxe:** 
```
"<text>"<field selector>"<text>"
	"<text>"<dummy field (selector)>
"<text>"<not present>
```

**Definition:**	
Outputs the text between the quotes only if `<field selector>`,`<dummy field (selector)>` or `<not present>` evaluates to TRUE. Both prefix and suffix literals can be placed together when using <field selector>, and data field content is also output.
If combined with `<dummy field (selector)>`, output is generated if data field is present. If combined with `<not present>`, outputs only if data field is absent.

**Notes:**
`<text>` is produced only once, independing on repeatable fields.

**Exemplos:** 

```
"Author: "v1^a,
```

```
"this text outputs if data field 10 is present"d10,
```

```
"this text outputs if data field 10 is absent"n5,
```

**See also:**
**'string'** [unconditional literal]
**|string|** [repeatable conditional literal]
**d** [dummy field selector]
**n** [not present]
**v** [field selector]

---


## 'string' - unconditional literal

**Suporte:**  Standard

**Sintaxe:** 	
`'<text>'`

**Definition:**
Unconditionally outputs the text contained between a single quotes pair.


**Notes:**
Unconditional literals may be placed anywhere in a format and can be passed as parameters to functions.

**Exemplos:** 
```
this text will always output',
```

```
'Name: ',v1/,
```

**See also:**
**"string"** [conditional literal]
**|string|** [repeatable conditional literal]


---

## |string| - repeatable conditional literal

**Suporte:**  Standard

**Sintaxe:** 

```
|<text>|<+><field selector><+>|<text>|
```

**Definition:**
Outputs the text between the vertical bars for each occurrence of a
repeatable field, only if field selector evaluates to TRUE. Combined with a repeatable field, command behavior can be extended by using the `<+>` operator.
When `<+>` is present, the first prefix literal and/or the last suffix literal is not output.

ex: 

```
(|; |+v1), /* prefix-literal */ (v1+|; |), /* suffix-literal */
```

**Notes:**
Prefix and suffix-literals can be used together, including with `<+>` operator.
If a prefix or suffix-literal is used with `<+>` outside a repeatable group, literal contents may not be output as desired. If field is not repeatable, literal output occurs for the first and only occurrence of data field.

**Exemplos:** 

```
(|; |+v1^s,|,|v1^n*0.1|.|),
```

```
(v10|: |, ,v11,| - |v12),
```

**See also:**

**"string"** [conditional literal]
**'string'** [unconditional literal]
**(format)** [repeatable group]
**v** [field selector]

---


## (format) - repeatable group

**Suporte:**   Standard

**Sintaxe:** 
```
 (<format>)
 ```

**Definição:** 
Applies  the  format  between  the  parenthesis  to  all  occurrences  of  repeatable  field(s)  individually,  or  only  once,  if  no  repeatable  field  is  present.

**Notes:**  
Repeatable  groups  cannot  be  nested.

**Examples:**

```language
(|;  |+v2^s/),
```

```language
(v1,c15,v2,c35,v3/),
```

```language
(if  iocc<=3  then  f(iocc,1,0),|  -  |v3/ else  '-> more than  3'/,  fi),
```

**Veja também:** 

**|string|** [repeatable  conditional  literal]

**v** [field  selector]


---


## / - conditional newline

Support: Standard

Syntax:
```
/
```

**Definition:**
Begins a new line if not at the beginning of a line.


**Notes:**

Several conditional newline commands `(,/,/,/,/,)` have the same effect of a single one.

**Exemplos:** 
```
v1/,
```

```
v1/,v3/,v10/,mfn/,
```

```
s(v1,v3,v10)/,
```


**See also:**

**#** [unconditional newline]
**%** [reset blank line]


---


## /\*string\*/ - comment

**Suporte:**  CISIS
**Sintaxe:** 

```
/* <comment> */
```

**Definition:**
Encapsulates a comment.

**Notes:**
Comments can span over several lines.


**Exemplos:** 
```
/* this is a single line comment */,
```

```
/* this comment begins here and ends here */,
```

```
if a(v10) /*and p(v20) */ then v20/ fi,
```

---


## @ - include format file

**Suporte:**  CISIS

**Sintaxe:**  

``` 
@<filename>
```

**Definition:**
Includes a format specification stored in a file in the current format.

**Notes:**
`<filename>` may include drive and path information. Syntax of commands from the included file is evaluated when current format is executed. It is mandatory to separate `<filename>` with commas.

**Exemplos:** 

```language
@test.pft,v20,
```

```language
s(@c:\temp\test.pft,v3),
```

```language
if v1='L' then @large.pft, fi,
```

---


# A
## a(field selector) - absence check

**Suporte:**   Standard

**Function  type:**  Boolean

**Sintaxe:** 
```
a(<field  selector>)
```

**Definition:**
Returns  TRUE  if  data  field  is  absent,  otherwise  returns  FALSE.

**Notes:**
All  components  of  field  selector may be  used,  except  indent.

**Exemplos:** 
```
 if  a(v12) then  v13  else  v12, fi,
 ```
 

```
if  a(v20^b) and  p(v30) then  v40/,  fi,
```

**Veja também:** 

**p** function

**v** [field  selector]


---


# B
## break - conditional  branching/quitting

**Suporte:**  CISIS

Syntax:
```
break
```

**Definition:**

Breaks  the  execution  of  a repeatable  group  format.  When  outside  a  repeatable  group,  quits  the  execution  of  the  current  format.


**Notes:**
The  execution  resumes  after  the  end  of  the  repeatable  group.  When  used  inside a **ref function**, execution continues with the format after the  function.

**Exemplos:** 
```
(if  iocc  >  10  then '10+  occurrences'/,**break** else  v5^n|-|,v5^s,/,  fi,),
```

**Veja também:** 
**(format)** [repeatable  group]


---


# C
## c - column
**Suporte:**  Standard

**Sintaxe:** 
```
c<int>
```

**Definition:**
Skips  to  the  specified  column  in  the  current  or  next  line.

**Exemplos:** 
```
'Name:  ',c10,v1^n/,
```

```
if  p(v1^s)  then  c10,v1^s/,  fi,
```

**Veja também:** 

**x** [spacing]


---


## cat(file) - dump  file

**Suporte:**  CISIS

**Function  type:** String

**Sintaxe:** 
```
cat(<format>)
```

**Definition:**
Outputs  the  contents  of  a  file  whose  name  is  generated  by  `<format>`. Used for display file.

**Exemplos:** 

```
mfn,cat('myfile.html'),
```

```
cat('current  document'/,  ,if  v10='c'  then  'firstdoc.txt'  else  'default.doc'  fi),
```

```
cat(v101),
```

**Veja também:** 

**s(expression)**


---



## continue - repeatable  conditional  branching

**Support:**  CISIS

**Syntax:** continue

**Definition:**  Executes  the  next  occurrence  of  a  repeatable  group  if  at  least  one  data  field  has  a  subsequent  occurrence.

**Notes:**

Examples: 


```language
(if  iocc  =  1  then  **continue** else  v10/  fi),
```


```language
2  (f(iocc,1,0),'=',v70,continue/),
```


**See  also:**
(format) [repeatable  group]

---



# D
## d - dummy  field  selector

**Suporte:**  Standard

**Sintaxe:** 

```
d<field tag><subfield>
```

**Definition:**
Outputs the conditional literal prefix if a data field or subfield exists. Used  in  conjunction  with  conditional literals.

**Notes:**
Dummy  field  (selector) does  not  return  a  value.

**Known  bugs:**
When  in  a  repeatable  group,  `<subfield>`  is  evaluated  only  for  the  first  occurrence  of  data  field.

**Exemplos:** 
```
"this  text  outputs  if  data  field  10 exists"**d**10,
```

```
Name:  "v20(5,5)/,  ,"Name:  "n20,v21(5,5)/,
```

**Veja também:** 
**"string"**  [conditional  literal]
**n**  [not  present]  v  [field  selector]


---


## date date(keyword) - current  date

**Suporte:**  CISIS
**Function  type:**  String

**Sintaxe:** 

```date```

```date(<keyword>)```

**Definition:**
Outputs  current  system  date.  Used  without  parameters,  returns:

```yyyymmdd  hhmmss  w  nnn```

where:
- mm  = month
- dd  =  day
- mm  =  minute
- ss  =  second
- nnn  =  number of  elapsed  days  from Jan  1st.

**Components:**

keywords  **DATETIME** and  **DATEONLY**

**Notes:**

**DATETIME** shows  system  date  in  european  format  plus  current  time  ***(dd/mm/yy hh:mm:ss)*** while **DATEONLY** displays the same output  without  time  information.

**Exemplos:** 

```
'Today  is  ',**date**,
```

```
'Current  date:  ',date(DATEONLY)/,  ,'Current  time:  ',mid(date(DATETIME),10,8)/,
```


---



# F
## f(num expr,length,decimals) - format value

**Suporte:**  Standard

**Function type:** String

**Sintaxe:** 

```
f(<format>,<expr-1>,<expr-2>)
```

**Definition:**
Converts a numeric value to string. `<format>` is the numeric expression to be converted. `<expr-1>` and `<expr-2>` are optional and determine the minimum output length and the number of decimal places respectively.

**Notes:**
If `<format>` is not a valid numeric expression, an error is issued. If `<expr-2>` is set, `<expr-1>` must also be placed or a syntax error is issued. If only `<expr-1>` is defined, the result is output in scientific exponent notation. If the number of characters required to represent `<format>` is greater than `<expr-1>`, additional positions are provided automatically. If `<expr-1>` is missing, a width of 16 characters is assumed.

**Exemplos:** 
```
f(val(v1),2),
```

```
f(((3+5)/2)+1,4,2),
```

```
f(v2),
```

**See also:**
**val** function

---



# G
## getenv(expression) - get  environment  variable

**Suporte:**  CISIS

**Function type:** String

**Sintaxe:** 
```
getenv(<format>)
```

**Definition:**
Returns the value of an environment variable.

**Notes:**
If `<format>` does not generate a valid environment variable name, no value is returned.

**Exemplos:** 
```
'Current path: ',getenv('PATH'),
```

```
(v1|=|,getenv(v1)/),
```

**See also:**
**putenv** function


---


# I
## if … then … else … fi - conditional  flow  control

**Suporte:**  Standard

**Sintaxe:** 
```
if <bool expr> then <format-1> [else <format-2> ] fi
```

**Definition:**
Executes a block of formatting language specifications (`<format-1>`) if `<bool expr>` evaluates to TRUE. Allows the execution of another block of formatting language specifications (`<format-2>`) by using the clause else when `<bool expr>` evaluates to FALSE.

**Notes:**
Clause then precedes the first block of formatting language specifications. else is optional and if present in the code, must be followed by a format. The fi clause must always end the command scope and if missing, a syntax error is issued. The if…fi command can span over several lines, therefore it is recommended the use of indentation.

**Exemplos:** 
```
,ifinstr(v5,'ab')>0 then ,v5/, fi,
```

```
,if p(v10) then ,|Title: |v3, else ,|Alternate title: |v4, ,fi,
```

---




## instr(string1,string2) - find  string
**Suporte:**  CISIS

**Function type:** Numeric

**Sintaxe:** 
```
instr(<format-1>,<format-2>)
```

**Definition:**
Returns a number specifying the starting position of the string generated by `<format-2>`, found in string settled by `<format-1>`. If there is no match, return value is zero.

**Notes:**
Both `<format-1>` and `<format-2>` must generate strings, otherwise a syntax error occurs. The use of s function may help in cases where a complex string is required as parameter.

Examples:
```
if instr(v5,'ab')>0 then v5/, fi,
```

```
if instr(s(|'|v1|'|),v5)>0 then v1, fi,
```

```
left(v18,instr(v18,'.')-1),
```

---




## iocc - occurrence  index
**Suporte:**  CISIS

**Function type:** Numeric

**Sintaxe:**  iocc

**Definition:**
Returns the occurrence index number (starting from 1), otherwise returns zero.

**Exemplos:** 
```
("Author: "v1/, ,if iocc > 3 then 'et all',break, fi),
```

```
(f(iocc,3,0),|.|v10/),
```

**See also:**
**nocc** function


---



# L
## l(key) l([inverted file],key) - key  lookup

**Suporte:**  Standard/CISIS

**Function type:** Numeric

**Sintaxe:** 
```
l(<format key>)
```

```
l([<format ifname>]<format key>)
```


**Definition:**
Returns the MFN of the first posting (if any) by using the key generated by `<format key>` to search the current inverted file. It can also seek in a specific inverted file defined by `<format ifname>`.

**Notes:**
Keys are converted to upper case before the expression is seek. Default display mode used by lookup is mpl. If a different mode is specified in the FST file, key must also use the appropriate mode. If key is not found, function returns zero. The `<format ifname>` parameter must evaluate to a string having a valid inverted file name, otherwise a syntax error is issued. This is often used in conjunction with ref function to allow output of data fields from a different record.


**Exemplos:** 
```
if l(v15)<> 0 then |Term: |v15, fi,
```

```
ref(l(['books']v1,'-',v2),v10/),
```

**See also:**
**ref** function


---


## left(string,length) - left  substring

**Suporte:**  CISIS

**Function type:** String

**Sintaxe:**  
```
left(<format-1>,<format-2>)
```

**Definition:**
Returns a new string, containing the leftmost characters from of the original string generated by `<format-1>`. `<format-2>` specifies the actual number of characters to be read from `<format-1>` starting from left to right.

**Notes:**
If the string generated by `<format-2>` is greater than the size defined by `<format-1>`, function returns the `<format-1>` string. If `<format-2>` is zero or is set to a negative number, returns a NULL string.

**Exemplos:** 
```
if left(v1^n,2)='Ma' then v1^n/, fi,
```

```
left(v1,instr(v1,'.')-1),
```

**See also:**
**right** function
**mid** function

---



## lw(number) - set  line  width

**Suporte:**  CISIS

**Function type:** Numeric

**Sintaxe:**  
```
lw(<int>)
```

**Definition:**
Sets the output line width to <int> characters.

**Notes:**
Output line width default depends on the application program

**Exemplos:** 
```
if size(v10) > 76 then lw(254), fi,
```

```
lw(70),v20/,lw(10),v30/,
```

---



# M

## mdl, mdu, mhl, mhu, mpl, mpu - mode

**Suporte:**  Standard

**Sintaxe:**  
```
m<mode><conv>
```


**Definition:**
Sets a new displaying mode for the current output.

**Notes:**
Default mode is mpl. `<mode>` represents the desired mode to be set. `<conv>` specifies whether upper case conversion is set. Mode may appear several times in a format and its formatting effect is active until a new mode is set.

`<mode>` can be as follows:
- p = proof: fields are displayed as they are stored in records.
- h = heading: control characters and descriptor delimiters are ignored, except subfield descriptor, which are translated to punctuation.
- d = data: similar to heading mode, appends a full stop at the end of data fields, followed by two spaces.
`<conv>` can be as follows:
- u: converts data to upper case
- l: leaves data unchanged

**Exemplos:** 

```
mpl,"First author: "v10[1]/,
```

```
mpu,"Second author: "v10[2]/,
```

```
mdl,"Third author: "v10[3]/,
```


---





## mfn mfn(length) - record number

**Suporte:**  Standard

**Function type:** String or numeric

**Sintaxe:**  
```
mfn
```

```
mfn(<int>)
```

**Definition:**
Returns the master file number of a record.

**Notes:**
An integer value can be passed as parameter to set the return value size. mfn returns the appropriate return type according to the format requirements.

**Exemplos:** 
```
'Record: ',mfn(3)/,
```

```
if mfn > 2 then mfn/, fi,
```

```
ref(mfn-1,v2/),
```

**See also:**
**ref** function
**l** function

---



## mid(string, start, length) - substring

**Suporte:**  CISIS

**Function type:** String

**Sintaxe:**  
```
mid(<format-1>,<format-2>,<format-3>)
```

**Definition:**
Returns a new string, containing a specified number of characters from the original string (`<format-1>`). `<format-3>` gives the actual number of characters to be read from `<format-1>` and `<format-2>` gives the start position in string where extraction begins.

**Notes:**
If `<format-2>` is greater than `<format-1>` size, function returns a `NULL` string. If `<format-2>` is zero or is set to a negative number, default is 1.

**Exemplos:** 
```
mid(v2,2,80),
```

```
mid(v1,instr(v1,'key'),size(v1))/,
```

**See also:**
**right** function
**left** function


---




## mstname - master file name

**Suporte:**  CISIS

**Function type:** String

**Sintaxe:**  
```
mstname
```

**Definition:**
Returns the current master filename.

**Exemplos:** 
```
'Current database: ',mstname/,
```

```
ref(['names']l(['names']'X39BJ'), ,'Database now is ',mstname/),
```

---



# N
## n - not  present  (dummy  field  selector)

**Suporte:**  Standard

**Sintaxe:**  
`n<field tag>`

**Definition:**
Tests the absence of a data field. Used in conjunction with conditional literals.

**Notes:**
As a dummy (field) selector, it does not return a value.

**Exemplos:** 
```
"this text outputs if data field 10 is absent"n10,
```

```
"Author:"v10/, ,"Author: "n10,v20/,
```


**See also:**
**"string"** [conditional literal]
**d** [dummy field selector]
**v** [field selector]


---


## newline(string) - set  newline

**Suporte:**  CISIS

**Function type:** String

**Sintaxe:**  
`newline(<format>)`

**Definition:**
Sets and/or resets default CR/LF pair with character(s) from resulting <format>.

**Notes:**
`<format>` may even contain reserved escape sequences such as:
`\r` - carriage return
`\n` - line feed
Subsequent `\` commands will be automatically replaced by resulting format until a newline sets a new character or string.

**Exemplos:** 
```
newline(if v151='unix' then '\n' else '\r\n' fi,
```

```
newline(v301),
```

```
newline('<BR>'),
```

**See also:**
**/** [conditional newline]
**#** [unconditional newline]


---


## nocc(field) - number  of  occurrences

**Suporte:**  CISIS
**Function type:** Numeric

**Sintaxe:**  
```
nocc(<field selector>)
```

**Definition:**
Returns the number of occurrences of a data field or subfield defined by <field selector>.

**Notes:**

`<field selector>` means only field and subfield in this function scope. All other field selector components, if used, issue a syntax error.

**Exemplos:** 

```
if nocc(v3)> 10 then 'Too many occurrences.'/, fi,
```
```
'There are ',f(nocc(v20),2,0),' authors.'/,
```

**See also:**
**iocc** function
**v** [field selector]



---


## npost(key) npost([inverted file],key)

**Suporte:**  CISIS

**Function type:** Numeric

**Sintaxe:**  
```
npost(<format key>)
```

```
npost([<format>],<format key>)
```

**Definition:**
Returns the total postings for a key (given by `<format key>`) in an inverted file. `<format>` if defined, must generate a string containing the inverted file name. `<format key>` settles the key to be searched in the inverted file.

**Exemplos:** 
```
if npost(v1)> 1 then 'duplicate key ',v1,' found'/, fi,
```

```
'There are ',f(npost(v20),3,0),'keys for ',v20,'. '/,
```

**See also:**
**l** function



---



# P
## p(field selector) - presence  check

**Suporte:**  Standard

**Function type:** Boolean

**Sintaxe:** 
```
p(<field selector>)
```

**Definition:**
Returns TRUE if data field is present, otherwise returns FALSE.

**Notes:**
All field selector components can be used, except indent.

**Exemplos:** 

```
if p(v12) then v12 else v13, fi,
```

```
if p(v50^a) and p(v50^b) then v50^a/,v50^b/, fi,
```


**See also:**
**a** function
**v** [field selector]


---



## proc(field update format) - field  update

**Suporte:**  CISIS
**Function type:** String

**Sintaxe:** 

```
proc(<fldupd format>)
```

**Definition:**
Appends or replaces data fields in the current record. `<fldupd format>` is a format that generates the field update specific commands to be executed by the function.

**Notes:**
A CISIS field update specification is a string of d (delete) and a(add) and h (add) commands to be applied in the current record. All d (delete) commands must preceed the add commands.

**The following commands are available:**
`d*` - deletes all present fields
`d<field tag>` - deletes all occurrences of `<field tag>`
`d<field tag>/<occ>` - deletes occurrence `<occ>` of `<field tag>`
`a<field tag>#<string>#` - adds `<string>` as a new occurrence of `<field tag>`
`h<field tag> <n> <string>` - adds `<string>`, `<n>` bytes long, as a new occurrence of `<field tag>`
The `#` delimiter may be any non-numeric character.
A space must be provided between the `<field tag>`,  `<n>` and `<string>` parameters of the h command.

**Exemplos:** 

```
proc('d70',|a10#|v70|#|),
```

```
proc(if v24*0.4 = 'Tech' then 'd*', fi),
```


---



## putenv(expression) - environment  variable  set

**Suporte:**  CISIS

**Function type:** String

**Sintaxe:** 

```
putenv(<format>)
```

**Definition:**
Sets an environment variable at the operating system level with its corresponding value.

**Notes:**
The variable is available only within the scope of current process.

**Exemplos:** 
```
putenv('TEST=test'),getenv('TEST'),
```
```
set CIPAR=somefile
set
mx null "pft=putenv('CIPAR=another'),getenv('CIPAR')/"
set
```

**See also:**
**getenv** function


---


# R
## ravr(string) - average  value  of  expression

**Suporte:**  Standard

**Function  type:** Numeric

**Sintaxe:** 

```
ravr(<format>)
```

**Definition:**
Returns  the  average  value  of a  given  format.  `<format>`  must  generate  a  string  expression.

**Notes:**
Can  be  used  to  compute  the  average  of  numeric  values  in  repeatable  fields.

**Exemplos:** 
```
f(**ravr(**s(v8,x1,v1)**)**,3,0),
 ```

```
f(**ravr(**v1,x1,v2**)**,5,2),
```

```
f(**ravr(**'8;15;16.73'**)**,3,2),
```

```
if  **ravr(**v20|;|**)**>=5  then  'pass'/  else  'fail'/,  fi,
```

**Veja também:** 
**rmin** function
**rmax** function
**rsum** function

---


## record number

## ref(mfn, format) ref([master file]mfn, format) - record  reference  link
**Suporte:**  Standard/CISIS
**Function type:** String

**Sintaxe:** 
`ref(<expr>,<format>)`
`ref([<format dbname>]<expr>,<format>)`


**Definition:**
Executes <format> with the record selected by <expr>. If <format dbname> is set, another (or the same) database can be referenced and a different record is selected.


**Notes:**
<expr> can be any format returning the MFN of a record. l function can be used to perform a seek and return the MFN.
Examples:

```
ref(l(v3),v1/,v2/,v3/),
```

```
if ref(['account']l(['user']v2),v4)='active' then |Name: |v10/, fi,
```

```
(if p(v99) then ref([v99]1,v30/), fi),
```

**See also:**
**l** function

---



## replace(string1, string2, string3) - replace

**Suporte:**  CISIS
**Function type:** String

**Sintaxe:** 
```
replace(<format-1>,<format-2>, <format3)
```

**Definition:**
Returns a new string, after replacing `<format-2>` with `<format-3>`.

**Notes:**
If `<format-2>` is a null string or is not found in `<format-1>`), function returns `<format-1>` string.
If `<format-3>` is null, `<format-2>` string will be excluded from `<format-1>`.
replace is case sensitive for both search string (`<format-2>`) and replace string (`<format-3>`).

**Exemplos:** 
```
replace('Mary And John','And','and')/,
```

```
if replace(v1^a,'01x','01X')= '894501X' then v1^n/, fi,
```

```
replace(s(v304,v333),',',', ')/,
```

```
replace(s(if v415='spanish' then v299 else 'none' fi),v1,v759)/,
```

---



## right(string, length) - right  substring

**Suporte:**  CISIS

**Function type:** String

**Sintaxe:** 
```
right(<format-1>,<format-2>)
```

**Definition:**
Returns a new string, containing the rightmost characters of the original string (`<format-1>`). `<format-2>` gives the actual number of characters to be read from `<format-1>` starting from right to left.

**Notes:**
If `<format-2>` is greater than `<format-1>` size, function returns `<format-1>` string. If `<format-2>` is zero or is set to a negative number, returns nothing.

***Exemplos:** *
```
if right(v1^n,1) = 'r' then v1^n/, fi,
```

```
right(v65,4)/,
```

---



## rmax(string) - maximum  value  of  expression

**Suporte:**  Standard
**Function type:** Numeric
**Sintaxe:**  
```
rmax(<format>)
```

**Definition:**
Returns the maximum value of a given format. `<format>` must generate a string expression.

Notes:
Can be used to compute the maximum of numeric values in a repeatable field.
Examples:
```
f(rmax('72,54,2'),2,0),
```

```
f(rmax(v1,x1,v4,x1,(v8|,|)),5,2),
```

```
if rmax(v40|;|)>val(v41) then 'Limit of ',v41,'exceeded.'/, fi,
```

**See also:**
**rmin** function
**ravr** function
**rsum** function

---



## rmin(string) - minimum  value  of  expression

**Suporte:**  Standard

**Function  type:** Numeric

**Sintaxe:**  

```
rmin(<format>)
```

**Definition:**
Returns  the  minimum  value  of  a  given  format.  `<format>`  must  generate  a  string  expression.

**Notes:**
Similar  to  **rmax  function**,  rmin  can  compute  the  minimum  of  numeric  values  in a  repeatable  field.

**Examples:**

```
f(rmin('10;2;5;4;-2'),2,0),
```


```
f(rmin(v1,x1,v2,x1,'44'),4,2),
```

```
if rmin(v80||,v90|  |,v100|  |)<  1990  then  'Wrong  decade.'/,  fi,
```


**Veja também:** 
**rmax** function
**ravr** function
**rsum** function

---



## rsum(string) - sum  of  expression

**Suporte:**   Standard

**Function  type:**  Numeric

**Sintaxe:** 
```
rsum(<format>)
```

**Definition:**
Returns  the  sum  of  a  given  format.  `<format>`  must  generate  a  string  expression.

Notes:  Similar  to **rmax** and  **rmin  functions**,  rsum  computes  the  sum  of  numeric  values  in a  repeatable  field.

Examples:
```
f(rsum('102,45,-37'),2,0),
```

```
f(rsum(v1,x1,v3,x1,f(val(v8)+2)),4,2),
```

```
if rsum(v20^d)>1000  then  'Aborted.'/  else  'OK'/,  fi,
```

**Veja também:** 
**rmax** function
**ravr** function
**rmin** function

---



# S
## s(expression) - string

**Suporte:**   Standard

**Function  type:**  String

**Sintaxe:** 
``` 
s(<format>)[command  component]
``` 

**Definition:**
Returns  the  concatenation  of  string expressions  generated  by  <format>.

**Components:**
extraction

**extraction:**
Extracts partial content of the resulting string. `<offset int>` is the first  position to start extraction, while `<length int>` determines how many  characters will be extracted. If `<length int>` is omitted or is greater than the  resulting  string,  the  default  is  the  end  of  the  resulting  string.

Notes:  Can  be  passed  to  functions  that  require  a  string  expression  as  parameter.


---


## select … case … elsecase … endsel - conditional  branch  control

**Suporte:**  CISIS

**Sintaxe:** 

```
	select <format expr>
case <option-1>: <format-1>
	case <option-2>: <format-2>
	case <option-n>: <format-n> [elsecase <format-0>]
	endsel
```

**Definition:**
Evaluates `<format expr>` and compares the result to each case option (`<option-1>, <option-2>…<option-n>`). If an option matches `<format expr>`, the appropriate block of formatting language specifications is executed (`<format-1>, <format-2>…<format-n>`), otherwise elsecaseclause (if defined) is executed (format-0).

**Notes:**
`<format expr>` must generate a string or numeric value. If `<format expr>` evaluates to string, all option values in case clauses must be of string type, otherwise, if `<format expr>` is numeric, option values must be also numeric.

**Exemplos:** 

```
select s(v5)
	case '1': ,f(val(v5)/2,2,2)/,
	case '2': ,v5/,
case '3': ,v6,'-',v1/,
elsecase ,|Error in field v5 = |v5/,
endsel,

```


```
select nocc(v7)
	case 0: 'absent'/,
	case 1: 'one occurrence'/,
case 2: 'two occurrences'/,
elsecase 'more than 2 occurrences'/,
endsel,
```


**See also:**
if … then … else .. fi

---


## size(string) - string  size
**Suporte:**   CISIS
**Function  type:**  Numeric
**Sintaxe:** 
```
size(<format>)
```

**Definition:**
Returns  the  string  size.

**Notes:**
`<format>`  must  return  a string  or a  syntax  error occurs.

**Exemplos:** 

```
if size(v10)>  76  then  lw(254),  fi,
```

```
f(size(v10,v20),1,0),
```

---



## system(expression) - system  call
**Support**:  CISIS
**Function  type:**  String

**Sintaxe:** 
```
system(<format>)
```

**Definition:**
Executes  the  argument  produced  by  `<format>`  as  an  operating  system  command.

**Notes:**
`<format>` must generate a string containing the code to be executed. The  possible  output  from  the  command  is  sent directly  to  the  standard  output.

**Examples:**
```
system('dir'),
```

```
if p(v2) then system('type ',v2),fi,
```

---


---
# T

## type(string) - string  type

**Suporte:**   CISIS

**Function  type:** String

**Sintaxe:**  

`type(<format>)`

**Definition:**
Returns  the  string  type  as  follows:
- A  -  if  string  contains  only  alphabetic  characters  (according  to  a  default  alphabetic  character  table, like  ISISAC.TAB)  or space
- N  -  if  string  contains  only  numeric  characters  (0-9)  
- X  -  for all other cases

**Notes:**
Format  must  generate  a  string  or a  syntax  error  is  issued.

**Exemplos:** 

```
if  type(**v1**)**='N'  then  f(val(v1),3,2)/  else  v1/,  fi,
```

```
if  s(type(v1),type(v2),type(v3))<>'AAA'  then  'Invalid  character  type detected'/,  fi,
```


---


# V
## v - field  selector
**Suporte:**  Standard

**Sintaxe:** 
```
v<field tag>[command components]
```

**Definition:**

Outputs data field contents. Content can be selected, restricted, narrowed, extracted or indented by using command components (see below). v stands for variable length field.
Components:	subfield, occurence, extraction and indent

**syntactic orde	r:**
```
^<subfield id> [<index>[..<upper index>]] *<offset int>.<length int>
(<first line int>,<next line int>)
```

**subfield:**
Restricts the output to the contents of a subfield. If data field exists but subfield is not present, no output is generated.



**occurrence:**
Narrows the output to one or a range of occurrences of a repeatable field.
`<index>` and `<upper index>` refer to the first (or unique) and last occurrences, respectively. If the specified <index> is greater than the actual number of occurrences, no output is generated. The same occurs if data field is not repeatable and <index> is set to a number equal or greater than

2. However, if `<index>` is set to 1 and it is used in a non-repeatable field, content is normally output. This component must be used outside a repeatable group; otherwise, `<upper index>` is ignored. If double dot (..) is used and `<upper index>` is missing LAST is assumed. The LAST keyword is set with the value of total occurrences of a data field.
extraction:	Extracts partial content of a data field, subfield or occurrence. `<offset int>` is the first position to start extraction, while `<length int>` determines how many characters will be extracted. If `<length int>` is omitted or is greater than field length, the default is the end of data field.
indent:	Aligns the output of data field, subfield, occurrence or extracted content, according to `<first line int>` (alignment for the first line) and `<next line int>` (alignment for successive lines). Both values are numeric constants. If current line position differs from zero, indentantion is disabled.
Notes:	The behavior of the field command depends on the component(s) used. No output is generated when data field is absent or when component performs a restriction or extraction that is out of data boundary.

**Exemplos:** 	

```
v2/,v3^a| - |,v1/,
```

```
v1^n*0.3,
```

```
(|; |+v3^s)/,
```

```
v20[4],
```


```
v10[2..7]/,
```

```
v5[3..]/,/* equals to ,v5[3..LAST], */
```
	
```
v1[LAST]*2.7/,
```

```
v1(5,5)/,
```

```
|Title: |v1^n(5,5)/,
```

**See also:**
**"string"** [conditional literal]
**d** [dummy field selector]
**n** [not present]
**|string|** [repeatable conditional literal]
**(format)** [repeatable group]


---




## val(string) - string  to  value

**Suporte:**  Standard

**Function  type:** Numeric

**Sintaxe:** 

`val(<format>)`

**Definition:**
  Returns  the  numeric  value  of  the  argument  generated  by  <format>.

**Notes:**
If  `<format>`  produces  only  non-numeric  characters,  function  returns  zero.

If  more  than  one  numeric  value  is encountered,  only  the  first one  is  returned.

**Exemplos:** 

`if  val(v2)>5  then 'Error'/  else 'OK'/, fi,`

`f(val(v2)/3,4,2),`

---



# X
## x - spacing

**Suporte:**   Standard

**Sintaxe:** 
`x<int>`

**Definition:**
Inserts  the  number  of  spaces  defined  by  `<int>`  before  the  next  block  of  formatting  language  specifications  is  output.

**Notes:**
If  `<int>`  is  greater  than  the  available  space  in  the  current  line,  it  skips  to  the  next  line.

**Exemplos:** 

```
'Name:  ', x5,v1^n/,
```

```
(v1,x3,v2,x8,v3/),
```


**Veja também:** 
**c** [column]