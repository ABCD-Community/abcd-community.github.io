---
title: Módulos ABCD
description: Este capítulo trata das principais funções [!!] do módulo 'Central' do sistema ABCD.
lang: pt
lang-ref: abcd-modules
---

# ABCD Modules

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Introdução e configuração geral

Este capítulo aborda as principais funções do sistema ABCD. Como um software de automação de bibliotecas integrado, o sistema oferece ferramentas para gerenciamento de bases de dados (tanto para bases de dados bibliográficas/documentais como bases de dados administrativas, tais como de usuários, aquisições e empréstimos), entrada de dados, estatísticas, circulação, controle de periódicos e funções de pesquisa (OPAC em um ambiente de "portal").

Estas funções são apresentadas em diferentes partes de uma suíte, que são relativamente independentes uns dos outros, mas não totalmente. As partes são acessadas através de sua própria URL. Dentro de uma parte podem existir vários módulos que também cooperam entre si. Por exemplo, as informações de pré-catalogação produzidas para aquisições serão reutilizadas na base de dados de itens para o módulo de circulação, que por sua vez utiliza informações bibliográficas dos catálogos. Estatísticas podem ser aplicadas a qualquer base de dados ISIS, não somente à base de dados de circulação, Assim, esta função também irá aparecer em várias instâncias dentro do software. A tecnologia OPAC pode ser executada em qualquer base ISIS, não só nos catálogos do próprio ABCD. Por isso vai ser descrito como uma ferramenta relativamente independente, como será o caso com o Controle de Periódicos.

**Importante**
Como acessar as partes da suíte diretamente?

-   Os primeiros seis módulos juntos constituem a parte 'Central' da suíte ABCD. Pode ser acessada pela URL http://[serverURL]:9090. "index.php" é opcional, se foi informado ao servidor web (Apache) que index.php é uma das páginas default na pasta (como é, por exemplo, também "index.html").
   
-   O combinado OPAC-com-portal (site) pode ser acessado por http://[serverURL]/site/index.php, com a página de administrador para este Site sendo http://[serverURL]/site/admin/index.php.
  
-   A parte de Controle de Periódicos deve ser acessada pela URL http://[serverURL]/secs-web/index.php.
   
-   EmpWeb pode ser acessado , se instalado, pela URL http://[serverURL]/empweb/ (observe a barra no fim da URL!)
   
Para todas estas partes ou módulos do ABCD, dados de “start login” estão disponíveis publicamente, que precisam ser lidos a partir do arquivo “leiame.txt” ou “readme.txt" que vem com o pacote de instalação. É de responsabilidade do administrador de sistema substituir os dados de login do sistema pelos dados de login locais – e localmente controladas.

ABCD gerencia o controle de quem pode acessar o sistema e com quais privilégios, através de um sistema de "perfis" (introduzido com a versão 1.0). Os perfis são conjuntos de módulos, bases de dados e formulários permitidos. Usuários ABCD (não usuários da biblioteca), então, serão atribuídos a um dos perfis definidos (ver "Administração de perfis de Usuários” na seção seguinte).

## Configuração de multilíngue
    
ABCD é totalmente concebido como um software multilíngue, permitindo a criação e uso de qualquer idioma. Todos os elementos sensíveis ao idioma, como mensagens de tela e arquivos de ajuda, mas para bancos de dados, por exemplo. também formatos de exibição, definição de campo e tabelas de seleção etc. são armazenados em subpastas separadas para cada idioma. Essas subpastas são nomeadas de acordo com os códigos de idioma que são definidos no arquivo 'lang.tab' do diretório 'bases'. Um exemplo desse arquivo lang.tab, no qual dois idiomas adicionais (alfabeto não latino) foram adicionados aos quatro idiomas padrão originais, está listado aqui:

* pt=português
* es=spanish
* en=english
* fr=french
* am=amharic
* si=sinhalese

Com esta lista todas as mensagens (o banco de dados 'lang') e estruturas de banco de dados e formatos de impressão terão (precisam) ter subpastas pt, es, en, fr, am e si. A lista de idiomas deve ser repetida em cada subpasta lang, se desejado, traduzindo cada um dos valores de idioma (não 'chaves', pois os códigos de abreviação precisam permanecer constantes!) ' está ligado (ver infra) - mesmo escrito em alfabetos não latinos. Cuidado com caracteres não ASCII, como 'ñ' (por exemplo, em español), pois eles são codificados de maneira diferente em ANSI (Windows) versus Unicode.

Como o ABCD pode lidar com múltiplas pastas de banco de dados (veja infra), será necessário definir o caminho para o banco de dados 'lang' para as mensagens com a variável '$msg_path'. Este padrão é o diretório definido por $db_path em config.php, mas também pode ser definido independentemente para qualquer pasta no sistema.

Uma linguagem 'virtual' especial com o código '00' é usada no ABCD para armazenar todas as mensagens das quais as traduções do idioma serão derivadas. Esses pares de valores-chave são definidos principalmente em inglês. As chaves são as referidas nos scripts PHP sempre que exibir um texto dependente do idioma nas telas, mas serão pesquisadas na tabela relacionada no idioma ativo, a menos que não seja encontrado lá: então o idioma '00' atua como a opção de reserva de reserva. Isso significa que, se uma mensagem não aparecer em seu próprio idioma, mas em inglês (supondo que seu idioma não seja inglês), essa chave ainda precisa ser traduzida (adicionada) à tabela correspondente ao seu idioma e a mensagem exibida é extraída do '00'-linguagem.

Mais adiante neste manual, uma seção dedicada discutirá como criar um novo idioma no ABCD com um exemplo Unicode não latino.

## Os principais arquivos de configuração do ABCD Central

A configuração principal do ABCD Central é baseada nos seguintes arquivos:

1.  config.php
2.  system_conf.php and abcd.def
3.  database_conf.php and dr_path.def

### CONFIG.PHP
Este arquivo contém as variáveis locais que são gerenciadas pelo administrador do sistema. Atualmente a lista de variáveis é a seguinte:

-   Date_default_timezone_set (os valores permitidos podem ser encontrados na URL [https://www.php.net/manual/pt_BR/function.date-default-timezone-set.php](https://www.php.net/manual/pt_BR/function.date-default-timezone-set.php)
-   $open_new_window : se definido como 'Y' após o login, uma nova janela com a interface ABCD principal será aberta além da tela de login
-   $context_menu : se definido como 'N', a interface Central na nova janela não conterá elementos de navegação (por exemplo, clicando com o botão direito do mouse) - isso é mais seguro para manter o trabalho ABCD separado de outras atividades do navegador e forçar o operador a usar a interface elementos em vez de elementos do navegador, por exemplo. voltar'
-   $config_date_format: define o formato das datas utilizadas; para ser dado como DD para dias, MM para meses e YY para a exibição do ano, cada vez separados por barras '/'.

> Nota:
> Se um campo for definido como 'ISO'-date, o formato será
> automaticamente ser aaaammdd; isso pode ser derivado automaticamente de um
> campo de data normal anterior definido com $config_date_format

- $Inventory_numeric :Se definido como 'Sim, os zeros à esquerda serão omitidos ao ler o número do inventário (ou código de barras) para torná-lo um valor numérico real
- $max_inventory_length: um número definindo o número fixo de posições no código de barras ou números de inventário; As posições ausentes se tornarão líderes do Zero.Este parâmetro é levado em consideração nos processos relacionados à atribuição dos números de inventário das cópias do banco de dados
- $max_cn_length : O mesmo que $ max_inventory_length, mas para o campo de número de controle: as posições ausentes até o número definido aqui serão preenchidas com zero
- $app_path: o nome da pasta agindo como 'central' com todos os scripts centrais; melhor manter como 'central'; Se renomeado, alguns scripts podem falhar.
- $log: Se definido como 'Y' um log na subpasta existente no diretório de banco de dados, todas as chamadas para o executável WXIS serão registradas em um arquivo por dia, de acordo com a data e com as seguintes informações:

Primeira linha: 
```
** Friday 30th of November 2012 07:34:35 AM Operator: abcd Identifies the date, time, and operator executing the transaction
```

Segunda linha: 
```
/central/dataentry/inicio_main.php/ABCD/www/htdocs/central/dataentry/wxis/login.xis IsisScript = / ABCD / www / htdocs / central / dataentry / wxis / login.xis ? Base = access & cipar = c: /bases_abcd/ bases/par/acces.par & Login = abcd & password = adm & path_db = c: / bases_abcd / bases / & cttype = s
```

Onde os seguintes elementos são identificados: Nome do script PHP que está em execução, nome do script WXIS sendo chamado, parâmetros enviados ao isisscript para a execução correspondente

> Nota:
> No futuro, este registro também será dependente de banco de dados.

- $img_path : Caminho padrão em que as imagens e documentos digitais vinculados aos registros dos bancos de dados serão armazenados.Este diretório padrão pode ser modificado usando o arquivo dr_path.def que fornece informações mais específicas sobre o armazenamento de documentos digitais para um banco de dados específico (consulte Infra).
- $msg_path : caminho para o banco de dados Lang para as mensagens da interface; Esse caminho pode estar em uma das pastas de banco de dados definidos, mas também fora de qualquer um deles
- $lang: linguagem padrão usada ao abrir o centro
- $lang_db: Idioma padrão para o módulo de administração de banco de dados (pode ser diferente de $ lang)
- $change_password: Se 'sim ou' não os operadores podem alterar suas senhas (na tela de login)
- $adm_login: Um nome de login opcionalmente interno para (temporariamente) permitir a entrada no sistema central, mesmo que o acesso aos bancos de dados não seja possível, por exemplo, por razões de depuração/teste; Por razões de segurança: remova este login quando não for necessário.
- $adm_password: uma senha opcionalmente interna para o login com $adm_login;

> Nota:
> Lembre-se de que esse login/senha atua no nível de administrador completo e, portanto, está em um nível de alto risco!

- $dirtree = 1: 1 mostra ou 0 oculta o ícone de menu que dê acesso à exploração do ditetório de bases; Alguns gerentes de rede ou servidores não permitirão essa função em seu sistema!
- $MD5 = Quando definido como 1 (on), as senhas serão criptografadas com a criptografia MD5
- $fix_file_name = Define uma matriz com substituições de caracteres a serem aplicadas em nomes de arquivos para arquivos carregados (para evitar complicados, por exemplo, caracteres diacríticos; os valores padrão são:

```
array('Š'=>'S', 'š'=>'s', 'Ž'=>'Z', 'ž'=>'z', 'À'=>'A', 'Á'=>'A', 'Â'=>'A', 'Ã'=>'A', 'Ä'=>'A', 'Å'=>'A', 'Æ'=>'A', 'Ç'=>'C', 'È'=>'E', 'É'=>'E', 'Ê'=>'E', 'Ë'=>'E', 'Ì'=>'I', 'Í'=>'I', 'Î'=>'I', 'Ï'=>'I','Ñ'=>'N', 'Ò'=>'O', 'Ó'=>'O', 'Ô'=>'O', 'Õ'=>'O', 'Ö'=>'O', 'Ø'=>'O', 'Ù'=>'U', 'Ú'=>'U', 'Û'=>'U','Ü'=>'U', 'Ý'=>'Y', 'Þ'=>'B', 'ß'=>'Ss', 'à'=>'a', 'á'=>'a', 'â'=>'a', 'ã'=>'a', 'ä'=>'a', 'å'=>'a', 'æ'=>'a','ç'=>'c', 'è'=>'e', 'é'=>'e', 'ê'=>'e', 'ë'=>'e', 'ì'=>'i', 'í'=>'i', 'î'=>'i', 'ï'=>'i', 'ð'=>'o', 'ñ'=>'n', 'ò'=>'o','ó'=>'o', 'ô'=>'o', 'õ'=>'o', 'ö'=>'o', 'ø'=>'o', 'ù'=>'u', 'ú'=>'u', 'û'=>'u', 'ý'=>'y', 'þ'=>'b', 'ÿ'=>'y',' '=>'_' );
```

> Nota:
> O último elemento substitui um espaço para um sublinhado em nomes de arquivos

- $show_acces = Quando definido como y (es), o 'Acces'-Database com os operadores e suas senhas (sim ou não criptografado, dependendo de $ md5) será mostrado na lista de banco de dados disponível (se incluído lá).
- $Empweb = Quando definido como 1 (on), o sistema de empréstimos usará o módulo de empréstimos avançados e os mechanismos do Empweb, p.em 'mysite' ou verificação de disponibilidade.
- Uma nova seção pode ser opcionalmente adicionada ao config.php que lida com as variáveis necessárias para a função de tentificação LDAP, com dados de exemplo fornecidos:

```
$use_ldap=false;
$ldap_host = "ldap://zflexldap.com";
$ldap_dn = "cn=ro_admin,ou=sysadmins,dc=zflexsoftware,dc=com";
$ldap_search_context = "ou=guests,dc=zflexsoftware,dc=com";
$ldap_port = "389";
$ldap_pass = "zflexpass";
```
  

- Finalmente, uma seção opcional pode ser adicionada para ajudar a configuração do Empweb (se usado), mais especificamente para predefinir algumas variáveis e redefinir algumas portas:

```
ProxyPass /empweb/ http://127.0.0.1:8080/empweb/ // to direct calls to empweb to port 8080 instead of 9090
ProxyPassReverse / http://127.0.0.1:8080/ // reverse of previous

$empwebservicequerylocation  =  "http://localhost:8086/ewengine/services/Empweb- QueryService";
$empwebservicetranslocation = "http://localhost:8086/ewengine/services/EmpwebTransac- tionService";
$empwebserviceobjectsdb = "objetos";
$empwebserviceusersdb = "*";
```
  

> Nota:
> Variáveis obsoletas: $ institucion_name e $institucion_url não são mais usadas, mas substituídas por variáveis no abcd.def (consulte a próxima seção).

### Variáveis do sistema definidos em abcd.def

No diretório das bases de dados o arquivo 'abcd.def' define variáveis em todo o sistema. No Windows, por exemplo fica em C:\ABCD\www\bases, no Linux : /var/opt/ABCD/bases, mas depende do local da intalação. 

As principais variáveis atuais aqui estão :

- LEGEND1 = seguido pelo texto a ser exibido na segunda linha do rodapé central
   
> Nota: a primeira linha do rodapé é definida no código do script 'htdocs/central/common/footer.php.
> Neste script, também são organizadas as seguintes variáveis, para que o administrador 
> possa prever reorganizá-las, se assim o desejar, alterando o script (simples).

- LEGEND2 = seguido pelo texto a ser exibido no cabeçalho da Central (ao lado do logotipo ABCD)
- URL1 = seguido pelo texto a ser exibido como a terceira linha de rodapé como um link
- URL2 = seguido pelo texto a ser exibido como a quarta linha de rodapé como um link
- FRAME_1H = Um valor (normalmente 100) definindo o número de pixels para a altura do segmento superior (principalmente fundo azul escuro com logotipo ABCD) nas telas centrais de entrada de dados
- FRAME_2H = Um valor (normalmente menor que 100) definindo o número de pixels para a altura da barra de ferramentas (com a caixa de pesquisa) das telas centrais de entrada de dados.

> Observação: com as variáveis Frame_1H e Frame_2H O Administrador pode ajustar 
> a interface para diferentes telas de resolução, no entanto, apenas em um nível em todo o sistema.
> As telas de menor resolução exigirão valores mais baixos.

- MULTIPLE_DB_FORMATS =
- UNICODE =
- DIRTREE_EXT =
- LOGO = [nome do arquivo com imagem do logotipo]: referência ao arquivo de imagem a ser usado como logotipo na parte superior do
    
Tela central. O padrão logoabcd.jpg ![](/pt/images/logoabcd.jpg) pode ser substituído por qualquer imagem localizada aqui.Verifique se a imagem é pequena o suficiente (por exemplo, máx. 3 kb, enquanto o padrão é de apenas 1,2kb). Existem ferramentas para redimensionar imagens que estão disponíveis gratuitamente para o Windows e Linux.pode ser substituído por qualquer imagem localizada aqui.Verifique se a imagem é pequena o suficiente (por exemplo, máx. 3 kb, enquanto o padrão é de apenas 1,2kb).As ferramentas para redimensionar imagens estão disponíveis gratuitamente para o Windows e o Linux.

> Observe o logotipo do ABCD IAH e o site precisam ser definidos de maneira diferente.
> Por exemplo: Para o OPAC (IAH), a imagem é definida no arquivo
> htdocs/iah/iah.def.php com 
> a variável 'LOGO IMAGE='

  
### Variáveis de banco de dados definidos em dr_path.def

Neste arquivo dr_path.def (database-related paths definition), está localizada no diretório de base para cada banco de dados. Algumas variáveis podem ser definidas para redefinir as características do banco de dados. Esses parâmetros são todos opcionais! Atualmente, a lista de variáveis nesse nível é:

- ROOT = Define o caminho padrão para este banco de dados onde os arquivos anexados ao registro como imagens, PDFs... serão armazenadas.

 ```
ROOT=/var/opt/ABCD/bases/marc/dr/
```

- IMPORTPDF = Define com Y ou N se os documentos (PDFs) podem ser importados para esse banco de dados. Se "Y" o ícone para PDF será mostrado na barra de ferramentas central
- barcode = define com 'y' ou 'n' se os códigos de barras são usados ou não neste banco de dados; Este parâmetro define se o ícone de código de barras será mostrado na barra de ferramentas central
- tesaurus = Define o nome do banco de dados de tesauro a ser usado com este banco de dados, por exemplo:

```
tesaurus = Agrovoc
```

> Nota:
> A ortografia espanhola de 'Tesaurus' neste caso

- prefix_search_tesaurus = Define o prefixo com o qual os descritores no banco de dados são indexados, por exemplo: MA_
- COLLECTION = Define que o caminho onde as coleções de bibliotecas digitais serão armazenadas para este banco de dados. Esse diretório pode ser definido no próprio diretório da base de dado (por exemplo,/var/opt/abcd/bases/dubcore/collections/) ou como um diretório coletivo para todos os bancos de dados no sistema (por exemplo,/var/opt/abcd/bases/collections).
- UNICODE = Define com '1' ou '0' se o banco de dados usa o UTF8 ou o conteúdo codificado do Unicode. De fato, qualquer valor maior que 0 pode ser usado, p.'Y' simplesmente indicará 'sim, use unicode', '1', mas também '2' etc. também indicará 'sim, use unicode', mas, ao mesmo tempo, identificará o unicode subconjuntos de caracteres a serem usados, por exemplo: '1' inclui amárico, '2' inclui cingaleses, '3' inclui árabe etc. Esses códigos são relevantes para o OPAC, onde os alfabetos serão mostrados em ícones clicáveis.
    
### Definindo diferentes diretores de banco de dados: db_path.dat

O arquivo 'db_path.dat' na pasta-base permite definir vários diretórios (ou pastas) a serem usados como pasta-base, não apenas o atual (definido em CONFIG.PHP). As linhas neste arquivo opcional contêm o caminho, seguido por um separador de colunas `'|'` e uma descrição como mostrado no menu de seleção.

Por exemplo, para definir 2 pastas de banco de dados, uma com bases de dados operacionais e outra com bases de dados de teste, o arquivo db_path.dat seria (exemplo para Windows):
```
C:/ABCD/www/bases/|Acervo padrão
D:/databases/|Bases para testes
```
Essas duas opções aparecerão em uma lista na tela de login da ABCD Central e a variável $db_path será substituída pelo selecionado.


## Configuração de login do ABCD Central

O arquivo de configuração mais importante para o ABCD Central é o arquivo 'config.php' na pasta /www/htdocs/central. Discutimos alguns parâmetros gerais em outro tópico (na seção sobre instalação) enquanto eles lidam com os caminhos de instalação e a linguagem padrão a serem usados, mas no final alguns parâmetros são introduzidos, que fornecem uma solução de recuperação para o caso quando o administrador geral de dados de login foram perdidos (o que significa que o sistema não pode mais ser inserido por ninguém!).

Esses parâmetros são:

```
//USE THIS LOGIN AND PASSWORD IN CASE OF CORRUPTION OF THE OPERATORS DATABASE OR IF YOU DELETED, BY ERROR, THE SYSTEM ADMINISTRATOR

$adm_login=""; $adm_password="";
```  

```
//USE THIS PARAMETER TO ENABLE/DISABLE THE MD5 PASSWORD ENCRYPTION (0=OFF 1=ON)
$MD5=1;
```
Editando manualmente (por exemplo, com o bloco de notas ou outro editor de texto plano), os parâmetros $adm_login e $adm_password permitem criar dados de login temporários, o que permitirá criar logins reais novamente (usando as ferramentas de administração de banco de dados para o bancos de dados de usuários). É fortemente aconselhado remover imediatamente os dados de login deste arquivo config.php - por razões óbvias de segurança.

O parâmetro $md5 invocará a criptografia de senha (usando o algoritmo MD5) quando colocado em '1' ou não se for colocado em '0'.

## Administração dos perfis de usuário do ABCD.

Na opção principal do menu central 'Administração de usuários', pode -se inserir a opção 'Criar/editar perfis', além de criar/editar/excluir usuários do sistema.

A partir do menu principal central, opção "Administração de usuários", pode-se entrar na opção “Criar/Editar perfis” para criar/editar apagar usuários do sistema.
Alguns perfis vêm com a instalação do ABCD, como, por exemplo:
- Administrador do Sistema;
- Administrador de Bases de Dados;
- Operador de Bases de Dados;
- Operador LIS.

![](/pt/images/abcddoabcd1_html_a518da47462207ea.gif)
    

Como pode ser observado a partir desta tela, o administrador tem de informar os seguintes dados:
1. Nome do perfil: qualquer nome (curto) para o novo perfil a ser criado;
2. Descrição do perfil: qualquer informação que descreva o perfil;
3. Para cada base de dados listada: se é ou não concedido acesso e quais planilhas de entrada de dados podem ser utilizadas por este perfil. Se todas, a opção “Todas” pode ser selecionada simplesmente;
4. Permissões: para cada módulo (Catalogação – Circulação – Aquisição) a opção de menu (ou função) que esse perfil pode ter acesso deve ser ativada (na caixinha).
    
> Nota:
> A lista de perfis é mantida pelo Sistema Operacional no arquivo 'perfis.lst' nas 'bases/partes/perfis' e para 
> cada perfil as características (bancos de dados permitidos, módulos permitidos são mantidos em um arquivo 
> com o nome do perfil (sem extensão). Os privilégios não concedidos no perfil são assumidos como 'não' 
> permitidos. Os privilégios têm nomes breves, mas principalmente auto-explicativos, por exemplo, 
> "delrec" para apagar registros, "expimp" para exportar e importar registros, etc.


## Loging no sistema
    

Após terem sido criados os perfis (ou adotados perfis padrão) e atribuídos usuários de sistema, qualquer login de usuários de sistema pode ser usado para entrar no mesmo. Ao contrário de versões anteriores do ABCD, não é mais necessário, obviamente, selecionar um nível de autorização quando efetuar o login, já que este está agora junto com o login em si. Portanto, além de nome de login e senha apenas o idioma a ser utilizado deve ser selecionado (esta lista é obtida no arquivo lang.tab da pasta “bases” do ABCD (padrão: /ABCD/www/bases).

![](/pt/images/abcddoabcd1_html_7886a69038206032.png)
 
A partir de ABCD 1.5 e 2.0 na tela de login, também fornece um link para alterar a senha, que fornece uma caixa de diálogo para entrar no user_id, senha antiga e a nova senha duas vezes, conforme ilustrado aqui:
  
![](https://lh3.googleusercontent.com/MIVslA5az-6SPXmXrnrfTLPvaoDsEzVmcm1-XuOlyCMuWjg5IklAsVe0VbwcLlNYQbM_n0erw1D7bhrtK8wQbMniz48hq5Qe4prdZLQb579NPPj9ksmOIMp88tYSabqsspGHjgBQ=s0)  

Esta tela de login tem uma opção 'Abrir na nova janela' ![](https://lh6.googleusercontent.com/NOO262msBChAvhySwoftlShZTmKmEhtgbqSIbG1_I7oimt9TGi25YraXZnHQc5zFwGUS6H_Rpohq642tQL9XmBMU2gwAwW2ofubnOiKw_jKrAk4EOg8cpSlOIYFnVX3dWAU0RKnz=s0) como uma 'caixa de seleção' para a qual o valor padrão é definido no arquivo de configuração geral 'config.php' do ABCD-Central com o parâmetro-nome '$open_new_window' que pode ser definido como "Y" (ou seja, após o login o ABCD usará uma janela separada, o que evita a interferência com outras abas ou o uso errado do botão 'BACK' do navegador) ou "N" para simplesmente abrir a janela do ABCD na mesma área; o outro parâmetro ligado a este comportamento em 'config.php' é '$context_menu' que também pode ser definido como "Y" ou "N" para resp. permitir ou não o menu-janela invocado ao clicar com o botão direito na página - mais uma vez isto pode evitar o uso errado do botão 'BACK', já que esta volta deve ser feita preferencialmente através dos botões de interface ABCD, e não através dos botões do navegador que não tem controle sobre certos problemas de navegação ABCD necessários. 
  
  
Clicando na seta (“Ir/Entrar”)![](https://lh3.googleusercontent.com/IdcZJXwvLz7q9ffvgfqwMqsIq0so55S4mLn1WHzi2nL4c10G1f5WyDfmAkc5N0lIv7Zl67Vz2bp-XXpziJaCWrPbVzzia4zPW1unNpQumXi8lDZ_9VfAQ882FfvT8YyAkkBF00U7=s0) o usuário vai entrar no menu Central principal - ajustado às permissões do perfil. Todas as opções deste menu são discutidas nas próximas seções deste manual. Isto inclui a administração de usuários, ligando-os a um perfil, uma vez que a base de dados de usuários pode ser vista como apenas mais uma base de dados ABCD, para a qual ferramentas de administração geral de bases de dados do ABCD devem ser usadas.

## Usando autenticação LDAP
    
O uso de um servidor de autenticação LDAP é um novo recurso no ABCD 2.0.O acrônimo significa "protocolo de acesso ao diretório leve" e, na prática do ABCD, significa que você pode usar um servidor dedicado, principalmente em toda a instituição, que mantém registros de todos os usuários autorizados. Por exemplo, em uma universidade, um 'Escritório de Registro' poderia gerenciar uma lista de alunos tão centralmente coordenada, que o sistema da biblioteca consulta sempre que um usuário deseja fazer login. Isso significa que a própria biblioteca não é mais responsável pela manutenção atualizada desta lista. Por exemplo: quando um aluno seria "expulso" da universidade, a biblioteca não precisa mais saber disso imediatamente para evitar esse usuário - muitas vezes bastante frustrado!- Entrar no sistema da biblioteca para bagunçar.

Essa funcionalidade LDAP pode ser ativada para as seguintes partidas ABCD:
- Login central para operadores
- Site: Faça login para usuários finais no mysite
- Secs-Web: Faça login no módulo de controle de seriados.
   
As lógicas do uso do LDAP no ABCD são as seguintes:

- No config.php, o parâmetro está ligado ou desligado (na verdade: verdadeiro ou falso), portanto o uso do LDAP é completamente opcional;
-Sempre que um operador (bibliotecário) deseja fazer login no ABCD Central, ou um usuário final deseja fazer login no módulo 'Mysite', os dados de login inseridos são verificados pela primeira vez contra o servidor LDAP;Se esse responder 'claro', o login será concedido, se não o login, será rejeitado;
-Se o LDAP-Server não souber o login (que é diferente de 'rejeitar o login'), o login será posteriormente verificado com o a base de dados local local ('acces' para operadores, 'users' para usuários);
    
Um pré-requisito para o LDAP funcionar no ABCD é ter a biblioteca PHP extra instalada para LDAP: 

```
sudo apt-get install php7.0-ldap
```

[substituto 7.0 pela versão que estiver usando o php] e reiniciar seu apachecom um comando como no Linux:

```
sudo service apache2 restart
```

Outros arquivos recém-exigidos (em comparação com as versões pré-ABCD2.0) são:

- O script ldap.php a ser copiado para diretório htdocs/central/common
- um IsisScript dedicado 'loginldap.xis' a ser copiado no diretório htdocs/central/dataEntry/wxis
- Novas versões de inicio.php e inicio_mysite.php (já feitas por padrão no ABCD 2.0) com as seguintes alterações:
	- no início (por exemplo, após a linha require_once (“../config.php”);) Adicione uma nova linha com a seguinte instrução: 	require_once ("ldap.php");
	- No final do script, altere a parte 'Verificarusuario ();' da seguinte:

```
if (isset($arrHttp["login"])){
	 global $use_ldap; 
 if($use_ldap) VerificarUsuarioLDAP(); 
	 else 
 VerificarUsuario();  
```
  

- Três novas funções adicionadas: VerificarUsuarioLDAP(), LeerRegistroLDAP(), LoginNLDAP(), and Session($llave).
- um novo CSS - elemento definido no CSS htdocs/central/css/layout.css no final antes do fechamento '}':
```
 .dl- horizontal { 
	float: left; 
	width: 45px; 
	overflow: hidden; 
	clear: left; 
	text-align: left; 
	text-overflow: ellipsis; 
	white-space: nowrap; 
	border-radius:150px; 
	display: block; 
	margin: 0 auto; 
	margin-left: -50px;

```
- Para o módulo de empréstimos ABCD: uma nova versão do script htdocs/central/circulação/usuario_prestamos_preseub.php com
- Na seção de declarações "include" inicial, include ../common/ldap.php
- na linha 627 Código adicionado:

```
if($use_ldap){ 
	if(!Exist($arrHttp["usuario "])) { 
	ProduceOutput("<h4>".$ms- gstr["ldapExi"]."</h4>",""); 
die; 
	} 
}
```
- Para fins de referência, também observamos as alterações adicionais para o módulo SECS-Web se o LDAP for usado:
-Em htdocs \ secs-web \ index.php add: requim_once (bvs_dir. "/htdocs/central/config.php") após require_once ("./common/ini/config.ini.php");para verificar se deve ou não usar o LDAP no Secs-Web
- Nova versão da classe  htdocs\secs-web\common\class\session.class.php: uma nova função $misession->check- LoginLDAP() for implementado que será usado se o LDAP estiver ativo no config.php (Lista item anterior), em vez da função $misession->checkLogin().
- Em htdocs\secs-web\common\class\session.class.php a sessão do manager adicionou instruções no início para incluir o script LDAP e observar sua configuração de ON/OFF:

```
require_once(BVS_DIR. "/htdocs/central/common/ldap.php"); 
require_once(BVS_DIR. "/htdocs/central/config.php");
```

A configuração do LDAP deve ser definida da seguinte forma no config.php do diretório central:

- $use_ldap : Verdadeiro ou falso, conjuntos ou desative o uso de LDAP;
- $ldap_host : o nome ou servidor-IP do servidor LDAP;
- $ldap_dn : os dados do domínio LDAP em formato delimitado por vírgula;
- $ldap_search_context : dados adicionais usados pelo servidor LDAP para especificar o uso;
- $ldap_port : a porta usada pelo servidor LDAP;
- $ldap_pass : a senha necessária para acessar o servidor LDAP;

Na prática, você obterá todos esses dados padrão do gerente do LDAP-Server.
Um exemplo de configuração no script de config.php do Central ABCD para um servidor de teste de teste gratuito é fornecido abaixo:

```
$use_ldap=false;
$ldap_host = "ldap://zflexldap.com";
$ldap_dn = "cn=ro_admin,ou=sysadmins,dc=zflexsoftware,dc=com";
$ldap_search_context = "ou=guests,dc=zflexsoftware,dc=com";
$ldap_port = "389";
$ldap_pass = "zflexpass";  
```

Este exemplo de configuração é retirado de um servidor LDAP gratuito que também pode ser usado para testar, consulte o URL: [http://www.zflexldapadministrator.com] (http://www.zflexldapadministrator.com/).Os usuários de exemplo disponíveis são 'guest1' (Senha: guest1password), Guest2 (Senha: guest2password) e Guest3 (Senha: guest3password).

Observe que, para o seu próprio ABCD LDAP, você provavelmente trabalhará com o administrador em sua organização ou instituição para definir a configuração correta e fazer o teste.