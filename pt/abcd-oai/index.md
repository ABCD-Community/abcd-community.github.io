---
title: A interface ABCD OAI
description: Esta seção apresentará a interface ABCD OAI, que é uma implementação do 'ISIS-OAI- PROVIDER' da BIREME, uma ferramenta geral para fornecer acesso aos bancos de dados ISIS através do protocolo OAI-PMH.
lang: pt
lang-ref: abcd-oai
---


# The ABCD OAI interface

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---

  
Esta seção apresentará a interface ABCD OAI, que é uma implementação do 'Provedor-ISIS-OAI' da Bireme, uma ferramenta geral para fornecer acesso aos bancos de dados do ISIS através do protocolo OAI-PMH.

  

## Breve introdução ao conceito OAI-PMH.

OAI, ou 'Open Archive Initiative' é uma iniciativa mundial nas comunidades da informação para aproveitar as informações de uma maneira aberta e livre.

Para obter mais informações sobre esta organização, o 'Openarchives.org', consulte [http://www.openarchives.org.] (Http://www.openarchives.org/)

A iniciativa de arquivos abertos desenvolve e promove padrões de interoperabilidade que visam facilitar a disseminação eficiente do conteúdo. A OAI tem suas raízes nos movimentos de acesso aberto e repositório institucional.

As três principais áreas de atividade atuais são:
1. OAI-PMH: Protocolo OAI para colheita de metadados: um protocolo para permitir a recuperação de metadados em documentos eletrônicos com um padrão aberto, o que significa que não é necessário usar o software com o qual os metadados foram/são gerenciados.
2. Especificação da estrutura do ResourceSync: um protocolo para possibilitar que os servidores sincronizem suas referências a recursos que possam se mover ou migratir no www, de modo a permanecer sempre atualizados (apontando para a URL correta)
3. Open Archives Initiative Object Exchange and Reuse : um mecanismo para permitir que 'documentos informativos ricos' (com imagens, filmes etc.) sejam apresentados como um 'recurso agregado' independente da localização individual dos componentes. Por exemplo, mídia social A intenção é desenvolver padrões que generalizem todas as informações baseadas na web, incluindo as crescentes redes sociais populares da "web 2.0".  


No ABCD, a primeira destas três características é implementada: o Protocolo de Colheita de Metadados ou OAI-PMH. O OAI-PMH é o principal protocolo desenvolvido e promovido pela OAI, e descrito como:

> O "Open Archives Initiative Protocol for Metadata Harvesting" (OAI-PMH) é um mecanismo de baixa barreira para a interoperabilidade dos 
> repositórios. Os provedores de dados são repositórios que expõem metadados estruturados através do OAI-PMH. Os Provedores de serviços então 
> fazem solicitações de serviço OAI-PMH para coletar esses metadados. OAI-PMH é um conjunto de seis verbos 
> ou serviços que são invocados dentro do HTTP. ”

A idéia é fornecer acesso a informações 'abertas' baseadas em meta-dados, na medida do possível de forma 'genérica' e aberta,
o que significa que qualquer necessidade de software específico deve ser evitada. Por este motivo, o protocolo permite em 6 'verbos'.
ou comandos que permitam identificar adequadamente a fonte das informações e a recuperação de meta-dados básicos
informações de documentos disponíveis, muitas vezes em um "repositório", seja em uma lista de documentos-identificadores ou, com base em um
tal identificador, um documento específico. A fim de facilitar a atualização dos repositórios, retirando suas informações de outros
repositórios, as seleções podem ser limitadas por datas.




## Implementação e configuração no ABCD
 
A implementação no ABCD é totalmente baseada na ferramenta "ISIS-OAI-PROVIDER" produzida pela BIREME como parte
de sua Biblioteca Virtual de Saúde (ver, por exemplo, o website sobre esta ferramenta [https://github.com/bireme/isis-oai-](http://wiki.bireme.org/en/index.php/Isis-oai-provider) e para baixar o software original o repositório GitHub: [https://github.com/bireme/isis-oai-](http://wiki.bireme.org/en/index.php/Isis-oai-provider). [Provido por](http://wiki.bireme.org/en/index.php/Isis-oai-provider)

Como nenhum software relacionado ao ABCD ou outro ISIS pode existir ao lado dos usuários, o mecanismo é fornecer uma URL e apresentar a interface como apenas uma página web de livre acesso. Portanto, nenhum link de dentro do ABCD (por exemplo, no módulo "Central") é fornecido, mas a URL deve ser inserida diretamente na barra de endereços do navegador (ou referenciada por um atalho, etc.). No caso de uma instalação ABCD 'localhost:9090', este URL seria: http://localhost:9090/isis-oai-provider/index.php.

A página aberta por esse URL deve ser como a ilustração a seguir:

![](https://lh5.googleusercontent.com/f1EYMwsBO1rReclD6jf-NCB0IKaarFg-mYaPDhikP964JQ4kTHP3YpEOte8zKnhgHuQKyhQ4e0qb980FJtvbN0OrkCxWfmnkyHJKYHBJxRFvCqpXCLB081DSmDvjIhhDGjPofXw=s0)

Como pode ser visto, na parte esquerda do acesso à interface é dada a cada um dos 6 principais 'verbos' ou operadores, com uma breve descrição de cada verbo após a seleção de um deles, enquanto na parte direita a interâmica do usuáriopossui duas partes: os critérios definidos pelo usuário na parte superior e o XML-Output (a ser 'capturado' com cópia/pasta, em alguns navegadores da 'fonte do quadro' se o código XML completo for necessário) como oresultado da ação de colheita. 

Primeiro discutiremos brevemente a configuração necessária para fazer com que isso funcione para o ISIS-Databases local no ABCD e depois discutirá cada um dos 6 verbos com alguma ilustração.

### Configuração da interface

Configurando o ABCD para a interface OAI compreende duas partes: uma configuração geral e um arquivo de configuração para todos os bancos de dados envolvidos.

#### A configuração geral
    
O arquivo 'oai-config.php' está localizado na 'raiz' do módulo **isis-oai-provider** no ABCD, que é armazenado, ao lado de outros módulos como central, iah, secs-web e site, na pasta htdocs do ABCD. Uma visão típica do gerenciador de arquivos do Windows do conteúdo desta pasta se parece com isto:

![](https://lh3.googleusercontent.com/7S58qqg99TZ3eMo4ikRuv8OWoNFdufxw6jigaiASdp-uX_yVx4XqTrUSCxaDAYry-oAP0z5WdnXU6KAf5iyMhtDcJY8ocLAuSx-7Lg7xDze5rLfbu_u9XhHil8_85lpCu-Kkl-E=s0)

Assim, este módulo usa suas próprias folhas de estilo e imagens CSS, permite a aplicação de gizmo's e usa um arquivo JavaScript com 'funções' chamadas a partir dos scripts. Os sudiretórios mais importantes aqui são :

- **lib**: este diretório contém os principais scripts PHP para a interface, em parte obtidos - herdados - das bibliotecas gerais PHP-OAI (por exemplo, OAIServer.php) e em parte dedicados a scripts PHP para lidar com as respostas ISIS-bases de dados (ISISD- b.php) ou um (ISISItem.php) ou mais (ISISItemFactory.php) registros ISIS. Os scripts de análise de configuração também estão aqui para analisar a configuração do ABCD-OAI ou o 'mapeamento' dos campos do banco de dados para o padrão Dublin Core.
  
- **map**: este diretório contém pelo menos um arquivo para cada banco de dados envolvido, ou seja, seguindo uma das duas sintaxes permitidas: OAI_DC (arquivos com o nome do banco de dados seguido da extensão .i2x) ou ISIS (formatos mais tradicionais ISIS PFT com a extensão .pft). Este mapeamento será discutido em mais detalhes abaixo.
  
- **wxis**: alguns ISISScripts usados pelo principal executável wxis (ISIS habilitado para web). getidientifiers.xis, getrecord.xis e gettotal.xis. Estas são instruções ISISScript bastante 'normais', tomando variáveis do ambiente CGI e depois especificando as instruções para operar sobre as variáveis, por exemplo, imprimir os títulos em um loop etc.
  
- No diretório isis-oai-provider principal encontramos a abertura PHP-script index.php (que contém a interface) e os arquivos de amostra e de configuração reais como PHP-scripts.

Para a configuração da interface ABCD-OAI, precisamos considerar dois arquivos: um para a configuração geral, outro para os bancos de dados.

Uma listagem de exemplo, como vem com a implementação da demonstração, é dada aqui, onde linhas começando com ';' são comentários, por exemplo, para ilustrar as alternativas do Windows:

```
[ENVIRONMENT]  
; Set the directory of application. The effect will be [http://your-site.org/DIRECTORY](http://your-site.org/DIRECTORY)

DIRECTORY=/isis-oai-provider 
;Full path to folder 'site' in folder bases. Windows users must NOT put letter unit in path
DATABASE_PATH=/var/opt/ABCD/bases/;
DATABASE_PATH=/ABCD/www/bases/ EXE_EXTENSION=;
EXE_EXTENSION=.exe

;Set the directory configured to execute cgi-bin applications.

CGI-BIN_DIRECTORY=/cgi-bin/ 

;[INFORMATION] 
;Set the repository's name. 
NAME=ABCD

; Set the email of the system admin [EMAIL=egbert.desmet@uantwerpen.be](mailto:EMAIL%3Degbert.desmet@uantwerpen.be) 
IDPREFIX=be

IDDOMAIN=netcat 
EARLIESTDATESTAMP=2011-01-01 
MAX_ITEMS_PER_PASS=20
```

Na seção **[ENVIRONMENT]**, as seguintes variáveis precisam ser definidas:

- **DIRECTORY**: a pasta do módulo, a partir do 'ABCD DocumentRoot' (como definido no servidor web, por exemplo, Apache), portanto, no caso padrão do ABCD no Linux, onde a raíz do documento é definida como '/opt/ABCD/wwww/ htdocs', definir o DIRECTOY como 'isis-oai-provider' significa que o módulo OAI está localizado em /opt/ABCD/ wwww/htdocs/is-oai-provider.
- **DATABASE_PATH**: o diretório onde os bancos de dados podem ser encontrados.
- **EXE_EXTENSION**: a extensão a ser adicionada ao nome executável 'wxis', em Windows : ".exe", no Linux não é utilizada nenhuma extensão.
- **CGI-BIN_DIRECTORY** : the directory as it should be recognized in the URL. In the case of Apache the Apache- configuration explains which real directory corresponds with the URL '/cgi-bin/'.
 
Na seção **[INFORMATION]** definimos: 

- **NAME**: o nome do seu repositório, como você deseja que ele seja visto pelo usuário
- **EMAIL**: O endereço de e-mail do administrador que pode ser contatado sobre o repositório
- **IDPREFIX** and **IDDOMAIN**: juntos eles identificam o 'domínio' do servidor
- **EARLIESTDATESTAMP**: Os dados iniciais do repositório, ou seja, a data dos documentos mais antigos, no formato YYYY-MM-DD.
- **MAX_ITEMS_PER_PASS**: O número de registros a serem listados nos verbos ListIdentifers ou ListRecords.No final da lista, será fornecido um código de retomada que pode ser usado para definir o início do próximo lote.O padrão aqui são 20 itens.  
    
### A configuração dos bancos de dados

Um ou mais bancos de dados podem ser usados na interface OAI, onde são referidos, no vocabulário da OAI, como "conjuntos". A implementação da amostra no ABCD utiliza dois desses conjuntos: MARC (um catálogo marc21) e DUBCORE. (um repositório com papéis, mas este é apenas um exemplo de banco de dados de texto completo que o administrador do ABCD tem que implementar !)

#### A definição do banco de dados:

Cada banco de dados precisa ser definido, mas também precisará de pelo menos um arquivo de 'mapeamento' que discutiremos depois das alas. Os parâmetros a serem definidos para cada um deles são bastante auto-explicativos, como nome, descrição, caminho (para os arquivos base de dados), banco de dados (o verdadeiro arquivo.nome ao qual será adicionado '.mst' para definir o arquivo ISIS MST), enquanto alguns outros parâmetros podem ser brevemente explicados adicionalmente:

- **mapping**: o arquivo onde o 'mapeamento' (dos campos ISIS correspondentes com os elementos relacionados DublinCore) são descritos em um formato 'DC' muito simples (.i2x) ou um formato mais sofisticado baseado na linguagem de formatação ISIS (.pft), veja mais adiante;
- **idprefix**: a cadeia a ser prefixada (adicionado "antes") o identificador real ao listar os identificadores de registro; esta cadeia adicional é opcional;
- **cisis_version**: este é o identificador da versão específica CISIS que é usada (a partir do ABCD2.0 podem ser usadas diferentes versões CISIS, por exemplo, BIGISIS ou UTF8/FFI etc.). A versão especificada aqui deve refletir a estrutura do (sub)diretório que se encontra no diretório 'cgi-bin' onde está localizado o 'wxis' correto (ou no Windows : wxis.exe) para lidar com o banco de dados concêntrico. Isto pode ser diferente para qualquer banco de dados definido.


> Nota:
> Mudamos o nome original da variável 'isis_key_length' (por exemplo 1030, 1660...), 
> mas de fato, no ABCD, a versão CISIS deve ser referida aqui. 
> Esta é uma diferença real com a ferramenta padrão original da BIREME.
 

- **identifier-field**: a etiqueta (número) do campo ISIS que contém o identificador do registro;
- **date-stamp-field**: a etiqueta (número) do campo ISIS que contém o carimbo de dados do registro.

Usamos os 2 bancos de dados ou 'conjuntos' mencionados anteriores para ilustrar a configuração de um banco de dados (neste caso para Linux):

```
    [marc] name=marc

description="MARC" 
path=/var/opt/ABCD/bases/marc/data database=/var/opt/ABCD/bases/marc/data/marc 
mapping=marc.i2x

prefix=oai_date_ cisis_version=ansi 
; identifier_field=1 
datestamp_field=980 [dubcore] 
name=dubcore  



description="DublinCore repository"
path=/var/opt/ABCD/bases/dubcore/data
database=/var/opt/ABCD/bases/dubcore/data/dubcore
mapping=dubcore.i2x

prefix=oai_date_ 
cisis_version=utf8/bigisis ; dentifier_field=111
datestamp_field=507
```

O 'mapeamento' do banco de dados explica como os campos ISIS correspondem com os elementos DC ou XML. É melhor ilustrar isto com base nas amostras fornecidas, começando com o exemplo muito simples 'marc.i2x' :

  
```
root=oai-dc 245 dc:title
500 dc:description
650 dc:subject
001 dc:identifier
980 dc:date
```    

Primeiro, a cadeia 'raiz' é definida como sendo usada na interface registros-exibição. No caso do prefixo oai-dc usado (veja a seção 'uso' abaixo) basta colocar 'oai-dc'.

Essa 'raiz' é seguida por uma lista de campos, um para cada linha, consistindo na ISIS-field-tag seguida pelo nome do elemento Dublin Core, por exemplo, o campo de título MARC21 245 torna-se: 245 dc-title. Observe que esta lista pode ser uma seleção de campos a serem mostrados. Os campos não definidos aqui apenas manterão a tag de campo como o elemento XML, sem tradução para um elemento DC adequado.

Quando uma formatação mais poderosa é desejada, por exemplo. no nível de subcampos, pode-se usar a sintaxe alternativa mais elaborada de uma PFT, referindo-se então a um arquivo com a extensão .pft. Tal PFT 'imprime' as tags XML necessárias, ou seja, as informações do líder XML, como 'literais (strings entre aspas incondicionais):

```
<oai_dc:dc
xmlns:oai_dc="http://www.openarchives.org/OAI/2.0/oai_dc/"
xmlns:dc="http://purl.org/dc/elements/1.1/"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.openarchives.org/OAI/2.0/oai_dc/ http://www.openarchives.org/OAI/2.0/oai_dc.xsd">'/
```

seguido pelos campos ISIS individuais na sintaxe da Linguagem de Formatação usada para adicionar literais para a saída DC-XML, no caso de, por exemplo, o 'título' (v2 no Dubcore):

```
if p(v2) then
(| <dc:title><![CDATA[|v2^*|]]></dc:title>|/), 
fi,
```

ou, para o título e autores n Marc:

```
if p(v245) then
(| <dc:title><![CDATA[|v245^*|]]></dc:title>|/),
| <dc:title><![CDATA[|v246^*|]]></dc:title>|/,
fi,
```

```
if p(v100) or p(v110) then
(if p(v100) then
| <dc:creator><![CDATA[|v100^*|]]></dc:creator>|/,
else
| <dc:creator><![CDATA[|v110^*|]]></dc:creator>|/,
fi), fi
```

que deve ser lido como : se o título estiver presente, então imprima as tags XML `<dc:title>` e `</dc:title>` com o valor real da v2 (qualquer subcampo, indicado pelo operador `^*`, entre o atributo [CDATA[...].
Qualquer declaração PFT mais complicada pode ser utilizada, por exemplo, para exibir o formato do documento, se for indicada em `v9`:

```
' <dc:format>'select s(mpu,v9,mpl)
case 'A':'text',if p(v8^q) then '/'v8[1]^q fi,
case 'MATERIAL TEXTUAL':'text',
case 'G':'video',
case 'I':'audio',
elsecase if a(v9) then 'text',if p(v8^q) then '/'v8[1]^q fi, 
else 'other' fi
endsel,
'</dc:format>'/,
```
Qualquer seqüência de campos ISIS pode ser tratada desta forma, mas campos não mencionados aqui serão omitidos da saída.
Ao invés de campos também podem ser usados subcampos ou grupos de campos, usando o poder da linguagem de formatação.
O melhor é reutilizar um modelo existente, como fornecido com a demo-instalação, para um novo banco de dados local diferente, adaptando principalmente as tags de campo à estrutura local do banco de dados. É preciso ter muito cuidado, como sempre com a Linguagem de Formatação ISIS: a falta de uma cotação ou qualquer outro erro de sintaxe não produzirá nenhuma saída, exceto algumas mensagens de erro na saída de XML!


## Usando a interface

Quando tudo está devidamente configurado - muitos testes preliminares são aconselhados, afinal a OAI significa expor seu banco de dados para o mundo inteiro! - os seguintes resultados podem ser obtidos, apresentados por cada um dos seis 'verbos' OAI-PHM :


> Nota: 
> Com a maioria das ilustrações aqui embaixo, 
> a saída de XML está incompleta, em outras palavras: 
> a saída real contém mais dados, mas apenas parte pode ser mostrada aqui.


> Nota: As ilustrações são geradas com o navegador Firefox, 
> mostrando imediatamente a saída de XML porque não há nenhum 
> estilo XML disponível ('Este arquivo XML não parece ter nenhuma 
> informação de estilo associada a ele. A árvore de documentos é mostrada abaixo"). 
> Outros navegadores podem mostrar apenas a saída de texto, 
> sendo que o XML completo ainda está disponível clicando 
> com o botão direito do mouse e solicitando o 'frame-source'.

  

### Identificação

Este verbo retorna as principais informações do protocolo. Parâmetros obrigatórios do verbo (inseridos automaticamente ao eleger este verbo).

A saída contém todas as informações necessárias conforme acordado pelo protocolo, por exemplo, o 'nome' do protocolo, conforme indicado no script oai-config.  
 
### ListMetadataFormats

![](https://lh3.googleusercontent.com/6f0E2NSTeGar6fjrd1bcAQeZYQHtzva_3wkuqxdLr7cH2AhUhehTCmeMWIzT6qQ7OEzPjcntEt6jp7cLRcKMHKYJDQ79JxOzv30AMn0GnCjGKMre-M10TpimikTVIj9IU0bW0Ng=s0)
    
Este verbo descreve os formatos de metadados utilizados no protocolo. Parâmetros obrigatórios verbo No ABCD usamos dois formatos diferentes: oai_dc e isis. que corresponderão ao arquivo de 'mapeamento' definido, ou i2x (para oai-dc) ou pft para isis.  

### ListSets

![](https://lh5.googleusercontent.com/noGNA6WpWzDJxl6TocVjIGVOqHIvH6TE0Ro8xvhUJ2QUV7sVVafS3BxxjpJ7fXltzKKoXG3oItP1Gv9aOWsffrrTBOtkypv-P97sgRfWOjfuMxkwe9HBKzJbmRsyMIC126_ozTU=s0)
   

Recupera uma lista de todos os bancos de dados disponíveis neste repositório. Parâmetros compulsórios verbo Retorno de parâmetro resumptionToken

> Nota: 'parâmetro exclusivo' significa que este 
> parâmetro não é permitido, pois é incompatível com a 
> idéia do próprio verbo. A interface não 
> permitirá a colocação de um parâmetro exclusivo.

No caso de nossas duas bases de dados de demonstração aqui (Marc e Dubcore), a saída parecerá algo como:

### ListIdentifiers

![](https://lh3.googleusercontent.com/wQz-eoTP6LfgmBsBfS5LOkwIYxbc9B5v5qbgeF_ELnZ8MYvXG5OVBFAVVgbhVV49Fw2POb-tmj9lnHKkRgJOAMk19X7Nx9MQSYIIdbbguixg_GHD8H543cwSkX1qj7CQgadwdo8=s0)
    
This verb retrieves a list with the single identifier of each document published. Compulsory parameters verb metadataPrefix Optional parameters from until set Exclusive parameter resumptionToken retrieves a list with the single identifier of each document published. Compulsory parameters verb metadataPrefix Optional parameters from until set Exclusive parameter resumptionToken.

Dependendo do campo fornecido na configuração do banco de dados como contendo o identificador do registro, os registros serão listados com esse campo:  

![](https://lh6.googleusercontent.com/91zcJCxAgaa4bosa0f86nu4spU7pi8-u4yEWuEsrfWeC1NO64TgeBCvxpA4gAQC19JG0HrgGupXIq87AKwIUiZkrH-D1-ujis6oPuwNcHF7KdtJGJt52JgnA3sIpN5kh63Vp0hE=s0)

We are showing here the end of the output, because an interesting feature is visible there : the 'resumptionToken can be copied from there, to be filled in into the corresponding form-element in order to resume further listing with the given one as the first, so allowing subsequent batches to be retrieved (or 'harvested' in the IOAI-vocabulary).  

![](https://lh5.googleusercontent.com/C25Nq5y3MGwZVEA7wDJM1EbuiH8fYY4M3acSer7otCSUVTFUoeHTtFfbPoOaisLONg4GwPZbS6pesNUNg20QV4fDbDowQaxcpHtBlNT31Gdlg140RCVxsM1_XnOP81_1hZ1w5Jw=s0)

### ListRecords

Este verbo recupera a lista de documentos. Parâmetros obrigatórios metadataPrefix de parâmetros opcionais até definir o retomar exclusivo do parâmetro resumptionToken.  

![](https://lh5.googleusercontent.com/C25Nq5y3MGwZVEA7wDJM1EbuiH8fYY4M3acSer7otCSUVTFUoeHTtFfbPoOaisLONg4GwPZbS6pesNUNg20QV4fDbDowQaxcpHtBlNT31Gdlg140RCVxsM1_XnOP81_1hZ1w5Jw=s0)

Como no caso dos 'ListIdentifiers', um resumptionToken pode ser usado para continuar listando mais registros a partir do último mostrado anteriormente. Note que também podem ser inseridas datas 'de' e 'até' para limitar os registros listados a um determinado período de tempo.

### ListRecord

Finalmente, o último 'verbo' é recuperar os metadados de um registro específico. Parâmetros obrigatórios Identificador verbal metadataPrefix. Aqui é mostrado um formulário de registro base de dados demonstrativa do Dubcore, usando o dubcore_dc.pft 'arquivo de mapeamento', que também faz parte da demonstração.

![](https://lh4.googleusercontent.com/14ZvlkoFGdbxtE8y1RxxOiA56KtM-91sVobilKzRbgSZ3eTm48vaS4FULlZRia7wxqYL1UekDhU7bkbJADaiHhEsJchq1pl--3lzBp7lQyb_DX-VQW_E5jP7C-CvLqdwMJ7SW_0=s0)
