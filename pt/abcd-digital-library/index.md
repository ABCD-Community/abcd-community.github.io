---
title: Características da biblioteca digital em ABCD
description: In this section we discuss some features and techniques to create and use digital libraries as 'full-text' databases in ABCD.
tags: 
 - biblioteca digital
 - coleções
lang: pt
lang-ref: abcd-digital-library
---


# Recursos da biblioteca digital no ABCD

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---


Nesta seção, discutimos alguns recursos e técnicas para criar e usar bibliotecas digitais como bancos de dados de 'texto completo' no ABCD.  


## O conceito de Biblioteca Digital no ABCD
   
No ABCD, simplificamos o significado de uma 'biblioteca digital' como um banco de dados de 'texto completo', em que os registros contêm, além de 'metadados' - o texto completo de um documento ou têm um link para o documento de texto completo enquanto as palavras nesse texto completo podem ser pesquisadas.

Como o ABCD é baseado na tecnologia CDS/ISIS, portanto, foca na recuperação de texto, as imagens e outros elementos não-textuais de um documento não serão processados, mas permanecerão disponíveis, é claro, nos documentos vinculados originais.

Por exemplo, as ilustrações em um PDF não farão parte do registro ABCD, mas clicando nos links dos documentos o PDF, incluindo as figuras, será aberto no navegador.

Uma limitação importante é a ausência de 'classificação de relevância': o mecanismo de indexação do ISIS pode lidar com palavras (indexação de texto completo), mas não tem provisão para classificação de relevância, por exemplo, armazenando um 'peso' denotando a relevância de um documento com base no frequência (estatística) da palavra que ocorre no documento. No ABCD 2.0 existe uma palavra ou não, e isso certamente tem consequências para a eficiência da busca. Para a 'indexação de texto completo classificado', temos que nos referir à versão de nova geração do ABCD: versão 3.0, que é baseada no J-ISIS e, portanto, no mecanismo Lucene que possui provisão para classificação.

  
Outra limitação é o tamanho dos documentos: se for usada a versão especial do CISIS 'BigISIS', os registros podem conter até 1 Mb de texto. Em nossos testes, a maioria dos documentos (PDFs) cabem dentro desse limite, exceto para os documentos textuais realmente longos. A maioria dos arquivos PDF maiores são grandes porque contêm muitas imagens ou elementos binários (BLOBs), mas o texto extraído caberá principalmente no limite de 1 MB. Colocar o texto do documento dentro do registro, portanto, deve ser usado apenas - afinal, é uma opção - se a maior parte da coleção consistir em documentos textuais não muito longos. O script gerar os ABCD-registros de um banco de dados biblioteca digital irá avisar para documentos não cabendo (ou superior do conjunto PHP-limite para upload_max_filesize' parâmetro -. Que por sinal tem muito baixa correlação com o texto-tamanho real dos documentos.

Entretanto , apesar das limitações, usar um banco de dados para uma biblioteca digital no ABCD também tem vantagens:

1. A biblioteca digital pode ser gerenciada como qualquer outro banco de dados, por exemplo, pesquisar / editar no ABCD Central, incluindo adicionar / editar campos de metadados
    
2. O banco de dados ou biblioteca digital pode ser apresentado no site ABCD e pesquisado junto como qualquer outro banco de dados (por exemplo, catálogo, coleção de periódicos ...) na opção MetaSearch do ABCD
    
3. Se o documento-texto for - como recurso opcional - armazenado dentro do registro, ele também pode ser editado junto com quaisquer outros campos (metadados).
    
4. O número de documentos na coleção dificilmente afeta a velocidade das operações, por exemplo, o CISIS pode lidar com quase 17 milhões de documentos sem qualquer penalidade de velocidade na pesquisa.
    
5. Se os diretórios dos arquivos originais forem estruturados em subdiretórios, o ABCD irá gerar e indexar esses nomes de diretório automaticamente como metadados no campo 'seções' dos registros. Isso significa que a pesquisa pode ser baseada nesses nomes de diretório ou pasta.


Um recurso especial usado pelo ABCD - assim como muitos outros softwares de biblioteca digital dedicados semelhantes - é usar o recurso de extração de 'metadados' da biblioteca TIKA da Apache Software Foundation, que é um extrator de texto de uso geral. Isso significa que, desde (não é óbvio - a maioria dos autores não está dando atenção a esse recurso de seu processador de texto) que nas propriedades do documento os campos relacionados foram inseridos, os metadados disponíveis, como título e autor, serão inseridos automaticamente nos campos de o registro do banco de dados (veja abaixo um registro de amostra com esses metadados extraídos automaticamente). Se definidos na Tabela de Seleção de Campos, esses campos também poderão ser pesquisados na Central e no OPAC (ou Site Metasearch).


Uma instância especial de uma biblioteca digital no ABCD seria um 'repositório DSpace' criado a partir de uma coleção existente do DSpace. Para isso, consulte a seção dedicada neste manual.

## Criação de uma coleção em modo

A criação em lote de uma coleção refere-se à possibilidade de adicionar um conjunto de documentos, pré-organizados em uma ou mais (sub-)pastas, em uma base de dados ABCD existente. Sugerimos utilizar a base de dados demográfica "Dublin Core", uma vez que ela já tem os campos básicos do Dublin Core disponíveis e o roteiro de criação apresenta estes campos já como padrão (mas eles ainda podem ser alterados).

Um caso de uso típico seria a criação inicial de uma coleção de teses, onde as teses como documentos PDF são armazenadas em uma pasta, estruturada, por exemplo, pelo corpo docente, departamento e ano de apresentação. Estes nomes de pastas serão automaticamente introduzidos como meta-dados ('seções') no banco de dados - registros e podem ser usados como critérios de pesquisa.

Outro caso de uso é adicionar uma série de documentos recém-chegados (por exemplo, artigos de periódicos) a uma coleção existente. Para adições de documentos individuais, seja em um registro novo ou existente da coleção, um script diferente será usado, veja a próxima seção 1.3.

### Preparação de sua coleção

Os elementos a seguir são os pré-requisitos para permitir a criação de uma coleção em modo de lote:
- Um banco de dados com FDT, FST e PFT pré-definidos, no qual os documentos serão adicionados como registros
- Um novo parâmetro 'COLLECTION=' no arquivo dr_path.def do banco de dados relacionado: este parâmetro indica o caminho completo para a subpasta de coleção na qual os arquivos de coleção serão armazenados. Esta subpasta pode estar em qualquer lugar em seu sistema, mas normalmente será ou um diretório 'coleção' no diretório 'bases' de seu sistema ABCD (por exemplo, ABCD\bases\ coleção em Windows) ou um diretório-subdiretório de coleção para um banco de dados específico (por exemplo, /var/opt/ABCD/bases/dubcore/collection em Linux). Esta pasta precisará de acesso/controle completo para o script que cria os registros de documentos.
- Opcionalmente: um campo no qual o texto do documento será armazenado   
- Um PFT especial (a ser editado manualmente ou copiado da base de dados existente na biblioteca digital PFT), no qual duas instruções especiais são dadas:
    
1. instrução para exibir o texto-conteúdo do documento em um 'Iframe' da janela :

```
if p(v96) then 
'<tr>
<td width=20% valign=top><font face=arial size=2><b>Text source</b>'
'</td>
<td valign=top>
<font face=arial size=2>
<iframe height=200 width=800 scrolling=yes src=http://localhost:9090/', replace(v96*1,'ABCD/www/bases/','collec- tion/') ,'>
</iframe></td></tr>' 
fi
```
  

> Nota:
> Este exemplo funciona para 'localhost' com a porta 9090, pois a
> 'fonte' do arquivo é referenciada por 'http: // localhost: 9090', e a
> string 'ABCD/www/bases/' no caminho do arquivo e nome na v96 serão
> substituídos por 'coleção', então isso supõe que o Apache tem um 'apelido' no
> qual 'coleção' se refere ao diretório do banco de dados real. O nome do
banco de dados (por exemplo, 'dubcore') deverá estar presente, bem como o
nome da subpasta> 'ABCDSourceRepo'.


2. Instruções para exibir o link para o arquivo de documento original no servidor :
   
```
if p(v98) then 
'<tr><td width=20% valign=top>
<font face=arial size=2><b>URL</b></td>
<td valign=top> 
<div id=divurld',f(mfn,1,0),' name=di- vurld',f(mfn,1,0),'>
<a href=javascript:DisplayURL(',f(mfn,1,0),')>DISPLAY</a></div>
<div id=divurl',f(mfn,1,0),' name=divurl',f(mfn,1,0),' style=display:none>
<font face=arial size=2>
<a href="',v98'" target=new>'v98+|<br>|,'</A>
</div>
</td>' 
fi/
```
  

> Nota:
> Este exemplo é um pouco mais avançado, pois inclui o
> mecanismo para ocultar o URL com apenas um link 'DISPLAY', que aciona uma
> função Javascript 'DisplayURL' que convida o usuário a fazer login
> como um usuário da biblioteca e somente se estiver corretamente logado irá realmente
> exibir o URL real. Esse URL é indicado pelo valor
de v98 neste exemplo. Como alternativa ao 'login', o ABCD também pode usar uma verificação no número de IP dos usuários finais (ou intervalo) e mostrar a URL apenas para usuários dentro do intervalo de IP aceito:


O código Javascript de login, a ser adicionado no topo do PFT, está listado aqui:

```
<script  language=javascript>  
function  DisplayURL(id)  {  
var  login- to=document.getElementById("into").value;  
if  (loginto=="no")  {  
var posicion_x;  
var  posicion_y;  
posicion_x=(screen.width/2)-(315);  
posicion_y=(screen.height/2)-(235); 
sel = window.open("/site/login.php?id="+id, "ABCD Log In Windows", 
"width=630,
height=470,
menubar=0,
toolbar=0,
directories=0,
scrollbars=no,
resizable=no,left="+posicion_x+",top="+posi- cion_y+"");  
}  else  {  
document.getElementById("divurld"+id).style.dis- play="none";
document.getElementById("divurl"+id).style.display="block"; 
} 
}
</script>
```

Como alternativa, a faixa IP do usuário final pode ser verificada para (des)permitir a exibição da URL, com o seguinte código adicionado ao PFT:


```
proc('<9000>',getenv('REMOTE_ADDR'),'</9000>'),
s1:=(left(v9000,instr(v9000,'.')-1)),
s2:=(mid(v9000,instr(v9000,'.')+1,size(v9000)))/, 
s2:=(left(s2,instr(s2,'.')-1)),
if p(v98) then '<tr><td width=20% valign=top>
<font face=arial size=2><b>URL</b></td>
<td valign=top>', if val(s1)=127 then if
val(s2)=0 then 
'<a href="http://127.0.0.1:9090//docs/dubcore/collec-
tion/',v98, '" target="new">'v98,'</a></td>' 
else 'IP not allowed' fi else
'IP not allowed' fi fi,
```

>Nota:
>Esta instrução tem duas partes separadas: no início do
>PFT um' proc 'é usado para armazenar o número do IP em um campo virtual v9000
>e então suas partes nas variáveis ​​locais 's1' e 's2' respectivamente.
>Então, no local do PFT onde você deseja exibir (ou não)
>o URL, e se v98 (com as informações do URL) estiver presente apenas, os valores de
>s1 e s2 são verificados para ver se eles estão contidos dentro do permitido intervalo,
>neste caso 'localhost' (127.0.xx).


Em princípio, o gerente do sistema (ou bibliotecário) precisa decidir qual método restringir o acesso aos documentos originais a serem usados: com base no login ou com base no intervalo de IP. No entanto, usando as instruções normais de PFT (por exemplo, `IF ... THEN ... FI`), pode-se combiná-los ou simplesmente usar ambos, por exemplo, rotulados como 'Exibir após o login' e 'Exibir no campus'.

- Um FST especial, denominado 'fulltext.fst' no diretório 'data' do banco de dados, que contém uma instrução de indexação (linha) que usa o texto do documento como entrada para o mecanismo de indexação com a instrução 'cat', por exemplo, no caso do banco de dados Dublin Core existente ('dubcore'):

   
        99 8 '/TW_/',if p(v96) then proc('Gload/99/nonl='v96) fi,v99

Esta instrução cria um índice identificado por '99', usando o método de indexação de palavras prefixadas (8) do ISIS, criando primeiro o prefixo 'TW_' (palavras-texto, normalmente o índice para a pesquisa simples de ABCD OPAC), então se o campo 96 estiver presente para indicar o caminho / nome do arquivo-texto, para carregar esse arquivo em v99 (sem caracteres de nova linha) e use esse texto como entrada para o mecanismo de indexação. Além desta instrução especial, todas as outras instruções de indexação orientadas a metadados, por exemplo, para incluir título / autor, etc., podem ser usadas neste FST especial.

- Um FST 'normal', principalmente orientado a metadados, a ser usado sempre que os campos de metadados do registro forem editados e salvos.      
- Um subdiretório de 'coleção' de nome fixo do diretório de banco de dados relacionado
- Um subdiretório de nome fixo do diretório de COLEÇÃO 'ABCDImportRepo' no qual os documentos a serem processados estão localizados.


***É de extrema importância que as subpastas da coleção - e ABCDImportRepo- tenham acesso total (ou no 'Controle Total' do Windows) aos usuários, uma vez que os arquivos serão movidos de lá e novos arquivos serão gravados na coleção- pasta. *** Certifique-se, usando a interface do seu sistema operacional, que esta condição seja cumprida. Por exemplo, no Windows, clique com o botão direito do mouse na pasta e verifique se a guia 'segurança' indica 'controle total' para os usuários. No Linux, certifique-se de que o diretório tenha atributos '777' (por exemplo, com o comando 'chmod -R 777 collection'). Observe também que também os diretórios ou pastas de nível superior precisam ter acesso total, já que o sistema operacional analisará todos os níveis, desde a 'raiz' até o diretório de coleção relacionado, e parará de fazer isso se nenhum acesso completo for permitido.

Uma estrutura típica será semelhante à seguinte, onde os documentos estão relacionados a ABCD, ISIS, Greenstone (GSDO) ou J-ISIS, portanto, dentro do subdiretório ABCDImportRepo, os documentos originais foram armazenados em subpastas com nomes correspondentes (ABCD, ISIS, GSDL, J-ISIS), exceto para um documento especial 'ISISorigins.pdf' que foi deixado de fora desta estrutura de seções e, portanto, acabará na 'raiz' da coleção.

Figura 2.3. Estrutura COLEÇÃO
![](https://lh4.googleusercontent.com/PQFZshDsKeQgHWqg3KQJQtHAxt6rghclE-Oocr7XFxLeIrvGesQomgc9GSXGspQZUCQM_1-I1uXtagHYuPcYmnhLQWIlJL5QwTV1O1fTQ-wkMPpKbQM5xkC7k238VEO2E0cpSKE=s0)  

O subdiretório ABCDSourceRepo conterá todos-arquivos HTML com textos extraídos, todos os docu- mentos originais (por exemplo, PDFs, Documentos do Word ...) serão armazenados nas subpastas correspondentes conforme estavam presentes no diretório ABCDImportRepo, mas com alguma numeração aleatória adicionada ao nome do arquivo. Isso é para garantir que os documentos com os mesmos nomes de documentos ainda sejam identificados individualmente. O registro ABCD resultante terá tanto a referência ao arquivo HTML (em ABCDSourceRepo) quanto o documento original em seus campos dedicados, no banco de dados DUBCORE demo: resp. v96 e v99. Neste exemplo, o'isisorigins.pdf 'não foi movido para uma subpasta

- apenas para fins de demonstração - porque dentro da pasta ABCDImportRepo ele também residia no nível' raiz '.
 

### Usando o script de criação


Depois de garantir que todas as etapas de preparação sejam tratadas corretamente, o uso do script para criar registros de biblioteca digital é bastante simples.

O script para importação em lote de documentos é o primeiro no novo submenu 'UTILITÁRIOS EXTRA' do menu Utilitários Centrais:


Figura 2.4. Menu de utilitários
![](https://lh4.googleusercontent.com/HbIp-oJ7MU0pbCdUwPAylXr_k-YHkSxBk56VH6yAX7SA3XVmhm_I-va0BIT6xWaJOBUx-q75COsJbxiIv-svzrn09dwDStX5rr2vsup0MFy0VQ1XGvvsqP5T2wxyXVVrmiJg3jE=s0)  

Após a opção 'Documentos lote de importação' é selecionado, a tela principal é mostrado, na caso da versão Linux após uma contagem regressiva para carregar o servidor Tika na memória (já que a versão do servidor, não usada no Windows) leva mais tempo para carregar): 

Figura 2.5. Principais documentos em lote tela
![](https://lh3.googleusercontent.com/3vgNTxShUJRVhdHVohjIycFHPKXHydrJ5F7TQ7LoNTkkMsh1HhveSSZKsxVTjWxrq5wNKM96ODpfNtllM0pTAVylxRptKB7qm3Yd3_-H2ICIMtpUs-tfBmXPVrptJ2jQpXKcppc=s0)  

Nesta tela o bibliotecário tem a 'match' os metadados extraídos automaticamente (Dublin Core baseado em) para os campos da sua base de dados, juntamente com alguns campos especiais: o campo que contém as 'secções' (= subpastas da colecção), a fonte do documento, o identificador do documento e opcionalmente o campo que contém o texto completo do documento extraído pelo TIKA. Observe que isso não é usado por padrão, pois exigirá a versão do BIGISIS CISIS para usar registros maiores.

Clicar no botão 'Atualizar' iniciará o script iterativo que processa todos os arquivos no subdiretório ABCDImportRepo e exibe o progresso na tela até que seja concluído. A ilustração abaixo mostra a última parte dessa lista quando o script foi concluído.
  
Figura 2.6. Resultados da lista após a execução de script de criação de coleção
![](https://lh6.googleusercontent.com/oeMq4ObdTqwxsm6_KI4KGnjJq3YumujJAkEzY23sfUpIgHqS-v3KM_tSXOWFv4Dkl8DkdY4KfiWzTzQc_aXnM7E2wD5X6-5jp1RBPx6kBXBKYmfpofvnNwrRV9DZnPEYTdOOV9I=s0)  

Agora entrando (ainda dentro Central) no banco de dados e navegar para o último registro mostrará um registro típico da seguinte forma:


Figura 2.7. Mostrar registro DigLib em Central 
![](https://lh5.googleusercontent.com/3SZi9Ww6HrOvKFmXRCUEEjGb9I6EwyVFCU4df5ZMdHtwZOa7969XSck-BzqRyHU1gbhManGNLNPBYcvvrFA7COfCYvvl9psrHBrokCq0RQMs2-P0S8gH_yiSfeWiJqaR8k5TTQw=s0)  

As necessidades de banco de dados para ser totalmente indexados ( 'geração do arquivo invertido completo' em ISIS-vocabulário) usando os homens anteriores - referenciado FST especial 'fulltext.fst', mas também usando o parâmetro especial '/ m' a fim de evitar o armazenamento de todas as informações detalhadas de posição nas postagens de índice:

Figura 2.8. Indexação de texto completo da coleção da Biblioteca Digital
  
![](https://lh4.googleusercontent.com/t-EXYP1O9uwEvVQUCvfbZe3YgnksOCrjkgR_NpXSb8dykJ2X4n1iK_QwNArgPZw1GEivtflK177dj6pjEyKPJ5cmlKe3SIVLe7rbdE-c7_n-67NXQqUD1Y0cm7ycPDhc6aU8FdQ=s0)  
  

Um exemplo de - parte de - um índice de texto completo é mostrado na próxima ilustração:
 

Figura 2.9. Índice de texto completo listando
![](https://lh5.googleusercontent.com/Oi-1e6Lpk7x0CXxOw1vDATQAR0RT4uI8nPV8oeYNceH0mfzlZY8fqSRuz1rlMx8ldIUN03FzL3w_skJn3cQoFVfunDBhU-JS-_KJxdlOUBUeA2MSyRX7cUGXNZwcaRs_9127OR8=s0)  

Selecionando uma ou mais palavras, como também é feito em qualquer outra ação de pesquisa Central em qualquer outro banco de dados, resultados na exibição do (s) registro (s) com destaque para os termos de pesquisa:
  

Figura 2.10. Pesquisa Biblioteca Digital de exibição recorde
![](https://lh3.googleusercontent.com/QmOzgg-3Am4rhfEsGWk5OWWDnuxpCQ5jox4XY27IJUFsi6Ysk4-zHePLIspTecuz25z6-Ep816yO2i1QdRu8aXQ0kZLWnObFthLC2PVkXDO5TuX4FfzLIwCqDJg4IxpC0ksj-GQ=s0)  

O texto-fonte é mostrado apenas como uma primeira verificação rápida para avaliar a relevância do documento; isso é de uso limitado, mas, por exemplo, no OPAC pode ajudar os usuários finais a decidir se clicam ou não no link da URL para visualizar o documento original em formato completo.  


Para ilustrar o recurso de 'seções' mencionado anteriormente, onde o ABCD usa as subpastas pré-configuradas do diretório ABCDImportRepo para atribuir automaticamente 'seções' à coleção, aqui está a lista do índice de 'seções' no ABCD Central:


Figura 2.11. Secções Biblioteca Digital ABCD listagem 
![](https://lh4.googleusercontent.com/BtVS6AiGpMAqOU69jbw5W_mtlDFKnSylzcA1Hx0MXX52p7rHY-1JhrJX47OZ0QAr6O_j5LyPyTl6i-fd8VAvTPvEG7DIA5N8SOyG6aOTjJESa6wx-JH5vlxepeed4GsuEFQD9P0=s0)  

Isso reflete a estrutura da pasta agora ajustado da  subpastas de ABCDImportRepo foram reconstruídos para a coleção -root pasta com os arquivos originais movidos para lá, e a pasta ABCDImportRepo é esvaziada, deixando apenas os arquivos não processados lá (por exemplo, muito grandes):

  

Figura 2.12. Biblioteca Digital ABCD nova estrutura de diretório coleção
![](https://lh5.googleusercontent.com/XJchXKfLypvlu2RfnnGQpoZLzQsLO_H8CXUhCeclnmsjGzZE1yv_DIHXjH2hPqaNy4qLa0p0bj6J4qztaJsedEOj2f1c98T9yWvNlkz8Crf89l-RGYaHUlCPwBvk-51E98SXdN8=s0)  

Como se pode  além de pasta 'ABCDImportRepo' (agora esvaziado) há uma pasta 'ABCDSourceRepo' contendo todos os arquivos html com textos extraídos, e há pastas de 'seção' para ABCD, GSDL, ISIS, JISIS e 'Vários', enquanto dois PDFs não faziam parte das seções e, portanto, permanecem na 'raiz' -nível da coleção sem informações de 'seção'.
  

O banco de dados da biblioteca digital pode ser incluído no ABCD Site MetaSearch (como é o caso na instalação de demonstração) e pesquisado pelos usuários finais como qualquer outro banco de dados. A exibição do resultado é muito semelhante à acima na Central:

  

Figura 2.13. Biblioteca Digital resultado da pesquisa em iAH-OPAC
![](https://lh6.googleusercontent.com/Y1XhawZUTMcJzw_p_RRcBxW1cGwa4-uA3wUrPvudm6M5iHUSzLtzfNzFx2IG-tnz1yJtSrPpHvsZ0kJwlGNMfu2YdyTtnNhO8ToMiLR9s9UaLpI71XA8ilmgVr9zjftZGm59xcU=s0)

Esta imagem mostra também no lado direito do documento PDF original, depois de ter clicado no URL -link como um hiperlink.

> Nota:
> O método de proteção baseado em 'login' usando o javascript
> 'Display_URL' não funciona no Central, mas funciona - conforme pretendido -
> no iAH OPAC.
