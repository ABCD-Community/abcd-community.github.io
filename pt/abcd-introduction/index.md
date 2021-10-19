---
title: Introdução - informações básicas  
description: Introdução geral ao ABCD como um conjunto de software  
lang: pt  
lang-ref: abcd-introduction
---

# Introdução: informações básicas

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Introdução geral ao ABCD como um conjunto de software

ABCD é a sigla para um conjunto de software para a automação de bibliotecas e centros de documentação. Em espanhol esta é, na íntegra: 'Automatisación de Bibliotécas y Centros de Documentación', que mantém a mesma sigla válida também para o francês (Automation des Bibliothèques et Centres de Documentacion) ou português (Automatização das Bibliotecas e dos Centros de Documentação). Mesmo em outras línguas não latinas, com algumas variações leves mas bastante aceitáveis, - por exemplo, holandês: 'Automatisering van Bibliotheken en Centra voor Documentatie' - o acrônimo ainda pode ser mantido.

O próprio nome já expressa a ambição da suíte de software: não apenas fornecer funções de automação para as bibliotecas 'clássicas', mas também outros fornecedores de informação, tais como centros de documentação. A flexibilidade e a versatilidade estão na vanguarda dos critérios sobre os quais o software é desenvolvido. Esta flexibilidade, por exemplo, é ilustrada pelo fato de que em princípio, mas também na prática, qualquer estrutura bibliográfica pode ser gerenciada pelo software, ou mesmo criada por ele mesmo. Mesmo estruturas não-bibliográficas podem ser criadas, desde que as informações sejam principalmente informações 'textuais', pois esta é a limitação colocada pela tecnologia de banco de dados subjacente, que é o banco de dados textuais (CDS/)ISIS. O bom entendimento de alguns conceitos e técnicas básicas relacionadas ao ISIS, por exemplo, a linguagem de formatação, é crucial para o pleno domínio do ABCD-software. Por este motivo, algumas seções deste Manual também tratarão da tecnologia ISIS subjacente.

O ABCD é chamado de 'suite' de softwares para automação de bibliotecas e centros de documentação porque existe de alguns módulos relativamente independentes, que podem cooperar plenamente, mas também podem existir uns sem os outros. De fato, alguns softwares avançados existentes, a maioria já tendo demonstrado seu potencial em ambientes exigentes nas aplicações da BIREME (dentro do contexto da Biblioteca Virtual em Saúde), foram adotados e adaptados no ABCD - é por isso que os nomes originais como iAH, SeCS (ambos desenvolvidos pela BIREME) e EmpWeb (Empréstimos en Web) desenvolvidos originalmente por KALIO ltda. do Uruguai e amplamente testados em Valparaiso na Universidade) são mantidos. Estas partes principais são mostradas, com suas relações hierárquicas, no segundo nível na figura a seguir e posteriormente discutidas brevemente :

![Slide2](https://user-images.githubusercontent.com/20482054/137317710-09934ef8-971e-499b-ac63-0cb54f7677c2.JPG)


### a ABCD Central

O módulo 'Central' do ABCD compreende módulos para Administração de Bancos de Dados (criação de bancos de dados, edição de estruturas de bancos de dados, utilitários de bancos de dados), Catalogação, Aquisições, Circulação/Empréstimos e Estatística. Um módulo de administração de tesauro também está sendo preparado como parte do módulo de catalogação para uma base de dados específica da estrutura saurus com controle de consistência dos níveis hierárquicos. Como parte deste 'módulo central' também gostaríamos de mencionar serviços de importação e exportação, impressão e ferramentas de banco de dados como bloqueio/desbloqueio e 'mudanças globais' de campos em registros. Esta parte 'Central' de fato representa a parte 'back-office' do ABCD, os usuários finais não serão confrontados com isto, mas o que eles verão e serão oferecidos está totalmente definido nesta parte central de gerenciamento do software!

Qualquer estrutura de base de dados ISIS pode ser definida e gerenciada, com registros atualmente de 1Mb de tamanho máximo e 4Gb máximo, bancos de dados (mas estas restrições serão tornadas obsoletas pela próxima geração de ISIS e ABCD baseada no NBP). Em comparação com a tecnologia ISIS 'normal', são usadas chaves de indexação de 60 caracteres (em comparação com 30 caracteres), há recursos de controle de autoridade muito mais fortes disponíveis (listas de seleção baseadas em tabelas ou bancos de dados de autoridade, tais como thesauri) no estágio de entrada de dados com formatos de validação flexíveis) e toda a interação é baseada na tecnologia WWW, naturalmente, permitindo, por exemplo, cadeias de texto codificadas em HTML para indexação de texto completo, hiperlinks para páginas de ajuda, etc.

É perfeitamente possível automatizar completamente uma biblioteca menor com a maioria dos usuários internos com todas as funções necessárias, utilizando apenas esta parte Central, pois, por exemplo, uma opção de busca avançada é incorporada, de modo que todas as funções sejam cobertas com um mínimo de complexidade tecnológica (ou seja, apenas ISIS e PHP).

### o ABCD OPAC (iAH)

A interface de busca pública (OPAC) é uma versão adaptada da 'interface avançada para informações de saúde' (iAH) geral da BIREME. Ela permite metabuscas não apenas nos catálogos locais, mas também em muitos outros recursos de informação.

A interface iAH desenvolvida pela BIREME está sendo atualizada para o iAHx, garantindo o alinhamento perfeito com os modernos conceitos e técnicas de recuperação de informações (por exemplo, agrupamento, classificação de relevância com base na indexação Lucene).

### O site do ABCD

A função de busca é oferecida como parte de uma página de portal de 'usuários finais', apresentando o(s) próprio(s) catálogo(s) num contexto de informação muito mais amplo, fornecendo acesso a outros recursos de informação (por exemplo, Google, Medline...) e comunicação (anúncios, alertas), abrindo também o caminho para funções semelhantes à 'Web 2.0'.

O Administrador do Site na verdade é um Sistema de Gerenciamento de Conteúdo específico que permite projetar a estrutura e os componentes da página do portal do ABCD.

### o Sistema de Controle de Séries ABCD (SeCS)

Este módulo oferece uma ferramenta de gerenciamento avançada para publicações em série (clássicas e/ou eletrônicas) de qualquer tipo de publicação pub (referente à periodicidade). Séries como tais, mas também edições de uma série e todos os tipos de padrões de publicação podem ser gerenciados por este módulo. A BIREME utiliza esta tecnologia, por exemplo, para seus produtos 'Portal de Periódicos Científicos' (ver : [http://portal.revistas.bvs.br/main.php?home=true&lang=en)](http://portal.revistas.bvs.br/main.php?home=true&lang=en)) e SCAD (ver : http://scad.bvs.br/php/index.php?lang=en) que é o catálogo do sindicato brasileiro de mais de 12.000 periódicos (com milhões de edições) de mais de 50 bibliotecas.

### o módulo de Empréstimos Avançados ABCD (EmpWeb)

Este módulo oferece gerenciamento avançado de empréstimos com mais algumas características extras para organizações maiores e mais complexas. Ele oferece uma função 'MyLibrary' aos usuários finais através do OPAC e é baseado na tecnologia 'web-services'. Ele pode ser usado para substituir o módulo integrado de empréstimos do ABCD em caso de necessidade de lidar com situações de múltiplas filiais/políticas e de volume de transações muito alto.

A idéia da 'suíte' reflete o fato de que o ABCD tem partes relativamente independentes - como é o caso das suítes de automação de escritório (por exemplo, Open Office, Microsoft Office) - mas com vínculos óbvios para cooperar. O módulo Estatísticas, por exemplo, como parte do módulo Circulação/Empréstimo, pode funcionar em qualquer base de dados ISIS, enquanto o iAH-OPAC também pode oferecer recuperação avançada baseada na web em qualquer (conjunto de) bases de dados ISIS, não apenas as mantidas pelo ABCD. O Sistema de Controle de Séries (SeCS) gerencia as bases de dados ISIS para séries dentro ou fora do contexto do ABCD. Mas juntos, acreditamos, estas partes constituem um conjunto muito poderoso de ferramentas, e como parte integrada esperamos que "a soma seja mais do que apenas as partes somadas"!

## A família de software ISIS (história e visão geral)

Neste parágrafo queremos apresentar brevemente a "família de software ISIS" mais ampla à qual a ABCD pertence. Como em todas as 'famílias', os membros compartilham muitas características, mas não todas.

As características comuns da família ISIS relacionam-se com a forma como a informação (de natureza textual) é armazenada e gerenciada, colocando-a em campos repetíveis de comprimento variável com a possibilidade de subdividir os campos em subcampos. Os campos são na verdade casais de um ID de campo (uma 'tag') combinado com um valor de campo (um texto, ou na nova geração ISIS, qualquer objeto, como por exemplo 'objetos grandes binários' ou blobs).

Além das características tecnológicas comuns, a maioria dos membros da família ISIS, se não todos, também compartilham características 'sociais', como por exemplo

*   sendo principalmente utilizados em países em desenvolvimento ou 'o Sul', com uma presença muito forte na América Latina, mas também - mais do que pode ser 'medido' em todos os tipos de centros de informação pequenos, muitas vezes privados de conexão (sem Internet) na África e na Ásia.
*   sendo promovidos por muitos membros e projetos das Nações Unidas, naturalmente em primeiro lugar nos ambientes da UNESCO, mas - como mostra o exemplo da BIREME - também da OMS e da FAO (os sistemas AGRIS e ASFISIS da FAO podem ser dados como exemplos aqui, mas também a origem do sistema de biblioteca WEBLIS). Os programas IFAP e "Sociedade do Conhecimento" das Nações Unidas não devem subestimar o impacto real das ferramentas de informação promovidas pela UNES- CO como ISIS, IDAMS, Greenstone etc. - às vezes até mesmo indicando que o impacto pode ser o contrário de uma dada contribuição financeira ou publicidade.

A ilustração a seguir resume a família completa até o momento.

![](https://user-images.githubusercontent.com/20482054/137317546-bc0995fe-fd92-40c8-aefc-9c69d7e12103.JPG)

Pode-se resumir a história afirmando que a "família" tem agora 4 gerações enquanto a 5ª geração está sendo preparada:

*   A primeira geração : CDS/ISIS e Micro-ISISIS
*   A segunda geração : interfaces ISIS/Pascal enriquecidas, ferramentas CISIS
*   A terceira geração : gráfica, multimídia e multi-base de dados : WinISIS, ISISDLL
*   A quarta geração : Versões para a WWW (wwwisis, isis3w, openisisis...) .

Em vista de algumas grandes mudanças tecnológicas introduzidas na mais nova geração a partir de 2008, talvez se deva considerar os mais novos membros do ISIS (J-ISISIS e ISIS/NBP) como representando mais uma nova 5ª geração.

Alguns destaques de cada geração são dados abaixo.

#### 1975 - A primeira geração

CDS/ISIS no Sistema de Documentação Centralizado da Organização Internacional do Trabalho (OIT) fundiu-se com o Conjunto Integrado de Serviços de Informação que funciona no VAX OS em mainframes

#### 1985 - A segunda geração

Micro-ISIS G. Del Bigio se une à UNESCO e cria uma versão baseada em PC-DOS e integra funções separadas em uma interface geral personalizável e multilíngüe baseada em menus com documentação completa como versão 2.3 Versão 3.0 - 3.8 : multiusuário em rede, ISIS/Pascal UNIX-versão para o UNIX OS baseado em Intel Versão mundial de distri- buição e enorme sucesso nos países em desenvolvimento


*   Os add-ons programados ISIS/Pascal (ex. Heurisko, ADEM, IRIS e ODIN, LAMP) criam ferramentas ricas; ex. IR- BIS (Rússia) para bibliotecas, FAO usa ISIS para seu sistema AGRIS e extensões ODIN/IRIS para seu sistema ASFISIS-
*   Bireme/OPS (WHO Brasil) cria o conjunto de ferramentas CISIS para gerenciamento de banco de dados de linha de comando, utiliza-o para seus enormes bancos de dados de informações sobre saúde na Internet; estes são multiplataforma (executados em Unix/Linux e DOS)

#### 1995 - A terceira geração

*   A UNESCO produz a versão Windows : WinISIS, com muitos gráficos, multi-media e fea- tures multi-database de dados
    *   Sistemas completos de automação de bibliotecas podem ser e são desenvolvidos, por exemplo, PURNA (Índia)
    *   outras bibliotecas começam a utilizar o ISIS para automação completa da biblioteca, por exemplo, a SNAL (Tanzânia) utiliza o sistema de biblioteca em rede ODIN/IRIS para sua biblioteca universitária
    *   A Bireme distribui uma versão web-server do ISIS como 'wwwisis' rodando tanto no DOS/Windows quanto no UNIX/ Linux; muitas aplicações são desenvolvidas JavaISIS (Itália) e isis3w (Polônia) adicionadas à família

#### 2005 - A quarta geração

*   Ferramentas avançadas baseadas na web lideram novos desenvolvimentos : GenISIS (França) permite a fácil criação de interfaces de busca baseadas na web
*   WEBLIS (Polônia/FAO) é um sistema avançado e completo de automação de bibliotecas baseado na web
*   Bireme desenvolve WXIS e adiciona XML ao ISIS
*   Os sistemas de biblioteca baseados em WXIS são desenvolvidos na América Latina (por exemplo, OpenMarcoPolo)
*   OpenISIS (Alemanha) cria a primeira versão totalmente Open Source (webserver, PHP-library) mas segue seu próprio caminho (Malete, Selene)

#### 2008 - A quinta geração

*   A UNESCO desenvolve uma interface gráfica completamente nova baseada em Java 'J-ISIS' usando não apenas o JAVA-technol- ogy, mas também o Berkeley DB embutido para a camada de armazenamento. Este projeto é um projeto totalmente orientado para FOSS.
*   BIREME desenvolve ABCD e - ao mesmo tempo - uma tecnologia totalmente nova para seus futuros produtos ISIS : ISIS/NBP. O ABCD deve ser a primeira aplicação a ser migrada para NBP.

NBP ou 'Network Based Platform' é a nova tecnologia ISIS que tem como principais características :

Arquitetura flexível na qual as 'células ISIS' se comunicarão através de protocolos conhecidos com várias formas e interfaces de placa; as células ISIS também permitirão a utilização de diferentes modelos de armazenamento, pois estes estarão contidos dentro das células, mas se comportarão da mesma forma padronizada em relação à tecnologia externa utilizada;

Os bancos de dados ISIS não terão mais limitações desatualizadas em relação aos tamanhos de banco de dados, registros e campos;

Os bancos de dados ISIS serão compatíveis com UNICODE.

A indexação será feita usando outros indexadores de texto completo FOSS, como Lucene (da Apache Software Foundation).

ISIS está sendo usado por dez mil usuários, a maioria nos países em desenvolvimento onde é promovido pela UNES- CO e BIREME (para a maioria da América Latina). Na América Latina, ISIS está fortemente representado em bibliotecas e centros de documentação (tem uma posição 'dominante' mesmo aqui), na África e no Sudeste Asiático há um número desconhecido, mas alto de usuários, muitos deles freqüentemente sem conexão com a Internet e, portanto, ainda usando tecnologia mais antiga - a nologia e com habilidades relativamente pobres em TIC. Isto cria um desafio especial para o apoio da comunidade de usuários.

No 3º Congresso Mundial sobre ISIS (Rio de Janeiro, Brasil, setembro de 2008) a Comunidade de Usuários decidiu tornar ISIS totalmente 'FOSS' e coordenada por um 'Comitê de Coordenação Internacional sobre ISIS' (ICCI), ver : [http://www.unesco.org/new/en/member-states/single-view/news/3rd_world_congress_on_isis_to_focus_on_latest_developments_o/](http://www.unesco.org/new/en/member-states/single-view/news/3rd_world_congress_on_isis_to_focus_on_latest_developments_o/)

Resumindo a longa história do ISIS, pode-se dizer que o ISIS combina princípios básicos de 'banco de dados textuais' muito sólidos, uma forte tradição e uma comunidade de usuários mundial mas insuficientemente coordenada com o desenvolvimento tecnológico ainda moderno de última geração.

## De 'livre' a 'FOSS'.

> Dica:  
> Você pode estar interessado em ler o artigo completo sobre este tópico, publicado em: 'Innovation', no. 36 June 2008, p. 39-47.  
> CDS/ISIS como um software tem sido 'livre' e 'aberto' desde seus primeiros dias, muito antes do 'FOSS' (Free and Open Source Software) se tornar um modelo conhecido de software (ou deveria ser colocado no sentido inverso : muito antes do 'software comercial fechado' se tornar amplamente praticado' ).

### ISIS como software 'aberto'.

Considerando que ISIS, a partir da versão DOS produzida e distribuída pela UNESCO desde 1985, sempre foi "livre".

*   ou seja, sem custo, mas com restrição apenas aos setores sem fins lucrativos - o software não era 'aberto' no sentido estrito do conceito como hoje em dia conhecido como 'Open Source Software' com suas diferentes definições (ver [http://www.opensource.org/docs/osd](http://www.opensource.org/docs/osd)) e licenças (por exemplo, (L)GPL, BSD, Creative Commons...).

Mas em 3 significados já existiam, desde este início - e portanto muito antes do movimento FOSS começar a se tornar realmente visível -, elementos de estar 'aberto' além de ser livre(mercadoria) :

1.  as normas eram abertas e publicadas. No 'Manual de Referência CDS/ISISIS', escrito por seu pai fundador Gi- anpaolo Del Bigio (trabalhando para a OIT então UNESCO), os detalhes técnicos foram publicados nos anexos, permitindo que outros programassem suas próprias versões de ISIS usando as mesmas normas compatíveis. Por exemplo, na Eslováquia, Marek Smihla tinha programado executáveis (por exemplo, ADEM para entrada de dados) que funcionavam independentemente dos executáveis ISIS da UNESCO e podiam escrever e ler os registros ISIS. A Bireme em São Paulo, Brasil, fez algo semelhante: eles pro-programaram ferramentas de escrita, leitura e indexação com muitas características avançadas (por exemplo, unindo bancos de dados, ligando-os como relações etc...) no idioma C (portanto CISIS) que ainda são a base para seus outros softwares relacionados ao ISIS: a DLL e os servidores web (WWWISIS, WXIS) e que agora têm capacidade expandida, por exemplo, 4 Gb tamanho máximo do banco de dados, 1 Mb tamanho de registro, 60 chaves de índice de caracteres. A cooperação foi então estabelecida com a UNESCO, por exemplo, permitindo que o 'CDS/ISISIS for Windows' se tornasse uma mistura de módulos programados pela UNESCO e pela Bireme.

uma interface aberta e ajustável: o software em si foi apresentado como um ambiente muito flexível, com três características principais que foram utilizadas em todo o mundo não apenas para mudar sua 'interface', mas também as funções e características.

Uma estrutura de menu aberta: o Micro-CDS/ISIS foi totalmente baseado em menus que podiam ser produzidos e alterados usando o próprio software, incluindo a definição de 'ações' a serem invocadas por cada opção de menu e permitindo sub-menus hierárquicos, bem como opções de queda/adicionamento.

Um sistema de mensagens aberto: todas as mensagens eram/são baseadas em pequenas bases de dados ISIS que podem ser editadas (cada idioma tem sua própria base de dados de mensagens) e expandidas. Isto não só permitiu (muitas vezes junto com a característica anterior de menu aberto) a criação de conformações bastante diferentes do software - levando em conta também as cores e as características da tela que poderiam ser alteradas - mas também a expansão e introdução de parâmetros (que poderiam então ser 'lidos' como mensagens) para software adicional executado dentro do ISIS (veja mais adiante: add-ons ISIS/Pascal), como amplamente utilizado, por exemplo, pela interface de catalogação 'ODIN' e OPAC 'IRIS' (pelo autor deste artigo).

Uma ferramenta de programação 'ISIS/Pascal' que atuava como uma 'API' (com chamadas publicadas para funções e seus para-metros) dentro do CDS/ISISIS. Os programas ISIS/Pascal, variando de algumas linhas a milhares de linhas para aplicações sofisticadas, poderiam ser incluídos no programa como 'saídas de formato' (para expandir as funções da já muito rica linguagem de formatação) ou como 'saídas de menu' para expandir as funções dos menus, permitindo interfaces quase independentes para 'assumir' o ambiente CDS/ISISIS na criação e manipulação de seus bancos de dados. Uma característica que ilustra a 'abertura' foi a possibilidade de adicionar um parâmetro no arquivo de inicialização 'SYSPAR.PAR' para invocar automaticamente um menu e sua opção, permitindo assim que a interface de menu seja pulada e apresente imediatamente a nova interface ISIS/Pascal. Desta forma, foram escritos módulos OPAC completos (por exemplo, IRIS usando uma tela de boas-vindas que poderia ser invocada por um mecanismo de time-out após uma sessão anterior ter sido deixada) e módulos de busca em CD-ROM (HEURISKO é um exemplo), foram produzidos sistemas de empréstimo para bibliotecas e ferramentas de gerenciamento de thesaurus.

Por último, mas não menos importante: o 'caráter aberto' da linguagem de formatação. A Linguagem de Formatação é uma gramática usada para definir de forma detalhada como os elementos do banco de dados, retirados de campos e subcampos repetíveis, também de outros registros no mesmo ou em outros bancos de dados (portanto, assemelhando-se a abordagens relacionais) e com links de navegação, serão 'processados' em alguma saída (para exibição, classificação, impressão, exportação). Foi amplamente expandido com recursos gráficos na versão Windows (RichText, mas também imagens e caixas de texto e imagem extras). Juntas, estas fortes características de 'processamento de dados' e 'apresentação' da linguagem de formatação permitiram a produção de 'identidades' bastante novas do software, por exemplo, como um software de Gerenciamento de Biblioteca com OPAC e Sistema de Empréstimos (por exemplo, PURNA da Índia). Em aplicações atuais, baseadas na tecnologia web, a Linguagem de Formatação ainda é graciosamente utilizada para produzir elementos HTML (por exemplo, links, mas também tabelas), mesmo que ferramentas mais dedicadas para isso, por exemplo, PHP, sejam agora adicionadas ao poder da própria Linguagem de Formatação ISIS.

### ISIS como software de código aberto completo

Já em 2001 a UNESCO decidiu embarcar nesta abordagem relativamente nova de não apenas fornecer o software gratuitamente, mas também tornar os códigos fonte em princípio 'abertos', ou seja, disponíveis ao público (ver : [http://portal.unesco.org/ci/en/](http://portal.unesco.org/ci/en/) ev.php-URL\_ID=13803&URL\_DO=DO\_TOPIC&URL\_SECTION=201.html). Isto finalmente levou a um trabalho de enquadramento de sua abordagem mais ampla de 'Free and Open Source Portal', promovendo a idéia e adicionando outros softwares, por exemplo Greenstone, em sua 'cesta' de softwares apoiados e promovidos para melhor desenvolvimento profissional também nos países do Sul e em transição. O Portal FOSS da UNESCO pode ser encontrado em : http://www.unesco.org/cgi-bin/webworld/portal_freesoftware/cgi/page.cgi?d=1](http://www.unesco.org/cgi-bin/webworld/portal_freesoftware/cgi/page.cgi?d=1), com links interessantes para discussões sobre a história do FOSS, li- censos e estudos de caso. Na realidade, porém, os códigos fonte dos softwares ISIS existentes devem ser solicitados à UNESCO, mas os novos softwares estarão totalmente disponíveis em sites públicos.

Na Bireme/OPS/WHO, uma decisão semelhante foi tomada em 2006/7. O instituto não cobraria mais uma pequena taxa por seu software (como era o caso antes, por exemplo, 150 USD para registro oficial como usuário com direitos de suporte) e, portanto, o tornaria "gratuito", mas também as fontes foram e estão sendo preparadas para a publicação de todos os seus softwares, incluindo os módulos básicos do CISIS. Seu novo software de geração ISIS, chamado 'ISIS-NBP' (Network Based Platform) seguirá os métodos FOSS (incluindo uma 'comunidade' com possibilidades de contribuir, discutir e baixar fontes na URL http://reddes.bireme.br) para mostrar seu firme compromisso com o FOSS. Como a mais nova aplicação completa, o ABCD será totalmente publicado como código aberto, mesmo que o desenvolvimento original ainda seja gerenciado centralmente pela Bireme e seus próprios programadores, já que o projeto agora também é apoiado pelo Conselho Interuniversitário Flamengo (VLIR) com requisitos específicos para apresentá-lo como um concorrente completo de outros sistemas de bibliotecas (incluindo outros softwares FOSS como KOHA e NewGenLib) e, para este fim, necessita de mais algum controle central para propósitos específicos.

A vantagem de se tornar totalmente aberto - para todos os softwares - reside no fato de que os usuários, certamente (programando) qualificados, podem verificar completamente os mecanismos internos e propor/executar mudanças, se assim o desejarem. Um exemplo: WinISIS tem uma forma ligeiramente diferente de classificar os valores tomados pela função 'VAL' (isto é, remover primeiro o padding 0's) que não é um bug como tal e, portanto, não 'precisa' ser corrigido pelo fornecedor do software; com acesso aos códigos-fonte, no entanto, pode-se mudar isso.

Como sempre acontece com o software de código aberto, seria melhor não fazer tais mudanças sem consultar/informar a comunidade de 'desenvolvedores'.

## Objetivos do ABCD

O ABCD visa fornecer uma ferramenta integrada de gerenciamento de biblioteca que cobre todas as principais funções de uma biblioteca, ou seja, aquisições, gerenciamento de bancos de dados bibliográficos, gerenciamento de usuários, gerenciamento de empréstimos, controle de séries, busca de usuários finais em bancos de dados bibliográficos locais e externos e portal da biblioteca.

não é a primeira vez na história e no ambiente ISIS que tal esforço foi empreendido. MarcoPolo aberto, Clabel e - como um esforço mais avançado - o WEBLIS são predecessores do ABCD neste sentido.

#### ABCD como uma ferramenta bibliográfica genérica e flexível

Como o próprio nome sugere, a ABCD, entretanto, não visa apenas fornecer uma solução para bibliotecas, mas também para centros de documentação e documentação. Estas tipicamente têm necessidades ligeiramente diferentes, por exemplo, têm coleções mais especializadas, maiores necessidades de divulgação de conteúdo (por exemplo, fornecendo resumos, usando thesauri etc.) e exigem maior flexibilidade nas estruturas bibliográficas. Por este motivo, o ABCD não só tentou incluir recursos de texto completo, mas foi concebido principalmente para oferecer uma solução muito aberta, permitindo que qualquer estrutura de campos seja criada e mantida dentro do mesmo software. Pela própria tecnologia de banco de dados do ISIS, que é bastante flexível e não restritiva, estruturas bibliográficas podem ser criadas sem a necessidade de 'normalizar' todos os elementos em uma série de tabelas ou relações (como é o caso da tecnologia de banco de dados relacional) e na maioria dos casos todos os elementos bibliográficos podem ser contidos em um único banco de dados - apenas para fins de otimização o ISIS esperaria que algumas abordagens semi-relacionais fossem implementadas.

Como sistema de biblioteca, porém, o ABCD vem pré-configurado para alguns padrões bibliográficos importantes, ou seja, MARC21, CEPAL e AGRIS. Mas repetimos: os mesmos mecanismos, interface e formulários podem ser usados para criar e manter qualquer estrutura, seja ela bibliográfica ou não.

Assim, para colocar os objetivos um pouco mais precisos : o ABCD visa fornecer uma ferramenta muito genérica/generalizável para o gerenciamento de bibliotecas e centros de documentação.

#### ABCD como uma ferramenta orientada para bibliotecários

Outro objetivo específico do ABCD é oferecer uma ferramenta para bibliotecários, em vez de técnicos de TIC. Isto é conseguido tomando como ponto de partida os princípios da biblioteca e da ciência da informação (ao invés de princípios de informática ou programação), mesmo na concepção dos próprios bancos de dados. Tipicamente um registro bibliográfico é uma entidade real em um banco de dados ISIS, não uma série complicada de elementos 'consultados' ou 'unidos' a partir de muitas tabelas (como em sistemas relacionais), porém preservando critérios como eficiência (no uso do espaço, velocidade de operação...). Cada entidade pode posteriormente ser "moldada" completamente pelos próprios bibliotecários com o uso da linguagem de formatação ISIS (FL), que permite lidar com todos os elementos de uma entidade (por exemplo, um substrato de um subcampo de uma ocorrência de um campo específico em nível de micro-detalhe) sem programação real - mesmo que o FL permita algum grau de lógica de programação como loops e condições aninhadas - para a criação de qualquer formato de saída. Esta saída pode ser qualquer coisa como uma chave de ordenação, uma chave de indexação, um formato de tela ou - como é o caso, por exemplo, ABCD - dados ISIS incorporados em páginas web ou qualquer outra gramática, como XML. Muitas experiências de ensino com ISIS mostram que os bibliotecários são perfeitamente capazes de entender e usar tudo isso, alcançando resultados avançados sem nenhuma programação real.

#### ABCD como uma ferramenta para países em desenvolvimento

A ABCD visa fornecer aos bibliotecários e trabalhadores da informação nos países em desenvolvimento uma ferramenta muito poderosa, que leva em conta algumas realidades específicas, tais como :

baixa disponibilidade de habilidades em TIC: como em soluções anteriores baseadas em ISIS, os bibliotecários estão - em princípio - capacitados a resolver seus problemas evitando arquiteturas de software desnecessárias enquanto ainda permitem flexibilidade dentro do software (por exemplo, através da linguagem de formatação);

baixa disponibilidade de largura de banda e conectividade : usando modernas tecnologias web como AJAX e JavaScript, o tráfego de dados entre cliente e servidor é mantido mínimo, permitindo que o computador local (no 'lado do cliente') processe os dados o máximo possível sem sempre se referir ao servidor; também o projeto gráfico é mantido bastante sóbrio pelo mesmo motivo.

## Atores e parceiros da ABCD

O ABCD, como todos os grandes projetos de software, é um esforço de conglomerado de vários atores e parceiros. Na seguinte URL é mantida uma lista dos principais atores e parceiros : [http://reddes.bvsaude.org/projects/abcd/wiki/HallFame?version=20](http://reddes.bvsaude.org/projects/abcd/wiki/HallFame?version=20)

A principal contribuição, obviamente, vem do instituto brasileiro BIREME (ver http://www.bireme.br), que utilizou toda sua tecnologia baseada no ISIS para ser combinada em um produto "culminar" que é de fato o ABCD. De fato, a idéia original deriva de seu diretor atual, o Sr. Abel Packer, que generosamente aproveitou também o tempo de trabalho de seus programadores e gerentes de software.

Uma menção especial é certamente apropriada para a Sra. Guilda Ascencio, Venezuela, que foi a programadora principal da parte central do ABCD com seus módulos, baseada em seu próprio software 'Orbital Documental', no qual ela provou que aplicações muito avançadas, combinando biblioteca e outras questões de gerenciamento de documentação, poderiam ser construídas usando ISIS e tecnologia web.

\[!!\] Os generosos programadores da BIREME, Sr. Abel Packer, contribuíram desde anos para o desenvolvimento do ABCD iAH, Site e SeCS. Estas contribuições representam inúmeras e inestimáveis contribuições ao software ABCD - e, além disso, continuarão a desenvolver o software, uma vez que agora ele também será usado para os projetos da própria BIREME, acrescentando significativamente à futura "sustentabilidade".

Tanto o autor deste livro quanto o Sr. Ernesto Spinak, coordenador da equipe da BIREME, atuaram como coordenadores do projeto de desenvolvimento do ABCD, tentando montar as muitas peças do quebra-cabeça - e para garantir que a imagem final do quebra-cabeça não só seja mais ou menos correta, mas também de alguma forma atraente.

Mais dois parceiros institucionais também têm que ser mencionados:

UNESCO : como explicado acima na seção sobre a história do ISIS, é claro que a UNESCO tem um enorme mérito em desenvolver e promover o ISIS. A ABCD se tornará parte do conjunto de produtos ISIS promovidos pela UNESCO, mas através de uma Memória de Entendimento entre a UNESCO e a BIREME será assegurada uma supervisão técnica estreita por parte da BIREME.

VLIR/UOS : a seção 'Cooperação para o Desenvolvimento' do Conselho Interuniversitário Flamengo (VLIR, Bélgica, veja http://www.vliruos.be), através de um projeto 'Desenvolvimento de e Capacitação em Sistemas de Automação de Bibliotecas Baseados em ISIS' (DOCBIBLAS) que é promovido pelo co-autor belga deste manual, selecionou a ABCD como a solução de automação de bibliotecas que deseja promover com suas bibliotecas universitárias parceiras no Sul (América Latina, África e Sudeste Asiático).
