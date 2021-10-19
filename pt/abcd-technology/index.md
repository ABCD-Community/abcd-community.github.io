---
title: Tecnologia ABCD
description: Este tópico fala sobre as tecnologias utilizadas para desenvolver o ABCD.
lang: pt
lang-ref: abcd-technology
---

# Tecnologia ABCD


{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Bases de dados ISIS

Bases de dados ISIS são arquivos em que as informações contidas nos registros numerados (MFN’s ou Master File Numbers) com valores (na maior parte textual) armazenadas em campos com uma "tag" (ou identificador numérico) e subcampos (com um identificador de um caractere). Subcampos, campos e registros são todos de tamanho variável e “ocorrências variáveis” variando de 0 (ausente) a qualquer número maior que zero ocorrências, com um máximo dependendo da tecnologia ISIS utilizada, mas na nova geração (em J-ISIS e ISIS NBP), sem limite.

Os registros são estruturalmente descritos em um 'cabeçalho' para cada registro em si, em vez do cabeçalho de tabela usual em bases de dados relacionais. Ao fazer assim, ISIS reflete mais o conceito de que cada registro sendo um "documento" por si com a sua própria estrutura de “documento” de fato, como por exemplo, livros, artigos ou páginas web. Por isso, preferimos chamar ISIS uma “base de dados documental", no qual os documentos são armazenados como um registro com estrutura e tamanho variáveis. Isto evita estruturas complicadas de estruturas relacionais "normalizadas", que são muito eficientes no armazenamento de dados altamente estruturados, mas nem tanto para dados textuais semi-estruturados.

Isto significa que os registros podem ser bastante polimórficos, ou seja, estruturalmente diferentes com quaisquer combinações de campos. Em princípio ISIS pode manipular registros bibliográficos, juntamente com os dados do usuário e dados transacionais (por exemplo, empréstimos) em uma única base de dados, mas por causa de capacidades “semi-relacionais” (recuperação rápida de qualquer parte de um registro em qualquer base de dados, o ISIS, em tempo de execução, ou seja, pela Linguagem de Formatação, criando a saída sem a necessidade de dispor destas "relações" a serem pré-definidas) aplicações ISIS normalmente irão utilizar poucas bases de dados, por exemplo, no ABCD apenas 3 ou 4 bases de dados (uma para as entidades bibliográficas, uma para os usuários, uma para as transações e, possivelmente, uma para itens) podem possibilitar rodar uma biblioteca completa.

Na tecnologia ISIS “clássica" todos os registros de tamanho variável (com (sub-) campos contendo os valores) são armazenados em um arquivo “Master” (.MST) e as posições de registros são mantidas no arquivo de "Referência Cruzada" (.XRF), que pode ser visto como um índice normal de “primeira ordem” dos registros na base de dados. Registros novos e mesmo registros apenas editados são sempre anexados ao final do arquivo mestre e as referências no XRF são atualizadas de acordo, necessitando às vezes alguma “compactação” pela eliminação (de versões) de registros excluídos e/ou inativos.

Todos os valores especificados por uma "Tabela de Seleção de Campo" (que usa a Linguagem de Formatação, permitindo, portanto, definição muito flexível e poderosa de elementos selecionados), são incluídos em um “Arquivo Invertido” de árvore B, que pode ser visto como um "dicionário" de termos com o “endereço” exato (Registro, tag do campo, ocorrência, posição dentro de ocorrência) associado. Isto permite recuperação muito eficiente, incluindo bases de texto integral, de qualquer elemento definido como sendo "recuperável". ISIS foi um dos primeiros a oferecer bases de dados de texto integral, que se tornou popular somente décadas mais tarde. Este “Arquivo Invertido” (ou IF) tem várias componentes (com nodos arquivos N01/.N02 e folhas arquivos .L01/L02) para uma organização eficiente  - porque, em determinadas aplicações com indexação intensivas o IF pode ser ainda maior do que o arquivo da base de dados em si!

Então, tipicamente bases de dados ISIS contém cerca de 10 arquivos: um MST com XRF, os Arquivos Invertidos Árvore B e algumas tabelas de definição para os campos, os dados do formulário de entrada e de indexação. Tudo isso está mudando com as novas tecnologias de bases de dados introduzidas em 2009 com, por exemplo, J-ISIS: usa Berkeley DB, um tipo de armazenamento diferente em arquivos separados com as definições incorporadas nos principais arquivos de dados. Mas basicamente o conceito de pares "tag-valor" (um identificador e um conteúdo), em que é aplicada uma poderosa Linguagem de Formatação, baseada em campos, e acrescido de indexação de texto integral, continuam a ser o núcleo de bases de dados ISIS.

## Utilitários CISIS

Utilitários CISIS é um conjunto de softwares desenvolvidos pela BIREME para manipular bases de dados ISIS através de linha de comandos em UNIX/Linux ou DOS/Windows. Este software foi escrito na linguagem de programação C e daí o nome desse membro da família ISIS. CISIS consiste principalmente de uma série de "utilitários", ou seja, executáveis ativados por comandos que realizam todos os tipos de funções nas bases de dados ISIS, como criar registros, atualização e recuperá-los, atualização do arquivo invertido, importação e exportação e muitas outras funções, por vezes únicos na "Família ISIS", por exemplo, juntar registros de diferentes bases de dados, de acordo com chaves comuns, indexação e pesquisa a partir de diferentes arquivos invertidos para uma base de dados.
Atualmente CISIS como um conjunto de utilitários contém mais de 25 diferentes ferramentas ou executáveis. 

Para conhecer todas as ferramentas, vá para a página [CISIS Utilitários](/pt/abcd-technology/cisis-utils/)


### A ferramenta de referência MasterXross: MX

A ferramenta MX é o principal utilitário CISIS, poderia facilmente ser batizado como "CDS/ISIS para linha de comando", significando que a maioria das coisas que podem ser feitas com arquivos (M)estre e arquivos (X)rf - daí “mx” - com ISIS, também podem ser feitas com MX. Só para dar uma idéia, listamos os parâmetros aceitos pelo mx (como essa lista é apresentada quando se invoca o ambiente de linha de comando como a janela CMD do Windows ou a janela de um terminal em UNIX/Linux. Como pode ser visto, muitos são os parâmetros disponíveis, significando que mx é uma ferramenta extremamente poderosa para gerenciamento de bases de dados ISIS, mas que merece um manual e treinamento próprio!

**![](https://lh5.googleusercontent.com/Onej8W2i6TGtd-ETfna8h0s3fvwzcspGkYwtHX-srEdQpo_Yadp41zI0Spis6Z31o5i3aYGo-PIu1qfmJ6L4RiuvPbElZA7L_TrRxEVcJ-PIu86gVhzvuB4nO1tYmfZPXjBJPgda=s0)**

Um olhar sobre os vários parâmetros mostra que mx pode não só pesquisar bases de dados ISIS (bool =), mas aplicar "on-the-fly" Gizmo (substituição de strings) e conversão ANSI (ansi=), juntar campos de registros de diferentes bases de dados, mas identificadas pelas suas entrada IF (join= e jchk =), aplicar processos de entrada de dados (proc =) e operações de arquivo invertido.

Como CISIS vem em diversas variações, de acordo com a capacidade das bases de dados e Chaves do Arquivo invertido pretendidas, temos que especificar que, para o ABCD só usaremos a variação '16/60 ' de mx e outras ferramentas CISIS. Isto pode ser verificado a partir das informações mx oferece quando invocado sem qualquer parâmetro, como ilustrado:

![](https://lh5.googleusercontent.com/0AvWw9FZmlv63nUjXS52-vb1P-FNLTMuWm-4EB871bhv3jZNiOvjwgon4BIQX9v1RrnesyPoOCkXFlZgGZ69PnZCk3ofRODNGhXwOInlggaXOPaFPjdGM1djTe667ByL008WRiaL=s0)


Os usos mais relevantes de mx neste contexto do ABCD são:
Importação de registros ISO para uma base de dados ISIS, por exemplo, o comando: 

```
mx iso=MeusRegistros.iso create=minhabase now -all tell=100
```
    
Irá ler o arquivo MeusRegistros.iso e criar uma base de dados ISIS 'minha base' sem esperar por qualquer entrada do usuário ('now'ait) e sem mostrar qualquer informação na tela (-all), mas mostrando o progresso após cada 100 registros importados.

  
>Nota: 
>No ABCD este comando é usado para importar uma quantidade maior de registros ISO para uma base de dados, visto que um número grande e, portanto, longo tempo de processamento poderia invocar o tempo limite (time-out) do servidor web, para interromper o processo.

  

Indexar uma base de dados ISIS, por exemplo, o comando:

```
mx mydb ifupd/create=mydb fst=@mydb.fst stw=@mydb.stw now -all
```

Irá criar um “Arquivo Invertido” chamado “mydb” usando a base de dados mydb com as especificações de indexação constantes na FST “mydb.fst” e omitindo os stopwords listados no “mydb.stw”, novamente sem modo interativo ou de saída (now -all).


> Nota: 
> No ABCD o mx é usado para criar um índice off-line no caso de – como é o caso frequentemente – a base de dados ser grande.


### Ferramentas de Arquivo Invertido: mz, ifupd, ifkeys, ifload, ifmerge
  
Estas são ferramentas mais especializadas para gerar/atualizar o Arquivo Invertido ISIS com sua tecnologia de Árvore B (B-Tree) e suas partes (nodos e folhas) a partir da linha de comandos com velocidade um pouco mais otimizada e mais opções. Exemplo, intervalos de MFN podem ser definidos, chaves podem ser extraídos do LK (link), arquivos criados anteriormente (ifload), ou arquivos de nodos (ifmerge) da Árvore B (B-Tree), que podem ser balanceados, etc.

Normalmente não é necessário usar estes recursos com ABCD, mas conhecendo as possibilidades existentes, especialmente no caso de bases de dados muito grandes, certamente são úteis.

### Outras ferramentas CISIS

Outras ferramentas que podem ser apenas mencionadas brevemente são:

1. retag: esta ferramenta irá mudar as etiquetas (tags) dos campos de acordo com uma determinada especificação - que pode ter instruções sobre muitos campos em uma execução 
2. mfcrunch e ifcrunch: para converter os arquivos ISIS (resp .MST e arquivos IF) de DOS/Windows para Unix/Linux e v.v. 
3. mkxrf: para recriar o arquivo .XRF para uma determinada base de dados, caso este tenha sido perdido ou danificado - a ferramenta irá analisar o arquivo MST e atribuir registros XRF ao arquivo .XRF. 
4. ctlmfn: para editar os valores do “registro de controle” da base de dados, no qual o maxMFN e outros valores muito técnicos para a base de dados são armazenados - só para os peritos!

## Linguagem de formatação ISIS

A Linguagem de Formatação ISIS (LF é uma das peças mais importantes do software porque oferece aos gerentes ISIS a possibilidade de definir exatamente o que ISIS irá produzir como saída de bases de dados em vários estágios do software, por exemplo:

  • o que ISIS irá mostrar na tela, ou seja, apresentar (definido no tabela de formato de impressão ou PFT);
  • o que ISIS irá utilizar para a criação de chaves de indexação (definido na coluna 3 da Tabela ou Seleção de Campo (FST));
  • o que ISIS irá utilizar para classificar os registros;
  • o que ISIS irá utilizar como valores exportados (definido na FST de reformatação);
  • o que ISIS irá usar como valores para validar a entrada  de dados em campos (indicados nas tabelas de validação).

### A Linguagem de Formatação para apresentação de valores

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

A documentação completa sobre a Linguagem de Formatação CISIS está disponível [nesta página](/pt/abcd-technology/cisis-formatting/)

### A LF para definição de chaves de indexação
  
A mesma Linguagem de Formatação (LF), mas é claro sem efeitos de aparência relacionados, pode ser usada para definir exatamente quais os valores devem ir para o Arquivo Invertido do ISIS. Isso será definido na terceira coluna da “Field Select Table” onde o formato de extração usando a LF deve ser usado. Veja também a discussão sobre a definição da FST no capítulo sobre definição  e gestão de bases de dados deste manual.


Visto que a Linguagem de Formatação completa - exceto elementos gráficos - está disponível, a função REF, por exemplo, pode ser usada para ter no arquivo invertido valores diferentes do conteúdo de campo atual, mesmo de outra base de dados. Isto, por exemplo, pode ser utilizado para substituir os códigos por sua descrição completa ou vice-versa.


### A LF para definição de chaves de classificação 
    
O mesmo raciocínio pode ser aplicado para a definição das chaves que ISIS irá utilizar para classificar registros: mais uma vez os valores reais de classificação podem ser processados com valores provenientes de valores do campo atual, usando a LF.


### A LF para conversão durante importação/exportação

Durante a importação/exportação de registros, a maioria das aplicações ISIS permitirá a utilização de uma FST de "reformatação", que tem na terceira coluna, a definição exata do que deve ser  exportado/importado, e na primeira coluna a tag (o “Identificador”) a ser atribuída a esse valor.

### A LF para instruções de validação

A Linguagem de Formatação também pode ser usada para criar mensagens de erro, no caso de condições definidas são (ou não) satisfeitas. Estas condições serão verificadas quando gravar os dados inseridos em um formulário (planilha) de entrada de dados no registro. ABCD oferece esta técnica, por default, como explicado na seção sobre validação de registros. Um exemplo pode novamente esclarecer isso facilmente:

```
if a(Vx) then 'This field is mandatory, please check again !' fi
```

Essa declaração vai produzir, na tela, a mensagem "Este campo é obrigatório, por favor, verifique!" se o valor do campo com tag x não existir ou está a(usente).

Instruções mais sofisticadas podem ser usadas para obter qualidade de verificação mais avançada/consistente, por exemplo, usando um “SELECT”, ou mesmo verificando o valor em outra base (com a anteriormente discutida função “REF”) para ver se é uma entrada válida.


## ISIS Script

ISIS Script é uma linguagem de script, desenvolvida pela BIREME, a fim de tornar mais forte as funções disponíveis para o servidor WEB ISIS “WWWISIS" para criação de páginas com elementos de Bases de dados ISIS. ISIS Script de fato foi um dos principais elementos na evolução de WWWISIS para “WXIS" que é o servidor web subjacente para o ABCD.

Scripts de ISIS script são armazenados como arquivos com a extensão .XIS. ABCD usa mais de 100 scripts, a maioria deles na pasta php/dataentry/wxis mas também o iAH (o OPAC) faz amplo uso de tais scripts. 

Obviamente não se pode discutir todo o poder da linguagem de ISIS Script aqui. Como uma linguagem, usa instruções semelhantes a XML, como, por exemplo, entre as tags  ```<pft>``` e ```</pft>``` pode ser colocado um formato de impressão e esse formato pode ser apresentado, colocando-o entre as tags ```<display>``` and ```</display>```. Todos os parâmetros WXIS podem ser definidos dentro das tags ```<parm>``` e ```</parm>``` e campos podem ser definidos com valores, por exemplo
 
```
<field action="replace" tag="6000">ValueOfField6000</field>
```
vai colocar a string “Valor_do_campo_6000” no campo de tag 6000 (tais valores elevados de tag, na verdade todas as tags  acima de 999, são utilizadas em geral em aplicativos ISIS para valores temporários internos que na realidade não são armazenados em registros ISIS, mas como “registros virtuais".

ISIS Script permite uma manipulação mais flexível de elementos de dados, provenientes de bases de dados ISIS,  em páginas web. Em combinação com o PHP (veja a seção dedicada a PHP), que é uma linguagem para criação de páginas web, resultados sofisticados são possíveis e isto certamente contribui para a funcionalidade geral avançada do ABCD. 

É claro que mais detalhes sobre a linguagem ISIS Script podem ser encontradas na documentação específica.

## J-ISIS

J-ISIS ou J(ava)-ISIS é a nova tecnologia atual na família ISIS, baseada em Java.

Há mais tempo, uma primeira tentativa de criar uma versão ISIS baseada em java foi feita por uma equipe italiana. O resultado foi uma solução funcional para consultar as bases de dados ISIS remotamente usando java, embora não fosse muito eficiente. Este esforço parou o desenvolvimento após alguns anos e não é mais mantido ou disponível.


A partir de 2005, o especialista em software da UNESCO, Sr. Jean-Claude Dauphin, responsável principalmente pelo software IDAMS mantido pela UNESCO (para gerenciamento estatístico), começou a desenvolver uma versão ISIS totalmente nova, não mais baseada na abordagem 'MST/XRF' até então única, mas armazenando os dados em um banco de dados de valores-chave sem esquema 'Berkeley DB' (veja, por exemplo [http://www.oracle.com/technetwork/products/berkeleydb/overview/index-085366.html](http://www.oracle.com/technetwork/products/berkeleydb/overview/index-085366.html) ), disponível ainda como FOSS da Oracle. Para o motor de busca e indexação foi utilizada a tecnologia comprovada da Lucene da Apache Software Foundation.

A verdadeira tecnologia ISIS dos conceitos de registros de comprimento variável, campos e subcampos com a linguagem de formatação ISIS (PFT) usada não apenas na apresentação de saída, mas também na Tabela de Seleção de Campo (para definir a seqüência exata a ser levada no índice) ainda está presente e na verdade faz com que J-ISISIS ainda seja ISIS. A propósito, o J-ISIS é a primeira versão que contém um PFT-parser para verificação gramatical e assistência.


O uso do Berkeley DB significa que não são mais impostos limites aos comprimentos de registros (no ISIS tradicional até 32Kb com possibilidade de extensão no CISIS até 1Mb) ou tamanhos de banco de dados.

O uso da tecnologia de indexação Lucene significa que não apenas todas as técnicas de indexação anteriores permanecem disponíveis, mas também a 'classificação' agora é adicionada, tornando o J-ISIS mais adequado para, por exemplo, aplicações de texto completo. Uma base de dados de 'biblioteca digital', baseada no conceito de usar a biblioteca TIKA para extração de texto de formatos de documentos simplesmente carregando um documento em um campo de texto, está incluída no pacote de distribuição do J-ISIS.

Pelo menos uma vez por ano uma nova atualização é disponibilizada, antes através do kenai.com, hoje (a partir de abril de 2017) na URL  [https://github.com/J-ISIS/J-ISIS](https://github.com/J-ISIS/J-ISIS ) .

A 'nova geração' ABCD (versão 3.x) será baseada no J-ISIS e está atualmente sendo desenvolvida por uma equipe da 'Universidad de Ciencias Informáticas' (UCI) em Havana, Cuba.

## PHP
    
PHP é uma linguagem “Hypertext Pré-processing”, o que significa que é uma linguagem de programação para páginas web. Como um dos produtos de sucesso “FOSS" é hoje muito popular e largamente utilizado, frequentemente em combinação com o Apache e banco de dados MySQL. Isto tem mesmo levado a pacotes como o "WAMP” e “EasyPHP” (Windows, Apache, MySQL e PHP), que permitem instalar esses softwares, muitas vezes combinadas em um pacote.

Como de costume, há algumas críticas sobre o PHP como uma linguagem, mas o fato é que é muito popular e está ficando cada vez mais poderosa com cada lançamento. ABCD usa, por exemplo, também "controles" ou módulos prontos disponíveis para funções específicas, que estão livremente disponíveis.

ABCD 2.0 é compatível com as versões atuais do PHP, ou seja, 5.x e 7.x. Não mais - como no ABCD 1.x - o parâmetro 'short_open_tag' precisa ser ativado, mas algumas 'extensões' não padronizadas precisam ser ativadas (em php.ini) : gd2, xsl, yaz, xmlrpc, e se as funções relacionadas forem usadas : ldap, mysqli (para EmpWeb) e mbstring (para Unicode).

## JavaScript
    
O nome oficial do JavaScript é "ECMA Script", mas o JavaScript é o nome popular de uma tecnologia que é hoje utilizada em muitas páginas web: relativamente pequenos programas incorporados ao códigos das páginas HTML. Contrariamente ao nome, a linguagem realmente não está ligada à linguagem de programação JAVA. JavaScript hoje em dia é suportado por todos os atuais  navegadores web  e não precisa de nenhum software adicional ou configuração. 
No entanto, continua a ser uma opção que também pode ser desligada (por exemplo, no Firefox: **Ferramentas -> Opções -> Conteúdo**, onde ambos JavaScript e Java podem ser desabiblitados), para se certificar de que a opção JavaScript está habilitado para o uso do ABCD.

ABCD utiliza ”scripts” de JavaScript dentro de suas páginas em muitos e muitos casos, uma razão é que, ao fazer assim, o computador local pode processar dados sem a necessidade de  tráfego intenso entre o servidor e o cliente (o que é importante em condições de conectividade lenta).

Como exemplo de um JavaScript simples podemos nos referir ao script “lrtrim.js” (na pasta `\www\htdocs\php\dataentry\js\`), que é chamado a partir de várias páginas ABCD-PHP. O script retira espaços em branco à direita ou à esquerda de strings. Isto pode perfeitamente ser feito localmente, sem a necessidade de envio da string para o servidor juntamente com o pedido de retirada e depois enviando de volta do servidor. Portanto, o script é carregado em uma página ABCD e executado localmente.


Também módulos JavaScript existentes e disponíveis frequentemente estão sendo usados, por exemplo, para a função de calendário no módulo de Empréstimo ou para o "Editor HTML" (FCKEditor.js). Abaixo um exemplo de calendário é mostrado, com base no JavaScript “Popcalendar.js” que pode ser encontrado, por exemplo, na pasta php/loans/js  da pasta “home” ABCD (/ABCD/www/htdocs). 

Esta pequena ferramenta exibe qualquer mês do calendário e permite a marcação dos feriados para levá-los em conta no cálculo do período de empréstimos!

  
![](https://lh6.googleusercontent.com/Mnn3D39lRsOzRc4pYefnVMSjV8Xg7d6yAIuKN7cqWRUR2GAhG8NKlE875jD7DJCnHTvewPZbYKkXASR5Er_YrKs6acSpIb9X-SU-IXgkgLF_RTOrHSi3Nel7C-OUGEBcZaDWJfyc=s0)  
  

A maioria das funções JavaScript, no entanto, não são visíveis na tela, mas desempenham funções úteis dentro de páginas web do ABCD. Assim, mesmo que ferramentas como as acima mencionadas (o editor HTML ou do calendário) sejam consideradas desnecessárias, ainda é importante para manter a opção de executar o JavaScript no seu navegador em “on”. Assim como com o Java, esta opção, por exemplo, no Firefox pode ser verificado no menu **Ferramentas -> Opções -> guia de conteúdo** (no Internet Explorer deve-se ativar para scripts ativos na seção da zona de segurança “Internet” em **Ferramentas -> Opções da Internet -> Segurança**).

## JAVA, Groovy e Jetty
    
JAVA é ao mesmo tempo uma linguagem de programação (como por exemplo 'C++') e um 'compilador em tempo de execução', o que significa que programas escritos em JAVA precisam de uma versão 'RunTime Environment' (RTE) de JAVA que compilará o programa para a combinação do Sistema Operacional e CPU em tempo de execução (ou seja, quando o usuário executa o programa). Ao fazer isso, os programas JAVA são completamente 'multi-plataforma' (Windows, UNIX, Linux, OS/X...) porque tais RTE's existem para todas as plataformas e estão disponíveis gratuitamente para instalação. Portanto, certifique-se de que seu computador tenha seu próprio JAVA RTE instalado ! Tanto a Sun (a verdadeira promotora Java) como a Microsoft oferecem versões gratuitas de Java (por exemplo, em http:// java.com/pt/download). JAVA não é apenas gratuito, mas também 'Open Source' e, portanto, pode ser relatado como sendo totalmente 'FOSS', assim como o ABCD.

ABCD usa JAVA apenas para o "módulo avançado de empréstimo”, que vem com uma opção extra (ver o capítulo sobre o módulo de Circulação). Este módulo avançado de gerenciamento de circulação é destinado apenas para as instituições com regras mais complexas de circulação e múltiplas setoriais, com suas próprias políticas de empréstimo ou com bases de dados de usuário em outros formatos (por exemplo, SQL). Também funções de estilo “MinhaBiblioteca” mais interativas podem ser oferecidas. A fim de permitir estas combinações mais complicadas dos softwares, ABCD chama Java para fornecer “web-services” e os links com banco de dados de outros modelos.

Groovy é uma linguagem de programação orientada a objetos para a plataforma Java, que pode ser utilizado como uma linguagem de script para a plataforma Java. 

O módulo avançado de empréstimo do ABCD (EmpWeb) também usa tecnologia Jetty, que é um servidor http Server e recipiente de “Servlet” escrito em Java. 

Jetty pode ser usado como:
  • um servidor web tradicional autônomo para conteúdo estático e dinâmico;
  • um servidor de conteúdo dinâmico por trás de um servidor HTTP dedicado como o Apache, usando “mod_proxy”;
  • um componente incorporado em um aplicativo Java.


## MySQL

MySQL é um banco de dados relacional desenvolvido como FOSS, mas com um esquema de 'licença dupla, permitindo tanto  aplicativos comerciais como gratuitos. Atualmente o MySQL foi adquirida pela Sun Microsystems, um forte defensor de software FOSS, por exemplo, JAVA. Recentemente, a Sun Microsystems foi retomada pela Oracle, assim o futuro não é tão claro.

Como um banco de dados, MySQL tornou-se extremamente popular devido à sua facilidade de uso e empacotamento combinado com, por exemplo, Apache e PHP para facilitar a implantação de bases de dados orientadas para websites.

Exemplos de tais pré-embaladas combinações de Apache/PHP com MySQL são: EasyPHP (http://www.easyphp.org) e WAMP para Windows ou XAMP para Linux  (http://www.wampserver.com). Ambos são Open Source e de uso livre (licença GPL).

Os críticos alegam que suas qualidades “relacionais” ainda estão atrasadas - mesmo que tenha melhorado muito nos últimos tempos – comparado ao exemplo de PosgreSQL ou certamente aos principais bancos de dados relacionais como Oracle ou IBM DBII. Alguns outros pacotes de automação de bibliotecas estão usando completamente o MySQL para a base de dados, sendo KOHA o mais conhecido (apesar de que atualmente KOHA prevê mudar para outro tipo de banco de dados, ou seja, “Zebra” justamente para evitar limitações do MySQL, para fins de biblioteca.

A parte 'SQL' do nome significa "Standard Query Language", denotando uma gramática padrão para recuperação de dados a partir de relações (tabelas relacionadas), baseando-se, porém, fortemente em sua estrutura relacional. Por esta razão, por exemplo, ISIS não utilizar o SQL visto que não armazena seus dados em tabelas com células e estruturas fixas.

MySQL será usado no ABCD apenas no módulo de "Empréstimos Avançado", que é um módulo extra não-padrão (consulte o capítulo sobre o módulo de empréstimo neste manual). Será usado para armazenar as transações do sistema de empréstimo, visto que estes são dados administrativos, que podem ser tratados de forma mais eficiente por esse tipo de base de dados, em comparação com ISIS com todos os seus recursos - neste caso, desnecessários - flexibilidade e baseada em texto.


## YAZ

YAZ é um software disponível livremente para a incorporação do protocolo Z39.50 nas aplicações.
Z39.50 é usado como um protocolo para recuperar dados de outros catálogos, principalmente em formato MARC.
ABCD usa YAZ para a sua função "Z39.50" no módulo de catalogação.


## Apache
    

Apache é o nome do software do servidor web muito utilizado em servidores web “open source”. De fato, estamos falando de um software chamado “httpd”, que é apenas um produto da poderosa “Apache Software Foundation", que também fornece outros produtos interessantes, como por exemplo Indexação Lucene (que também vai ser utilizado nas próximas versões do ABCD), Tomcat (um Servlet Java e Servidor “Server Pages”) e Derby DB. 

Apache, como um servidor web, parece ser o mais amplamente utilizado atualmente na Internet, que é um dos (poucos) exemplos em que o software livre domina sobre as soluções comerciais oferecidas. Todas as informações sobre o servidor web Apache e arquivos para baixar podem ser encontrados na URL: [http://www.apache.org](http://www.apache.org).

Em muitos casos, o software servidor web Apache já estará instalado no servidor onde ABCD irá residir, como também provavelmente é o caso do PHP (e MySQL). Por esta razão ABCD virá com dois pacotes, um incluindo Apache e PHP e outro sem os mesmos. No caso de um servidor web Apache existente, alguém com conhecimentos sobre o Apache deve estar disponível para integrar ABCD com as aplicações existentes baseados no Apache. Por exemplo, um servidor virtual para ABCD poderia ser criada com “aliases” específicos para o sistema ABCD (home do htdocs) e cgi (pasta de scripts). No caso do pacote completo, a versão http Apache mais recente “estável” será incluída, pré-configurada para trabalhar com ABCD como 'localhost' (que significa: o próprio PC roda tanto o cliente como o servidor). Um pequeno script irá iniciar o serviço httpd (ou Apache) com base nesta configuração, de modo que os esforços de instalação e configuração, em princípio, podem ser reduzidos ao mínimo indispensável. Em caso de configuração adicional ainda necessária, o usuário deve estar plenamente consciente do fato de que o Apache, como um software baseado em Linux, é “case-sensitive” para seus parâmetros e nomes de arquivos (com as informações de caminho)!

*Em relação aos servidores web, devemos mencionar "IIS" (Internet Information Services) da Microsoft, software gratuito, mas não livre, que é o servidor web que vem com o Windows. As diferenças estão principalmente na forma como deve/pode ser configurado e gerenciado, em vez de em desempenho, segurança, etc .. A terminologia é um pouco diferente (por exemplo, 'aliases' são chamados de "pastas virtuais" e não há arquivo de configuração ASCII facilmente acessível, como no Apache e seu “httpd.conf”).
ABCD funciona perfeitamente com IIS, como acontece com outros softwares de servidor web (por exemplo, Xitami), mas esse manual não suporta a implementação no IIS.*