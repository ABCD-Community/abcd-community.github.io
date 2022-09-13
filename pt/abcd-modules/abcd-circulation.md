---
title: Módulo central - empréstimos/circulação
description: Esta seção é sobre o módulo de empréstimos básicos ABCD, pois vem pré-configurado com o sistema. Ainda assim, sempre seguindo a filosofia de flexibilidade do ABCD, o sistema de empréstimos pode trabalhar com qualquer banco de dados bibliográfico e de objetos.
lang: pt
lang-ref: abcd-modules/abcd-circulation
---

# Módulo central : empréstimos/circulação

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---


Esta seção é sobre o módulo de empréstimos BASIC ABCD, pois é pré-configurado com o sistema.Ainda assim, sempre seguindo a filosofia da flexibilidade do ABCD, o sistema de empréstimos pode funcionar com qualquer banco de dados bibliográfico e de objetos.

Além disso, o ABCD oferece um módulo 'empréstimos avançados' (EMPWEB) que pode lidar com situações muito mais complicadas em, por exemplo,Organizações de várias ramificações com diferentes políticas de empréstimos etc. [!!] As transações neste módulo de empréstimos avançadas serão armazenadas em table SQL e também podem acessar os dados do usuário (através de serviços webs) armazenados em table SQL em outros lugares, além de acessaros dados do usuário no banco de dados do usuário ABCD (no formato do ISIS).É claro que isso permite aplicações muito avançadas de alto desempenho do módulo de empréstimos.Além disso, os empréstimos avançados da Empweb ou da ABCD oferecerão uma função de reserva e uma função 'MySite', onde os usuários finais podem verificar e acompanhar a disponibilidade de objeto de empréstimos em sua conta pessoal (protegida por senha) de empréstimos ABCD.

[!!] Este módulo avançado, no entanto, requer a instalação de software adicional (Java/Jetty e um banco de dados SQL) e é oferecido apenas como um módulo extra opcional.

Sugerimos verificar os seguintes critérios para decidir se você precisará do módulo avançado ou não:
- Vários servidores em seu sistema?
- Múltiplos bancos de dados de usuários/cópias em seu sistema?
- Alto volume de transações?
- Qualquer fonte de dados precisa do driver ODBCs ? (ODBC drivers are software to couple mostly relational databases or SQL-tables to software)

Se você tiver um 'sim' com séria importância para o seu sistema, estará melhor com o módulo de empréstimos avançados.[!!] A maioria das bibliotecas menores, no entanto, certamente onde há uma falta de experiência no uso de Java e SQL-Databases, será melhor com este módulo de empréstimos centrais do ABCD, pois é totalmente baseado na tecnologia ISIS-Database e nãoPrecisa de qualquer software adicional a ser instalado.

## Os bancos de dados de abstiços e whompensobjects de inventário ABCD
  
O ABCD usa dois bancos de dados diferentes para lidar com informações com base nos objetos físicos na biblioteca: as cópias e os objetos do WHONSOBS.Ambos os bancos de dados têm propósitos e escopos diferentes e, portanto, os dados são mantidos separados.Uma boa compreensão de seus diferentes propósitos e estruturas ajudará a entender o ABCD.Vamos discutir cada um deles aqui.

1.  O banco de dados ABCD COPIES.
  
Esse banco de dados tem a função de acompanhar todos os dados administrativos em objetos nas coleções da biblioteca. Esses dados, em princípio, precisam ser mantidos por razões de inventário e manutenção de livros, enquanto os dados relacionados a objetos de empréstimo podem ser excluídos quando o objeto de empréstimo é removido da coleção. Na verdade, o registro criado no final de um procedimento de aquisições (da sugestão ao item recebido ou em qualquer lugar) será armazenado neste banco de dados de cópias. A estrutura do campo de cópias é a seguinte (as tags de campo são seguidas pelo nome do campo):


```
1|Número de controle
10|Base de dados
20|Número de chamada
30|Número de inventário
200|Status
35|Biblioteca Central
40|Biblioteca Setorial
50|Tomo
60|Volume/Parte
63|Número da Cópia
68|Tipo de aquisição
70|Fornecedor/Doador/Instituição
80|Data de chegada
85|Data de chegada ISO
90|Preço
95|Fornecedor
100|Ordem de compra
110|Número da sugestão
300|Condições
400|Em troca de

```  

O campo 30 (número do inventário) é criado pelo mecanismo de incremento automático do ABCD: o próximo número a ser atribuído é armazenado em um pequeno arquivo 'Control_number.cn' no dobrador de dados do banco de dados (neste caso cópias),Como cada registro deve ser identificado por um valor exclusivo que pode ser usado para vincular os outros bancos de dados (como 'chave primária').

Diferentemente do banco LOANOBJECTS o banco COPIES possui um registro por objeto. Esses registros são normalmente criados pela função 'Adicionar à cópia' do módulo de catalogação. Ou o módulo de aquisições.

Este banco de dados deve ser indexado com 2 chaves obrigatórias:

```
1 0 "CN_"V10,"_"V1,
200 0 "STATUS_"V200^a
```

A primeira chave aqui garante que o identificador de cada cópia possa ser rapidamente referido pelo prefixo 'cn_' seguido pelo nome do banco de dados bibliográfico V10 (porque vários catálogos podem ser combinados em uma cópia-dados) e o identificador nesse catálogo em si (V1).Para que uma entrada no Database de cópias seja permitida para entrar no banco de dados do BomanObjects, ele precisa de tal entrada no arquivo invertido (e assumiu que o campo de status está pelo menos no nível 2, o que significa 'verificado e carimbado', ou seja,Por que o segundo índice de entrada FST no status de cada cópia).

No módulo de catalogação, os registros de cópia serão mostrados em uma janela menor separada ao clicar no ícone 'Adicionar cópia' do registro-toolbar e depois em 'Exibir cópias'.

2. O banco de dados do Loanobjects ABCD

Esse banco de dados tem objetivos diferentes do banco COPIES: seu objetivo é apenas fornecer os dados necessários sobre todos os objetos que podem ser usados no sistema de empréstimos.Seu conteúdo é bastante limitado:

```
1|Número de controle
10|banco de dados
959|Cópias:
i|Número de inventário
l|Biblioteca
b|Biblioteca setorial
o|tipo de objeto
b|volume
t|parte
```

Como pode ser visto a partir desta lista muito curta de campos (de fato apenas 3), cada empréstimo - o objeto é identificado pelo seu Control_Number v1, o banco de dados bibliográfico a ser vinculado ao `V10` e os detalhes reais em cada cópia como uma repetida nos subcampos de `V959` (isto está disponível na tecnologia ISIS com o desempenho mais rápido em caso de alto número de cópias).Os subcampos permitem especificar o identificador exclusivo (por exemplo, código de barras) de cada cópia, a biblioteca principal e a localização nessa biblioteca (por exemplo, informações sobre as prateleiras), o tipo de objeto de empréstimo (livros, por exemplo, terão diferentes parâmetros de empréstimos dos vídeos) e no caso deUm trabalho de vários volumes e identificadores de volume e peça.


O banco de dados BomanObjects deve ser indexado com pelo menos a seguinte instrução:
```
1 0 "CN_"v10,"_"V1
```

Porque (como na base COPIES), a string `'cn_'` seguida pelo nome do catálogo e pelo identificador de catálogo permite que cada cópia seja identificada.Se esta entrada não puder ser encontrada no banco de dados de objeto de empréstimos para um determinado livro, não será possível usar o objeto no sistema de empréstimos.

Os objetos para empréstimos normalmente são criados a partir do módulo de catalogação depois de criar a cópia de inventário conforme os ícones no bar da margem do registro do módulo de catalogação:![](/pt/images/abcddoabcd1_html_c8a1b05a410cd4d2.gif)

Depois de ter clicado em "Adicionar à base de empréstimos" o registro terá sido criado na base de dados "loanobjects". Se esta base de dados deve ser editada diretamente como uma base de dados ABCD, lembre-se de incluí-la na lista de bases de dados (bases.dat, que pode ser acessado diretamente do Sistema Operacional, mas também através do menu “Atualizar definições de base de dados" correspondente do ABCD Central) e no perfil dos usuários que necessitam de acesso a esta base de dados diretamente. Ali os registros de "loanobjects" serão apresentados para navegação e edição em formato de tabela (conforme explicado na seção sobre definição de FDT para campos tipo "grupo").

**![](/pt/images/abcddoabcd1_html_1971839d9ac0f509.png)**

## O módulo básico de empréstimos ABCD
    

### Introdução
    
Esse módulo de empréstimos é chamado de 'básico' porque está totalmente integrado aos outros módulos centrais do ABCD, usando a mesma tecnologia subjacente: ISIS - Bancos de dados, script ISIS e PHP. Olhando para sua funcionalidade, no entanto, dificilmente se poderia chamar isso de 'básico': este módulo toma como ponto de partida que os 'objetos' criados pelo módulo de aquisições no banco de da dos 'cópias', para aplicar regras sobre todos os tipos de 'transações' nelas:emitindo a um usuário, retornando, reserva, renovação de empréstimos.As regras para todos os tipos de transações podem ser definidas e serão aplicadas de acordo com a categoria de objeto em combinação com a categoria do usuário.Categorias para objetos e usuários podem ser definidos 'ad libitum' com número especificado de objetos, horas/dias (levando em consideração um calendário específico para a biblioteca), multas e condições de renovação para cada objeto/usuário combinado.

O menu principal deste módulo de empréstimos tem três seções:

1. Transações: Aqui as verdadeiras transações de empréstimos diários (emprestando um livro a um usuário, devolvendo-o, reservas etc.) são tratados.
2. Bancos de dados: Aqui os bancos de dados nos quais o sistema de empréstimos se baseia podem ser acessados e gerenciados: os mutuários ou usuários, as transações, as reservas e as multas.
3. Configuração do sistema de empréstimos: aqui as 'regras' podem ser definidas para combinações de tipos de objetos com categorias de usuário e calendários, moeda etc. podem ser definidos.
    
    
### Parâmetros de empréstimos gerais e configuração em abcd.def
O arquivo 'abcd.def' (na pasta Bases - do sistema ABCD) contém os parâmetros aplicados a todo o sistema. Alguns deles se relacionam, no entanto, especificamente ao sistema de circulação central do ABCD. Uma breve lista com explicação é dada aqui:
  

Tabela 2.2.Parâmetros de configuração de empréstimos centrais do ABCD em abcd.def

|||
|-|-|
|LOGO_OPAC|URL do logotipo que é exibido na principal solicitação, declaração e reservas on-line|
|BG_WEB|Cor de fundo da janela de solicitação de login|
|WEBRENO- VATION|Y / N Para ativar / desativar a opção de renovação online|
|RESERVATION|Y / N para ativar / desativar o acesso ao processo de reserva dos menus de empréstimo|
|LOAN_POLICY|BY_USER para indicar que o tipo de objeto do item a ser emprestado é solicitado no momento do processamento do empréstimo. Esta opção deve ser usada quando não for fornecida no banco de dados de cópias e o inventário dos objetos não possui um subcampo com o tipo de objeto|
|ASK_LPN|Se a opção de solicitar a data de retorno está ativada, ou seja, não a calcule a partir da política|
|E-MAIL|Y / N Para ativar / desativar o envio de e -mails de lembrete de empréstimos|
|AC_SUSP|Define a data a partir da qual começa uma suspensão. O valor Y indica que deve começar a partir da última suspensão ativa do usuário.O valor N indica que começa a partir do dia em que está registrado.|
|CALENDAR|Para estabelecer a maneira como o período de multas e suspensões é calculado|

Como exemplo, seção dos parâmetros de configuração de empréstimos ABCD.DEF:
```
LOGO_OPAC = ../css/logo_opac.png
BG_WEB = #ffffff
LOAN_POLICY = BY_USER
WEBRENOVATION = N
EMAIL = Y
RESERVATION = N
```
### Configuração detalhada de empréstimos ABCD

A configuração de empréstimo no ABCD permite definir quais bases de dados bibliográficas “fonte” (catálogos) devem ser linkadas ao sistema de empréstimo – pode ser, de fato, qualquer base de dados! – e para definir os parâmetros que constituirão a "política" a ser aplicada a cada combinação objeto/usuário.

  
![](/pt/images/abcddoabcd1_html_80e27d020d7e24dd.gif)  
  

Uma vez que qualquer base de dados pode ser linkada como "fonte" ao sistema de empréstimo, há uma necessidade de explicar ao sistema de empréstimo como os valores a partir destas bases de dados serão utilizados no sistema de empréstimo. Podemos ilustrar melhor isto, dando o exemplo da base de dados CEPAL modelo da aplicação ABCD:
  
![](https://lh6.googleusercontent.com/h7xGmc7cp6O_342sS27bUebhaGIxmi4VKgkcklq-wToV2RPH3Va0u516LtoKGGGW9vrxNnojG4j1wj_FnM6DlrKYH-cef3nxDIqtvJyWH_RWtXYb22d1qIAYQYOhtCSKoYz8Fyir=s0)  

Este formulário apresenta as informações necessárias para o sistema de empréstimo, por exemplo, qual prefixo que é usado no índice para o número de acesso ou quais os formatos de impressão (PFT's) a serem usados para produzir os dados nas telas de empréstimo.
  
A capacidade da Linguagem de Formatação pode ser aplicada aqui, é claro. Por exemplo, ao invés do exemplo simples acima, como a "PFT para ser usado para extrair o tipo de registro", pode-se definir um tipo diferente (consequentemente, com diferentes parâmetros de empréstimo para o tipo) de acordo com algumas condições como, por exemplo, a data, o mês, etc. 

Assim, um objeto que é um objeto de empréstimo normal, pode ser transformado em "material especial" durante o período de provas, etc.

A Linguagem de Formatação ISIS fornece a maioria das funções necessárias (por exemplo, Date() com extração de substring) para este propósito.
O mesmo vale para a definição dos dados de usuários:
![](https://lh5.googleusercontent.com/wLOo5NOPZiHWg8B6Q_CjF0m9mR2RzeXUCLnVsq1tW0ZfAHMdc2fwA78d5O8Ru6jftpDJylLdO3Q9kSUdrbT5QHMkAUWP_OoV_04llaElodP34f2P85W5v-SBU_c6R2IJStUg_hH2=s0)  
  

Em vez de simplesmente apanhar o "valor do campo 10" (v10) para definir o tipo de usuário, pode-se colocar uma declaração de Linguagem de Formatação mais sofisticada aqui, para fazer com que o status do usuário dependa, dinamicamente, de outras condições (novamente: a data, mas também outras condições podem ser definidas). Usando uma tabela ABCD, então, apresentará os tipos de usuários definidos e permite adicionar qualquer número de tais tipos:

  
![](https://lh6.googleusercontent.com/rvBEt9ZoDB4vhrenRG6GVP_Y6qrhT50iL2aEPYiQ6jn08m1lDIZX4wgr651YWZ7VCTx5CRRMietK4pOn70_EqXwuKpWuwkIx8WnGmn5TNQj3POl9vpQpWXb-Nbnu8_hhSNALD7od=s0)  

Aqui vamos mostrar apenas parte da tabela, mas na verdade, a interface oferecerá sempre mais algumas linhas em branco para adicionar mais tipos, e linhas com um tipo também podem ser adicionados entre as linhas existentes. A mesma abordagem é usada para a definição dos tipos de objetos:

  
![](https://lh6.googleusercontent.com/9ZQuOp9pys-PFpi8L6PsUNltDDpNeCybMppbHj7FAwmInaCgk7Uve8lr9W4xv1G0o4YKeGi0RxQX5NJzhUHuT7-_H8EZl7mm5XpT8riELdt3FViKkMPHYkz-1IgtnN5QTW4HRX0T=s0)  

É desnecessário dizer que sempre está previsto um botão "Cancelar" ou "Atualizar” para cancelar a edição da tabela ou para armazená-la novamente.

A partir destes dois tipos (usuários e objetos), ABCD então cria a tabela "política de empréstimos", que lista em uma matriz todas as combinações possíveis de tipos de usuários e tipos de objetos, e os parâmetros podem ser informados para muitos aspectos da política de empréstimos:

Como pode ser observado, muitos dos parâmetros são armazenados e utilizados no processo de tomada de decisão de cada transação (por exemplo, este usuário tem permissão para empréstimo deste tipo de material, quantos do mesmo, por quanto tempo, qual é a multa por atraso de devolução, etc.). As unidades podem ser dias ou horas e o cálculo do "número de dias decorridos" será baseado em uma função do calendário (veja abaixo).![](https://lh3.googleusercontent.com/68czHaXI1MwuSNOueTQ1Hz50sP4MUFXCPzyaXHNHxkj5RNSC6ORJrtAWCwlPaLFpYqUvt4I0keY__bzVRiSRzB3yqgZdknJ0IiSov8_xc17mTndZnW9Mb0poqriCx-RhXGwI6-_U=s0)

Um recurso especial (novo como a partir da v1.5) é permitir que o bibliotecário desvie do parâmetro 'duração' armazenada: no momento de emprestar o número de dias ou a data de retorno pode ser alterada manualmente, tornando-o diferente do prazo oficial calculado de acordo com a política definida. Para isso, um novo parâmetro deve ser adicionado ao arquivo abcd.def:

    ASK_LPN = Y/N.

A configuração do sistema de empréstimos continua com mais duas opções :

- definição da moeda, a unidade de multa, formato de data e dias/horas de trabalho: ![](https://lh4.googleusercontent.com/6beCi6irD2Sl-95UpAmWFP6E3oX0exc4-MVfMYi8w3LfRspcOaJ61E4cZG_C6pq-LjZFQi9_w42A3UG-xAyernChFj4nNQJbQpC-XE4vT3l8IH01rC31KV3g-0vWzD_2Bb5CLWTM=s0)
    
> Cuidado!
> 
> Para que o sistema de empréstimo trabalhe bem, não deixe este "calendário de dias úteis" vazio! 
> Se não são definidas horas ou dias úteis a criação de um registro de empréstimo dará erro, 
> visto que não  pode ser calculada a data de devolução errada.
> - Definição dos feriados no calendário, onde simplesmente os feriados precisam ser indicados no mapa de cada mês:    

![](https://lh6.googleusercontent.com/Mnn3D39lRsOzRc4pYefnVMSjV8Xg7d6yAIuKN7cqWRUR2GAhG8NKlE875jD7DJCnHTvewPZbYKkXASR5Er_YrKs6acSpIb9X-SU-IXgkgLF_RTOrHSi3Nel7C-OUGEBcZaDWJfyc=s0)


- geração de relatórios de empréstimos: para cada base de dados de empréstimo (transações, usuários e suspensões) um conjunto de PFT's (visto que estes são, de fato, os relatórios no ABCD) podem ser gerados, usando a mesma interface usada para outras PFT's (por exemplo, no módulo de Administração de Bases de Dados). Como o procedimento é totalmente idêntico não vamos repetir os passos aqui, por favor, consulte a seção específica no capítulo do módulo Administração de Bases de Dados.
    

  
![](https://lh6.googleusercontent.com/ZbZ4sQHpFvItLVlZFSJLnen4LXmtqY_1UHnpgTPMH5HZZAAE1LjYeGqmWsDU_y3Rs-HoG-tP05AeYF_4TwqPuVoQtYwYnveZQDlddxA4tt4rDCrB8xz0SRR8ujv39ZdGJTPGb2ot=s0)



### Transações: empréstimo, devolução, reserva, renovação, multa/suspensão
    
A maioria das operações em si são bastante fáceis de entender. A eficiência é a chave aqui: em geral o sistema necessita apenas que um ou dois códigos de barras a serem escaneados, e apertando um botão "ir" para gravar a transação. Uma lista de transações possíveis é mostrado no menu de transações do ABCD:

![](https://lh6.googleusercontent.com/6YnR4t80Fo-q_PImJMADjjLBRhvSwuVztD-euVPu8xKn9CUluSkpgZbu4CUs_vsa76xRyU1bNocTynaY9QfLixkAE3dpYUdkEDYdDa0W2ka6gJlfe6Rh-EpNUNzlqSd3wQbdZopq=s0)


Vamos discutir cada uma agora.

### Efetuando empréstimo de um objeto

Esta página oferece caixas de identificação tanto para o objeto como para o usuário, os dois elementos cruciais de qualquer operação de empréstimo (nas quais tanto o código de barras ou de identificação podem ser digitados diretamente ou selecionados a partir de uma lista). 
**![](https://lh5.googleusercontent.com/2fSP_FSboOOmsz4xUSc1Lic4_q2oWHVsi96DlslGybteqcosWYQrBVd_X6eeifoRqgrHG7Inzhw0usASxEpM3YdgwZoay99bKe0yupLlcr964JpjnctEdNf4sifJkjbtTe74bkJl=s0)**

Depois de ter identificado os dois elementos, um simples clique no botão "Emprestar" vai efetivamente criar a transação (na base de dados de empréstimos). As informações do usuário são exibidas e todas as transações de empréstimo relacionadas ao usuário serão listadas em uma tabela, onde uma ou mais transações podem ser selecionadas para edição imediata (por exemplo, devolução ou renovação de empréstimo).

**![](https://lh6.googleusercontent.com/DG-5Au7hLm3P8FkTDwtLddB-9O4lavdXbFC5VT-TmOZp5sjYuTa_ahs6NhC7GvJNmXEZyDviRFKc1PeHars5e2fdH9R0ZfteTTCwNoutFuK7wXLC0YLczI11kAsmpjJvDjtTPYEr=s0)**

### Devolvendo um objeto

Aqui apenas o objeto devolvido deve ser identificado e com um simples clique o registro da transação da base de dados de empréstimos vai notar o fato de que o objeto foi devolvido. O objeto emprestado também pode ser devolvido a partir da tabela em "declaração" do usuário, a transação será removida da tabela.

### Renovando um empréstimo

Esta é uma simples continuação de um empréstimo em execução, mas depende novamente de regras precisas como, se o objeto não foi reservado por outra pessoa e se o usuário que está solicitando a renovação não tem multas pendentes, etc. Quando consultar a lista, apenas os objetos emprestados serão listados. No caso de todas as condições para a renovação serem preenchidas, a transação será concedida e listada, se não uma mensagem de aviso ou erro será mostrada, por exemplo:
**![](https://lh5.googleusercontent.com/dNWC1wNy2xvr5fLMeStDh38yRPprjj19dRzXCNbGO2aca_a0yvZOkGsmT0p0YbLsVyN9zWRaH5Eo8H5bF1XoIJpi6KC-Ofs0xrV4nvgv4YjeA1J-c_XaQbq4WvWA5HxGkLzXsGkb=s0)**

#### Multas e suspensões de usuários
   
Multas e suspensão de usuários são oferecidas na mesma página ABCD:  

![](https://lh5.googleusercontent.com/1J4Vidce2YbB_6jVMmf6wAB-YeamvQH9AHbftJXf3Ofzmz-v8BC-p19SiJCcwnLXK9xbD5XOg_11WesLtwUf0lROIheLG4ZWWzRU31wF2wIqQT7wh1cBSQ91nm_ve8_yZQ1adc9r=s0)

Para o usuário selecionado os seguintes campos podem ser preenchidos: o tipo de sanção (multa ou suspensão), a data, o número de dias ou o montante da multa, o motivo e qualquer comentário.

#### Declaração do usuário
A partir desta tela todas as informações sobre um tomador de empréstimo ou usuário são exibidas, dando também acesso direto a outras funções, onde apenas um acesso a partir do objeto foi dado, por exemplo, permitir a renovação, a partir da identificação do usuário, em vez do objeto.
Interessante notar que os usuários não só podem ser selecionados a partir da lista de usuários, mas também a partir do número de registro/tombo dos objetos emprestados para o usuário.![](https://lh3.googleusercontent.com/P3gCoCY1EOshWnu8CqoEttEP8TRkzcD8WJtMDOoltTeQolpp_nA0m9CR9yLB0_XGcwECixpxrHU4MWXS7F1S_u0Hn3Fz1N21xlVmxoNnUgsBHRPaxPvwbPwYkWR2UZEOooDouS1A=s0)

#### Estado de um item

Assim como acontece com a declaração do usuário, uma visão geral (histórico) de todos os empréstimos desse determinado item ou objeto pode ser recuperado aqui.


### Bases de dados do módulo de Empréstimo
![](https://lh5.googleusercontent.com/VUKJlGTEWKWBRywofBDcrrQvb5DCBlM59Akf1-yNTdUhSNCjDt0y4UVO0SVj2V0js_wNSTU0C7snhq9kM7uGDAPOEVZkmXIay5aYhyot1_zl5u7Z5jHQDoFIZGdgF3J_8pT4sx12=s0)
    
As seguintes bases de dados são usadas no módulo de Empréstimo Central:
  
![](https://lh6.googleusercontent.com/PvShCrOz6KIGdgpDbGO3nzwBxaGICizAb9MfG2o0cySUvNPQdmKVA64nVBzBbt2_goOGTchRTDk4iYJfLthjSuTNVwBSjQ_fwLBqpTYRoAUf2XK2own5jNW_MzEiJv8eJjVRYnsv=s0)  

Para cada uma dessas bases, cujos nomes explicam sua finalidade, é apresentada uma interface que lista os registros com uma função de pesquisa e botões de Editar ou Excluir.

A base de dados de transações registra os eventos atuais do sistema de empréstimo. ABCD opta por manter esta base de dados tão "magra" (compacta, p.e.) quanto possível, sem duplicação de dados, como, por exemplo, as bases de dados bibliográficas. Esta base de dados será um pouco "dinâmica" com muitos movimentos, e visto que tal ambiente não é o melhor para o ISIS (para o qual tabelas simples, com estruturas fixas, seriam mais adequadas) é preciso manter a sua estrutura tão compacta quanto possível, usando a função REF do ISIS para dados de "empréstimo" de outras bases de dados, por exemplo, os dados bibliográficos.

Então, isso permitirá ao bibliotecário interagir diretamente com os registros dos usuários (por exemplo, criar novos usuários da biblioteca), as transações (por exemplo, para verificar um registro de empréstimo), reservas e suspensões ou multas. Nesta última base de dados o bibliotecário poderia interferir com multas por atraso e suspensões de usuários em caso de necessidade de fazê-lo ignorando as regras - tome cuidado!



### Administração de Empréstimo
   
Esta terceira e última seção sobre o módulo de empréstimo não só oferece a opção de configuração de empréstimos (discutidos acima), mas também dá acesso ao módulo de Estatísticas (que também é discutido em outra parte deste manual) e a opção "Relatórios", que será acrescentada em uma versão mais recente do software ABCD. Este módulo irá criar todos os tipos de documentos de saída, por exemplo, alertas, confirmações de empréstimos, etc.


![](https://lh5.googleusercontent.com/vfnqTJnSEqf6trRYHyyP3Euk7Bc0hdkZvyiq5yhCngDGvYQ7Lp2ugtBmYPgxv_S2bZW9idEQlEr9AUqvD-GiW8BW1tRxmhCBd7GMhyPYmhpuWS1buSMsaBU4LpQjvH1Uy97so9oX=s0)

  

## O módulo avançado de empréstimo 

O módulo de empréstimo avançado do ABCD é um módulo "add-on"  que pode ser instalado como um membro independente da "Suíte ABCD". Ele exige tecnologia de software adicional para ser instalado (por exemplo, JAVA, MySQL)  e também pode ser utilizado como um software independente. Visto que este módulo foi originalmente programado como um software DOS, denominado "Emp" (de "Empréstimo" em português, o módulo é chamado de "EmpWeb", já que no ABCD foi convertido em um Software Web, utilizando novas tecnologias Web, como "Web Services". Então, nós consideramos o "EmpWeb" como um"Módulo Extra ou "aumentado", talvez mudando "ABCD" para "ABCDE"!

As funcionalidades extras em relação ao módulo de empréstimo integrado são:
- melhor capacidade para lidar com estruturas organizacionais complexas  (por exemplo, bibliotecas multi-filiais/setoriais com políticas de empréstimos diferentes, diferentes servidores);
- tratamento mais robusto com situações de transações de grande volume;
- maior interação com os usuários a partir do módulo OPAC, por exemplo, a função "MySite" para permitir que usuários logados possam manter controle do seu próprio status, etc. a partir do OPAC;
- uma função "MySite" permite que usuários finais registrados possam (após se logarem no site) entrar em seu próprio espaço no sistema de empréstimo para verificar o seu status como um usuário da biblioteca e outros usuários interativos. Esta função, neste momento, ainda não está disponível no módulo Central de Empréstimo;
Alguns conceitos importantes de EmpWeb são resumidamente apresentados aqui:
- web-services: em vez de necessitar de acesso completo aos recursos externos (bases de dados), o que pode, em alguns casos, criar problemas com os provedores de dados, os "pedidos" (requests) baseados na web são enviados ao servidor apenas para entregar – como resposta ao pedido – alguns dados específicos.
- pipelines: qualquer transação (como um empréstimo, uma reserva, uma devolução) passa por condições de pipeline que podem ser definidas. Somente se todas as condições estiverem reunidas no pipeline, a transação será "permitida", se não simplesmente pára e retorna a mensagem de erro definida (pelo software) ou a instrução (por exemplo: "Usuário foi suspenso"). Isso permite que qualquer número de condições e regras seja aplicado a qualquer decisão tomada pelo software.
EmpWeb, portanto, pode ser executado em qualquer conjunto de dados externos para os quais drivers estão disponíveis ou podem ser acessados por "Web Services" e aplicar um conjunto de regras para estes dados e executar processos (como alterar um registro) em caso de ter conseguido passar por todas as regras e condições. EmpWeb, desta forma, é mais um motor transacional genérico, mas utilizado como um sistema de empréstimo no ABCD.

  **![](https://lh5.googleusercontent.com/_K5Avz3PD4Pl_OG63mU5JEWnctpdBKIQ-qrvcmuIqRjwOU_Q58ViR1RgulNfC96nvoEW9iyMoHB2IRMYKlEpL6y0Q8AOWDEi0GVy8BwtJFmRMZkKHj3Rok6u2prokAIMPZejYjYX=s0)**

> Este módulo avançado empréstimo é discutido em detalhe em um manual separado.
