---
title: Módulo central - gerenciamento de banco de dados
description: Nesta seção discutimos brevemente as principais técnicas de uma das funções mais poderosas do ABCD 
lang: pt
lang-ref: abcd-modules/database-management
---



# Central module : database management

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---

Nesta seção, discutimos brevemente as principais técnicas de uma das funções mais poderosas do ABCD: criando novos bancos de dados e modificando estruturas de banco de dados.Como os dados-dados do ISIS não exigem estruturas reagentes 'normalizadas' sofisticadas e ainda podem lidar com elementos em relacionamentos muitos para muitos (como autores com publicações), o ABCD pode ser usado para lidar com qualquer banco de dados 'localmente' criadorelativamente facilmente.Recomendamos a ABCD para ambientes em que várias aplicações, como por exemplo,Repositórios institucionais, coleções de patrimônio cultural, Vo-Cabularies e ontologias ou mesmo apenas 'trechos' (unidades de informação textual soltas) provavelmente serão criadas e usadas.

Discutimos nas seções a seguir cada uma das opções fornecidas no menu principal do gerenciamento de banco de dados ABCD :![](https://lh5.googleusercontent.com/BE-QOz1IhYm4yArieSfqJz9alwkHKd10jYQD4LP66teGuVQuIHGXClJn43ynGbjbiH9kaqHZ7QD1Hmo4fSH_N2w55zn578cLHjCCsGFEZn4KLqcq28Yu6gN8p9MQezE7t_BGDzHC=s0)

 
> Nota:
> Este menu é criado no php-script 'homepage.php' no
> pasta '\abcd\www\htdocs\php\' onde cada nível de login recebe seu próprio
> função para criar o menu (por exemplo, função menuAdministrador() para o
> administrador do sistema), por isso, se for necessário alterar a sequência de
> As funções deste menu, este arquivo deve ser editado por alguém que
> Entende a codificação HTML dentro.
 
> Preferimos discutir as opções neste menu principal ligeiramente
> Sequência diferente (que pode ser obtida também no menu editando
> o script 'homepage.php' mencionado acima), porque antes de fazer
> qualquer outra coisa que a administração dos usuários deve ser pelo menos executada
> uma vez para definir um administrador de sistema local e provavelmente (bastante) alguns
> Outros usuários do sistema.

> [!!] em vista da importância da opção de menu 'entrada de dados' aqui um
> A seção dedicada deste manual será dedicada a ele seguindo o
> Discussão das outras funções centrais.Também os procedimentos para
> Siga para criar cópias e objetos de empréstimos para o inventário resp.
> Databases de empréstimos serão explicados lá, pois fazem parte dos dados
> Função de entrada.


## Administração de usuários

A opção de administração de usuários do menu principal de administração de banco de dados ABCD é um caso específico de gerenciamento de base, usando principalmente as técnicas gerais discutidas nesta seção, mas para um banco de dados específico 'usuários' nos quais apenas o administrador do sistema pode criar perfis e('Registrar') novos usuários ou editá -los.

> Nota:
> IMPORTANTE!Antes de fazer qualquer outra coisa, o ABCD deve ter, por
> Usando a opção de administração desta usuários, um novo sistema local
> Administrador com seus próprios dados de login!O login padrão
> 'abcd/adm' será amplamente conhecido como publicado, então não dá
> Qualquer segurança de fato!
  

A tela após a seleção da 'Administração de Usuários' no menu principal principal mostrará 2 opções:  

![](https://lh3.googleusercontent.com/-qWWxqxHbNDV4H_ckIFQLOUbEZ9EXq9ojXk7lVKkMva53tCRv10pW85-FXQ4ea13lvzgo_JfERlF-2-2bgjoSbDeK4MTgfAjhpoGHGmyC1Q-SxuKbG9Z5-CCcaMDDjcd0GAre2fA=s0)  
  

A segunda opção de gerenciar os perfis é discutida em outros lugares.A opção no gerenciamento de usuários é apresentada mostrando primeiro os usuários existentes (deve haver pelo menos um usuário de 'administrador do sistema'!) E dando as opções para editá -las, excluir ou adicionar (criar) um novo usuário.![](https://lh4.googleusercontent.com/lCWxZcCRXs6_4aR2OcR_pHwg7eObQuLh0yC-kfCnu4sGWZ4R80BgZpNK1lg1vDMLut45QICuQgQ5PKYBvSu0SgJs9WttQ847dGnZNZLw9nR8JOduU5NV8hIt2MHmZZ3OOY-3mPEH=s0)

Ao clicar no ícone 'Edição de registro' (primeiro dos três apresentados para cada usuário: ![](https://lh5.googleusercontent.com/DLZoceS22SkSxwdb2bE953Hj5KcGdr2VHpPcF5KZC0UJ4EgvUBobWXfYFNH5G5iMN83FTYMF2o3mP-5VSTBXSqFq1SGpPP3ImvfvQi2TbjjSY4zC7pYMDmICA_Cxy-EbxOALmFAC=s0) ) O registro com os dados do usuário será mostrado em um formulário de edição interativo :

  
![](https://lh3.googleusercontent.com/dCeLrTK6NagnAkFlULrem84wwtHl5ZoI2xaQBLKtMj8bRaj6vUIY8bopj_Q37hKkqpwWUyk0SEvjb0tV6cyRObaewa0vBx87JZvbDC-Rope4vKxj-sSYjMM0nt7sErVtA5WtDUs9=s0)  

Este formulário de edição tem as seguintes partes:

1. O nome de usuário, que pode ser um nome completo
2. O login a ser usado na tela de login, principalmente um nome mais curto
3. A senha para este usuário
4. Os perfis que foram criados e que podem ser atribuídos a esse usuário.Um conjunto de perfis de demonstração está incluído no pacote de instalação ABCD.
5. A data de 'Expiração' para o usuário atual, no formato de data 'normal' (conforme definido em Config.php) e o formato obrigatório de Data ISO que será criado automaticamente pelo próprio software.
6. Depois de editar o novo usuário, o registro deve ser salvo e, em seguida, poderá usar imediatamente o sistema.


## Criando um novo banco de dados no ABCD 

Após a seleção da opção de menu 'Criar banco de dados', os três elementos a seguir precisam ser especificados:![](https://lh4.googleusercontent.com/0kY0d4W0NeDCkRgbEspkVOaJ9f-5_YIUgeLVmhLAjSSXQ_nK3bkUOLZTmVmQBDjnz8I2WuhoSYyNXteNvvX-saKtrHpMcRVXUlMm7uLvYeoMibjM0LNNjBwh8yWph2Tly3_28uwm=s0)

Na primeira caixa, o software solicita o 'nome do banco de dados', que será o nome interno real do arquivo do novo banco de dados.Esses nomes não estão mais confinados ao nome antigo de '6 caracteres' de CDs/ISIS ou Winisis, mas os nomes curtos ainda são preferíveis.O nome apresentado aos usuários será especificado na 2ª caixa: a 'descrição'.

> Dica:
> Nomes e descrições de banco de dados podem ser abordados diretamente no
> arquivo 'bases.tab' na pasta \ abcd \ www \ bases.Neste arquivo cada
> Banco de dados, fornecido aos usuários, tem uma linha com cada dois valores: o
> 'Nome' e a 'Descrição', separados por um tubo ('|').

A 3ª caixa sempre fornecerá as opções 'Novo banco de dados' - significando criar um banco de dados a partir do zero - e 'banco de dados Winisis' - significando copiar uma estrutura existente de um banco de dados do Winisis ou de fato qualquer banco de dados ISIS com FDT, FST e PFT.Em seguida, os bancos de dados existentes serão fornecidos como modelos a serem usados como base para criar o novo banco de dados.Lidamos apenas com as duas primeiras opções, pois a cópia de um banco de dados ABCD-existente é bastante direto (o ABCD simplesmente cria o banco de dados copiando todos os arquivos necessários em suas pastas apropriadas e adicionando o novo banco de dados à lista de bancos de dados existentes).

A criação de um novo banco de dados 'do zero', significando: não baseado em um modelo existente, mas a partir de um zero-basis, envolve entender bastante algumas técnicas de ISIS, esp.A linguagem de formatação, porque isso será usado não apenas na criação do formato de apresentação do novo banco de dados, mas também em vários atributos específicos de ABCD dos campos (na planilha de entrada e entrada de dados) e no FST para indexação.

### Criação de um novo banco de dados do zero
    
#### Editando o FDT

[!!] Desde a versão 1.0 do ABCD, duas interfaces são fornecidas para editar o FDT: um 'completo' e um 'abreviado'. A forma abreviada não mostrará os subcampos, a menos que o próprio campo seja selecionado por seu link na primeira coluna - eles aparecerão na forma subsequente em que todos os detalhes dos subcampos podem ser editados, por exemplo A largura das colunas como 'não. das colunas, caso os subcampos sejam apresentados em uma tabela em vez de campos de entrada separados (que é o tipo padrão de entrada: texto/textarea). Este abreviado FDT -Editor é bastante prático - e mais rápido - em caso de grandes estruturas complicadas (isto é, usando muitas subcampos), como o MARC (mesmo quando o uso apenas de catalogação 'mínimo' e 'nacional', o número de elementos possíveis é muito alto, P.E. Existem 14 tipos de registros diferentes, cada um com o seu próprio campo 'polimórfico' 8 e listas de pick-listas correspondentes, também para os Marc-Indicadores ... resultando em mais de 140 mesas de coleta por idioma). Para outras estruturas mais simples, o editor FDT completo pode ser usado.

[!!] No caso, o editor FDT completo é selecionado ou, quando no editor abreviado, um campo é apresentado em um formato detalhado, o link na primeira coluna pode ser usado para mostrar o campo de uma maneira detalhada 'vertical', então apresentando apenas o campo selecionado de forma normal.Isso então é mais prático para lidar com os elementos individuais a serem definidos.
  
[!!] A tela FDT-Editor é provavelmente a mais complicada de ABCD, pois apresenta um FDT vazio, mas como no ABCD esse FDT também define a planilha para entrada de dados (ou catalogação), ao contrário de outros ISIS-SoftwaresOnde uma 'FMT' separada, mas simples, é definida e, além de, além disso, o ABCD usa alguns recursos de entrada de dados mais avançados, como listas de listas e validações, essa etapa é bastante exigente.

> Dica para 'editar' o formulário, clique duas vezes dentro de uma célula do
> Tabela!Clicar simples apenas selecionará a linha, mas não fará a célula
> Editável ou invocar o menu anexado à célula.

Vamos lidar com cada 'coluna' da tabela agora, mas, para um teste simples, pode ser suficiente simplesmente usar apenas as 11 primeiras colunas e as 2 últimas, sendo a parte restante dedicada à definição opcional de listas de picking:

![](https://lh6.googleusercontent.com/kPazwK_Jv1KbLvSgrKNfdrxF8_JP_ZblxQFRtfj7C8599QfET0wftqNq2wmat-QWM3Re2yUJvAgWlQYzvD4tdrF-NeCCuU9esA2IenOppk8uZ65TZ7mhgHINzdjRgKoNhv12We8K=s0)  


#### A. Definindo os campos
1. A primeira coluna: este é apenas um número, atribuído pelo sistema.No entanto, pode ser usado, se desejado, para abrir a linha em uma janela separada para apresentar todas as colunas como caixas separadas para interagir, clicando no hiperlink do próprio número.Uma apresentação de linha vazia se parece com a seguinte:

![](https://lh6.googleusercontent.com/zN2AIz2DBmeqK6pNjYvtk0WyZjgAbr1AJ3jGhU_KvsbBO5YycCNhKqhwUTPqHFZRmXnGD6necfQ01tnjE0_8iJB23I703QXWaPPFrshOYjdztaJf83Ch5LJ32W6BGyVoy_Asci2g=s0)


2. A segunda coluna é sobre o 'tipo' do campo, que pode ser um dos seguintes tipos:![](https://lh5.googleusercontent.com/dRjJTJs8TLrPN6lfaXwf5IM899xU4IPEHbLLJ0pBGICZFPabenTtBv3wnSBQboBNLjcQqU2TtvSvvp_ISq8yBZOifEO1eO1-ZafzTLvRMqrIQKAgErXnWBkL9k2kWL21ux4Lj1NO=s0)
    
	* Campo: a unidade básica dentro de um registro, que deve ser usado caso o elemento não seja um dos seguintes tipos: um subcampo, um campo fixo, um campo ou líder de Marc, ou um 'grupo' que é um repetidocampo com subcampos.
    *  [!!] Autoincremento: Este é um campo especial que o próprio sistema normalmente gerenciará, levando o número salvo no pequeno arquivo 'Control_number.cn' no dobrador de dados do banco de dados e adicionando 1 para cada registro subsequente usando este campo.Quando, por algum motivo especial, essa numeração automática precisa ser alterada manualmente, o 'atribuições' permitirá fazê-lo.
    * [!!] Um subcampo: quando anteriormente um campo foi criado com valores para subcampos dados na coluna 'Subfields' (ver infra), o ABCD espera que, posteriormente, todos os subcampos sejam descritos imediatamente após o campo ao qual pertencem.O subcampo-identificador deve ser colocado na coluna para 'subcampos' e o sub-campo como o nome do campo.Os indicadores utilizados nas estruturas de Marc devem ser tratados como subcampos, mas com identificadores numéricos.
    * Um campo fixo: permite criar um campo simples com um comprimento fixo
    * [!!] Data (Marc 005): Este é o campo de data especial com a tag 005, conforme usado em Marc.
    * [!!]Marc-Leader: O campo de líder da estrutura fixa.O suporte dedicado para todas as posições deste campo especial é fornecido.
    * 'Grupo': Este é um campo subsefamado que é repetível.Como em um campo subsefamado normal, ele deve ser seguido imediatamente com os subcampos pertencentes ao grupo, mas cada série de subcampos será repetível.Um exemplo típico de um grupo é o 'autor', pois uma definição de autor contém principalmente várias 'partes' (ou subcampos), como nome, primeiro nome, função etc. e documentos em princípio podem ter mais de um autor,Portanto, esse campo deve ser repetível.O elemento de entrada de dados 'tabela' é bastante adequado para representar um campo tão complicado em um formulário de entrada de dados: cada linha da tabela será uma repetição do campo e as colunas representam os subcampos.[!!] Os tamanhos das colunas podem ser definidos como o parâmetro 'linha' da primeira linha de definição do subcampo.O número de linhas na tabela definirá quantas ocorrências serão mostradas, mas o ABCD sempre adicionará uma linha vazia para permitir a criação de ocorrências adicionais.
    * Uma 'linha' é apenas um elemento gráfico para separar campos na planilha para entrada de dados.Não precisa de mais especificações.
    * Um 'cabeçalho' é um texto curto que pode definir uma 'seção' na planilha de entrada de dados para 'campos de grupo' juntos;O ABCD fornecerá automaticamente os hiperlinks-da forma para navegar diretamente para qualquer um dos títulos definidos.Em Marc, um "cabeçalho" típico pode ser, por exemplo'entradas primárias' ou 'entradas secas'.
    * Operador e data: Este campo será preenchido automaticamente pela ABCD com o nome do operador logado que edita os registros e o estampamento de tempo da criação.
    

3.  A terceira coluna é usada para definir a 'tag' ou identificador numérico do campo, conforme exigido pelo ISO-2709.Esses números variam de 1 a 999. ABCD (assim como o cisis) usa muitos campos com valores superiores a 1000 para usos internos e principalmente temporários.As marcas de campo podem ser arbitrárias (por exemplo, 1, 2, 3 ...), mas geralmente devem cumprir os padrões existentes, p.O Marc21 usa '245' para o campo principal do título.É a responsabilidade do designer (você ..) decidir sobre uma lista adequada de marcas de campo.
    
4.  Coluna no.4 Permite identificar o campo com um 'nome' ou 'título' para explicar o significado do campo.Aqui, qualquer indicação - de preferência curta - pode ser usada no idioma real.
    

> Nota:
> ABCD, ao contrário de Winisis e outros Ísis-Variants, permite a criação de
> FDT para cada idioma usado, para que os nomes de campo possam ser dependentes da linguagem!

5. Coluna no.5 permite selecionar um - e apenas um!- Campo em um banco de dados a ser usado como o 'Indentifier Field no qual as listas (consulte, por exemplo, a' ferramenta de seleção A-Z ') será baseada.Não é o mesmo que o campo 'Primária Chave' em bancos de dados relacionais, mas de fato define o campo marcado como 'i' - já que esta coluna permite apenas 'ativar' ou 'desactivar' - e, portanto, ser usado para classificaros registros para seleção direta.
    
6. Coluna no.6, como o anterior, permite apenas 'ativar' ou 'desativar', neste caso denotar se um campo é repetível ou não.Esta é uma decisão importante a ser tomada, de acordo com a visão dos designers sobre a estrutura do banco de dados, mas diferentes raciocínio podem ser aplicados.Por exemplo.Em uma estrutura simples, o 'título' pode ser feito 'repetível' para conter também todos os tipos de títulos (por exemplo, subtítulos, títulos traduzidos e originais ...) para enfrentar os usuários com apenas um 'título'-campo.Marc quer que todos os tipos de títulos estejam em diferentes campos, mas ainda prefere que o campo de título-Proper seja repetível!Sugerimos tornar os campos repetíveis em caso de dúvida, pois é mais fácil usar um campo repetível apenas uma vez, em vez de exibir repetições corretamente em um campo definido como não repetível (nesse caso, a definição de campo deve ser alterada noFDT é a necessidade da PFT de ser ajustada!).
    
7. Coluna no.7 Permite definir os caracteres únicos (0-9 ou A-Z, insensível ao caso) que identificarão os sub-campos, se houver.Lembre -se de que, se os subcampos forem fornecidos aqui, as linhas ou linhas subsequentes devem lidar com cada uma delas individualmente, caso contrário, será fornecido um erro lógico.[!!] Na linha de mesa que define o subcampo específico, esta coluna deve conter o subcampo-identificador.
    
8. A coluna 8 permite definir opcionalmente caracteres como pontuação (, :: etc.) que serão convertidos - na mesma sequência; portanto, tenha cuidado e verifique se há consistência!- nos identificadores de subcampo.Isso permite que a equipe de entrada de dados use a pontuação em vez dos identificadores de subcampo menos obsivos, mas lembre-se de que o ABCD também permite lidar com cada subcampo individualmente sem ter que se preocupar com os identificadores (consulte a seção em 'entrada de dados').

9.  [!!] A coluna 9 permite definir o tipo de componente de entrada HTML que o formulário de entrada de dados fornecerá, onde houver 15 possibilidades:

![](https://lh3.googleusercontent.com/u-8-cS31wEnibu0cmG6cb4U-MMt4JTr2qBTU6PDZ11lL2kCspQZWFrhxLdDEn4GnuaYNHDPfYPbF34ODHAcP7GaJ5hewHhawkRZmM-j9sOxvvVAASgC16xBNuugb1iwfO827_pf_=s0)


![](https://lh3.googleusercontent.com/-TAFo7WPCWDZlR6kscNHtFIcWMNvjbgkt2z6HtElNTpzED2CQlXGupzO979kcGyYbOXPd91ezgznpLDeoUpmzXYxUTJ82J2TNOjgO1jX3u7PLcEEcu_xizVM9H-I3yQd-cI6NIz-=s0)


![](https://lh6.googleusercontent.com/MNRAKw2VaT_UMhQWbs8zFvrNMtjmsS2oPJCefLGn8IIky3Fk3B8puPvoz_h3gO8PnZqvN4EWkaD_XtGtUSnMDZfkkYB3MGpyzUJIGJRkmVg2rahGmbphLegPc92XHwbyeTgj1J65=s0)  

* Texto/textarea apresentará uma caixa de texto de comprimento variável. O número indicado na coluna 'linhas' define o número de linhas que serão apresentadas nesta caixa.
* O texto (comprimento fixo) apresentará uma caixa de texto de comprimento fixo. O número indicado na coluna 'colunas' define o número de caracteres que poderão entrar nesta caixa.
* A tabela apresentará uma tabela na qual, nas linhas, as ocorrências do campo podem ser inseridas e, nas colunas, os subcampos dessa ocorrência podem ser inseridos. Os números em resp. As colunas 'linhas' e 'colunas' definem, como pode ser esperado, o número de ocorrências e subcampos que serão capturados para este campo.
* A opção 'Senha' fornece uma caixa de texto na qual a caixa será preenchida com * para cada caractere digitado, para ocultar o conteúdo deste campo especial. Se a opção MD5 for ativada no arquivo config.php, as senhas serão criptografadas.
* A data é a opção de capturar uma data, com a assistência de um controle JavaScript para oferecer a seleção de data de um calendário.
 * [!!] ISO-DATE é o campo Data de data formatada por ISO (AAYYYMMDD), principalmente preenchida automaticamente pelo ABCD para uso interno.
* Selecionar Simples permitirá a seleção de apenas um elemento de uma lista de opções predefinidas.
* Selecionar múltiplas permitirá a seleção de mais de um elemento de uma lista de opções predefinidas.
* Caixa de seleção é a opção de permitir que uma ou mais caixas sejam 'marcadas' (ativadas) para selecioná -las.
* O rádio é a opção de permitir que apenas um botão rodada seja ativado para selecionar a opção relacionada.
* A área HTML é a opção de apresentar ao usuário um html-editor completo (Controle JavaScript, no ABCD, usamos o FCKeditor) para edição, no modo wysiwyg, texto com código HTML.
* O HTML externo é a opção de criar, como em 10, um texto-html-código, mas isso será armazenado não no banco de dados, mas como um arquivo externo, com um link no registro do ISIS neste arquivo.
* O arquivo de upload é a opção de apresentar um controle JavaScript para carregar arquivos no servidor e criar um link de acordo.
* [!!] somente leitura é um campo que não será editável depois que ele foi inserido, pois é somente leitura.
* [!!] oculto: um campo que não será mostrado após ter sido inserido.
 
10.  A coluna 10 permite definir o número de 'linhas' que o componente HTML de entrada de dados oferecerá.Dependendo do tipo exato selecionado na coluna anterior, isso significa o número de linhas de texto que podem ser exibidas na caixa ou o número de ocorrências de um campo (em uma tabela para conter um 'grupo') será permitido etc..

11.  Como na coluna anterior, esta coluna permite definir um número, mas desta vez o número de 'colunas' no componente de entrada HTML, que pode ser, por exemploO número de caracteres (em uma caixa de texto de comprimento fixo) ou o número de subfieldas (em uma tabela) ou, mais geralmente, a 'largura' da caixa.
    
Em princípio, depois de definir essas 11 colunas e se não houver necessidade para definir 'Lista de seleção', o que é restante é simplesmente definir, se desejado, um valor 'padrão' para este campo na última, mas uma coluna, e paraIndique se uma página de ajuda para o campo atual deve ser disponibilizada.[!!] Essas páginas de ajuda devem ser chamadas de URL (arquivos locais ou páginas da web online).

No final da tabela, são fornecidas opções para salvar a tabela, mas também para testá -la e validá -la![](https://lh3.googleusercontent.com/9HhAv5eLud0hhqtTRGEUkE1ZGL4Lf097h2CHHMjsbhK5LWtdpqPIQqttSBnATqbFTDCu-JyREbI5TEj6gd3rtNdL2fZXF3VUOOTkrlySKX37rZtcHFnsfFVFs0zSDHeqBS9w2nxU=s0)

Aqui, as opções 'Teste' e 'Validar' resp.Exiba o formulário resultante para obter uma idéia sobre o resultado e exibir a tabela em uma janela diferente com uma mensagem indicando se todos os erros lógicos ou gramaticais estão presentes na tabela.Escusado será dizer que esses erros precisam ser corrigidos antes de 'salvar' ou 'atualizar' o FDT com a última opção apresentada aqui.

A opção 'Lista' fornece uma lista da tabela em uma janela separada, por exemplopermitindo imprimi -lo ou salvá -lo como um arquivo separado.

#### B. A definição de listas de picaretas
    
Continuamos aqui discutindo as colunas do FDT, desta vez com as colunas 12-20, que (exceto o último 2) lidam com a definição de 'lista de pick-lists' a serem apresentadas no formulário de entrada de dados para apoiarControle de terminologia, controle de autoridade ou simplesmente para facilitar a entrada de dados, fornecendo as opções disponíveis.

12. Tipo de lista de pick -list: aqui definimos o tipo de lista de controle a ser usada, com as seguintes opções: [!!] Banco de dados, tabela ou sinário.
    
Um banco de dados é na verdade um ISIS-Database com seu arquivo invertido, fornecendo um número quase ilimitado de possibilidades, mas sendo uma solução bastante complicada.[!!] Uma lista simples (tabela) será baseada em um arquivo ASCII (ou TXT-) contendo em cada opção Linha um.O 'Thesaurus'-opção é de fato um banco de dados (ISIS-) novamente, mas desta vez usando uma estrutura de campo específica com referências aos diferentes relacionamentos hier-sinônimos (e padronizados) do hierus, como 'sinônimo', 'termo mais amplo', 'termo mais estreito', 'nota de escopo', 'uso para' ou 'usado para'.Esse sinário-database normalmente fornece maneiras de 'navegar' para os termos relacionados e, portanto, oferece até um nível mais alto de suporte à entrada de dados, fornecendo de maneira científica descritores de um determinado campo científico ou tópico.

13. Nome: Aqui o nome do banco de dados ou do arquivo no qual a lista de controle é baseado, deve ser colocado.Isso também pode ser retirado da opção 'Procurar' na 15ª coluna (ver infra).
   
14. Prefixo: aqui o curto prefixo deve ser colocado caso um banco de dados esteja produzindo a lista de seleção, pois essa lista será produzida a partir do arquivo invertido desse banco de dados e que geralmente será dividido em 'seções' pelo uso de um prefixo
    

- Este é o único a ser colocado aqui para permitir a apresentação parcial do arquivo invertido.Se, por exemplo,A lista de controle é usada para facilitar a entrada de nomes de editores (como muitos voltam com frequência), provavelmente os editores do banco de dados são indexados com um prefixo como 'PU =', então colocar este prefixo aqui exibirá apenas a seção do IF com com com com com com com com com com a seção 'Esse prefixo.

15. 'Browse': este é um link que, quando clicado, abrirá a seguinte janela separada, que permite definir algumas informações sobre o picklist-database em caixas separadas, antes de tudo o nome do banco de dados que pode ser selecionado para os jáacessível.
    
![](https://lh6.googleusercontent.com/PJZthcOQDtRu9jxxBxRaqW9DWs-ZVysRsC2sxAXkgMZ9mpIRjQ2cmdvFl-iMcFJ_VyBG4CT89a6qv7r0b1HuaIMgDBLY7v1KzL-bEmQu5rZiD5rL9xP_2kTd2NsLgxj4HwHJ5vzc=s0)

 16. O formato de exibição (ou 'Lista como') indica a PFT que define como os valores na lista serão exibidos com a linguagem de formatação.[!!] Aqui um PFT 'inline' pode ser dado, por exemplo'V11', ou uma referência a um formato externo pode ser fornecido como '@myformat.pft'.Esse formato externo deve ser escrito após um padrão predefinido para ser interpretado corretamente.
    
Veja o exemplo aqui usado para os arquivos de autoridade do banco de dados MARC: @autoridades.pft: selecione e3

```
case 1: v1
case 100: v100^a,`$$$`v100^a
case 110: v110^a,`$$$`v110
case 111: v111^a,`$$$`v111
case 245: v245^a,`$$$`f(mfn,1,0) case 260: v260^a," : "v260^b case 270: v270
case 340: v340
...
endsel
```
  

> Nota:
> [!!] Caso a PFT contenha pipes (|) não pode ser colocado em linha
> no FDT, mas deve ser colocado em uma PFT externa mencionada de
> Esta célula (isso ocorre porque os tubos também são usados como separadores para
> Os valores da coluna da tabela FDT conforme armazenados em asci- formato).

17.  Extraia como: define, novamente com a linguagem de formatação, como o conteúdo do campo precisa ser exatamente extraído dos valores do campo no registro em que a entrada na lista (como uma postagem de arquivo invertida) pontos.Se esse valor for omitido, os valores serão mantidos no formato definido como 'formato de exibição' na coluna anterior.Se o formato de exibição for um formato predefinido (@xxxx) e seguir as instruções para separar o formato de exibição do formato de extração por $$$, esta peça deve ser deixada vazia.

18.  Valor padrão: aqui o valor padrão pode ser colocado, que pode servir para campos que geralmente têm, no caso específico do banco de dados, o mesmo valor, que já será apresentado automaticamente.
 
19.  Ajuda: esta é uma caixa de ticks (ativa ou não) para indicar se um arquivo de ajuda para esse campo deve ser apresentado na planilha.As páginas de ajuda são armazenadas nas pasta_de_bases/dbn/ayudas, onde o DBN representa o nome do banco de dados.
   
#### A definição FST

Depois de definir a lista de campos (e as listas de apanhadas para eles), o ISIS espera que o gerente, que esteja criando um novo banco de dados, definir não apenas quais campos serão indexados, mas também exatamente como eles devem ser indexados.É isso que a tabela de seleção de campo (FST) deve fazer.

Existem excelentes documentos disponíveis como 'páginas de ajuda' no ABCD nessa complicada-técnica ISIS (e incluída como anexo com este manual), então aqui apenas apresentamos o objetivo principal das três colunas FST.

O FST contém 3 colunas:

1. **O identificador**
Esta é uma tag (um número) que será usada como campo de onde o termo do índice foi realizado, por exemplo,para permitir limitações de campo na pesquisa.Principalmente essa tag corresponderá ao campo real de onde o valor foi obtido, mas também pode ser um campo 'virtual' (por exemplo, agrupar vários títulos em um 'campo de título' para simplificar a estrutura da pesquisa).Por exemplo, pode-se criar a muito popular pesquisa de 'All Fields' (os usuários do Google não sabem mais de nada!), Indexando todos os campos significativos com um e o mesmo identificador, por exemplo'999' para permitir uma pesquisa 'não em campo'.

2. **A técnica de indexação**
O ISIS aproveita 9 técnicas para indexação, mas basicamente elas podem ser reduzidas para duas opções principais: o campo completo (abreviado para os primeiros 60 caracteres no ABCD) - chamado 'por linha' - ou uma indexação de texto completo - chamado 'por Word'.As técnicas de indexação de 5-9 são otimizadas para indexação usando um 'prefixo' (uma etiqueta curta que precede os valores para agrupar os valores na mesma seção alfabética do índice geral ou arquivo invertido).

3. **O formato de extração**
 Aqui, o formato real para produzir a picada a ser indexado é especificado usando a linguagem de formatação do ISIS.Todos os recursos da linguagem de formatação (exceto os recursos de apresentação) podem ser usados, incluindo a referência a outros bancos de dados.


A interface do ABCD torna a criação de um FST tão fácil quanto possível (mas não é fácil, devido às possibilidades avançadas disponíveis!), Não apenas fornecendo o FST em 3 colunas editáveis, mas também como umReferência, o FDT a partir do qual os campos podem ser usados com suas tags e também indicando se eles têm subcampos e são repetíveis ou não.![](https://lh4.googleusercontent.com/i5Vtr0vTJ6oJOQJfiU2Q3rg9LHa2Lk1qq-vjMxShCLhMFgoZssGo0Igo2GUjJ13FxTQk9c63bdnfyWxaWOzowQ8nwQMSc1S0hP7vcmm-HQumWuJMAMEZ1ay3o8ETkuZrOYNr4gzV=s0)  

Como pode ser visto em [!!] Este exemplo, que usa formatos de extração muito simples, sempre preferimos prefixos a serem usados, por exemplo, 'ID_'. Em vista de algumas opções internas da interface IAH OPAC para ABCD, recomendamos o uso de prefixos de 3 caracteres que terminam com um sublinhado ('_').

Como a linguagem de formatação (característica mais poderosa do ISIS) pode ser usada aqui em todo o seu poder (sem os recursos de apresentação gráfica), os valores podem ser processados antes de entrar no dicionário, por exemplo: ``'N:', f(mfn,1,0)`` produz o número de registro ou mfn, formatado (f) como uma string, mas exemplos mais complicados podem ser dados, por exemplo.

- Uma combinação de vários campos ou subcampos com pontuação adicional
- Formatos usando a função ref para se referir a bancos de dados externos para obter valores a partir daí depois de localizar o MFN com a função L- fazê-lo, por exemploOs códigos podem ser convertidos em valores para o dicionário.
    
After having edited the FST, it can be tested with any record of your database to check whether the actual values which will be indexed indeed comply with what was intended.![](https://lh5.googleusercontent.com/FRA6Z4MDzsH4LSRB2h7RIix9nvptfcgKSDdIlqn-IaG-aaR0p39PQ1u_-C_NEWjqnbqJL7vgWWtWngDP4oimbX-JNSpuuBlKzYg2cAHsu7YZsKVmc7eVcyH4nRoPiXQbJ0SG5hGW=s0)


#### The worksheet editor

As in any ISIS-application, ABCD allows the creation of many different worksheets for different purposes, e.g. to deal with only a smaller subset of fields, or with the fields in a different sequence etc.

For that reason ABCD offers in this option an easy tool to select which fields to present in the (new or edited) worksheet and in which sequence to present them :

  
![](https://lh5.googleusercontent.com/PqifZQf5Z9eKjkYTnqvq1ADR1IzJ5m1rFtXJH3tweCdwJdpYgm841-pdb7Nf42SSB6UmNagSYyqlYM4UE6YN26NFGXFbAawHlEizFva2Okle6mEajqtcUE9Lj4s5SbT_kPXW5IdX=s0)

In case an existing worksheet needs to be edited, it can be selected (in the upper part of the interface) from a list

-   where possibly also an existing worksheet can be deleted is so desired. The main part of the worksheet presents
    

the list of available fields with possibility to copy any field ( ) or all fields ( ![](https://lh4.googleusercontent.com/6vcKUqy6njvqCh-qXnxOoyLtj3GZAZZqTXg3Mdh8jSduvP2J0YA74-YYtPw7mZ5pviDiG81r2u881hlODieyOFR2s6VI1NyDTQ--lmMOhXk7kKbcqcd9i6q6w7Wj29b9rQjWgYiV=s0) ) to the worksheet list at the right side.![](https://lh4.googleusercontent.com/F778ssiMh_7PggbelfwBKygL6CBhIaW-sp9UR4VueZ4oWdzhsjbKns-q0P74R3qD41xf8kYM4szlPq3TzCZzPT50nW4Db2DspeoWTlAeLX8MUG4_XQIfMG93Yt3MGdrjoEQMwRC4=s0)

Finally the worksheet can be saved into the system with an internal name (short and lower-case only) and a description for easy identification.![](https://lh5.googleusercontent.com/EWTCud_6-VyUNX6KsiOJiofV2-p_IsAbjUok0WZCOcLCNKmW4_HXkVXVGPpEiNE0Y_7MPR3Y8iH9-FKqqdRQHm_jlyZOWt6-SMiBZgqi76ffz7iyoyWFXPb2RJh2XzJAHgVE7oWk=s0)

#### The PFT Editor

Since the ISIS Formatting Language is a very powerful tool with many possibilities, a dedicated document on the (C)ISIS Formatting Language is added as annex to this Manual on ABCD, but it can also be consulted from a link provided in this PFT-interface of ABCD. Here we just briefly explain how the ABCD interface allows easy creation of either HTML-formats (for presentation on the web-pages) or 'delimited' formats (for export to a comma-delimited file).  


The PFT-Editor has 4 parts :
  
![](https://lh3.googleusercontent.com/opZKqWrBzBAbc0la7a43dghMs8Ctu736CiBaj17dgO12FwP0jnzPsKbmUGKyH_lgjIaxx_6eu3p12MCGliowkSez-1UwyJuat3DY6xg78WRGfqPnldYwpey5oobFN7mwufYxbC0H=s0)  
  

1.  Use an existing format : a list of existing PFT's will be available to select from. It can be also deleted or uploaded from an external file if not yet available. The format then will be presented with an editor to make changes into it.![](https://lh6.googleusercontent.com/LF03KbwiDfsg4x-hd5dB_vMNQ-KW-2VS45WWZFh3c8VutA53ycDhnk_DnJUDPq2hvJYTLRk4PiX4QlkpmCeDYKfwBnf-FYd7n_o8Qm-krFEy70bN2GrwYLYzarC0uU1pOlexeeEk=s0)
    

2.  Create a format : as with other table editors in ABCD, first a list of available fields is presented, which can be copied either individually or altogether into the format and then re-ordered.

> Note: 
> Windows list-selection tricks can be used here : Ctrl-click to
> add an entry into your selection or Shift- click to select all options
> upto the cursor position.

![](https://lh3.googleusercontent.com/7qv2pzwlhbLF8WyorU87BxnIB1S8pzPbwajUhTCFsYYWb9cc_xLOFMj0VYqppz7Q1Nhknu5_OyRqfqoPf9_NUwy2fzeYvWboFr4XxbhHr0-PlbKb8puDvu9yRR6SW1Z6MDeHdLW2=s0)

  

3.  Generate output
  As mentioned and shown above, generating output to test the PFT can be one of three pre-defined standard ways of presenting data from your database : either a 'table-formatted' web-page (in colums) or 'paragraph-formatted' webpage (no columns), or - alternatively for quite different purposes - a delimited format for export to other software. ABCD will immediately generate the necessary code, combining HTML-tags as quoted 'literals' with values from the fields (Vx).  

[!!] In case a 'column'-based format ('delimited' will allow export to softwares such as spreadsheets and statis- tical analysis tools) is selected, in the right square the (sequende of the) headers of the columns can be defined, by default they will be the field-names already defined.

![](https://lh6.googleusercontent.com/1o1GalJS8J492Mhe31NMGVJ22cUvr12wGCm_IsJUN_s_8spLVRe5SRfpptM-zWInOb4hay6lBJBNhnMZUYDEB_BIIllRWdqb-3gaTraJZsIsWEJmZ2urNNCUokN2qYOr9ZPFQknM=s0)![](https://lh5.googleusercontent.com/wsOwFpqXoqdibccoPmD8OErSxaVrWE4C3cGGWIyAnkfAgWUN24xG2EGpJjFJH4uD1YYsdYdQkor_IE7wTx-W8Q3tQPvMBcInU_RBiEANiOyFgQarl4T3iGAI0SmM6EeBZtC2sWrf=s0)

This format then can indeed be 'tested' immediately on either a range or records or a selection defined by a search-statement.

![](https://lh3.googleusercontent.com/ttX0fvJNFH2qqzxWuWc-Jvg-8Fp7PjOTcHjDtdxtzQvWJieZvpnTPJtO04YkFKWJUUDz_BN8I102VBc_o-98w9C_RdWtx77kR46C5uFZ3c0kQ6kY0NvK6VbQJSgYfi6gutu_Ko4u=s0)

This will result, when 'previewed' within the interface as opposed to 'sent to a document or worksheet' (this last option is ideal when outputting data as 'delimited'), into a display format like the following :  

![](https://lh5.googleusercontent.com/Qm5qO48Xk515yl75gC4B_A-1pAu95qto6F09C38JkeNO6pFjBrhCW9ewUEq-Dvyk8vzyPJvtKXskPJW164Y9y7j4xqHo8z3LR7LEHubA8qJIPVM4U-bGuzLcxK3tHTTXgQRmVlw5=s0)


> Note:
> In this example subfield codes are still visible, but with simply
> adding a 'mode' statement like 'mhl' into the format ISIS will hide
> them.

*The other functions of defining/editing ABCD-database definitions will be discussed below when dealing with the'Update database definition' section.*

### Copying an existing WinISIS database
For creating an ABCD-database from your existing WinISIS database, here are the steps to be followed :

1.  Export your existing records into an ISO-export file using WinISIS (or another ISIS-tool allowing ISO-export); remember where you have saved this .ISO export file, normally it will reside in the WORK-folder of your WinISIS installation. No specific parameters need to be set, unless of course you would only want to use a subset of the records in that database (by using MFN-range minimum and maximum or a search result) or you need to 'convert' (reformat) the records before entering them into ABCD by the use of a 'reformatting FST'.
2.  Assign in ABCD, after having selected the 'Import from WinISIS' option, a name and a description - as with a new database, see supra. Then select your WinISIS database using the list in the 'Create from' part of the dialog.
3.  Select the FDT belonging to that database and click on 'Upload' in order to have the FDT loaded into the ABCD environment of the new database.
4.  Select the FST belonging to that database and click on 'Upload' in order to have the FST loaded into the ABCD environment of the new database.
5.  Select the PFT belonging to that database and click on 'Upload' in order to have the PFT loaded into the ABCD environment of the new database.

> Warning:
> Most WinISIS databases use a default PFT (with the name of the
> database) which contains typical Windows (as opposed to HTML) codes,
> such as e.g. 'BOX', 'FS' etc. These will result in a 'grammatical'
> error when later opening this in ABCD, so it is better to avoid this
> by selecting a PFT without such

typical Windows-elements ! If not available, remember to re-create a HTML-based format within ABCD to replace the default PFT for your new database.

6.  Click on the 'Create Database' option in order for ABCD to start writing the necessary folders and files for your new database. A message about successful creation (or not, in case of problems) will be displayed on your screen. Also you will be reminded of the fact that without assigning this database as accessible to at least one user, you won't be able to use this database.

7.  Now you can open the new database, as it has become part of the list, in the main database management window.
8.  As the database can be opened but with 0 records, the first thing to do is to import the ISO-records created in the first step of this series. To this end, click on the 'Utils' icon in the main toolbar of this data-entry screen (as described in the section dedicated to this) and select the option 'ISO import'. This procedure further, as can be expected, involves the selection of the source ISO-file, which then should be 'uploaded'.
9.  Now, a bit strange, the ISO-file is ready for being effectively imported into the database. For this, click on the 'Utils' icon again in the toolbar and select 'ISO-import', where now the uploaded ISO-file is available for effectively importing (converting) into your ABCD-database. The software will now ask you if it is o.k. to indeed start importing the ISO-records from the selected file. The list of imported records will be shown on your screen to monitor its progress and success.
10.  If your newly imported records don't immediately show up in the database, re-open the database from the main menu, this will refresh the database parameters.
11.  Now the records should be visible and editable as normal records, only they have not yet been indexed into the Inverted File, so use the option 'Inverted File' update in the 'Other utils' section of the 'Utils' screen.

> Warning:
> If your imported series of records is quite large (e.g. above
> a few hundreds), it is possible, depending on the system you are
> working on, that the process will be too long for the web-server
> (Apache in most cases) and it won't be allowed to finish. For this
> reason it will be necessary in such cases to perform the Inverted File
> generation action not from ABCD (as a web-environment) but directly
> from the command-line, using the dedicated CISIS-tools (for which
> another section of this manual will give the details).

  
### Copying an existing ABCD database

This last option is the easiest to perform, as only a new name and description need to be entered, after which ABCD will simply re-produce all necessary files into a new folder structure for the new database. The source databases from which you can choose are the ones listed in the database-menu, in other words : the database descriptions listed in the file 'bases.dat' in the ABCD bases-folder.

The system will simply - as above - list all files copied and created in their proper folder-structure and that is it ! An empty database, as a copy of the existing ABCD-database but with new name and description, will be available for normal use.


## Update database definitions

From this option it is possible to edit all existing 'structures' or definition tables related to a database in ABCD. In comparison with 'normal' ISIS-databases, and in order to support some more advanced features in ABCD, there are some more of such database definition elements, as can be seen from the following 'database definitions' menu :  

![](https://lh4.googleusercontent.com/VbTg7M4vPqy060v0DLr5r5Hc1-iRsXj23Hk5fpsyxo9t3FsRnhpk9wqnJihtlUXgiSE6tAD2IX6NN7u3NOM5Kl_BgCdV8N9ErylXlzgobzFoBdIcVwQP5y2592pTznr4MASFd16p=s0)

In fact only the first four tables are used in other ISIS-environments : the Field Definition Table (FDT), the Field Select Table (FST), the FMT or edit-worksheet and the Print Format Table or PFT. Since we needed these also in order to create a 'new' database in ABCD, they were discussed in the according section above, the only difference being that instead of an empty table a pre-filled table with the already existing definitions will be presented by ABCD.

Let us briefly deal with the additional definitions for ABCD-databases now.

### Type of records

Some database-structures, such as MARC, require the 'type of the record' to be specifically coded into a dedicated field of the record. The software can then use this code to adjust many features to the specific needs for the type indicated, e.g. worksheets and print-formats can be different according to this type, or simply - as is the case with MARC - the format wants to be very detailed.

The 'type of record' information needs to be gathered at the beginning of the creation of a new record, so a list of types defined (and therefore 'available') will be presented as links, each one leading to the appropriate subsequent data-entry form, as can be seen from the MARC demo in ABCD.

[!!] In order to define such types, ABCD uses a table 'Typeofrecord.tab' - located in the 'def' folder for the actual language within the www/bases/[DB]/ folder. This file is - as is often the case in ABCD - an ASCII-file which contains, for each type defined, 4 values separated by a `'|'` (pipe-character), so this can be edited directly with an ASCII-editor (e.g. Notepad), but within ABCD an easier-to-use table format is presented :  

![](https://lh3.googleusercontent.com/vxYJnzAQtoYOlQ42XpphksTV7sTvdyZ_1x92W50iot6_PXKSqKe2ieDqglYgSlHcjQL-FCxZ9Sy5URXL6kCe-FWtzROKyDW0N4DZWiqfRvM9NLbrbV9dq82EoyhnDzlaG1brsT2r=s0)

 
The example above is the MARC record-type definition, which is kept in (internal) tag 3006 and has the following 4 columns, each containing values for each type :

-   the name of the worksheet to be used for the given type of record - with the 'edit'-link next to this first column one can also immediately edit the worksheet
-   the 'Tag1' value, which is in fact a one-character code to internally identify the type of record
-   the 'Tag2' value, not used in this case
-   the description of the type as it will appear in the list of available types. Clicking on 'update' below the form will save the table with any changes made.
    

### Record validation
    
[!!} Record validation allows the database manager to define criteria against which input for a field can and will be checked before entering it actually in the fields, or after registration of the record. Record validation in ABCD can relate to one of the following elements :
-   record validation : conditions can be given for each field
-   begin format : code can be given to be executed when a (new) record is created, e.g. the date of creation can be added with the date() instruction
-   end format : code can be given to be executed when the record is saved, e.g. the date of last update can be added with the date() instruction.

After selecting on of the three options above, clicking on one of the listed (as pre-defined) record-types will show the editor where the validation conditions can be defined.

These criteria need to be formulated into - no surprise ! - the ISIS Formatting Language. With the Formatting Language one can check a condition and if (not) met, an error message, which will be shown on the next screen, can be produced by the format. [!!] If the validation criterion was defined as 'fatal' however the record will not be saved and the error has to be corrected first.  

  

In this menu-option from the 'Update database definitions' menu each defined field will be listed with a box to enter the validation statement. E.g. :![](https://lh3.googleusercontent.com/oKu8hUaxkI7DKnHNYYzV2n78dodM6df_kALvB7fNV4OKE31M0dUFYVaXevZtFtmCYmpX0qoAxSYXSV5HXNMQt1IP506Wqan-MpU2LTJslPAJNd9jIP_YtbIcqzFNMWt5DJ9J0638=s0)


The format used here checks on the 'absence' of a value in field with tag 2 and if indeed absent will produce an error message that this mandatory field is missing. [!!] As stated above, errors can be marked as 'fatal' or not. With the 'ADD' link in the left-most part for each field. As shown in the illustration above, with the 'ADD'-link in the left-most column one can add more fields, even fields already used with another validation criterion to be applied.

When clicking on the 'edit' icon to the right of the edit-window for this field, the box re-appears in a separate small window for editing and the statement can also be tested on a record to see if it is doing the right thing. After editing one has to click on 'send' to put the possibly edited validation format back to the main table.

### Advanced search form
    
The advanced search form is the one used in ABCD at two locations : within the cataloging module to allow the cataloger to quickly and/or efficiently identify a specific record for editing (or duplication checking or copying) and in the OPAC as the advanced search form. Here ABCD simply offers an editor for the table which defines that search form with 3 columns :![](https://lh4.googleusercontent.com/SorkLWvyRODpnX8jui2-hUL_LhB6NpILr_Za1vwKLytNe_4RfO-Lwp_tYm_V2A7ocRQSTA3GAejqLNWjzSDtsMvC6Hd05vWxnahjyTw50Euss-dbJHbefvokq_5FyuW9jjxGPpFL=s0)

-   The first column is the field-name or 'index' as it will appear in the search-form
-   The second column gives the identifier used for the given field (or in fact combination of fields) in the FST
-   The third and last column keeps the prefix or fixed start-string which is used (if any) in the ISIS Inverted File for this index.

ABCD will also present, next (to the right) to this table, the existing FST to facilitate the identification of indexes (fields for searching) and the identifiers used.

Clicking on 'update' saves the table, which in fact is a file 'busqueda.tab', stored in the language subfolder of the 'pfts' folder within the database folder.

### Available databases list or table
    
Here simply a list is given of the databases being defined as 'available' in the ABCD-system. Actions allowed here are only changing the sequence (by moving up or down) of the databases in the list and saving the changed list.  

![](https://lh4.googleusercontent.com/ft7Snl4rGz9hwaRty5XTgrPAanSM3zHrlHabOyEuj_6mGagJThOV6Hgc51WR9IXzKukInGcRBM1n-7l_3KyXpcOY0W4TUEem3QaYg6km54S0Tq2MkaianL_pJ1g6UH6QhNmP_x3n=s0)

  
For adding or deleting databases one has to actually create the new database or delete the one to be taken out of the list. ABCD will take care of the changes in this list automatically. [!!} Databases can be moved up or down by selecting them and using the UP/DOWN buttons as in many of such controls in the ABCD-interface.

### [dbn].par
For each ISIS-database in a multi-database application such as ABCD, there is a file needed to tell ISIS where to find the constituting parts of the database-files - which then consequently can reside anywhere in the system. Such files are named after the database-name (therefore indicated here as [dbn] with the .par extension. Again this is a simple ASCII-file which can be edited directly or, as is the case here, from this ABCD-menu.

  
![](https://lh6.googleusercontent.com/sJjlKFYiUph88YKCmjJvYnTZSiNFZUPnpIV3_aoEu2dX2GZ7iQ4_z5U71JO6GeRYcCRvfVWIy14Ic34k6X2gZjs1dRVw7kkpQbf9xMsUYulJVbHaIDhR5YAhzQnNOhHgi5ubFvt4=s0)  

In principle ABCD will take care of this file and make sure that the necessary paths are available. The only special feature here - as compared to the same concept of dbn.par in other ISIS-environments, is the use of 'variables', taken from the operating system's environment variables, which can be dynamically substituted for their actual values. E.g.

    %path_database%

is a variable which actually will contain the database-path defined in the config.php main configuration file of ABCD.

[!!] In the example of the illustration above, the last line is an interesting one as it gives the path to the 'loanob- jects'-database for displaying copy-information (if included in one of the MARC-pft's) with the REF-function. In order to find the loanobjects-database for the use of REF->loanobjects, ISIS needs to know the path to this other database and therefore it should be included into the dbn.par.  

  

> Note [!!] For this last feature also to work in the OPAC (iAH), one
> has to add the path to the first section of the dbn.def file. E.g. the
> loanobjects-database should be pointed to by a new line there
> containing : 

    FILE loanobjects.*=%path_database%loanobjects/data/loanobjects.*

### Help files on the database-fields
    

For each field in the database ABCD can provide a help-page, which can be edited from this menu-option. To support the creation of such a page, ABCD will automatically put all known information from the FDT on the given field already available. With the built-in (JavaScript-based) HTML-editor a real nice help-page can then be produced and saved. The 'preview' link of course allows checking the result of your editing effort.![](https://lh3.googleusercontent.com/86HYiZn_9klIyIPWshK6DiZqkH2UUbz3FDsEAfldXlD_OaOAbmvNTq7tKWm9nDicDZo8eqSAK0WoFf2AhTvtNCaEWnWnXfdLLy120Yqt8LJ8RlCX_xLHWnz2ZjGfbeohmeKpynE8=s0)

  

### Configure database in iAH (or OPAC)
    

[!!] In order to be able to use a newly defined ABCD-database with the advanced iAH OPAC-interface (or in the ABCD Site), a special configuration file is to be edited : dbn.def. (where dbn has to be substituted for the actual database-name).

This file has the following sections to be edited :

  

1.  The FILES section : here the paths to the files to be accessed need to be given. In this path both the `%path_database%` and `%lang%` variables can be used to refer to resp. the actual database and actual language in use.![](https://lh5.googleusercontent.com/XzbGmhr000O_9jU0KhhbX-0UJLCR9zI0rLo-L_A0z13CZaPHFL6UbDRpB4-mwbuKLBq7ep2OfyAsBpTNPfhGjrU4ZYHDKPzqQXk-Z6ByNQIIuekR6Czye_oWsRW1jnZYh4VU6yHp=s0)
    
2.  The INDEX-DEFINITION section : here all the information for the active languages (numbered as 1, 2, 3 etc.) has to be entered (in subfields) to allow the interface to recognize the prefixes used for each searchable field and to name the field accordingly. The first line with prefix 'TW_' is the one used for the 'simple' search interface (Google-like) for searching words from the fields defined (by the prefix in the FST) to be included in this simple search. This is indicated by the presence of the subfield `^d*`.  

3.  The GIZMO section : here - if necessary in specific cases - gizmo databases for automatic substitution of strings by other strings (which can be used to change character sets, but also change codes and abbreviations into full values etc...) can be pointed to.![](https://lh6.googleusercontent.com/i3z71qKLcIxk8mqXAMyAccsJ2Hx1QG_uB2OvNG9nlLNCryQDE2QUmKbltjRbUYsjYLrA2Kgl1hD3RkO8NqA_30i9U9xZ2_WcrsnJIx99Y0NHHKhYuP-UO8avSXhZdu0H091ud26f=s0)
    
4.  The FORMAT section : here the display formats used in the OPAC should be defined, with for each language (in the numbered subfields) the label to be used on the screen. Remember that only formats (files with .PFT extension) can be used which are referred to somehow in the FILES section ! Also the default format can be identified here by simply indicating which format earlier referred to should be used as default display format.
    
![](https://lh6.googleusercontent.com/njC4b_3cU7HUeqbQOeT3bVrsJ7jbEngMbisQdVhUxB8g5FYzmUFkZJlS3ISRFVUA4VzKmcgYnMmKeC4S1DA-aUGa0AD-vWEgeh3cz7GIGIkfFLzrCTgykCUDhru5dhvsYScb6PeX=s0)  
  

5.  The HELP form section : here simply the (HTML-)files containing resp. the help-page and notes-page for the user of this database in the OPAC should be referred to.
   
6.  The PREFERENCES section : here the system manager can indicated which of the three search interfaces (simple, advanced and free) will be available for this database, and some other additional features of the inter- face : whether sending a search result to an e-mail will be possible, whether the results should be listed with navigation buttons, the number of records to be shown in one page and whether XML-export will be offered.  
  

![](https://lh4.googleusercontent.com/SUqlv_DS-5N3Kxc36LQEGCNl49_0RclTci9RUwEjAFbRTp6F3rm55qyt1apeIPfGjOi4985rdzkLB6gKnntkAsckRq8NX5AxOQoTndC8SeZZQj1iZnwto9U4jj5h32emFdv_LRgp=s0)

### Statistics : list of variables
    
This option simply allows quick definition of the variables from the given database with which tables for statistical analysis will be computed. For each criterion or variable (either as row or column for the table) a name and an extraction format has to be given. The extraction format - using the Formatting Language of course - exactly defines how the values in the field should be taken to compute the value in the table. By doing so it is possible

e.g. to define ranges of field-values to be combined into one table-criterion. The file at stake is actually 'stats.cfg' in the (language-specific) def-section of the database-folder.

  
![](https://lh3.googleusercontent.com/wC2Pm3_FdQWQeRseA-9bJvV9cek-D4kLLVBFCxGOiBsn1HP357CwdJfYTJmOMXU-96a4o38eL5Tim6ZbtxW3UaQ2mZBIdfbO0Z3elCOPoEKLu_d9OnmbOqdNYdqKhVnHKHPfY5H4=s0)  

The option to define a prefix is not yet implemented in this version of ABCD. The idea is that the values would be taken from the Inverted File, prefixed with the string defined here. By doing so the values would be computed while 'inverting' the record, not at the stage of producing the statistics table, and therefore allow faster production of the table.


### Statistics : list of tables
   
As with the list of variables above, ABCD also keeps a simple list of available tables, which have been defined previously, for the statistics module. This file 'tabs.cfg' equally resides in the def-subfolder of the database. Each line in this file contains three values (separated by the pipe-character) : the name of the table followed by the two criteria used in this table, e.g. :

Classification code / Publication date|Classification LC|Publication date  

![](https://lh5.googleusercontent.com/4Yz-wvMo6dXPEaPLOyoNg3QkqnJqEGBFyWf8_UA5gUKhPkSqtEF-8Gpnyawe6T1qzTzTYjtg0iihrGdCocgsiUnbthqSA0Z8AQ8c9EbXYfmOGC2xQuOu13xg5fCSrREfP1xE__W9=s0)

  

As can be seen from the example the editor in ABCD simplifies editing by providing each of the three values individually but also by providing lists of available row- and column-criteria.

## Reports
In fact creating reports in ABCD means creating ISIS Formatting Language formats (PFT's) with which the reports will create output, because with the F.L. any type of report can be produced and saved for later re-use. We therefore refer to the section on 'Display Format (PFT)' of the 'Update Database Definitions' Central menu option. Exactly the same interface is used here.

## Utilities
In this option ABCD offers some very basic operations on databases :![](https://lh5.googleusercontent.com/jHTrAoEZoonuu-fniMYnXtwtpKFWZ6iSyvT3yhksNy7-s0LYqs7QO2znmgtGZIcv0ZK6sRt04TJusqcNN0sYDMT4z5_Cr8dopMFvIUjDBqop84967SdUx8E4SeYZLSSSzE7zOLzo=s0)

-   Initialize the database means to delete all records in the database but without changing the structures of the database.
-   Delete the database of course means fully deleting the whole database with all corresponding files and folders in the ABCD bases/ folder.
-   Lock the database means to prevent any other users to make any changes to the records (data-entry), e.g. when a full Inverted File generation would be envisaged. 
-   Unlock the dabase of course then means to avail the database again to other users. Use these options with all necessary care and caution !
-   Assign Control Number is the option to automatically put sequential control-numbers in a series of selected records. Only a continuous series of MFN's can be selected here.
-   Link database with the copies database : as explained on the screen itself, here the option to activate the use of the copies database for the actual (bibliographic) database has to be activated.
-   Reset Control Number is the function to manually re-set to a specific value the numerical value in the file 'control_number.cn' of the database, in case for some reason the numbering has to be managed manually. E.g.  
setting this number to 1000 will make ABCD to assign from the next record on control-numbers starting from 1000. This could be useful in conditions where e.g. different cataloging centres are using different ABCD- servers but the resulting databases have to be merged into one catalog with control_numbers not interfering, so covering different ranges. By default however reset will revert to 1 as the basic control_number to start from.

## Z39.50 Configuration
    

Here the ABCD interface allows setting some parameters to define which servers for Z39.50 shared cataloging services will be offered in the Z39.50 list and some more parameters to ensure proper use of the protocol for the server. Such technical information can be mostly obtained from the service provider, e.g. in the case of the Library of Congress consult the following website : [http://www.loc.gov/z3950/lcserver.html.](http://www.loc.gov/z3950/lcserver.html)

Configuring Z39.50 has the following parts :

  
![](https://lh6.googleusercontent.com/ITrPEbvuGaSe7_zQeYSHHfBd8_KKHSWJsncTede3hrzK76SanHdAtZjXecP_pYxAyswJym0WD0ISJA6wUAyjsQnW6LLxVAtjEScBwW0oZzCsDfb_aeIeOPszhN3x5QAu_e6j1TEk=s0)  

-   Configure Z39.50 servers : in an interface similar to the one of users-administration, the defined servers are to be configured, with the parameters name, URL, Port, Database and UTF-8 (or not), see the illustration under here for Library of Congress. New servers of course can also be added with the 'Create'-icon.![](https://lh5.googleusercontent.com/7abTBVqO1hMgGJI9lE5T0J-uC7hF66DKPF5C6CeZRd_UNwgYg26RwJpWkQtqiLn5cexTN8GeCRpM_i5W2wmOblqxOE7LVLQM-Et_9rjWsje-gZ-KUg9SdWyQOmI9JUHnl94HGTaI=s0)
    
-   Conversion formats : when the incoming records (mostly in MARC21 format) need to be converted to the format used in the destination database, a form can be edited here to specify the conversion from source to destination. The name , subfields and tag of the incoming field will be listed and in the 'Conversion formats' column the ISIS F.L. defines how to extract values for this field in the destination database. ABCD comes with one demo conversion table to convert from MARC to CEPAL formats, with the following example for converting the ISSN MARC field to CEPAL.![](https://lh6.googleusercontent.com/NzKlW54uaVPpDnsfqjqhPihGxAj66yQpcXmYVXHYXu5M8vlScNcr5oPrnfojykpvvFvtsgN7pKjEJo7AgjPN5-rgnPcJU-ROa-Jr1gDy3R-h9eOrjkWjbNAV4ku1XRobgzBvN_I3=s0)
    
-   MARC-8 to ANSI character conversion table : this is a table which converts characters from the MARC-8 table (e.g. âa) to ANSI format (e.g. á). This table can be edited here if necessary.
    
-   Finally the Z39.50 can be tested from here, with the same interface as used in the ABCD Data-Entry module (see infra).
    

## Translate messages and help pages

There are two types of language-sensitive content which ABCD uses and which needs to be edited when creating or adapting new or other language versions : short messages and labels on the one hand, full help-pages on the other hand. [!!] These can be edited into other languages for each module of ABCD Central.

### Translation of short messages and labels
  Editing these is facilitated by presenting the default (English) language terms and phrases in a table in wich in the second column the new values should be put by the translator. For each of the main functions such a table is presented:  

![](https://lh6.googleusercontent.com/m1hz1TJkkEYhsRxPYlyht1xMnpY6J0i5-pz0mnnWpYx6X55NuFqRs1ImHIPUDEQRMqmdmn_d-E0A8mysiZdHBaxbXTo64z97dJiR8n2cgRGBg1yjG-rJaiUIfIl_YxkxeSo0eUX-=s0)


Here is a sample of some messages translated from English to Dutch for the loans module:![](https://lh3.googleusercontent.com/O0iI1_pPKlVklFOKS-sGzp3vgeYfzn3osmyn-TV6Q6TYBX1DrmZ1VSExhfOWIuH6KrS6FrRZcZJjnz-w-me5BVRgeZlGt4TscelQuLcCZXHKIh04XkhhyEqZACxI1miCqJyBBcA6=s0)  

This screen provides a 'save' icon ![](https://lh3.googleusercontent.com/dXAH4i_glKZgtTCotEYcefBtDLWMyqWrBU9S9YAu6qxRLhe8UD8VGqaIIYhqZKLcGCmLOQwwyO9HdFGU20PzL6iJjEbTIAMcnDH4Sg2AlZCGVOeqlUZh69EVziP-zzlx3StZuLNP=s0) for storing the table with new translations.

### Translation of help pages
Here the approach is different : a list of available help-pages is given ![](https://lh4.googleusercontent.com/W84ZVXybbCMZqEaGoEVBhZ0kEuuMULAumIlD2Fgkgi2Br3ZacVBgWZUtlxSXNVjYFkocdIrNEGOcNXzQUmMQmSskQ6vI_b58cOKlrD0zZFqOvqk9O0EVkyfbyOE0F8BC02bQRSmr=s0)

  
and for each help-file one can 'preview' or 'edit' the page. In the case of editing the built-in JavaScript-based HTML-editor will be provided :![](https://lh3.googleusercontent.com/6p6kLKxf78YCkDM7Agwx-OgiarG2cPyZ-SlpwoJnzqu6pZ2baVtKRuJiGGU1uEFyBMOLl1I09ulIJcq5c18t10V36CLKPQa3UEXd4hMs9TdodCmAR3FpGahQCngPuOTYnV_PCBAy=s0)  

  
## Explore databases directory
    
[!!] Exploration of the databases directory can be done (when the dedicated option variable '$dirtree' is put to '1' in CONFIG.PHP !) using a special display in the ABCD-web-page of the folders of the database-folder of the system,
![](https://lh6.googleusercontent.com/0aF6Wene-a2HY8S_9g8yTE19Qdn195lR3Dppjawr4Y0sLECjEl6fQuAkwgcXOPYQJb64s5Kd2yd7-DBp8IWQnFchTEvETm9VDo6XtuFdyvJ-_nmSac7u_r3PEOKRX4eOxL9PNZfE=s0)

with some possibilities to enter within subfolders and even editing, renaming, zipping etc. some of the text-files
in thereon by clicking on the 'details' icon ![](https://lh6.googleusercontent.com/auQdMSP6XtrDRMBZbxonDmbg01ii0m7BKIUjaxtxWEJK_CccgXfNI11wiSCVaXkrHF6a3dHiqe8OXB1HAz7FtiOKUAqQiLNjTKVEfuwFseFHKSPJNBmRycQ9NUWAFPWXBRmeAYSw=s0) , given e.g. the following options to apply on the selected file:
![](https://lh5.googleusercontent.com/7wIzZpzlZ9Yo7YsN4mLs1N3z7Iiw9Hduh8FhK6rPUtFK_X8GurPs6qCU-Ya9UyoYjEyKG0iRMWY0ExHQ8_E6-PkCQcKZH0BU4piwyH1bl9SZUID694XNos8my4iYpchMWXWoAmKb=s0){:class="img-responsive"}  

## Statistics

The Statistics module of ABCD also has a dedicated chapter, so here we just refer to this chapter, as this function can also be accessed from this menu but also from the cataloging toolbar and several menu's in the acquisitions and loans modules.