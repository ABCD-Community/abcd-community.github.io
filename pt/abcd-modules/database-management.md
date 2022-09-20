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
    
Depois de editar o FST, ele pode ser testado com qualquer registro do seu banco de dados para verificar se os valores reais que serão indexados realmente cumprem o que foi planejado.![](https://lh5.googleusercontent.com/FRA6Z4MDzsH4LSRB2h7RIix9nvptfcgKSDdIlqn-IaG-aaR0p39PQ1u_-C_NEWjqnbqJL7vgWWtWngDP4oimbX-JNSpuuBlKzYg2cAHsu7YZsKVmc7eVcyH4nRoPiXQbJ0SG5hGW=s0)


#### O editor de planilhass

Como em qualquer aplicativo ISIS, o ABCD permite a criação de muitas planilhas diferentes para fins diferentes, p.lidar com apenas um subconjunto menor de campos, ou com os campos em uma sequência diferente etc.

Por esse motivo, o ABCD oferece nesta opção uma ferramenta fácil para selecionar quais campos apresentar na planilha (novos ou editados) e em que seqüência apresentá-los:

  
![](https://lh5.googleusercontent.com/PqifZQf5Z9eKjkYTnqvq1ADR1IzJ5m1rFtXJH3tweCdwJdpYgm841-pdb7Nf42SSB6UmNagSYyqlYM4UE6YN26NFGXFbAawHlEizFva2Okle6mEajqtcUE9Lj4s5SbT_kPXW5IdX=s0)

Caso uma folha de trabalho existente precise ser editada, ela pode ser selecionada (na parte superior da interface) de uma lista

- onde possivelmente também uma planilha existente possa ser apagada é tão desejada. A parte principal da folha de trabalho apresenta a lista de campos disponíveis com possibilidade de copiar qualquer campo ( ![](https://lh4.googleusercontent.com/6vcKUqy6njvqCh-qXnxOoyLtj3GZAZZqTXg3Mdh8jSduvP2J0YA74-YYtPw7mZ5pviDiG81r2u881hlODieyOFR2s6VI1NyDTQ--lmMOhXk7kKbcqcd9i6q6w7Wj29b9rQjWgYiV=s0) ) ou todos os campos ( ![](https://lh4.googleusercontent.com/F778ssiMh_7PggbelfwBKygL6CBhIaW-sp9UR4VueZ4oWdzhsjbKns-q0P74R3qD41xf8kYM4szlPq3TzCZzPT50nW4Db2DspeoWTlAeLX8MUG4_XQIfMG93Yt3MGdrjoEQMwRC4=s0) ) para a lista de planilhas no lado direito.


Finalmente, a planilha pode ser salva no sistema com um nome interno (apenas em letras minúsculas e curtas) e um descrição para facilitar a identificação.

![](https://lh5.googleusercontent.com/EWTCud_6-VyUNX6KsiOJiofV2-p_IsAbjUok0WZCOcLCNKmW4_HXkVXVGPpEiNE0Y_7MPR3Y8iH9-FKqqdRQHm_jlyZOWt6-SMiBZgqi76ffz7iyoyWFXPb2RJh2XzJAHgVE7oWk=s0)

#### O editor da PFT

Como a linguagem de formatação ISIS é uma ferramenta muito poderosa com muitas possibilidades, [um tópico dedicado sobre a linguagem de formatação CISIS foi adicionado neste Manual sobre ABCD](/pt/abcd-technology/cisis-formatting/), mas também pode ser consultado a partir de um link fornecido nesta interface PFT do ABCD. Aqui explicamos brevemente como a interface ABCD permite a fácil criação de formatos HTML (para apresentação nas páginas web) ou formatos 'delimitados' (para exportação para um arquivo delimitado por vírgulas). 


O editor PFT tem 4 partes:
  
![](https://lh3.googleusercontent.com/opZKqWrBzBAbc0la7a43dghMs8Ctu736CiBaj17dgO12FwP0jnzPsKbmUGKyH_lgjIaxx_6eu3p12MCGliowkSez-1UwyJuat3DY6xg78WRGfqPnldYwpey5oobFN7mwufYxbC0H=s0)  
  

1. **Use um formato existente**: uma lista de PFT's existentes estará disponível para seleção. Ela também pode ser excluída ou carregada de um arquivo externo, se ainda não estiver disponível. O formato então será apresentado com um editor para fazer alterações nele

![](https://lh6.googleusercontent.com/LF03KbwiDfsg4x-hd5dB_vMNQ-KW-2VS45WWZFh3c8VutA53ycDhnk_DnJUDPq2hvJYTLRk4PiX4QlkpmCeDYKfwBnf-FYd7n_o8Qm-krFEy70bN2GrwYLYzarC0uU1pOlexeeEk=s0)
    

2. **Criar um formato**: como com outros editores de tabela no ABCD, primeiro é apresentada uma lista de campos disponíveis, que podem ser copiados individualmente ou em conjunto para o formato e depois reordenados.

> Nota: 
> Os truques de seleção de lista de janelas podem ser usados aqui: 
> CTRL para adicionar uma entrada em sua seleção ou 
> SHIFT para selecionar todas as opções até a posição do cursor.

![](https://lh3.googleusercontent.com/7qv2pzwlhbLF8WyorU87BxnIB1S8pzPbwajUhTCFsYYWb9cc_xLOFMj0VYqppz7Q1Nhknu5_OyRqfqoPf9_NUwy2fzeYvWboFr4XxbhHr0-PlbKb8puDvu9yRR6SW1Z6MDeHdLW2=s0)

  

3. Gerar saída

 Como mencionado e mostrado acima, gerar resultados para testar o PFT pode ser uma das três formas padrão pré-definidas de apresentar dados de seu banco de dados: ou uma página web 'em formato de tabela' (em colunas) ou uma página web 'em formato de parágrafo' (sem colunas), ou - alternativamente, para fins bem diferentes - um formato delimitado para exportação para outros softwares. O ABCD gerará imediatamente o código necessário, combinando tags HTML como 'literais' citadas com valores dos campos (Vx).  

> Caso seja selecionado um formato baseado em 'colunas' ('delimitado' permitirá a exportação para softwares como planilhas e ferramentas de 
> análise de estatísticas), no quadrado direito podem ser definidos os cabeçalhos (seqüências dos) das colunas, por padrão eles 
> serão os nomes de campo já definidos.

![](https://lh6.googleusercontent.com/1o1GalJS8J492Mhe31NMGVJ22cUvr12wGCm_IsJUN_s_8spLVRe5SRfpptM-zWInOb4hay6lBJBNhnMZUYDEB_BIIllRWdqb-3gaTraJZsIsWEJmZ2urNNCUokN2qYOr9ZPFQknM=s0)![](https://lh5.googleusercontent.com/wsOwFpqXoqdibccoPmD8OErSxaVrWE4C3cGGWIyAnkfAgWUN24xG2EGpJjFJH4uD1YYsdYdQkor_IE7wTx-W8Q3tQPvMBcInU_RBiEANiOyFgQarl4T3iGAI0SmM6EeBZtC2sWrf=s0)

Esse formato pode realmente ser 'testado' imediatamente em um intervalo ou registros ou em uma seleção definida por uma declaração de pesquisa.

![](https://lh3.googleusercontent.com/ttX0fvJNFH2qqzxWuWc-Jvg-8Fp7PjOTcHjDtdxtzQvWJieZvpnTPJtO04YkFKWJUUDz_BN8I102VBc_o-98w9C_RdWtx77kR46C5uFZ3c0kQ6kY0NvK6VbQJSgYfi6gutu_Ko4u=s0)

Isso resultará, quando 'visualizado' dentro da interface, em oposição a 'enviado a um documento ou planilha' (esta última opção é ideal ao produzir dados como 'delimitados'), em um formato de exibição como o seguinte:  

![](https://lh5.googleusercontent.com/Qm5qO48Xk515yl75gC4B_A-1pAu95qto6F09C38JkeNO6pFjBrhCW9ewUEq-Dvyk8vzyPJvtKXskPJW164Y9y7j4xqHo8z3LR7LEHubA8qJIPVM4U-bGuzLcxK3tHTTXgQRmVlw5=s0)


> Nota:
> Neste exemplo, os códigos de subcampos ainda são visíveis, mas 
> com a simples adição de uma declaração de modo como 'mhl' 
> no formato ISIS irá escondê-los.

*As outras funções de definição/edição de definições de Database ABCD serão discutidas abaixo ao lidar com a seção 'Atualizar definição de banco de dados'.*

### Copiando um banco de dados Winisis existente

Para criar um ABCD-Database a partir do seu banco de dados WINISIS existente, aqui estão as etapas a serem seguidas:

1. Exporte seus registros existentes para um arquivo ISO de exportação usando WinISIS (ou outra ferramenta ISIS que permita a exportação ISO); lembre-se onde você salvou este arquivo .ISO de exportação, normalmente ele residirá na pasta WORK de sua instalação WinISIS. Nenhum parâmetro específico precisa ser definido, a menos, é claro, que você só queira usar um subconjunto dos registros nesse banco de dados (usando o mínimo e o máximo da faixa MFN ou um resultado de busca) ou você precisa 'converter' (reformatar) os registros antes de inseri-los no ABCD, usando uma reformatação de FST.

2. Atribuir no ABCD, após ter selecionado a opção "Importar do WinISIS", um nome e uma descrição - como em um novo banco de dados. Em seguida, selecione seu banco de dados WinISIS usando a lista na parte inferior 'Criar a partir de'.

3. Selecione o FDT pertencente a esse banco de dados e clique em 'Upload' para que o FDT seja carregado no ambiente ABCD do novo banco de dados.

4. Selecione o FST pertencente a esse banco de dados e clique em 'Upload' para que o FST seja carregado no ambiente ABCD do novo banco de dados.

5. Selecione o PFT pertencente a esse banco de dados e clique em 'Upload' para que o PFT seja carregado no ambiente ABCD do novo banco de dados.

> Advertência: 
> A maioria dos bancos de dados WinISIS usa um PFT padrão (com o nome do banco de dados) que 
> contém códigos típicos do Windows (em oposição ao HTML), como por exemplo, 'BOX', 'FS' etc. 
> Estes resultarão em um erro 'gramatical' ao abri-lo posteriormente no ABCD, portanto é melhor 
> evitar isto selecionando um PFT sem tais elementos típicos do Windows! Se não estiver disponível, 
> lembre-se de recriar um formato baseado em HTML dentro do ABCD para substituir 
> o PFT padrão para seu novo banco de dados.

6. Clique na opção 'Criar banco de dados' para que o ABCD comece a escrever as pastas e arquivos necessários para seu novo banco de dados. Uma mensagem sobre a criação bem sucedida (ou não, em caso de problemas) será exibida em sua tela. Também será lembrado que sem atribuir este banco de dados como acessível a pelo menos um usuário, você não será capaz de usar este banco de dados.

7. Agora você pode abrir o novo banco de dados, como se tornou parte da lista, na janela principal de gerenciamento do banco de dados.

8. Como o banco de dados pode ser aberto, mas com 0 registros, a primeira coisa a fazer é importar os registros ISO criados na primeira etapa desta série. Para isto, clique no ícone 'Utils' na barra de ferramentas principal desta tela de entrada de dados (como descrito na seção dedicada a isto) e selecione a opção 'importação ISO'. Este procedimento envolve ainda, como é de se esperar, a seleção do arquivo ISO de origem, que então deve ser 'carregado'.

9. Agora, um pouco estranho, o arquivo ISO está pronto para ser efetivamente importado para o banco de dados. Para isso, clique novamente no ícone 'Utilitários' na barra de ferramentas e selecione 'Importar ISO', onde agora o arquivo ISO carregado está disponível para importar (converter) efetivamente para sua base de dados ABCD. O software agora lhe perguntará se é possível realmente começar a importar os registros ISO a partir do arquivo selecionado. A lista de registros importados será mostrada em sua tela para monitorar seu progresso e sucesso.

10. Se seus registros recém importados não aparecerem imediatamente no banco de dados, reabra o banco de dados a partir do menu principal, isto atualizará os parâmetros do banco de dados.

11. Agora os registros devem estar visíveis e editáveis como registros normais, só que ainda não foram indexados no Arquivo Invertido, então use a opção 'Arquivo Invertido' de atualização na seção 'Outros utilitários' da tela 'Utilitários'.

> Advertência:
> Se sua série de registros importados for bastante grande (por exemplo, acima de algumas centenas), 
> é possível, dependendo do sistema em que você estiver trabalhando, que o processo seja muito longo 
> para o web-server (Apache na maioria dos casos) e não será permitido terminá-lo. Por este motivo 
> será necessário, em tais casos, realizar a ação de geração de Arquivo Invertido 
> não a partir do ABCD (como um ambiente web), mas diretamente da linha de comando, utilizando 
> as ferramentas CISIS dedicadas (para as quais outra seção deste manual dará os detalhes).

  
### Cópia de um banco de dados ABCD existente

Esta última opção é a mais fácil de executar, pois apenas um novo nome e descrição precisam ser inseridos, após o que o ABCD simplesmente reproduzirá todos os arquivos necessários em uma nova estrutura de pastas para o novo banco de dados. Os bancos de dados de origem que você pode escolher são os listados no menu banco de dados, em outras palavras: as descrições do banco de dados listadas no arquivo 'bases.dat' na pasta-bases do ABCD.

O sistema irá simplesmente - como acima - listar todos os arquivos copiados e criados em sua própria estrutura de pastas e pronto! Um banco de dados vazio, como uma cópia da base de dados ABCD existente, mas com novo nome e descrição, estará disponível para uso normal.


## Atualizar definições de banco de dados

A partir desta opção, é possível editar todas as 'estruturas' existentes ou tabelas de definição relacionadas a um banco de dados no ABCD. Em comparação com bases de dados ISIS 'normais', e a fim de suportar algumas características mais avançadas no ABCD, existem mais alguns desses elementos de definição de banco de dados, como pode ser visto no seguinte menu 'definições de banco de dados'.  

![](https://lh4.googleusercontent.com/VbTg7M4vPqy060v0DLr5r5Hc1-iRsXj23Hk5fpsyxo9t3FsRnhpk9wqnJihtlUXgiSE6tAD2IX6NN7u3NOM5Kl_BgCdV8N9ErylXlzgobzFoBdIcVwQP5y2592pTznr4MASFd16p=s0)

De fato, apenas as quatro primeiras tabelas são usadas em outros ambientes ISIS: a Tabela de Definição de Campo (FDT), a Tabela de Seleção de Campo (FST), a FMT ou folha de trabalho de edição e a Tabela de Formato de Impressão ou PFT. Como precisávamos delas também para criar um "novo" banco de dados no ABCD, elas foram discutidas na seção acima, com a única diferença de que, ao invés de uma tabela vazia, o ABCD apresentará uma tabela pré-preenchida com as definições já existentes.

Vamos agora tratar brevemente das definições adicionais para as bases de dados ABCD.

### Tipo de registros

Algumas estruturas de banco de dados, como o MARC, exigem que o "tipo do registro" seja codificado especificamente em um campo dedicado do registro. O software pode então usar este código para ajustar muitas características às necessidades específicas do tipo indicado, por exemplo, folhas de trabalho e formatos de impressão podem ser diferentes de acordo com este tipo, ou simplesmente - como é o caso do MARC - o formato quer ser muito detalhado.

O 'tipo de registro' de informações precisa ser coletado no início da criação de um novo registro, portanto, uma lista de tipos definidos (e, portanto, 'disponíveis') será apresentada como links, cada um levando à forma apropriada de entrada de dados subseqüente, como pode ser visto na demonstração MARC no ABCD.

Para definir tais tipos, o ABCD usa uma tabela 'Typeofrecord.tab' - localizada na pasta 'def' para o idioma real dentro da pasta www/base/[DB]/. Este arquivo é - como é freqüentemente o caso no ABCD - um arquivo ASCII que contém, para cada tipo definido, 4 valores separados por um `'|'` (caractere do pipe), de modo que isto pode ser editado diretamente com um editor ASCII (por exemplo, Notepad), mas dentro do ABCD é apresentado um formato de tabela mais fácil de usar:  

![](https://lh3.googleusercontent.com/vxYJnzAQtoYOlQ42XpphksTV7sTvdyZ_1x92W50iot6_PXKSqKe2ieDqglYgSlHcjQL-FCxZ9Sy5URXL6kCe-FWtzROKyDW0N4DZWiqfRvM9NLbrbV9dq82EoyhnDzlaG1brsT2r=s0)

 
O exemplo acima é a definição do tipo de registro MARC, que é mantido na etiqueta (interna) 3006 e tem as 4 seguintes colunas, cada uma contendo valores para cada tipo:

- o nome da planilha a ser usada para o tipo de registro dado - com o link "editar" ao lado desta primeira coluna também se pode editar imediatamente a planilha
- o valor 'Tag1', que na verdade é um código de um caractere para identificar internamente o tipo de registro
- o valor 'Tag2', não utilizado neste caso
- a descrição do tipo, como aparecerá na lista de tipos disponíveis. Clicando em "atualizar" abaixo do formulário, a tabela será salva com quaisquer alterações feitas.
    

### Validação de registros
    
A validação do registro permite que o gerente do banco de dados defina critérios em relação aos quais a entrada de um campo pode e será verificada antes de entrar efetivamente nos campos, ou após o registro do registro. A validação do registro no ABCD pode se relacionar a um dos seguintes elementos:
- validação de registros: as condições podem ser dadas para cada campo
- formato begin : o código pode ser dado para ser executado quando um (novo) registro é criado, por exemplo, a data de criação pode ser adicionada com a instrução date()
- formato final : o código pode ser dado para ser executado quando o registro é salvo, por exemplo, a data da última atualização pode ser adicionada com a instrução date().

Após selecionar uma das três opções acima, clicando em um dos tipos de registro listados (como pré-definidos), será mostrado ao editor onde as condições de validação podem ser definidas.

Estes critérios precisam ser formulados em - sem surpresa! - a linguagem de formatação ISIS. Com a linguagem de formatação pode-se verificar uma condição e, se (não) for atendida, uma mensagem de erro, que será exibida na tela seguinte, pode ser produzida pelo formato. Se o critério de validação foi definido como 'fatal', entretanto o registro não será salvo e o erro terá que ser corrigido primeiro.  

Neste menu-opção do menu 'Atualizar definições do banco de dados' cada campo definido será listado com uma caixa para inserir a declaração de validação. 

Por exemplo:

![](https://lh3.googleusercontent.com/oKu8hUaxkI7DKnHNYYzV2n78dodM6df_kALvB7fNV4OKE31M0dUFYVaXevZtFtmCYmpX0qoAxSYXSV5HXNMQt1IP506Wqan-MpU2LTJslPAJNd9jIP_YtbIcqzFNMWt5DJ9J0638=s0)


O formato usado aqui verifica a "ausência" de um valor no campo com etiqueta 2 e se de fato estiver ausente produzirá uma mensagem de erro de que este campo obrigatório está faltando. Como dito acima, os erros podem ser marcados como 'fatais' ou não. Com o link "ADD" na parte mais à esquerda de cada campo. Como mostrado na ilustração acima, com o link "ADD" na coluna mais à esquerda, pode-se adicionar mais campos, mesmo campos já utilizados com outro critério de validação a ser aplicado.

Ao clicar no ícone 'editar' à direita da janela de edição deste campo, a caixa reaparece em uma pequena janela separada para edição e a declaração também pode ser testada em um registro para ver se está fazendo a coisa certa. Após editar, é preciso clicar em 'enviar' para colocar o formato de validação possivelmente editado de volta à tabela principal.

### Formulário de pesquisa avançado
    
O formulário de pesquisa avançado é o usado no ABCD em dois locais: dentro do módulo de catalogação para permitir que o cataloger identifique rápida e/ou eficientemente um registro específico para edição (ou verificação de duplicação ou copiar) e no OPAC como o formulário de pesquisa avançada. Aqui o ABCD simplesmente oferece um editor para a tabela que define esse formulário de pesquisa com 3 colunas:
![](https://lh4.googleusercontent.com/SorkLWvyRODpnX8jui2-hUL_LhB6NpILr_Za1vwKLytNe_4RfO-Lwp_tYm_V2A7ocRQSTA3GAejqLNWjzSDtsMvC6Hd05vWxnahjyTw50Euss-dbJHbefvokq_5FyuW9jjxGPpFL=s0)

- A primeira coluna é o nome do campo ou 'índice', como aparecerá na forma de pesquisa
- A segunda coluna fornece o identificador usado para o campo especificado (ou de fato a combinação de campos) no FST
- A terceira e última coluna mantém o prefixo ou a cordão de inicialização fixo que é usado (se houver) no arquivo invertido ISIS para este índice.

O ABCD também apresentará, a seguir (à direita) desta tabela, o FST existente para facilitar a identificação de índices (campos para pesquisa) e os identificadores utilizados.

Clicar em 'Atualizar' salva a tabela, que de fato é o arquivo 'camposbusqueda.tab', armazenado na subpasta de idioma da pasta 'PFTs' na pasta do banco de dados.

### Lista de bancos de dados disponíveis ou tabela
    
Aqui, simplesmente é fornecida uma lista dos bancos de dados que estão sendo definidos como 'disponíveis' no sistema ABCD.As ações permitidas aqui estão apenas alterando a sequência (subindo ou para baixo) dos bancos de dados na lista e salvando a lista alterada.

![](https://lh4.googleusercontent.com/ft7Snl4rGz9hwaRty5XTgrPAanSM3zHrlHabOyEuj_6mGagJThOV6Hgc51WR9IXzKukInGcRBM1n-7l_3KyXpcOY0W4TUEem3QaYg6km54S0Tq2MkaianL_pJ1g6UH6QhNmP_x3n=s0)

  
Para adicionar ou excluir bancos de dados, é preciso criar o novo banco de dados ou excluir o que é retirado da lista. O ABCD cuidará automaticamente das alterações nesta lista.[!!} Os bancos de dados podem ser movidos para cima ou para baixo selecionando-os e usando os botões para cima/para baixo, como em muitos desses controles na interface ABCD.

### [dbn].par
Para cada banco de dados ISIS - em um aplicativo com vários dados, como o ABCD, há um arquivo necessário para informar o ISIS onde encontrar as partes constituintes dos arquivos de banco de dados - que, consequentemente, podem residir em qualquer lugar do sistema. Esses arquivos são nomeados após o nome do banco de dados (portanto, indicado aqui como [DBN] com a extensão .par. Novamente, este é um arquivo ASCII simples que pode ser editado diretamente ou, como é o caso aqui, neste menu ABCD.

  
![](https://lh6.googleusercontent.com/sJjlKFYiUph88YKCmjJvYnTZSiNFZUPnpIV3_aoEu2dX2GZ7iQ4_z5U71JO6GeRYcCRvfVWIy14Ic34k6X2gZjs1dRVw7kkpQbf9xMsUYulJVbHaIDhR5YAhzQnNOhHgi5ubFvt4=s0)  

Em princípio, o ABCD irá cuidar deste arquivo e certificar de que os caminhos (“paths”) necessários estão disponíveis. O único recurso especial aqui –- em comparação com o mesmo conceito de dbn.par em outros ambientes ISIS, é o uso de "variáveis", tomadas a partir de variáveis de ambiente do sistema operacional, que podem ser substituídas dinamicamente pelos seus valores reais. 

Por exemplo:

    %path_database%

É uma variável que realmente irá conter o caminho da base de dados definido em config.php, principal arquivo de configuração do ABCD.

No exemplo da Figura - Caminho dos arquivos das bases de dados, a última linha é uma linha interessante porque informa o caminho para a base de dados “loanobjects” para a exibição da informação de cópias – exemplares – (se incluído em uma das pft’s MARC), com a função REF. Com objetivo de encontrar a base de dados loanobjects para a utilização de REF->loanobjects, ISIS precisa saber o caminho para esta outra base de dados e, portanto, deve ser incluída no dbn.par.

  

> Nota:
> Para que este último recurso também funcione no OPAC (iAH), é preciso adicionar 
> o caminho para a primeira seção do arquivo dbn.def. 
> Por exemplo: a base de dados loanobjects deve ser apontado por uma nova linha que contém:


    FILE loanobjects.*=%path_database%loanobjects/data/loanobjects.*

### Arquivos de ajuda em campos da base de dados
    
Para cada campo da base de dados, o ABCD pode fornecer uma página de ajuda, que pode ser editada a partir desta opção de menu. Para apoiar a criação de tal página, ABCD colocará, automaticamente, todas as informações conhecidas da FDT já disponíveis no campo dado. Com o editor HTML embutido (baseado em JavaScript) uma página de ajuda bem simpática pode então ser produzida e salva. O link “Visualizar” permite verificar o resultado do seu esforço de edição.

![](https://lh3.googleusercontent.com/86HYiZn_9klIyIPWshK6DiZqkH2UUbz3FDsEAfldXlD_OaOAbmvNTq7tKWm9nDicDZo8eqSAK0WoFf2AhTvtNCaEWnWnXfdLLy120Yqt8LJ8RlCX_xLHWnz2ZjGfbeohmeKpynE8=s0)

  

### Configurar base de dados no iAH (ou OPAC)
    

A fim de poder utilizar uma base de dados ABCD recém definida com a avançado interface iAH OPAC (ou no Site ABCD), um arquivo de configuração especial deve ser editado: dbn.def. (onde dbn tem que ser substituído pelo nome da base de dados real)

Este arquivo tem as seguintes seções a serem editadas:
  

1. **Seção Files**: aqui precisam ser informados os caminhos (paths) para os arquivos a serem acessados. Nesse caminho, ambas as varáveis %path_database% e %lang% podem ser usadas para se referir respectivamente à base de dados e ao idioma reais em uso.
![](https://lh5.googleusercontent.com/XzbGmhr000O_9jU0KhhbX-0UJLCR9zI0rLo-L_A0z13CZaPHFL6UbDRpB4-mwbuKLBq7ep2OfyAsBpTNPfhGjrU4ZYHDKPzqQXk-Z6ByNQIIuekR6Czye_oWsRW1jnZYh4VU6yHp=s0)
    
2. **Seção de Index-definition**: aqui todas as informações para os idiomas ativos (numerados como 1, 2, 3, etc.) têm que ser fornecidas (em subcampos) para permitir à interface reconhecer os prefixos usados para cada campo pesquisável e nomear o campo de acordo. A primeira linha com o prefixo `TW_` é a que é utilizada para a interface de pesquisa “simples” (semelhante ao Google) para pesquisar palavras nos campos definidos (pelo prefixo da FST) para serem incluídos nesta pesquisa simples. Isto é indicado pela presença do subcampo `^d*`.

3. **Seção Gizmo**: aqui - se necessário em casos específicos – podem ser referenciadas bases de dados “gizmo” para substituição automática de strings por outras strings (que podem ser usadas para alterar os códigos da cadeia de caracteres, mas também para alterar códigos e abreviaturas para valores completos, etc.).
![](https://lh6.googleusercontent.com/i3z71qKLcIxk8mqXAMyAccsJ2Hx1QG_uB2OvNG9nlLNCryQDE2QUmKbltjRbUYsjYLrA2Kgl1hD3RkO8NqA_30i9U9xZ2_WcrsnJIx99Y0NHHKhYuP-UO8avSXhZdu0H091ud26f=s0)
    
4. **Seção Formato**: aqui devem ser definidos os formatos de exibição utilizados no OPAC para cada idioma (nos subcampos numerados), com o rótulo a ser usado na tela. Lembre-se que apenas os formatos (arquivos com extensão PFT) podem ser usados aos quais é feito referência, de alguma forma, na seção de ARQUIVOS! Também o formato default pode ser identificado, simplesmente indicando qual dos formatos anteriormente referidos deve ser utilizado como formato default de exibição.
![](https://lh6.googleusercontent.com/njC4b_3cU7HUeqbQOeT3bVrsJ7jbEngMbisQdVhUxB8g5FYzmUFkZJlS3ISRFVUA4VzKmcgYnMmKeC4S1DA-aUGa0AD-vWEgeh3cz7GIGIkfFLzrCTgykCUDhru5dhvsYScb6PeX=s0)  
5. **Seção Ajuda**: aqui simplesmente devem ser referenciados os arquivos (HTML) que contém as respectivas páginas de ajuda e páginas de notas para o usuário desta base de dados no OPAC.
   
6. **Seção de Preferências**: aqui o administrador do sistema pode indicar quais das três interfaces de pesquisa (simples, avançada e livre) estarão disponíveis para esta base de dados, bem como alguns outros recursos adicionais da interface: se será possível o envio de um resultado de pesquisa para um e-mail, se os resultados devem ser listados com botões de navegação, o número de registros a serem exibidos em uma página e se exportação XML será oferecida.

![](https://lh4.googleusercontent.com/SUqlv_DS-5N3Kxc36LQEGCNl49_0RclTci9RUwEjAFbRTp6F3rm55qyt1apeIPfGjOi4985rdzkLB6gKnntkAsckRq8NX5AxOQoTndC8SeZZQj1iZnwto9U4jj5h32emFdv_LRgp=s0)

### Estatísticas: lista de variáveis
    
Esta opção simplesmente permite definição rápida das variáveis da base de dados com as quais tabelas para análise estatística serão processadas. Para cada critério ou variável (como linha ou coluna da tabela) um nome e um formato de extração tem que ser informado. O formato de extração – usando a Linguagem de Formatação, é claro – define exatamente como os valores do campo devem ser obtidos para computar o valor da tabela. Fazendo isto, é possível, por exemplo, definir um intervalo de valores do campo para serem combinados para um critério da tabela. O arquivo em questão é na verdade ”stats.cfg” da seção def (específica de idioma) da pasta da base de dados.

  
![](https://lh3.googleusercontent.com/wC2Pm3_FdQWQeRseA-9bJvV9cek-D4kLLVBFCxGOiBsn1HP357CwdJfYTJmOMXU-96a4o38eL5Tim6ZbtxW3UaQ2mZBIdfbO0Z3elCOPoEKLu_d9OnmbOqdNYdqKhVnHKHPfY5H4=s0)  

A opção para definir um prefixo ainda não está implementada nesta versão do ABCD. A idéia é que os valores seriam retirados do Arquivo Invertido, prefixados pela string definida aqui. Ao fazer isso os valores seriam computados enquanto o registro for “invertido", não na ocasião de produção da tabela de estatísticas, e permitir, portanto, que a produção da tabela seja mais rápida.


### Estatísticas: lista de tabelas
   
Tal como acontece com a lista das variáveis acima, ABCD também mantém uma lista de tabelas disponíveis, que foram definidas anteriormente, para o módulo de estatísticas. Este arquivo ”tabs.cfg” igualmente fica na pasta def da base de dados.. Cada linha deste arquivo contém três valores (separados pelo caractere pipe): o nome da tabela, seguido por dois critérios utilizados nesta tabela, por exemplo:

    Classification code / Publication date|Classification LC|Publication date  

![](https://lh5.googleusercontent.com/4Yz-wvMo6dXPEaPLOyoNg3QkqnJqEGBFyWf8_UA5gUKhPkSqtEF-8Gpnyawe6T1qzTzTYjtg0iihrGdCocgsiUnbthqSA0Z8AQ8c9EbXYfmOGC2xQuOu13xg5fCSrREfP1xE__W9=s0)

Como pode ser visto a partir do exemplo, o editor no ABCD simplifica a edição, oferecendo cada um dos três valores individualmente, mas também através de listas de linhas e colunas de critérios disponíveis. 

## Relatórios

Na verdade a criação de relatórios no ABCD significa criar formatos (PFT’s) de Linguagem de Formatação ISIS com os quais a opção de Relatórios irá criar saídas, pois com a LF qualquer tipo de relatório pode ser produzido e salvo para posterior reutilização.
Por isso, consulte a seção "Formato de Visualização (PFT)" da opção "Atualizar Definições de Base de Dados” do menu Central. Exatamente a mesma interface é utilizada aqui.

## Utilitários
Nesta opção ABCD oferece algumas operações muito básicas sobre bases de dados: ![](https://lh5.googleusercontent.com/jHTrAoEZoonuu-fniMYnXtwtpKFWZ6iSyvT3yhksNy7-s0LYqs7QO2znmgtGZIcv0ZK6sRt04TJusqcNN0sYDMT4z5_Cr8dopMFvIUjDBqop84967SdUx8E4SeYZLSSSzE7zOLzo=s0)

- Inicializar a base de dados significa apagar todos os registros da base, mas sem mudar as estruturas da base de dados;
- Apagar a base de dados significa, naturalmente, eliminar totalmente toda a base de dados com todos os arquivos e pastas correspondentes da pasta \bases do ABCD;
- Bloquear a base de dados significa evitar que quaisquer outros usuários façam alterações nos registros (entrada de dados), por exemplo, quando estiver prevista uma geração completa do arquivo invertido; 
- Desbloquear a base de dados significa liberar novamente a base de dados para outros usuários. Use essas opções com todos os cuidados necessários e com precaução!; 
- Atribuir Número de Controle é a opção para atribuir automaticamente os números de controle sequênciais em uma série de registros selecionados. Somente uma série contínua de MFN’s pode ser selecionada aqui;
- Ligar a base de dados com a base de dados “copies”: como explicado na própria tela, aqui a opção para ativar o uso da base de dados “copies” pela base de dados (bibliográfica) deve ser ativada;
- Reiniciar o Número de Controle é a função para redefinir manualmente um valor numérico específico do arquivo “control_number.cn” da base de dados, no caso de, por algum motivo a numeração tiver que ser gerida manualmente. Por exemplo, colocando este número para 1000 fará o ABCD atribuir, a partir do próximo registro, os números de controle a partir de 1000. Isto pode ser útil em situações em que, por exemplo, diferentes centros de catalogação estão usando diferentes servidores ABCD, mas as bases de dados resultantes devem ser consolidadas em um catálogo com números de controle não interferindo, cobrindo assim diferentes faixas. Por default, no entanto, o reinício irá reverter o “control_number.cn” para 1, como o número de controle básico de onde começar.

## Configuração de Z39.50
    

Aqui a interface ABCD permite atribuir alguns parâmetros para definir quais os servidores para serviços de catalogação compartilhada Z39.50 serão oferecidos na lista Z39.50 e mais alguns parâmetros para assegurar o uso adequado do protocolo do servidor. Essas informações técnicas podem ser obtidas, em geral, do fornecedor do serviço, por exemplo, no caso da Biblioteca do Congresso (USA), consultar o seguinte website: [http://www.loc.gov/z3950/lcserver.html.](http://www.loc.gov/z3950/lcserver.html)

A configuração do Z39.50 tem as seguintes partes:

  
![](https://lh6.googleusercontent.com/ITrPEbvuGaSe7_zQeYSHHfBd8_KKHSWJsncTede3hrzK76SanHdAtZjXecP_pYxAyswJym0WD0ISJA6wUAyjsQnW6LLxVAtjEScBwW0oZzCsDfb_aeIeOPszhN3x5QAu_e6j1TEk=s0)  

- Configurar servidores Z39.50: os servidores definidos devem ser configurados em uma interface similar à de administração de usuários, com os nomes de parâmetros, URL, Porta, Base de dados e UTF-8 (ou não), veja a ilustração abaixo para a Biblioteca do Congresso. Novos servidores, é claro, também podem ser adicionados como o ícone “Criar”. ![](https://lh5.googleusercontent.com/7abTBVqO1hMgGJI9lE5T0J-uC7hF66DKPF5C6CeZRd_UNwgYg26RwJpWkQtqiLn5cexTN8GeCRpM_i5W2wmOblqxOE7LVLQM-Et_9rjWsje-gZ-KUg9SdWyQOmI9JUHnl94HGTaI=s0)

- Formatos de conversão: quando os registros de entrada (na maior parte em formato MARC21) precisam ser convertidos para o formato utilizado na base dados destino, aqui um formulário pode ser editado para especificar a conversão da fonte para o destino. O nome, subcampos e tag do campo de entrada serão listados e na coluna “formatos de conversão” a LF ISIS define a forma de extrair valores para este campo na base de dados de destino. ABCD vem com uma tabela de conversão demo para converter do formato MARC para o formato CEPAL, com o seguinte exemplo para converter o campo MARC ISSN para CEPAL. ![](https://lh6.googleusercontent.com/NzKlW54uaVPpDnsfqjqhPihGxAj66yQpcXmYVXHYXu5M8vlScNcr5oPrnfojykpvvFvtsgN7pKjEJo7AgjPN5-rgnPcJU-ROa-Jr1gDy3R-h9eOrjkWjbNAV4ku1XRobgzBvN_I3=s0)

- Tabela de conversão de caracteres MARC-8 para ANSI: esta é uma tabela que converte os caracteres MARC-8 (por exemplo, âa) para o formato ANSI (por exemplo, â). Esta tabela pode ser editada, se necessário.

-  Finalmente o Z39.50 pode ser testado a partir daqui, com a mesma interface usada no módulo de entrada dados do ABCD (ver abaixo).

## Traduzir mensagens e ajudar páginas

Existem dois tipos de conteúdo, sensíveis por idioma, utilizados pelo ABCD, que devem ser editados quando se vai criar novas ou adaptar outras versões  de idiomas: mensagens curtas e rótulos, por um lado, e páginas completas de ajuda por outro. Estas podem ser editadas para outros idiomas para cada módulo do ABCD Central.

### Tradução de mensagens curtas e rótulos

A edição destas é facilitada pela apresentação dos termos e frases do idioma default (Inglês) em uma tabela na qual na segunda coluna devem ser colocadas os novos valores pelo tradutor. Para cada uma das principais funções uma tabela como esta é apresentada:

![](https://lh6.googleusercontent.com/m1hz1TJkkEYhsRxPYlyht1xMnpY6J0i5-pz0mnnWpYx6X55NuFqRs1ImHIPUDEQRMqmdmn_d-E0A8mysiZdHBaxbXTo64z97dJiR8n2cgRGBg1yjG-rJaiUIfIl_YxkxeSo0eUX-=s0)

Aqui está um exemplo de algumas mensagens traduzidas do Inglês para Holandês referente ao módulo de empréstimo:
![](https://lh3.googleusercontent.com/O0iI1_pPKlVklFOKS-sGzp3vgeYfzn3osmyn-TV6Q6TYBX1DrmZ1VSExhfOWIuH6KrS6FrRZcZJjnz-w-me5BVRgeZlGt4TscelQuLcCZXHKIh04XkhhyEqZACxI1miCqJyBBcA6=s0)  

Essa tela fornece um ícone “salvar”  para armazenar a tabela com as novas traduções. ![](https://lh3.googleusercontent.com/dXAH4i_glKZgtTCotEYcefBtDLWMyqWrBU9S9YAu6qxRLhe8UD8VGqaIIYhqZKLcGCmLOQwwyO9HdFGU20PzL6iJjEbTIAMcnDH4Sg2AlZCGVOeqlUZh69EVziP-zzlx3StZuLNP=s0) for storing the table with new translations.

### Tradução de páginas de ajuda
Aqui a abordagem é diferente: é fornecida uma lista de páginas de ajuda disponíveis:  ![](https://lh4.googleusercontent.com/W84ZVXybbCMZqEaGoEVBhZ0kEuuMULAumIlD2Fgkgi2Br3ZacVBgWZUtlxSXNVjYFkocdIrNEGOcNXzQUmMQmSskQ6vI_b58cOKlrD0zZFqOvqk9O0EVkyfbyOE0F8BC02bQRSmr=s0)

Para cada arquivo de ajuda pode-se “visualizar” ou “editar” a página. No caso de edição, será provido o editor HTML embutido, baseado em JavaScript:
 ![](https://lh3.googleusercontent.com/6p6kLKxf78YCkDM7Agwx-OgiarG2cPyZ-SlpwoJnzqu6pZ2baVtKRuJiGGU1uEFyBMOLl1I09ulIJcq5c18t10V36CLKPQa3UEXd4hMs9TdodCmAR3FpGahQCngPuOTYnV_PCBAy=s0)  

  
## Explorar o diretório de bases de dados
    
A exploração do diretório de bases de dados pode ser feita (quando a opção de variável dedicada “$dirtree” no Config.php é colocada em “1”!), usando uma exibição especial na página web ABCD das pastas da pasta “\bases” do sistema:
![](https://lh6.googleusercontent.com/0aF6Wene-a2HY8S_9g8yTE19Qdn195lR3Dppjawr4Y0sLECjEl6fQuAkwgcXOPYQJb64s5Kd2yd7-DBp8IWQnFchTEvETm9VDo6XtuFdyvJ-_nmSac7u_r3PEOKRX4eOxL9PNZfE=s0)

É possível entrar em subpastas e até mesmo editar, renomear, zipar, etc., alguns dos arquivos texto e depois disso, clicando no ícone "detalhes" ![](https://lh6.googleusercontent.com/auQdMSP6XtrDRMBZbxonDmbg01ii0m7BKIUjaxtxWEJK_CccgXfNI11wiSCVaXkrHF6a3dHiqe8OXB1HAz7FtiOKUAqQiLNjTKVEfuwFseFHKSPJNBmRycQ9NUWAFPWXBRmeAYSw=s0) , dando, por exemplo, as seguintes opções para aplicar ao arquivo selecionado:
![](https://lh5.googleusercontent.com/7wIzZpzlZ9Yo7YsN4mLs1N3z7Iiw9Hduh8FhK6rPUtFK_X8GurPs6qCU-Ya9UyoYjEyKG0iRMWY0ExHQ8_E6-PkCQcKZH0BU4piwyH1bl9SZUID694XNos8my4iYpchMWXWoAmKb=s0){:class="img-responsive"}  

## Estatísticas

O módulo de Estatísticas do ABCD também tem um capítulo dedicado, por isso aqui faremos apenas a referência a este capítulo, visto que esta função também pode ser acessada a partir deste menu, mas também a partir da barra de menu de catalogação e de vários menus dos módulos de empréstimos e aquisições.