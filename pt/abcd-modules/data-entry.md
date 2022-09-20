---
title: Módulo central - entrada de dados (catalogação)
description: Nesta seção, discutimos brevemente as principais técnicas de uma das funções mais "centrais" do ABCD, criar registros em um banco de dados (em aplicações bibliográficas, em sua maioria referidas como "catalogação").
lang: pt
lang-ref: abcd-modules/data-entry
---

# Central module : data-entry (cataloging)

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---
 
Nesta seção, discutimos brevemente as principais técnicas de uma das funções mais “centrais" do ABCD: a criação de registros em uma base de dados (em geral referido como "catalogação" em aplicações bibliográficas). 

Estas operações, frequentemente usadas por catalogadores, são agrupadas em uma “barra de ferramentas” no topo da tela – desta forma,o ABCD tenta imitar o comportamento de um “software desktop” local:![](https://lh5.googleusercontent.com/enveLRJHTkYBpkH9l5-M2uukoUjLbxv5ZVxrgmXGlueoXpyAYMxmiS4Mxm6FwRBr3ZhurqrxtQjP9LzcF7n8zC8BPiVthiVAP8wtfUHBLnbkQ1hSz3dXakOS6c8UxGlRXa53nrqD=s0)  

  
A barra de ferramentas mostrada acima está relacionada com a base de dados. Sempre que um registro é mostrado, uma segunda barra de ferramentas menor será apresentada e que contém os botões relacionados ao registro atual:![](https://lh3.googleusercontent.com/mwCcNvQpHOJjtbkMpbdtHYY_sggNPv4alQ-XqDrLZl9D8AAtgoWr0xom1WxpxND_WIgKq0lSuuHK_c5s6HJDJ3COnDZYVQmRuZSdKlSdeaKbnE-jZhiMybW2MpgEhaxoyNk9ucOW=s0)

Vamos discutir todas as funções das barras de ferramentas brevemente aqui, da esquerda para a direita.

## Navegação pelos registros
    
Existem duas maneiras para localizar registros:

-   digitando o número do registro (MFN) na caixa dedicada
![](https://lh6.googleusercontent.com/emHTVDt5x4-uJO7zO-ZostzW1A9NIrHv6CmHIZrP_OwPvHjHlCC6leDtnkvnB2y5MP1Lt3OCenm9QIvSk3gODJWBuDA_DN7Wiqf49GuqrYi_NN3QQ_Jfv6FY4heuF-E9rlsU3FVn=s0)
   
Aqui você simplesmente tem que digitar um número de 1 até o maior MFN disponível na base de dados.

  

-   clicando em um dos "botões de navegação" para ir para o primeiro, anterior, seguinte, ou último registro.

![](https://lh6.googleusercontent.com/Bq7AHS3i_J-z7nvVjxBi6krrRMHK098i4WUd2NoHII05Yiq4xp8nzjpwNhapLowWY2eejYfuO_-Cq7Ws8P9UmGH-2SXcNjeJhojRaCgunkWG4aTTkX4QG5L-zNU-EHpfoY5ob1aa=s0)
   
Essa navegação será feita no banco de dados completo ou no conjunto de resultados de pesquisa, de acordo com a opção selecionada no menu adjacente.
  

## Pesquisando registros
    

Tal como acontece com a navegação, o ABCD oferece duas abordagens principais para identificar um registro específico para catalogadores: por pesquisa ou selecionando registros através de uma listagem alfabética (A a Z).

 ![](https://lh4.googleusercontent.com/6vDCBNQDd_4KLuaDHC7Y9kVPO41KuM66_SXtkgapa2E0DQCR753dXmVwFb15l7jnRMdxFfuTTu_1sttx1Q9UYYx-tdmweEcKqsmU7XKRH3fLwbdQektmwMM-6RivGzi9P3kxzMnr=s0)

realizando uma pesquisa com uma poderosa função de busca embutida no módulo de administração de bases de dados, resultando na apresentação de um verdadeiro formulário de pesquisa (tal como definido na função "Definir formulário de pesquisa" do menu principal de administração):
  
![](https://lh4.googleusercontent.com/kgo0wI_oIKFxaFkIXCqdxObFTdd6t-emz7mbx-p9nmZ_NPvCX8bcjzUJfNpp67USFjSBZVocYnNQFo9EN-1vQx0qN24GaRJRgWADaC8gwCLk14Cj_wZOPVU01WBcmDXlNg86sLFC=s0)

A pesquisa por este formulário é feita conforme explicado na "interface de pesquisa avançada" da seção do OPAC, que utiliza o mesmo formulário.

- ferramenta de seleção A a Z
    

![](https://lh3.googleusercontent.com/FoQsNh_sPLJF2DOEq4CHIj3UgWCL-yW3Yt37-ERX7fYjyiirdDlLmiHCGxsotbFi7F4I_sJCdi3Ut1AcIf8iHjC8wUzgLJXrOlcf0XuKbLgmr9MmNIgtfebXYYOh21h8GKzATTd9=s0)

Ao clicar neste botão, irá mostrar outra pequena janela, em que todos os registros da base de dados estão listados de acordo com o campo identificado como o "campo identificador" na tabela de definição da base de dados (coluna 3 'I'), em geral o campo de título em bases de dados bibliográficas, por exemplo.

Nesta lista, cada seção alfabética pode ser clicada, e depois clicando na linha pertinente, o registro referenciado por esta linha será automaticamente apresentado na janela principal, pronto para edição. 

Esta ferramenta agradável estende, como poderíamos colocar, o ABCD “all the way up” até Z!

![](https://lh4.googleusercontent.com/Gah_hVp-dQNlBTyE7NQTPSmjBmjNZTx-vDV3o9o_DYZecgGxbrhQkrk0SwJRppdkSdXhk4h_k35_IIGuC3KNYn0ilT3iuQ4W6qQ3EfYEvhHK2cVoLfpwIG91MqN4HjvslNhxQ3GU=s0)

  
## Usando os formulários de edição
    
[!!] Ao clicar no primeiro ícone da barra de ferramentas do registro, o registro será apresentado em um formulário (planilha) de edição. A mesma planilha - mas vazia - será utilizada para a criação ou cópia de um registro novo (da barra de ferramentas da base de dados).

> Nota
> No caso de bases de dados MARC21, sempre que editar um novo registro, 
> primeiro deve ser feita uma seleção a partir de uma lista de tipos de registro possíveis:


![](https://lh6.googleusercontent.com/Rq4b3rvw_kAR24UPoYfKVwIkE4Pxvx6iMPTEsfU7nvaxcKJ7OGNGLZhrE-NT_ZXk88qEVFn0OpjUjYRCj0dEq0Q9q4amNYaAgLsh3Yr-qvVNfT1wzIAP-J3wxaKgsFHm_PgyiHBZ=s0)

  
Selecionando um deles (ou seja, clicando no seu link), invocará subsequentemente a planilha correta com alguns valores pré-definidos (por exemplo, para o campos MARC de tamanho fixo).

O formulário de edição MARC21, com sua estrutura longa e complicada, será apresentado de uma maneira especial: seções do formulário podem ser "retraídos" ou "expandidos", clicando no link + de acordo com a seção. Os detalhes da seção serão mostrados ou ocultados.
  
![](https://lh4.googleusercontent.com/2CRPS_C0nr9d487Ebh2kipuBszK2oOvooi2fME6M9GEzBCZTidNCwWQRqfVCL0Jl0HBgKBit-LhUa9JBNiUfe-DNGdQGliY4A_lhK2RcZKdyBNXeGmRSC-tcpAXsBd3BQ1axlWgL=s0)

**Observação geral**: dependendo de como a Tabela de Definição de Campos do ABCD foi criada, que também define as características da planilha, ao contrário do WinISIS, a planilha pode aparecer como dividida em seções com links (botões) de acesso direto e botões para voltar ao início da planilha para uma navegação mais rápida dentro da mesma. 

Campos para edição podem ter um dos formatos mostrados a seguir, cada um com sua própria maneira de lidar com eles, resumidamente explicado da seguinte forma:

- um campo editável simples, como no caso  do campo ISBN abaixo, onde se pode entrar apenas um valor (por exemplo “^a8570251270”):

![](https://lh6.googleusercontent.com/qnKWTeD2qEEyTkIq6NdoXrQsk3NoIrhY3f156kfGI6JCWV131aRCIg09vBrgaWG1pgzoNHNgZkkSycdtnKkkQJQrKZNEvKnHTWQXAq5TiuvVSUUAgi9ObAd6X-hKWXiRwUtiXq-6=s0)
    

- um campo com um menu a partir do qual uma única opção deve ser selecionada, como, por exemplo "Monografia", como nível bibliográfico:

![](https://lh4.googleusercontent.com/Tir3_VlQN45zaM3W9GBYD_mIZKA9dzdFycUqDnT1jtMJqlta8Ta9WWl9K6b4dCdDHmGiOcdl0tiIHFJlAfntu-oeNlD1QZkd_Adtayns8qRgOlDqnWVVViYk-Y8hkiaDIAAlyzr_=s0)  
   
![](https://lh4.googleusercontent.com/fXYfQSsVCHkeFDjz8etxLm9dO61cn_7koiobm7Dd-8FEVa5I9wIt4oT4XGzgAusKNzEnxqy8zynVJpSA2dvyfo2DNd48_23AjB7KBua-yCYiWLURSLGt4eGkCFxD48wpQLCCmc7a=s0)

um campo subestruturado, com um botão  para dar acesso a uma janela separada na qual todas as subestruturas (por exemplo, subcampos ou partes do campo de dados fixos do MARC) podem ser entrados individualmente:

![](https://lh3.googleusercontent.com/CTpA_WhA4hH4DctcDwf5g9KULP7-ZLRdzrrj4csK0Jf67ijCMTM-nzZ6yVi6rNaVZ44DoydATXSibbgWMHjZbNUYtT9m4CJUhWX0gtSiBHbZlb5boUDThrIE_YvbzWVqj7D2yxgw=s0)

Clicando no ícone![](https://lh4.googleusercontent.com/fXYfQSsVCHkeFDjz8etxLm9dO61cn_7koiobm7Dd-8FEVa5I9wIt4oT4XGzgAusKNzEnxqy8zynVJpSA2dvyfo2DNd48_23AjB7KBua-yCYiWLURSLGt4eGkCFxD48wpQLCCmc7a=s0)
irá exibir uma nova janela na qual todas as subestruturas são apresentadas individualmente. Por exemplo, no campo MARC de Edição (250), existem subcampos para a “informação de edição própria” e um para “informação adicional":

  
![](https://lh4.googleusercontent.com/oXgEPHOkg8F8XMvF9V3gCSlrpcvdJioQgqJ75XEPXADo4olqMVYE2eYUnPYVn-eszmofCMZg5vJFv174DJ6mX0XMNUn6jUAz03iDGwECf17TRVK0_luuMrJmPkB6fqT1MCzip9Fi=s0)  

Nesta janela, cada valor da subestrutura pode ser inserido em sua própria caixa de edição, subcampos repetitivos podem ser adicionados com a opção "Adicionar" e todo o "grupo" da subestrutura pode ser repetido, pressionando o botão ![](https://lh3.googleusercontent.com/KTz_LfSbCMlNi5VAlUfmiBeZTSxzGQRArPxdvh5uFVHafBPTjxhZcKheIjg1q3N1nE5UT8Xgzp-jJeDYNsLH1PXTUAZ2n7vFXOBTBTtCMQF_ZtFvqxyqllzJBdGelGA4lSf5altL=s0) que irá adicionar uma série de subestruturas como uma nova ocorrência do mesmo campo.

Ao clicar no botão Aceitar ![](https://lh5.googleusercontent.com/5sJ0Fjl4CijxzEDy5GiCsSuKCAu8AUMYa4GGRmFvsxHxxZVLJRr37g4Izp4FL3gOvNPx2XS41s6VqeWdvQlEaHcCXX5zGgXwlNUNzG6vSq2DF6UIfoYp-WE2Bp_OLUl3N_e5PXiU=s0)os valores serão colocados na caixa do campo, acrescidos dos delimitadores próprios da subestrutura. ![](https://lh3.googleusercontent.com/PgLERHmFznvRqVapaWT3lwp5XX_3Q8kEPubXS4pQc-SjJRibyZUmgu6k-Hxi7q7IXoQtd9qUrUT3SXtgs7oYw9f4r6WQBL5Wm1gryT9yZnBfLJ34pIH8wbZWwS39GqJ35uVfoUv1=s0)
Ao clicar no botão  os valores editados serão inseridos na caixa do campo da janela de edição principal. Desnecessário dizer que a janela do botão “Cancelar” só irá fechar a "subestrutura", sem acrescentar valores ao campo.

É possível alterar a sequência de repetições de subestruturas usando os botões “para cima” e “para baixo” ![](https://lh3.googleusercontent.com/lx6KHUQ9E2bDQr12qcKmlji2cu75RYgB3UlPYi98DGmXGJnlFiFJdpxBZKoa8xpZCGUpjxQeIxeS2mqW8gi5hdVhBv2Eibdp49iaj4D6lHWj_zqxKxFIYJIyo80jnuEXWOxi0_ER=s0) para mover para cima/baixo a ocorrência selecionada.

Finalmente, também se pode excluir uma ocorrência de um campo subestruturado, clicando no botão  ![](https://lh3.googleusercontent.com/PikJVTAlv1fPvohI8Bd7TQshFzUyLYOKxIgKHmM-Jag2gTOQbLLFMmu10NFrJVpKplTjP9JWTXxLvz8_pQ6wD7L7huPv31KwO-6FL6gFMKrWNEfKYOH0Bq6XzULyx0B_Etfpt5g3=s0)

Experientes em entrada de dados, muitas vezes, não irão utilizar este recurso adicional da interface ABCD e entrar as subestruturas do campo com seus delimitadores apropriados diretamente no editor principal da planilha, o que é perfeitamente possível: a janela extra é na verdade apenas um recurso extra!

![](https://lh4.googleusercontent.com/ZRz9ASbmiTOM1gKYY0oGtb_PMiwNXv3GT1ypMICpS03quhmW6Ay7fco7fZDAcUww-DvTbxgEB5MP9AitFrhMm-vZl0Ly5ZU4eKzbYs0zgwC6hJoOfFlJV_l0FeqDD7nssm7NBygj=s0)

um campo com uma picklist, é indicado pelo o ícone:  em um campo com "controle de autoridades" por termos predefinidos listados em uma caixa separada, clicando neste ícone abrirá a lista em uma janela menor:

![](https://lh4.googleusercontent.com/2koGGBfKwLjVDIGI06ImlpRyfJN4wn7HQB7TH_gtCh1-0S9d5xmCFuh4oPl59kjvlgMSzxY6JkqwBdaVb0YyoszU2lWyfcjvajeJhwyYVu2uclF-EDg8pDW_OblGiTaT5F9semzw=s0)  

Dependendo da definição desta “picklist” (veja o parágrafo dedicado na seção relativa à definição de “picklists” de funções de definição de bases de dados), apenas um ou mais itens podem ser selecionados. 
É desnecessário dizer que os itens listados também deverão ser definidos corretamente, naquele conjunto de colunas de picklists, por exemplo, na Tabela de Definição Campos, pela definição de um prefixo comum com o qual os termos tenham sido indexados.
![](https://lh5.googleusercontent.com/wl7cVId_CAyinOal8GisdXNj_5XYLDK-UpJ4ksH5RiPL1hNnrujZ83FLos-TZQ0-TlJTtSkM7NiW-D5004yQiAJdhDAbKWyE1mSRSIkVXIDU_0fxCpQqAFPdJOrpA60E83wUV7P_=s0)

  

Nesta lista você pode navegar usando o controle alfabético ou selecionar um ou mais itens da lista com Shift-clique ou Ctrl-clique (ou arrastando o mouse) para seleção múltipla. Depois de feita a seleção de um ou mais termos, clique em "Continuar" (abaixo dentro da janela de “picklist”) para transferir sua seleção para o formulário de edição principal.
  

- um campo muito especial, interessante é o campo Editor de "Rich Text”, que se apresenta como segue:
    

Como pode ser visto, o campo é uma caixa de edição maior com uma série de ícones acima, como em um editor de texto real com muitos recursos de edição de texto, como listas detalhadas, ousado ou itálico etc. Esse campo no ABCD é editado com umFerramenta JavaScript Especial, ou seja, 'fckeditor', que permite usar os ícones para criar as tags HTML de acordo no texto do valor do campo.Sempre que esse valor é mostrado em um ambiente www (como o próprio ABCD, ou![](https://lh3.googleusercontent.com/RTjq7sXJY_6MlrGHjbQsP5KBw6kl8tsfDkos67JXF1lVCD0p5Vp6tByafO6Io3dB_qd0c82dPz3_uC6CcLCcvt02VzVMg_JUUN3hiFKohJcOGWMFYDg9jx77mtpDNmoUdnYIXUdb=s0)
por exemplo, no J-ISIS), as tags HTML serão interpretadas como tal e resultam em efeitos gráficos, pois este é o significado de tags HTML.
Também é possível “colar” em tal campo um texto obtido a partir de outro documento, (por exemplo, um documento Word), usando um mecanismo de conversão (para filtrar todos os elementos não-texto) fornecido pelo ABCD.


## Validação de registro e campo

ABCD permite ao administrador do sistema criar e implementar instruções de validação para controle de qualidade na fase de entrada de dados. Tais instruções são escritas na linguagem de formatação ISIS. Veja a seção sobre esse tópico acima – que é uma opção do menu principal Central de “Atualização de Definições de Bases de Dados”. Na barra de ferramentas do registro essa função pode ser executada para verificar o registro atual de acordo com a validação definida. As mensagens resultantes serão mostradas em uma pequena janela separada.

## Catalogação compartilhada através do Z39.50

Z39.50 é um protocolo que permite compartilhar registros (especialmente no formato MARC), primeiro, identificando-os através de uma pesquisa em uma série de servidores Z39.50 – como a Biblioteca do Congresso, em Washington, ou British Library, em Londres, – e depois baixar os registros no sistema local. Aqui está como funciona no ABCD.

### Configurando o Z39.50 do ABCD
Antes que você possa usar esta função, alguma configuração tem que ser feita, a fim de definir os hosts (servidores) do Z39.50 que você pode ou deseja usar e como acessá-los. ABCD oferece uma opção de menu (menu principal Central) para esta configuração.

### Usando a ferramenta Z39.50 do ABCD
Os seguintes passos devem ser tomados para realmente usar a ferramenta:

1. ![](https://lh3.googleusercontent.com/mYLyc9UE5nFRpHNEhFnQkiGjSXQsBPJfsdpYH-gKdVT7OZbqMXt3WqFwIm4B6Ha6B8AazmWjmTBPke8lJIPJ3cey4ya1ZkXWFMV_PMOt1GRa6Ajt4zj1WbW7_fY1VgwU4CsObgAC=s0)  clique no ícone Z39.50 na barra de ferramentas de catalogação, invocando uma tela que permite a seleção de um servidor Z39.50 e uma expressão de pesquisa ou um ou mais ISBN para ser(em) enviado(s) para identificar os registros para download:

  

![](https://lh3.googleusercontent.com/4cqkJQAoYNkknLVBCBw810c4gJwEuxhnTsJZbQX93ZnT6-zyO2NYI5-8MrCF9SJPbP66j0UDZcxhrKWMajNviFCuuUPBQRPyhnpQTc6ARttoff8T0FUJvVNwRJTiPgVsFdRSBSnQ=s0)

2. depois de ter clicado no botão “Pesquisar” (ou Search), se o pedido submetido for bem sucedido (ou seja: o servidor aceitou o seu pedido e identificou um ou mais registros, de acordo com os seus critérios de busca), uma nova janela do navegador irá apresentar a lista de resultados com um ícone de “copiar para base de dados” ![](https://lh3.googleusercontent.com/TpZsyfpKVlkL1bvjT2U8TUJDTqtnEpcD_20R61aCYDziT56gOy1QE7mMXku1-mEqpbF4i0BnxRa9j9YGAx-lgL-slzc5lIvHb95pCwWnJhstXp0p0OatRNomF2I9Q2cJ-H-J3nB4=s0)para cada registro individual:![](https://lh3.googleusercontent.com/xGZViNSp-WYv1rBFE0jYmVQaE7zjaO95CM3lMf_R4RVAMyMp0pkykniaC7H5NBF5D0wKvUaxkJiXSoHM2sDhJoAfjX2SVB4KIDDMwqN7-ziNGGeUyJjJOeN_J-xV_djapGtzg1Fb=s0)

  

3. ao clicar sobre o ícone "copiar-para-base-de-dados”, o registro selecionado será transferido para a tela de catalogação do ABCD como  registro atual (um novo MFN terá sido atribuído), onde o mesmo pode ser editado com o botão editar, se necessário.
    
Desnecessário dizer que, na maioria dos casos, esses registros são registros MARC de alta qualidade, de modo que esta catalogação compartilhada tem muitas vantagens, por exemplo, economia de tempo (se estiver disponível suficiente banda larga para a comunicação com o servidor) e melhorar a qualidade do seu catálogo. No entanto, se seu catálogo não usa o formato MARC, pode ser necessário primeiro preparar um mecanismo de conversão antes de importar registros em sua própria base de dados. Esta técnica é discutida em outra parte deste documento.

4. quando o ícone Z39.50 não é acessado a partir da barra de ferramentas da base de dados, mas a partir da barra de ferramentas do registro, o comportamento será um pouco diferente: selecionar o registro atual (de preferência pelo seu ISBN) e, quando disponível a partir do servidor Z39.50 selecionado, apenas os campos que faltam no registro atual serão acrescentados, a fim de completar o registro bibliográfico.
    

## Valores padrão

Esta é uma função simples da barra de ferramentas da base de dados: o formulário de edição será apresentado, se assim for desejado, e valores default podem ser inseridos (ou excluídos) neste formulário.


## Relatórios (impressões)
    
Como explicado anteriormente, os relatórios ABCD são gerados por Formatos de impressão ISIS e, portanto, a interface para a criação de PFT’s é reutilizada aqui. No futuro, provavelmente, ABCD irá oferecer algumas PFT's pré-definidas, frequentemente utilizadas ou típicas, por exemplo, para listagem de empréstimos vencidos, etc.

## Utilitários
    
Os utilitários oferecidos neste módulo de Entrada de Dados, a partir da barra de ferramentas da base de dados, são os seguintes:

![](https://lh4.googleusercontent.com/zW30yuC8T2m3RIK22yfxyN5AM6veR_1uiZD_CkYiv6dQJLMFlTwz2S-ZzZGuOnMP7AlYL4TKnZdGwf3rgkW13h6VQLzWmfz97y34vCVU8iuCMvxCGgW-htcYcT8dL-01gb08DWsL=s0)  

1. Importação:  arquivos estruturados baseados em texto podem ser importados através da definição de uma tabela de conversão, que pegará o rótulo para cada (sub)campo (ou as literais usadas para separar subcampos) do arquivo de entrada, o "separador-de-repetição” utilizado dentro de um campo para ocorrências diferentes e o formato de extração em Linguagem de Formatação ISIS: ![](https://lh6.googleusercontent.com/qc5XZnGE3tuQg35BFgdGwyxP6KW0Gdrzwx_FS0vMKirZPRLhCLdEiFHLisGrETOXcbJfCV7--7ujQDyMW7XDc8lEVMKg-kqMvUv61obSl0Zj_eJ5khZn17gwJwM755OL5w2Yng9f=s0)
    
Se o arquivo texto de entrada é um arquivo delimitado por TAB (um arquivo com os valores separados com TAB’s em vez de vírgula), simplesmente ative o botão e o ABCD – sem a necessidade de identificar cada campo ou coluna - importa cada valor em um campo seqeencial separado (ou seja: o primeiro valor ou coluna vai para o campo 001, etc.)

2. Importação ISO: arquivos ISO podem ser importados para uma base de dados ABCD em duas etapas: primeiro, o arquivo ISO tem que ser carregado, localizando-o através do botão “browse”:

![](https://lh5.googleusercontent.com/uhygoC1DmMxYY3jV6iEBotnwgFvlC2FqaRIf_n9FU1iOssVcKwo0734OFqKYvhGymnhBvfb5Sgu0Q-JIWPqGCzJ5K0_-zLiUXiGAj1Uj9xU1pNs2fZMdUrNlZ1dFy8GMEN1wIdn4=s0)

  
Em seguida, o arquivo ISO carregado será listado e pode ser efetivamente importado com o botão "ativar” verde, após o que ABCD vai realmente importar os registros ISO para a base de dados atual (usando para esta finalidade ferramenta CISIS), o que significa que em caso de grandes volumes o servidor web Apache pode emitir um erro de “Time-out” – então, use a feramente de linha de comando para isso!  :![](https://lh6.googleusercontent.com/YR_prDLfJjpCKHXjTJKCl7fHgnotjbFVtLLAImuNxP54owkA8ZSzrgJQ41uL2BA47tGDuyzE61BO1zWeKOKgJV9P6GCi5o1TbXfjKsqratfH5wbJ7owv8mYhUg_OkpXcP2Wwf5Xi=s0)

3. Exportar para ISO: esta função simplesmente pede uma seleção de registros (por intervalo de MFN ou expressão de pesquisa) para exportar e um nome para arquivo ISO de exportação:
  
![](https://lh3.googleusercontent.com/2J4DnZ_NtHRSXlYHgZadVupb0saBl0kFNcp9ImMBqMB3fyO8wzULWqTezY5T5A57vHt5ZAQYsK_eCHQSFaU9P4bTubsdwu0JgL9PHDLAAXt3j_BK0TJ-JKA2turJjW6MQ7rsUTKp=s0)  

4. Exportar para TXT: esta é a função inversa da de importação TXT, usando o mesmo formato de tabela de conversão, mas logicamente fazendo a operação inversa nos campos. Ao ativar a opção “delimitado por TAB’s””, a exportação será na verdade, um arquivo CSV que pode ser importado para planilhas etc.

5. Outros utilitários de bases de dados: além de importar e exportar bases de dados de e para diferentes formatos, ABCD também precisa fornecer algumas ferramentas para o administrador de bases de dados que vamos discutir resumidamente aqui:
  
![](https://lh4.googleusercontent.com/zW30yuC8T2m3RIK22yfxyN5AM6veR_1uiZD_CkYiv6dQJLMFlTwz2S-ZzZGuOnMP7AlYL4TKnZdGwf3rgkW13h6VQLzWmfz97y34vCVU8iuCMvxCGgW-htcYcT8dL-01gb08DWsL=s0)  

6. Desbloquear a base de dados: no caso de uma base de dados ficar bloqueada (como parte da proteção multi-usuário), sem ter a chance de ser desbloqueada, por exemplo, no caso de uma súbita interrupção de energia, a base de dados pode ser desbloqueada manualmente. ABCD simplesmente emite uma mensagem sobre o status após desbloqueio.
  
7. Listar registros bloqueados: ABCD irá listar os registros que estão bloqueados (se houver) com o seu status:![](https://lh6.googleusercontent.com/izVayTT0xR2vCzBqH3hIveTcm_VOYShDlU80sbxLoDavXkBvlAGT2aF862nqott20-43nD-l4hOAzAefbx7HnPyfDWNhwEpI4D9DEukbHUzHkh3XL_kd8tMf1mxi2H10Wz8YOwCF=s0)
    

8. Geração do arquivo invertido: no caso de terem sido feitas mudanças estruturais na FST, o administrador do sistema deve reindexar a base de dados para aplicar a nova definição de FST em todos os registros da base de dados (e não só nos recém editados, que serão indexados automaticamente). Se o conjunto de registros não for muito grande – o que pode ser observado também em função da complexidade da FST e o tamanho médio dos registros – a geração completa do arquivo invertido pode ser feita a partir do ABCD. No caso de bases de dados maiores isto deve ser feito a partir de uma operação de linha de comando com uma das ferramentas CISIS. Por exemplo:

```
mx MARC fst=@marc.fst fullinv=marc now - all tell=100
```
9. Mudanças Globais: como no WinISIS (e mesmo fornecido nos tempos antigos do CDS/ISIS para DOS, com programas ISIS/Pascal adicionais), as mudanças podem ser editadas semi-automaticamente na base de dados completa ou em um intervalo de registros (identificados por faixa de MFN’s ou expressão de pesquisa). A interface a seguir ilustra as possibilidades:

![](https://lh3.googleusercontent.com/XEUfl6-CDIMoQyC6WzP4_t7h7EuQRW-1_Y2-UvmRdI_UtreJDM3Qu4PSAeGNIoz52H-huEpLvKS5PZX7lFKO6hlCwUEzV6RbjFiNTz0bA5cxWcazH9HGEE9AyKy5_zbbXFqrR5oS=s0)

Finalmente, a operação pode ser executada ou o formulário pode ser restabelecido. ABCD irá mostrar o resultado da operação. É preciso ter cuidado extremo com estas operações, pois podem ser irreversíveis e afetam muitos registros. Fazendo um backup (exportação para ISO como explicado acima) é uma boa idéia.

10. Mudanças globais: como no WinISIS (e até mesmo fornecido nos velhos tempos do CDS/ISISIS para DOS com programas ISIS/Pascal adicionais) as mudanças podem ser editadas semi-automaticamente sobre o banco de dados completo ou sobre uma gama de registros (identificados por faixa ou expressão de busca). A interface a seguir ilustra as possibilidades aqui :

    - Selecione Campo: em qual campo operar
    - Tipo de alteração global: O valor 'novo' será adicionado como uma nova ocorrência do campo, o campo existente será modificado dentro ou excluído.
    - Escopo do campo: o campo completo deve ser correspondido ou qualquer substring no campo
    - Conteúdo a ser localizado: a sequência de ou dentro do campo a ser alterada
    - Valor a ser adicionado/alterado: a nova string que substituirá a string localizada
    - Campo dividido: Caso um delimitador - como dado aqui - é atendido no campo, a seção antes ou depois do delimitador (como verificada) pode ser excluída ou movida para outro campo (a ser selecionado na lista).
    - Finalmente, a operação pode ser executada ou o formulário pode ser redefinido.
    O ABCD mostrará o resultado da operação. A extrema cautela deve ser aplicada com essas operações, pois elas podem ser irreversíveis e afetar muitos registros. Fazer um backup (exportar para a ISO, conforme explicado acima) é uma boa ideia, com certeza.
    - O arquivo de ajuda dedicado para esses utilitários pode ser editado a partir desta opção. O texto existente será fornecido no editor HTML e pode ser editado e/ou traduzido.
    


## Estatísticas

Esta opção restante da barra de ferramentas da base de dados é o de Estatística (visto que não temos de discutir as opções de ajuda e home, pois são completamente auto-explicativos). Esta opção é explicada na sua própria seção, mas pode ser acessada também a partir da barra de ferramentas do catalogador.

## Códigos de barra
    

**Introdução**

O ABCD (como v1.5) tem uma função para ajudar na produção de códigos de barras. Mais cedo, os administradores do ABCD precisavam confiar em ferramentas externas - mas existentes e disponíveis gratuitamente para produzir seus códigos de barras, mas agora o ABCD tem sua própria opção de construção.

Somente bancos de dados que foram configurados para usar códigos de barras (pois esta não é uma opção obrigatória no ABCD) mostrarão o ícone de código de barras![](https://lh4.googleusercontent.com/ac4m0TThbI9oN16h-JHNzK569lgh_JDNMYC5dn75XMihdiaHj8e8bgB749j4xpWvr10Se3YiByWUVu9vNsZNU8N69nFiQaDSFn-HrHIvp56hVJh-Wv9mZ-CK25BNcQ73K-sBGDhv=s0) na barra de ferramentas.Para ativar esta opção para um banco de dados, adicione a seguinte linha ao arquivo 'dr_path.def' do banco de dados em questão:

    barcode=Y

Para acessar esta opção, o operador deve:
- Ser administrador do sistema ou
- tem todas as permissões de catalogação no banco de dados ou
- Tenha permissão para imprimir rótulos e códigos de barras (nas configurações de permissões do banco de dados relacionado).

Esta função ajudará a imprimir rótulos que identificam os objetos físicos no sistema de circulação ou outras bases de dados com códigos de barras.Um arquivo de configuração precisa ser editado, onde - entre outras variáveis - as dimensões dos rótulos ou códigos de barras são definidos.Os resultados podem ser enviados para a tela, para um arquivo txt ou para um processador de texto.Nesse momento, os códigos de barras só podem ser aplicados quando as informações do inventário são armazenadas dentro dos registros bibliográficos (o catálogo-dados, por exemplo, Marc).

Os rótulos podem ser produzidos por
- Números de classificação: uma gama de números de classificação de registro é fornecida e um relatório com códigos de barras é produzido para todos os números de inventário armazenados no registro
- um intervalo de números de inventário: ao invés de números de classificação, um intervalo de números de inventário precisa ser indicado; insira os números de inventário para os quais você deseja imprimir códigos de barras na caixa correspondente e separe-os por vírgulas (,)
- Faixa Mfn: é fornecida uma gama de MFNs e o relatório com códigos de barras é produzido para todos os números de inventário contidos em cada registro da faixa solicitada

A opção 'códigos de barras' com o ícone do código de barras acima mencionado, quando clicado, aparecerá da seguinte forma, juntamente com a opção 'inventário' (que será discutida na próxima sessão), com os três formatos principais, resp. 'códigos de barras, 'rótulos spine-labels' e '(normal) etiquetas':

![](https://lh6.googleusercontent.com/tY80-1x5VoajM_0iIra1nCbELxFg-IhL-ErAMbIxPgruH75_GnrT3lZQverwI0qCmW1KyyKYloFaluPcdokqhhm_TJtrC4pywS3eOtwGpLKzT9svkQL-FkrFeQjmlfCqFxV1oELO=s0)

  

**Configuração**
    
Esta seção define os parâmetros que ajudam a extrair informações do banco de dados, preparar a apresentação do rótulo e informar suas dimensões.As seguintes informações são solicitadas:


Tabela 2.1.Parâmetros de código de barras

|Parâmetro|Explicação|
|---|---|
|Prefixo do número de classificação FST|Preliteral usado para identificar o número de classificação no FST. Exemplo: ST_|
|Formato para localizar o número de classificação|Formato que será aplicado ao banco de dados para extrair o número de classificação.É precedido pelo prefixo anterior para apresentar a lista de números de classificação no processo de seleção dos registros. Exemplo: `if p(v82^a) then v82^a, "" v82^b"." V82^c, "" v82^d, "" v82^e, else v82^b, "." v82 fi` |
|Prefixo do número de inventário no FST (editado)| Preliteral usado para identificar os números de inventário no FST e apresentá -los adequadamente organizados para a pesquisa de classificação, por exemplo, para adicionar zeros à esquerda, mesmo que não tenha sido inserida dessa maneira.<br />Exemplo: NICLA_<br /><br />Observação:<br /> Recomenda-se adicionar este campo à tabela de indexação de registros (FST). Exemplo:<br /><br /> ```(if p (v900 ^ n) then 'NICLA_', If f (val (v900 ^ n), 1,0) = v900 ^ n then replace (f (val (v900 ^ n), 5.0), ``, `0`), else v900 ^ n, Eurlex.europa.eu eur-lex.europa.eu fi) ```<br /><br />O script neste formato:<br />• Determina se o campo é numérico (if f (val (v900 ^ n), 1,0) = v900 ^ n), que verifica se o valor do campo expresso em forma numérica é igual ao valor do campo;<br />• Nesse caso, o campo é convertido em um número em um formato fixo de 5 caracteres, preenchendo espaços à esquerda, que são substituídos por zeros:<br /><br /> ```replace (f (val (v900 ^ n), 5.0), ``, 0 ');``` <br /><br />• Se não for numérico, nenhuma alteração será feita no campo. Observe o valor 5 mostrado no formato deve ser adaptado ao número de posições atualmente ocupadas pelo principal código de barras inseridas no banco de dados.|
|Formato para localizar o número de inventário (editado)|Ele será aplicado ao banco de dados para localizar o número do inventário e apresentá -lo na janela de seleção de registros para emitir os rótulos por um intervalo ou por uma lista de números de inventário.Neste exemplo, os zeros foram adicionados à esquerda do número de inventário para garantir que a sequência apresentada e posteriormente recuperada esteja correta.<br /><br />Exemplo:<br />```if f (val (v900 ^ n), 1,0) = v900 ^ N then replace (f (val (v900^ n), 5.0), ``, `0`), else v900 ^n fi``` <br /><br />Este script acima:<br />- Determina se o campo é numérico (if f (val (v900 ^ n), 1,0) = v900 ^ n), que verifica se o valor do campo expresso em forma numérica é igual ao valor do campo; - Nesse caso, o campo é convertido em um número em um formato fixo de 5 caracteres, preenchendo espaços à esquerda, que são substituídos por zeros:<br />```replace (f (val (v900 ^ n), 5.0), ``, 0 ');``` <br/>- Se não for numérico, nenhuma alteração será feita no campo.<br /><br />Aqui está a lista apresentada para intervalos de números de inventário quando os zeros são adicionados à esquerda:<br />![](https://lh4.googleusercontent.com/WW2n1RGH42qo5aABD8d17omcsT491G5aM-8XDyQuUwPf3ZazcsEvedjbQSkioIZOuMLHfCCJxwJPuE75VoG69rV6zdRTNmkexKmnk693JIVbkIiHZND25C4Xg2VY53erLAkzHtLH=s0)Lembre -se de que você deve criar no FST a chave de recuperação nicla_ com os números de inventário com os zeros principais:<br /><br />```900 0 (if p (v900 ^ n) then 'NICLA _', if f (val (v900 ^ n), 1,0) = v900 ^ n then replace (f (val (v900 ^ n), 5.0), ``, `0`), else v900 ^ n fi, '%' / fi)```<br /><br />Veja a diferença se esse método de preenchimento de esquerda com zeros não for usado:<br />a.A indexação normal no FST seria ```900 0 (| NI_ | v900 ^ n |% | /)```<br />b.  O prefixo "NI_" seria usado para recuperar os números de inventário<br />c.  O formato de extração do número de inventário seria v900^n<br />d. A lista de números de inventário seria exibida da seguinte forma, mas impossibilitando o estabelecimento de uma faixa contínua de números de inventário.![](https://lh4.googleusercontent.com/4smbl2Df6zQecLxZQBhC3Z3quxVPrEuNWGGonxHaPtGTLFtjvi8jivjIQYD_dv3i_bW07LHuhxmtSPMENcnHqzUZ2r_l_2g13RTSt1gOdcqLjeeOxUTOHdc6WkAd9zN5xB6L80fj=s0)
|Prefix of the in- ventory number in the FST (unedited)|Preliteral usado para identificar os números de inventário no FST, respeitando a maneira como foram inseridos.Usado quando a impressão é solicitada através de uma lista de números de inventário, pois é necessário comparar a lista fornecida com o valor inserido em cada um dos registros.Exemplo: NI_|
|Formato de número de inventário (não editado)|Este formato será aplicado ao banco de dados para localizar o número do inventário, conforme foi inserido no banco de dados.É usado para determinar se o número de inventário do campo repetível dos itens de estoque corresponde ao intervalo ou à lista solicitada. <br />Exemplo:<br />```v900^n```|
|Formato de impressão (PFT)|Formato para usar para imprimir a etiqueta ou rótulo selecionado.<br />Exemplo de etiqueta de código de barras:<br /><br />```proc ('a1000 ~' if p (v84 [1]) then v84 [1] else v82 [1] fi '~'), (If p (v900 ^ n) then, 'INV *', </ Span> </ span> </ span> <span style= "font-size: V1000 ^ a [1], v1000 ^ b [1], v1000 ^ c [1], v1000^ d [1] '%%%' / fi)```<br /><br />Nota: Para entender o exemplo PFT acima :<br />a.  o uso de para codificar corretamente o PFT<br />b.  A inclusão da fonte selecionada para gerar o código de barras:<br />c.  A inclusão do literal *inv* antes e depois do número do inventário```(v900 ^ n)```. Isso é essencial porque, se você solicitar a impressão de um intervalo ou uma lista de números de inventário ABCD, você deverá ter acesso a esse valor para comparar as informações extraídas do registro com os valores solicitados para determinar se uma ocorrência dos itens de ações seráou não será incluído na saída solicitada.<br /><br />d. As quebras de linha foram adicionadas para fornecer melhor visibilidade ao formato.O arquivo de configuração não deve ter quebras de linha porque um parâmetro é interpretado por linha. Se desejar, o formato pode ser fornecido como uma PFT externa usando @format_name.pft|
|Formato de impressão (PFT) para enviar para TXT|O formato é aplicado quando o resultado deseja ser enviado para um arquivo txt para ser processado por uma impressora especial.Você pode entrar diretamente na caixa de texto ou fornecer o nome de um formato existente ou ser criado no mesmo processo. Use o ícone **Editar** para editar ou criar o formato correspondente.<br /><br />Exemplo do formato a ser usado para gerar um arquivo txt para imprimir códigos de barras em uma impressora do tipo Zebra:<br /><br />```proc ('a1000 ~'```<br /> ```if p (v84 [1]) then v84 [1] else v82 [1] fi '~'),```<br />``` (If p (v900 ^ n) then,```<br />``` 'INV *' , (2-methoxyphenyl) -2-methyl-2-oxo-1,2,3,4-tetrahydro- '^ XA ^ LL0203', / 'PW831', / 1, 1 H-NMR (DMSO-d 6):? 1, 1 H-NMR (DMSO-d 6):? 1, 1 H-NMR (DMSO-d 6):? 1, 1 H-NMR (DMSO-d 6):? 1, FT97,165 A0N, 25.43% FH + FD + FT97.134% A0N, 25.43% FH + FD + If a (v900 ^ m) and a (v900 ^ e) then | | V900 ^ l, else If a (v900 ^ m) and p (v900 ^ e) then | T. | V900 ^ e, | Ex. | V900 ^ l else If p (v900 ^ m) then | Vol. | V900 ^ m, | T. & lt; / RTI & gt; Ex. Fi, Fi, Fi, '^ FS', / 1, FT97,166 A0N, 25.43% FH + FD + FT97.165% A0N, 25.43% FH + FD + If p (v1000 ^ f) then v1000 ^ f fi '^ FS', / 1, 1 H-NMR (DMSO-d 6):? 1 H-NMR (300 MHz, CDCl3):? (1) 1, FT498.36 (M + H), 22.28 (M + H) + = 1, 1 H-NMR (DMSO-d 6):? 'PQ1,0,1, Y ^ XZ', / '%%%' Fi /)```<br /><br />Se desejar, o formato pode ser fornecido como uma PFT externa usando @format_name.pft<br /><br />Observação<br />• o texto 'INV *' Deve aparecer no início de cada ocorrência, porque dessa maneira o processo pode identificar o número de inventário correspondente para determinar se está ou não incluído nas listagens por classificação ou por número de inventário<br />• O número de classificação é adicionado ao campo 1000 e, em seguida, esse rótulo é mencionado no grupo repetível usando sempre a primeira ocorrência do mesmo campo<br />• / ' %%%' : Este é o marcador, em uma nova linha final, para separar as diferentes ocorrências geradas pelo formato|
|Tag height|Altura em centímetros do rótulo.Este valor será convertido para EM, multiplicando -o por 2.37106301584 com o objetivo de ajustar no quadro na impressora.|
|Width of the label|Largura em centímetros do rótulo.Esse valor será convertido para EM, multiplicando-o por 2.37106301584 com o objetivo de ajustar no quadro na impressora.|
|Number of labels per line (columns)|O número de códigos de barras/tags, para páginas com mais de um código de barras por linha|

**Exemplos de saída com o seguinte arquivo de configuração:**

• Exemplo de código de barras

![](https://lh6.googleusercontent.com/N58gdJQYOf2nT18k0seatyR488k2wrxcjRBbMiMJn5vuxkUHoJkYtUX_EoKL1sSCOlJZ-YIkblTu92S74XpQNZc94b80oskhWPlsgfxOYBj5aintpeKP6ofPJGjG_CABEThMrl1x=s0)

**Exemplo de configuração:**

Classification_number_pref:
```
ST_ V82 ^ b, v82 ^ b, v82 ^ b, v82 ^ b, "v82 ^ b," v82 ^ b,
```
Os componentes da fórmula (I) 


Prefixo de número de inventário:

```
NICLA_ (V (v900 ^ n), 5.0), ``, `0`), else v900 ^ n 
```

Inventory_number_pref_list:

```
NI_ 
```

Inventory_number_display:

```
v900^n
```

Label_format:

```
@barcode.pft
```

Label_format_txt:

    @barcodetxt.pft


Height: 4 
Width: 7
Cols: 3 

- Exemplo de rótulos da coluna 

**Configuração:**

Classification_number_pref:

```
ST_ V82 ^ b, v82 ^ b, v82 ^ b, v82 ^ b, "v82 ^ b," v82 ^ b, 
```

Os componentes da fórmula (I) Inventory_number_pref = ```NICLA_(V (v900 ^ n), 5.0), ``, `0`), else v900^n``` 

Inventory_number_pref_list:

```
NI_ 
```

Inventory_number_display


```
v900^n
```

Label_format:

```
@lomos.pft
```

Label_format_txt:

    @lomos_txt.php

    Height = 3
    Width = 5
    Cols = 4


Sample PFT : 


```
(if p (v900 ^ n) then 
'INV *' V900 ^ n '* INV *' 
'<center> <strong> <span style = "fontsize: 20px; font-face = arial">'
if p (v82 ^ a [1]) then V82 ^ a [1], v82 ^ b [1], v82 ^ c [1], v82 ^ d [1], " 1], 
else V82 ^
b [1], v82 ^ c [1], v82 ^ d [1], v82 ^ e [1], Fi '' ',
if a (v900 ^ m) and a (v900 ^ e) then Ex. | V900 ^ 1, Else If a (v900 ^ m) and p (v900 ^
e) then | T. | V900 ^ e, | Ex. Else If p (v900 ^ m) then Vol. | V900 ^ m, | T. & lt; / RTI
& gt; Ex. fi, fi, fi,
'%%%', fi /)
```


 Example output :![](https://lh5.googleusercontent.com/FG50ihhpXOJCgVCvVAYmbezkoDCk5mqtVNWIvIVoFI_C4A0YUPIPgr_FctE8g6YvR8ZxazajKtrEd9TVdVKBIzLTASIMu-sSLE5r9dzzzWXRs31SKgmCuhYkunnI5sSms3YyTvrX=s0)



-  Exemplo de etiquetas
    

  

#### Exemplo de configuração:

Classification_number_pref:

```
ST_ V82 ^ b, v82 ^ b, v82 ^ b, v82 ^ b, "v82 ^ b," v82 ^ b, 
```

Os componentes da fórmula (I) 
Inventory_number_pref:

```
NICLA_ (V (v900 ^ n), 5.0),``, `0`), else v900 ^ n 
```

Inventory_number_pref_list:

```
NI_
```


Inventory_number_display:

```
v900^n
```


Label_format:
```
@eags.pft
```

Label_format_txt:

```
@etiques_txt.php
```

    Height = 5
    Width = 10
    Cols = 2

Example PFT for labels :

```
('<Table> 
    <tr>
        <td valign = top align = center width = 50>' 
            'INV *' V900^n '* INV *' 
                if a (v82[1]) and a (v84[1]) then '' fi, 
                if p (v82^a[1]) then V82^a[1], v82^b[1], v82^c[1], v82^d[1], ''1], 
                 else 
                v82^b[1], v82^c[1], v82^d[1], v82^e[1], 
                fi,
                '' '
                if a (v900^m) and a(v900^e) then |Ex.| V900 ^ 1, 
                    else 
                    if a(v900^m) and p(v900^e) then |T.| V900 ^ e, | Ex. 
                        else 
                        if p(v900^m) then |Vol.| V900^m, |T. & lt; / RTI & gt; Ex. fi, 
                    fi, 
                fi, 
                (v100^a[1]) then '' '', v245^a, 
        '</ Td> 
        <td width = 50 valign = top align=right>' 
            v900^n'
        </td>
    </tr>
</table> 
%%%' /)
```
  
  

#### Exemplo de saída:  


![](https://lh6.googleusercontent.com/NhW7CnlSLG9183c9gk5PEW4VJHsNCBb9x7ongyH2JhutZdw55_9O-tGODA4zZf__s9ycrbfGV9ODjrIR9LOBqSWJrYQAAxleDgMGiciY8LnmUmjsDPlo5m2sEcD-oCad7IQw8WLA=s0)

  

#### Destino de saída: Enviar para
O meio ao qual os rótulos emitidos são enviados de acordo com as seguintes possibilidades:

Visualizar: Envia a saída gerada para a tela do computador.Você pode usar a opção de impressão no menu do navegador para obter uma cópia impressa;Nesse caso, você deve configurar a impressora para definir as margens e remover todos os cabeçalhos da página
Documento word: Envie a saída para um processador de texto.Foi testado com sucesso no OpenOffice.Depois que o documento é exibido no processador de texto, você deve definir as margens da palavra
Texto: Use esta opção para gerar um arquivo temporário com outro software que você deseja usar para imprimir tags geradas.Nesse caso, o ABCD usará o formato de exibição acima (PFT).Enviar para o TXT no arquivo de configuração correspondente.

#### Seleção de registros

Os seguintes métodos são fornecidos para definir o conjunto de registros em que os códigos de barras serão produzidos:

- Por número de classificação: usa o prefixo dos parâmetros do número de classificação no formato FST 'e' para localizar o número de classificação 'para exibir a lista de números de classificação.Selecione a partir desse formato também o intervalo 'de' e 'para' que você deseja extrair.Uma tag será gerada para cada número de inventário contido em cada registro no intervalo selecionado.
- Por intervalo de números de inventário: esse método usa o prefixo do número de inventário dos parâmetros no formato FST 'e' para localizar o número de inventário para exibir a lista de números de classificação '.Do mesmo PFT, o alcance 'de' e 'a' para extrair será levado.Uma tag será gerada para cada número de inventário contido em cada registro no intervalo selecionado.Lembre-se das considerações já explicadas acima para apresentar uma lista de números de inventário adequadamente ordenados, acolchoados à esquerda pelo Zero's.
- Por lista de números de inventário: este método usa o número de inventário de parâmetros 'Prefixo (não editado)' e 'formato de número de invenções (não editado)' para construir a pesquisa que localiza a lista de números de inventário.
- Por intervalo de MFNs: esses métodos lerão cada um dos registros do intervalo MFNS solicitado.Uma tag será gerada para cada número de inventário contido em cada registro no intervalo selecionado.
    
 

## Ferramenta de estoque
    

[Para uso futuro, para ser adicionado]

Como alternativa à interface ABCD para a participação em estoque, um método simples 'manual' pode ser usado, o que permitirá produzir relatórios sobre quais códigos de barras encontrados nas prateleiras estão ausentes nos objetos de WHONOBJETOS ou COPIES-DATABASES, mas também vice-Versa: Quais objetos ou cópias existentes não podem ser encontrados nas prateleiras.

Para este fim, são necessários os seguintes elementos - que podem ser criados usando as tecnologias centrais da ABCD discutidas anteriormente neste capítulo:
- Um banco de dados dedicado 'stock' (já incluído no diretório de bancos de dados como no ABCD 2.0), que servirá apenas para armazenar os códigos de barras encontrados nas prateleiras.Este banco de dados tem a estrutura mais simples possível (FDT):

```
F|1|Barcode|1|0|||X||10|||||||0||0|0||| 
F|2|Date of checking|0|0|||OD|||||||||0||0|0|||
```
onde até a segunda linha é opcional para armazenar também hora e data.Portanto, em essência, é necessário apenas um campo simples para armazenar os códigos de barras.Eles podem ser facilmente armazenados digitalizando o código de barras dos livros ao navegar nas prateleiras com um único clique no formulário de entrada de dados para este banco de dados e outro clique para salvar o registro.Como alternativa, também pode armazenar todos os códigos de barras como linhas em uma linha de texto e converter esse arquivo em um ISIS-Database com o comando:


    mx seq=mybarcodes.txt create=stock now -all

e no FST uma única instrução para indexar o código de barras em V1 com prefixo 'BC_' :


    1 5 '/BC_/', v1

- Um formato de impressão (PFT) para produzir um relatório da base de dados 'Stock' verificando a presença do código de barras no Database de cópias (ou base de dados loanobjects se esse nome de banco de dados for referenciado), que essencialmente deve conter o seguinte código:

```
if (ref->copies(L->copies('IN_'v1),v30)='')
then  'Livro com código de barras <b>'v1'</b><font color="red"> está faltando no banco de dados COPIES </font><br>'
else 'Ok livro com código de barras' v1 'Encontrado no inventário de cópias' 
fi,
```


- Um formato de impressão (PFT) para produzir um relatório 'inverso', significando: a partir do banco de dados de cópias, verificando o banco de dados de estoque para verificar se o código de barras real é encontrado nesse banco de dados, existe nas prateleiras:


```
if (ref->stock(L->stock('BC_'v30),v1)='')
then 'Livro com código de barras<b>'v30'</b><font color="red"> está faltando no banco de dados de stock </font><br>'
else 'Ok livro com código de barras' v30' found on shelves' 
fi,
```


> Observação:
> Estes são PFT básicos que podem ser elaborados para mais decoração
> ou inclusão de mais dados, p.o título do livro, para o qual
> Outro Ref(L()) construto, referindo-se ao banco de dados do catálogo este
> tempo, precisará ser adicionado.


O`REF(L())` função realmente verifica se o campo de código de barras, encontrado ao localizar `(L())` O código de barras no banco de dados alternativo permanece vazio, formulado como '' (duas citações únicas sem nada ou uma 'string vazia') indicando ausência.

A produção real dos relatórios de ações será feita-como pode ser esperado-a partir da opção de menu 'Relatórios' ou da barra de ferramentas. Ao produzir o relatório, selecione o PFT mencionado acima, com o seguinte raciocínio: se a existência de um código de barras, encontrada nas prateleiras (e, portanto, incluída na base de dados stock) deve ser verificada no sistema ABCD, use o PFT com a declaração `ref->copies(L->copies('IN_',v1) ='')` se, por outro lado, você deseja verificar se um código de barras (ou item) existente no sistema ABCD foi realmente encontrado nas prateleiras, use o PFT com a declaração `if (ref->stock(L->stock('BC_'v30),v1)='')`.

Esses relatórios podem ser enviados convenientemente para a tela, para um arquivo de texto ou processador de texto ou palavras ou, principalmente provavelmente a opção mais útil aqui, uma planilha, que pode ser adicionada ao relatório da biblioteca da biblioteca.

