---
title: Instalação do ABCD
description: Versões de instalação disponíveis
tags: 
 - installation
 - server
 - apache
lang: pt
lang-ref: abcd-installation
---

# Instalação do ABCD

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Versões de instalação disponíveis
    
A versão ABCD 1.0 veio originalmente em três versões principais :

1. pacote de instalação não assistida para Windows : este é um arquivo ZIP contendo todos os arquivos necessários, que simplesmente precisam ser descompactados na raiz de (um de seus) discos rígidos, por exemplo, C:\. Uma vez que abrange tanto o Apache quanto o PHP, depois de simplesmente descompactar ele deve normalmente funcionar! Aqui o Apache vem com seu próprio arquivo de configuração (httpd.conf), onde a porta 9090 é ativada para permitir a execução ao lado de possíveis outras instalações Apache em execução. Somente para alguns usos específicos, por exemplo, o uso do Z39.50 que necessita de módulos PHP adicionais (YAZ), será necessário fazer alguma edição (do php.ini, por exemplo).
 As instalações do ABCD que usarão o módulo Advanced Loans (EmpWeb) precisam descompactar adicionalmente o mais recente pacote EmpWeb. zip, onde uma subpasta principal extra no \ABCD será criada e alguns arquivos adicionais serão adicionados ao diretório central do ABCD.

2. Instalação assistida para Windows: este é um executável auto-instalável, que primeiro verificará se o Apache e o PHP já estão instalados no sistema. Se assim for, estas instalações serão puladas, caso contrário serão adicionadas à instalação básica do ABCD. Isto requer principalmente seguir os diálogos e instruções do próprio instalador. No final, uma pasta de diretório semelhante à do pacote sob 1. será o resultado.
    
3. pacote de instalação não assistida para Linux : este é um arquivo .tar.gz para sistemas Linux que deve ser des- empacotado no sistema de arquivos Linux, dependendo de sua organização (definição sobre onde tais aplicações podem ser colocadas). Se os direitos de acesso corretos forem concedidos (com os comandos apropriados do Linux, tais como chown e chmod) o ABCD pode ser instalado, como no Windows, sob a raiz do sistema de arquivos '/'. Em sistemas Linux a suposição é que Apache e PHP são instalados separadamente (por exemplo, com a ferramenta dedicada como apt-get ou Synaptic), assim o pacote contém apenas os arquivos ABCD apropriados no diretório 'www'-directory'.
    
A nova versão 2.0 é simplificada: não mais o ABCD vem com sua própria conifiguração do Apache com PHP para Windows, já que hoje em dia existem pacotes de instalação muito bons para estes ambientes (WAMP, XAMP), mas também estes pacotes estão em melhor posição para manter as diferentes versões do Apache (ASF, Bauhaus ???) em segurança de linha ou não compiladas com uma das muitas versões do MS Visual C (9, 10. 14) simplificadas com o
versões do PHP, novamente versões de 32 ou 64 bits, etc.

Portanto, a instalação para Windows é agora muito semelhante à do Linux: Apache e PHP devem ter sido pré-instalados e -configurados. O ABCD precisa apenas de um arquivo de configuração 'host virtual' para ser adicionado ao Apache-server a fim de ser executado a partir daquela versão pré-instalada. Por exemplo, WAMP o arquivo - que vem com a instalação

- httpd-hosts-abcd.conf simplesmente precisa ser adicionado ao 'alias' - diretório e Apache reiniciado.


## Problemas de instalação

Esta seção trata das questões de instalação para ABCD. Como o ABCD tem vários componentes totalmente diferentes, a instalação, por definição, engloba algumas armadilhas potenciais. Três razões principais podem ser dadas para a complexidade do sistema de emparelhamento:

1.  O ABCD é uma combinação de várias tecnologias de software : Bases de dados ISIS, scripts ISIS e formatos ISIS, um servidor web, PHP-scripting, mais (no caso do módulo avançado de Empréstimos) algumas partes JAVA e MySQL;  
2. Sendo baseado na web, o que significa que um servidor web tem que ser instalado e medidas especiais têm que ser tomadas sobre direitos de acesso e segurança: em princípio o mundo inteiro - com acesso à WWW - pode interferir.
3.  O ABCD será instalado em situações bem diferentes, variando desde um simples PC autônomo (mesmo sem rede) até servidores em grandes redes com um servidor web e muitas vezes também serviços de PHP-scripting já pré-instalados.

Anteriormente, os pacotes de instalação vinham em dois tipos :

1. um pacote completo, contendo todos os arquivos ABCD-proper mais o servidor web Apache e o mecanismo de PHP-scripting.
Nesta situação, um arquivo (.zip) precisa ser desempacotado em uma pasta raiz do sistema de arquivos (que pode ser qualquer sistema operacional no qual Apache/PHP e ISIS possam rodar). Após desempacotar, haverá uma pasta dedicada para o Apache, outra para o PHP, uma pasta cgi (para conter os executáveis acessíveis pela web) e uma pasta 'documentos' (no Apache chamada 'htdocs') que funciona como a página inicial da aplicação ABCD.
    - O Apache vem com um arquivo de configuração pré-definido (httpd.conf na subpasta conf da pasta Apache) que define os seguintes parâmetros específicos :



|**Apache parameter**| **explanation** |
|--|--|
|ServerRoot "/ABCD/apache"| the directory from where Apache runs|
|Listen 9090|the port used by ABCD, the default http-port being 80, but in order to avoid interference with other ex- isting http-applications, if so desired, a different port can be used, e.g. 9090. In case of using a different port-number, some adjustments will have to be made in the ABCD_start.bat script and in some OPAC- URL's.|
|PHPIniDir "/ABCD/php"|The folder from where PHP is running|
|DocumentRoot "/ABCD/www/htdocs"|The root-folder for all the files which are part of the application itself, so the ' homepage'|
|ScriptAlias /cgi-bin/ "/ABCD/www/cgi-bin/"|The folder in which Apache will executables allow to run from instructions in the web-pages|

> Nota: Certifique-se de que o módulo 'cgi' do PHP esteja instalado no Apache,
> o que não é mais o caso (como antes) nas instalações Apache mais recentes.
> O comando para instalar este módulo no Linux é :

```
sudo a2enmod cgi
```
-   PHP comes with a predefined configuration in php.ini.

#### Configurações PHP e php.ini

Como a ABCD usa PHP com alguns módulos adicionais de PHP (YAZ, XSLTProcessor...) as peras devem ser instaladas dentro da instalação do PHP e alguns módulos extras precisam ser copiados para a pasta 'ex- tensões' do PHP : php_yaz.dll, yaz.dll, yaz3.dll (estes dois servem a função Z39.50 da catalogação da ABCD), iconv.dll, libxm2l.dll, libxslt.dll (para o Processador XSLT). A pasta PHP-extensions precisa estar presente na variável de ambiente Path do sistema (no Windows por exemplo: vá para 'My Computer (right-click) `| Properties | Advanced | Environment Variables | System` e edite a variável Path adicionando, se não estiver presente: ';C:\ABCD\php\ext'). Certifique-se também de que seu php.ini (em \ABCD\php) tem as extensões mencionadas aqui com- mente as extensões (isto é, remova o ';' principal para ativar a extensão).

* extension=iconv.dll
* extension=iconv.dll
* extension=libxml2.dll
* extension=libxslt.dll
* extension=yaz3.dll
* extension=php_yaz.dll

Tenha cuidado com possíveis outros arquivos php.ini existentes, por exemplo, em Windows ou PHP, pois estes podem perturbar seu ABCD-PHP. Uma opção de teste PHP está disponível com o ABCD na URL : http://localthos:9090/info.php. Estamos especificamente interessados na seguinte seção abaixo, onde XSL e YAZ devem ser mencionados como executando

- se não verificar novamente sua variável path-environment e todos os caminhos, assim como a seção de 'extensões' de seu php.ini !
    
  
![](https://lh3.googleusercontent.com/pbkmTbhGVKMZUoDhfCpUtppoiU7g62SzdWYvph68NZ6bmxAk7jxFzqSCuuJOM1uw4zLhJclusfPHuLy2TkeeukzIDPnMZVm8PCXcMnCrS-v9HUwgEEO3hYrHLEF4_4EhhWFOfTgl=s0)  
  

- register_globals = On (padrão = Off)
- extension_dir = "/ABCD/php/ext" (ou ajustar ao caminho real para sua instalação ABCD)
- default_charset = "iso-8859-1" (default = não ativo) ou "utf8" se Unicode deve ser usado
- extension_dir = "/ABCD/php/ext" => define o diretório de extensões
- extension=yaz3.dll e extension=php_yaz.dll são listados no => são adicionados na seção 'Dy- namic Extensions' a fim de permitir que o módulo YAZ para Z3950 funcione

Nota
A partir do ABCD 2.0, não é mais necessário manter a configuração de 'short_open_tag' para 'On' (que é contra-indicada de qualquer forma). Todas as 'short open tags' ```<?``` foram alteradas para to ```<?php``` .

2. um pacote somente ABCD, requerendo Apache (ou outro web-server) e PHP já sendo instalado.

Neste caso, a suposição é que pelo menos alguma experiência está disponível para entender a instalação do web-server existente e a configuração do PHP. Usando 'pseudônimos' para a instalação do ABCD e da pasta cgi, que pode ser colocada em um arquivo de configuração de host virtual, o ABCD pode ser instalado em qualquer lugar dentro ou fora da pasta existente para o servidor web. Assim, somente a pasta cgi e a pasta htdocs estão incluídas neste pacote. Os gerentes de sistema devem consultar os manuais do Apache e do PHP caso não tenham certeza sobre como proceder com este tipo de instalação.

Alternativamente, pode-se também usar instalações pré-embaladas como EasyPHP ou WAMP (para Windows) / XAMP (para UNIX/Linux). Novamente neste caso Apache e PHP (e MySQL) serão instalados automaticamente e as pastas cgi-bin e htdocs do ABCD terão que ser movidas para as estruturas de pastas existentes (do Apache) e o php.ini terá que ser editado.

A partir do ABCD 2.0 somente o segundo tipo de distribuições estará disponível, deixando a instalação do Apache e PHP para outros pacotes mais especializados, como WAMP ou XAMP. Apenas um arquivo específico de configuração 'host virtual' para ABCD precisa ser adicionado à configuração do Apache (por exemplo, em WAMP : colocando no diretório 'alias') e algumas configurações do PHP precisam ser verificadas em php.ini para ativar extensões adicionais, por exemplo, para gd2, libxml, xsl, e se as funções relacionadas forem usadas : ldap, yaz, mysqli (para Empweb) e mbstring (para Unicode).

Uma ferramenta de instalação dedicada será criada como parte do software ABCD, mas em essência ainda fazendo o mesmo como descrito acima, somente após a coleta de alguns parâmetros para instalação (como qual disco usar, qual porta etc.).

# Estrutura de diretório e direitos de acesso

Após a instalação do ABCD, será criada a seguinte estrutura de pastas (neste caso, o EmpWeb está incluído) :![](https://lh4.googleusercontent.com/qLB6IsXz6bzbMin7kOq6XtfMJUFdkHZUzMBv0eAOZHTTtrrgJZ1H0ziZM7xsbJnwdVeNzQ6gVg17NG-rhtiHqK3fiaWqYI-mpnzbDKzIzIXgbYXp_QAA5XRF1G00OmffiXQ9p5GP=s0)

Como pode ser visto, 3 (ou 4 se a EmpWeb estiver incluída) subpastas foram criadas na pasta principal /ABCD. No caso da instalação da pasta opcional Advanced Loans, mais uma pasta contendo tecnologia básica para ABCD será adicionada: o Java Development Kit (JDK). As pastas padrão são resp. :

## apache [somente ABCD 1.x]

A pasta Apache contém o software Apache web-server, que na verdade é apenas de vários softwares importantes desenvolvidos pela Apache Software Foundation. Por padrão o Apache webserver é instalado em outra pasta base (por exemplo, no Windows: C:\Program Files\Apache Software Foundation\Apache2.2) e os gerentes de rede provavelmente terão instalado o Apache em seu(s) servidor(es) de acordo com suas próprias preferências, mas quando instalado a partir do 'pacote ABCD completo', o Apache será executado - com seu arquivo de configuração httpd.conf ajustado para esta situação a partir do Apache \ABCD\Apache.


## php [somente ABCD 1.x]

A pasta PHP contém o software PHP scripting. Novamente, como no Apache, em muitos casos este software será instalado por direito próprio, por exemplo em C:\PHP, ou muitas vezes também como parte de um pacote combinado contendo Apache, MySQL e PHP, por exemplo, com EasyPHP ou WAMP-server. Quando instalado como parte do ABCD, entretanto, o PHP será executado a partir daqui com os ajustes necessários feitos no arquivo principal de configuração do PHP php.ini.


## www
A pasta www contém todo o sistema ABCD, que está subdividido em 4 pastas :

![](https://lh5.googleusercontent.com/L8VMgbN73AAypaMHcVUEOHhI9UrXunKxtYtccKqiI-zlfep4M_mdguSBw7q0B8m3m94pCc5qhy5dZ41Ii-B4vEh9W9-btdHUw366bmpvEEc8FJeM5UzztH8Lso9mU7YeK9LGjVjx=s0)
	
* bases

A pasta bases contém as bases de dados de sua instalação ABCD, que é uma subpasta dedicada (com muitas subpastas por sua vez) para cada base de dados. Quando uma base de dados adicional é copiada ou criada usando ABCD, o sistema criará aqui uma subpasta extra dedicada. Uma lista típica de subpastas do banco de dados na pasta /bases de dados tem a seguinte aparência :

![](https://lh6.googleusercontent.com/LabEXUm9-Q2wVGwdg5rAzOSpf1CFC9hIZOBrv5_8SV174Q6yrlT1u5GC1LgsSoYQ-i50enpQwQZDgG6rJfy80AI8LAHji71wZSGkOzke4_V8wxTGPwbHC5-Z9Ou2TLbLOXvkzqr7=s0)

  
[!!] Como pode ser visto, existem muitas bases de dados (mas não tantas como existem tabelas em uma configuração relacional, uma vez que ISIS não pratica a 'normalização' em tabelas relacionadas), algumas delas - por exemplo, marc, biblo, dblil - são modelos que vêm com a instalação do ABCD, outras - neste caso, por exemplo gemim' - são criados pelo ABCD somente na instalação do autor, enquanto finalmente outros servem módulos específicos do sistema de biblioteca, por exemplo 'providers' e 'purchaseorder', são usados para o módulo de aquisições, 'suggestions', 'suspml', trans e usuários são usados para o Módulo de Empréstimos. Entretanto, as pastas 'recommend' e 'reserva' são pastas legadas para versões mais antigas do ABCD pré 1.0. Portanto, cada pasta ABCD-base será diferente de acordo com as bases de dados efetivamente utilizadas.

Alguns arquivos de configuração essenciais a serem localizados nesta pasta são :

- bases.dat : a lista de bancos de dados disponíveis para esta instalação central (ou seja, um nome de banco de dados, um arator de coluna  `'|'`  e uma descrição
- lang.tab : uma lista de idiomas utilizados como pares de valores-chave para linguagem de código, por exemplo, en=english
- abcd.def : o arquivo principal de configuração de todo o sistema, veja a seção de configuração
- loans.dat : se este arquivo existir, a ABCD Central utilizará as cópias/loanobjetos diretamente da base de dados do catálogo, e não das bases de dados dedicadas a cópias/loanobjetos;
- acquisitions.dat : um arquivo listando as bases de dados do catálogo a serem utilizadas para a aquisição de cópias, por exemplo 

    marc|Marc
    biblo|Cepal


Observe que, como mais de uma base-diretório pode ser definido (em db_path.dat), também podem ser usados arquivos diferentes abcd.def (com parâmetros LEGEND1 e LEGEND2 diferentes para identificar o diretório-base na tela no rodapé).

Um banco de dados especial é o banco de dados 'acces' que mantém os usuários (com seus dados de login) e seus direitos de acesso (nível de autoridade) aos bancos de dados.

Na pasta 'www'-folder ABCD mantém alguns pequenos arquivos especiais, por exemplo, os códigos html 'prolog' e 'epilog' que serão invocados resp. antes e depois do conteúdo da página principal de cada ABCD-página produzida por um ISIS-PFT. Aqui é onde o gerente do sistema pode - se assim desejar - adicionar o código (por exemplo, JavaScript) que eles querem que seja executado em cada página.

A pasta 'LANG' também é bastante especial: ela contém, para cada linguagem utilizada, as tabelas com mensagens utilizadas para cada um dos módulos Centrais. Por exemplo, o arquivo 'lang.tab' contém as informações sobre os 4 idiomas efetivamente suportados oficialmente : pt=Português fr=Francês en=Inglês es=Espanhol. Esta lista de idiomas para cada idioma é baseada no arquivo lang.tab de idioma básico na própria pasta bases (onde reside junto com a lista de bases de dados disponíveis: bases.dat).


> Nota: 
> [!!] A subpasta '00' lang contém as tabelas que servem como
> 'mestre' para os outros idiomas. Sempre que uma mensagem não for encontrada por
> ABCD no idioma selecionado, ele se referirá a estas tabelas e utilizará
> as mensagens aí contidas, para evitar mensagens ausentes em qualquer
> linguagem. Desta forma, também se pode começar a traduzir para um novo idioma
> sem ter que terminar o trabalho completo antes de usar o ABCD, pois o
> as mensagens em falta serão tiradas do idioma '00'.

Finalmente, também a pasta 'par' não é, como 'lang', uma pasta de banco de dados, mas contém os arquivos .par para cada banco de dados conhecido pelo ABCD. Um arquivo .par na verdade é um pequeno arquivo de texto (por isso pode ser editado por qualquer editor TXT como o Notepad) com em cada linha a referência completa do caminho para partes do banco de dados em questão. Por exemplo, um arquivo .par típico para ABCD se parece com isto :
  
```
marc.*=%path_database%marc/data/marc.* 
prologoact.pft=%path_database%www/prologoact.pft 
prologo.pft=%path_database%www/prologo.pft
epilogoact.pft=%path_database%www/epilogoact.pft
epilogo.pft=%path_database%www/epilogo.pft
autoridades.pft=%path_database%marc/pfts/en/autoridades.pft”
```
  
Cada elemento recebe, após o sinal da equação, seu caminho no sistema de arquivo. Como pode ser visto, variáveis retiradas do Ambiente do Sistema Operacional podem ser utilizadas, neste caso %path_database%, que é substituída pelo caminho real conforme definido no arquivo principal de configuração config.php (ver infra).

[!!] Enquanto normalmente todos os elementos aqui referidos pertencem ao banco de dados em questão, elementos de outras bases de dados também devem ser adicionados se forem utilizados em 'REF' - declarações dos formatos utilizados neste banco de dados, uma vez que o ISIS terá que saber onde localizar tal elemento externo do banco de dados se chamado de um formato - e procurará seu caminho aqui !

## cgi-bin

A pasta cgi-bin contém os executáveis que o ABCD chamará a partir de suas páginas web e que, portanto, devem ser autorizados a serem executados pelo servidor web (Apache) usando o protocolo CGI. No caso do ABCD, o executável principal é o wxis.exe ISIS-server, que faz a parte principal do trabalho. Algumas outras ferramentas CISIS, no entanto, também estão incluídas para tarefas específicas.

A subpasta wxis-modules aqui contém scripts (com extensão .xis) para o wxis-server, enquanto a pasta 'gizmo' contém algumas pequenas bases de dados ISIS que definem strings a serem substituídas por outra, por exemplo, para alterações devido a diferentes ambientes utilizados (DOS/ASCII, Windows/ANSI, WWW/XML.

## htdocs

O htdocs (usamos o tradicional nome da pasta 'documentos de hipertexto' Apache) é a 'pasta de origem' do site servido pelo servidor ABCD-Apache. Portanto, ele contém todos os elementos de software (exceto a tecnologia básica externa, como Apache e PHP) especificamente produzidos para o ABCD :

![](https://lh6.googleusercontent.com/sMJ-zXYZyOb7bqWiOXNhZrCwJcjDM4wMvDfQeBnPVvZNCQndBx7axGxsSj-RBXab_ZbqgtLplxoPpKSMcKaAfxK7zACGetmaU9_qmgbWQ9d_XcjFtdCZ440jyQI7DrxdZ7_SKn_7=s0)  

  
Dois scripts iniciais estão presentes dentro desta pasta da homepage: index.php (que é a home-page padrão de fato, permitindo que a URL do ABCD se refira apenas à parte do servidor) e o script [!!] 'what.php' para incluir as informações de rodapé.

Um arquivo opcional 'db_path.dat' pode ser localizado aqui para apontar para diferentes (cada um em uma linha) pastas de banco de dados.

Como o ABCD é um 'conjunto' de diferentes funções, cada um tem sua própria homepage, ou seja, o arquivo 'index.html' localizado na subpasta apropriada.

As pastas principais do sistema ABCD são descritas resumidamente a seguir:

1.  **bases***
Aqui para cada banco de dados (em uma subpasta dedicada) arquivos externos ligados a partir dos registros do banco de dados,
Por exemplo, os PDFs de texto completo ou imagens, serão armazenados. Por exemplo, as imagens do usuário podem ser armazenadas aqui em uma subpasta 'usuários', assim as fotos do usuário serão mostradas sempre que um usuário do sistema de empréstimos for apresentado. [!!] Não misture esta pasta com a pasta 'bases' onde os bancos de dados reais residem!

2.  **central***
Esta é de fato, como sugere o nome, a parte "central" do sistema onde a maior parte da administração do banco de dados e muitas atividades essenciais do software estão incluídas. Trataremos, portanto, das importantes subpastas aqui contidas:

![](https://lh4.googleusercontent.com/oAeaF6wjkV-srtvdNT7KsY7pnflDrxcCU7E-uN4E0v-GdTvGwGzEyQ1Fka6AJTAu_359kJoQSjhNNJ3aGbPKpB4ukRNKGZpfoevjmVursjPkc01DMh2s3vjhJ2icywVN-1arTz_8=s0)

Alguns scripts iniciais estão localizados neste nível : homepage.php e inicio.php são as páginas iniciais, que lêem na memória os principais parâmetros de configuração definidos em config.php (ou config.loans.php para o módulo Loans). Para a funcionalidade 'mySite', scripts iniciais adicionais também serão encontrados aqui: ini- ciomysite.php, homepagemysite.php e availibility.php. Estes scripts agora (a partir do ABCD2.0) contêm tanto o código para EmpWeb (usando consultas SQL) quanto para Empréstimos Centrais (usando ISIS-QL), portanto, por exemplo, 'empwe- bavailability.php' não é mais usado uma vez que o código está incluído no 'availability.php'.

Os arquivos de configuração básica CONFIG.PHP, SYSTEM_CONF.PHP e DATABASE_CONF.PHP, que também são encontrados aqui, serão discutidos com mais detalhes em suas seções dedicadas à configuração ABCD-.

As seguintes pastas aqui tratam de uma função ou módulo específico do ABCD, armazenando os scripts PHP com muitos elementos adicionais (imagens e folhas de estilo para as páginas web, etc.): aquisições, entrada de dados, dbadmin, empréstimos, estatísticas e useradm.

Os nomes das pastas são suficientemente auto-explicativos nestes casos. Aqui gostaríamos apenas de sublinhar a presença de um módulo 'administração de banco de dados' que permite a criação de qualquer estrutura ISIS para lidar com qualquer tipo de dados textuais, permitindo que o ABCD seja mais flexível do que a maioria dos outros sistemas e mais do que apenas um sistema de biblioteca.


As pastas especiais aqui dedicadas a funções especiais no ABCD são as seguintes:

- comuns : aqui há alguns php-scripts cruciais que são necessários para todos os módulos, por exemplo, 'header' e 'footer', mas também 'wxis-llamar.php' (que permite usar o método cgi-method de chamar executáveis (mais seguro) ou chamadas executáveis diretas a partir do PHP (mais rápido). O script instituational_info.php define o nome da instituição ressonsável da instalação do ABCD, que será chamada em muitas páginas.
- documentacion : obviamente esta pasta contém scripts para lidar com as funções de ajuda on line do ABCD.
- imagens : contém pequenas imagens utilizadas em muitas páginas (principalmente .png e .gif)
- css : contém as folhas de estilo em cascata utilizadas nesta parte central do ABCD
- estilos : contém a folha de estilo principal básica 'basic.css'.
- lang : contém para cada módulo um script para facilitar a troca de idioma ou a reversão para o idioma padrão
- teste [depreciado] : contém alguns scripts que testam a instalação do ABCD e o acesso ao cgi-executable.

3.  **empweb***

Esta pasta não é padrão e contém as subpastas e peças de software usadas pelo módulo de Empréstimos Avançados do ABCD, que não está mais detalhado neste manual.

4.  **iah***
iAH é o nome original da interface web avançada para "Informações de Saúde" da BIREME que atua como o OPAC do ABCD mas também como um mecanismo de metabusca em outras fontes definidas como relevantes.

5.  **isisws***
Esta pasta contém scripts para as funções relacionadas à SOAP do ABCD.

6.  **secs-web***

Este módulo permite que o ABCD ofereça ferramentas avançadas de gerenciamento de séries dentro do ambiente web:
Sistema de Controle de Seriados. vii.site

Finalmente, o módulo 'Site' combina a busca OPAC avançada (com possibilidades de metabusca) com um serviço 'por- tal', oferecendo a opção de busca dentro de um ambiente de outros recursos de informação em rede e comunicação com os usuários. A estrutura e o conteúdo deste portal podem ser editados on-line com um sistema de gerenciamento de conteúdo ABCD integrado.



# EmpWeb (somente se a instalação do EmpWeb foi adicionada!)
    
Esta pasta contém a maioria, mas não todos os arquivos necessários para executar o EmpWeb, por exemplo, o servidor Java Jetty e os scripts. O EmpWeb, entretanto, também precisa adicionar scripts na Central ABCD (isto permite que os Empréstimos Avançados sejam compatíveis com o sistema de Empréstimos embutido do ABCD) e - como ele usa uma base de dados SQL para armazenar as transações - uma instalação de uma das bases de dados SQL comuns (MySQL, PostGres, Oracle...), que precisa ser feita separadamente - use as instruções de instalação para a solução SQL escolhida. Um manual separado no EmpWeb está disponível.