---
title: Módulo central - gerenciamento de aquisições
description: Este módulo trata da administração de objetos recém-adquiridos e de uma função de pré-catalogação. Os objetos pré-catalogados podem, uma vez adquiridos, ser armazenados como objetos para o módulo de Empréstimos. É disto que se trata a 'integração' do ABCD.
lang: pt
lang-ref: abcd-modules/abcd-acquisitions
---

# Central module : acquisitions management

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---


Este módulo lida com a administração de objetos recém-adquiridos e uma função de pré-catalogação.Os objetos pré-catalogados podem, uma vez adquiridos, ser armazenados como objetos para o módulo de empréstimos.É disso que trata a 'integração' do ABCD.

O módulo de aquisição possui as seguintes funções lógicas principais:

1. Sugestões: O processo inicial de obtenção de objetos
2. Pedidos de compra: a aquisição real de objetos
3. Bancos de dados: Gerenciamento dos 4 bancos de dados relacionados a aquisições (sugestões, provedores, ordens e cópias)
4. Administração: Configuração, Estatística e Relatórios, Ecaking (descartando objetos).
   
   Vamos discutir cada um deles com mais detalhes.

  

## Sugestões
    
O 'fluxo de trabalho' lógico das aquisições começa com sugestões (por usuários da biblioteca, colegas ...) para comprar um livro, seguido logicamente por uma decisão de compra (aprovação ou rejeição), um processo de licitação e uma decisão sobre onde comprar o livro.De onde vêm as sugestões, neste momento, ainda não foi incluído no ABCD, mas é concebível que exista um formulário para enviar sugestões em uma página da Web (por exemplo, o site ABCD) ou um e-mail possa ser enviado ao bibliotecário, para ser convertido automaticamente em um registro de sugestão ou para ser editado manualmente em um registro por um bibliotecário.

Um recorde de livros sugeridos, realmente comprado, precisa ou não ser mantido para uso futuro (por exemplo, quando o mesmo livro é sugerido novamente).

Esse fluxo 'lógico' é mais ou menos refletido no módulo ABCD-aquisições.

![](https://lh3.googleusercontent.com/bcuWHmk_C_prO4coXDPmyKh70c1fZtTIuMoV_CcBvCcFoKTcJl9WsMwFyL98yVv1x4Y9RW7M5RGn9PFEd1wpcXb93ldJrXpL0jgZAK5ZHOdYADys3AhWPoUyOI1Ake4VonklF084=s0)
 

### Visão geral
 
Aqui, o bibliotecário pode consultar o status das atividades reais do sistema de aquisição, com a opção de obter uma listagem (aparecendo em uma janela separada) da atividade.

![](https://lh4.googleusercontent.com/IHJOwV2flvWXF32GOL1SD75oH2SBjncmd3N8rZvYfgQZC0X5JUx1TYPf2ljxQ0_XCnvIkHm2KjieLq7bpiP48RO5lRkTImbPGL4s6PbuxVvS6oesOottVyRKjoP9dIF4X6bQVC9E=s0)

Nenhuma alteração ou funções de edição são fornecidas aqui, portanto, isso é apenas para consulta do sistema de aquisições.
### New suggestions
    
Aqui é fornecida uma oficina para inserir uma nova sugestão para adquirir um objeto, com alguns campos bibliográficos, mas também o status e um campo 'recomendado por'.Aqui é mostrado parte da planilha de entrada de dados.

> Nota:
> Para o campo 'Data da sugestão', uma função pop-up é
> usado.

 ![](https://lh6.googleusercontent.com/9Knt0Wpqe7MLnlfwSP4vNuWYbhvar82E2oxiM_0zPR7km0q8D5O0OvIlfkZsprs3MmX1UgEBjGDO5rKouj9vJk6297S9pjRuohwT06n3ZFRKOZEsFrAuH7T7KhEWoxpLN-63fRsK=s0)

  

### Aprovação/rejeição
    
A ABCD fornecerá uma lista das atividades solicitadas com seu status, classificáveis por qualquer título, recomendado por ou data de recomendação.![](https://lh3.googleusercontent.com/b6XdMqJJ_d3R-wkVCCD29MMPF1ytPirgxp2TnBPgXZ35vCg39cUY86XAKuTtf0ofFVo1ZqOwh6hu9UfeTsJYsorDHowuBqTBUDe6FWzgYhet7qpknhrAquXGdGkv1jLfxxS_4NEy=s0)

Cada um dos itens pode ser aberto para edição, onde a aprovação ou rejeição real pode ser fornecida.Under é um exemplo de um item rejeitado:![](https://lh3.googleusercontent.com/iZri8tgNYj3XQTdX7XjqcUxdRfJpxUGMth99sx4jafOAVYxds9WIlJbUr7Z9iMAWsP0k514SIfB_1L60_2pk5cq4pjMtVBhW2LrbLEQGrrrpdr5M-C4i5ajpP11LmAbqoEpWYByt=s0)

Neste ponto, depois de ter cancelado ou salvo (atualizado) a transação, o acesso direto às opções do menu principal de aquisição também é oferecido:  

![](https://lh4.googleusercontent.com/fB363ccjR85F7WIgt5yMt3k8TwSr3S0E6yYtxeOAbPdvzKmZOmxL1nrCzRiv73E26kZT5_7g2KE3c4E_5GcKsgLm4M5zKLt-8GzBCGoUjyIkb9iyKO6jYa70O6GV3ZAq7WPFquFr=s0)

Também são fornecidas opções para enviar a listagem para um documento (formato .doc) ou uma planilha (.xls).

### Licitação
Nesta fase, o ABCD oferece, a partir de uma lista classificável das transações reais, uma planilha em que o processo de licitação pode ser mantido rastreado: para cada participante da licitação alguns dados essenciais (nome do licitante, preço oferecido etc.) pode ser armazenadocom uma caixa para marcar a aceitação ou não :![](https://lh6.googleusercontent.com/g_kBXTBxOL37DF1sUQoK9dKxqB0x41OVj2d_C16Y_PN6qgtPMdwNfqLdXyJBw0MTqaEf9GTkuVgWgd2ovN3UiCTbHoOyKktzmhGdI0tRFqZNjQaswA5I8Yg-u8gKf9lEbuCU6T7s=s0)

  
### Decisões
    
Finalmente, a administração de recomendações é concluída por uma lista das ofertas aprovadas em um formato (folha de trabalho) semelhante ao acima.Novamente, essa listagem pode ser exportada para um documento ou um software de planilha.

## Purchase orders![](https://lh4.googleusercontent.com/VvdeA8DWKRDWAKHdh7JCMUzdZzC2kyz9RdX2cWpvxLFSL_NsK-gwzIeeNjL4B13FjO4ZZjfMgaMrjVFETIslehLG-gNWEqwyy2Pe8I84fbM2Ldl0Pc2rcgZC5Php7EQKNsrs8ywa=s0)
    

[!!] As novas aquisições precisam primeiro ser categorizadas como compra, doação ou troca.De acordo com a opção selecionada, o formulário de edição subsequente conterá elementos ligeiramente diferentes, mas estes não precisam de muita explicação aqui.

  

> Nota:
> Em muitos casos
> Através do estágio de 'sugestões'.Aqui é possível criar um novo
> Encomende sem ter que se referir à fase de sugestões.No entanto, lá
> é outra opção aqui para lidar com sugestões aprovadas e para
> Continue o procedimento completo no processo de aquisição real.

O ABCD facilita a ordem dos objetos, fornecendo um formulário para criar um novo pedido, listando os pedidos pendentes com a possibilidade de edição e fornecendo uma possibilidade de listagem ou pesquisa na lista.Os itens recebidos, com seu preço e número de itens adquiridos, podem ser preenchidos. Sempre que uma seleção deve ser feita a partir de uma lista de candidatos, eles podem ser classificados por diferentes critérios listados acima da própria lista.

As aquisições recebidas podem ser inseridas no inventário com a data e o número de pedidos em um pequeno formulário:

![](https://lh3.googleusercontent.com/IJ1SR4jvJdoJG1Flo54azKvQM3I8_qE-NWjxKOsO41QhmVWWQRojyx6TXPmDwrVsPrQpzEHkE-ysbPWub4Boa1Dy4E84oIYVDo2xzx3PCnzq-taturS4OKkn0AmtM87xTzihzpSu=s0)

  
Listar os pedidos recebidos é a última opção aqui :![](https://lh3.googleusercontent.com/FwAkDrkyTDJsuH5oaOPNLLzT8xQQkYp1r5VWDdGdhewGmhFcAg2zQ-_1xa1wfKFDl0UgorZVSU0mqwHcdNNnU3Xsohf1ejU1RXfmSEIdx8KM0RvxNu999mN2_hs_87E5ETWP0B3m=s0)

  
  
## Bancos de dados
![](https://lh3.googleusercontent.com/H9nxCHjXX-oJSYHrnweFJcYHs50yedUiX25ybxXlgZGxlLbTVVg-UWxaLmShSr5Y06lQTfd3Ok9Q65WBNLJoL1ji6P3e33B5RDTWy-d6BKdw4AwKLeQxyWrUnY_Tpd8a5iJWW8EZ=s0)  

O módulo ABCD Aquisitions mantém 4 bancos de dados, que podem ser acessados diretamente aqui, cada vez com uma função de pesquisa para uma recuperação rápida de um registro específico.Cada um dos registros recuperados pode ser editado com sua planilha dedicada e salva, se as alterações foram feitas.Como exemplo, mostramos aqui o banco de dados de provedores.![](https://lh3.googleusercontent.com/6igvzaOdbOiX_jqNUsh16EAxlIQqapDOkSehCg4vrS0BvPJteHKmfWcTkrfNf1rL-hfEDTDL2AqVqOdx1wkx-w4sX0FXdqFyndz-z_weJ6miH4LKisa7e3klLBcpEI1T518FvmDP=s0)


O ícone 'Criar' permite criar um novo registro de provedor.

## Administração de módulo de aquisições

Nesta última seção do módulo de aquisições, algumas funções são oferecidas para gerenciar o sistema de aquisições com relatórios, estatísticas, configuração de alguns parâmetros e também erguer o sistema de aquisições, excluindo itens. Na versão inicial, apenas uma função é fornecida: redefinir o número de controle (que é o número do último item inserido ou número de controle de cópia, ao qual 1 será adicionado ao criar um novo (campo 'Auto-incremento'). Na verdade,Este número é mantido em um arquivo 'control_number.cn' na pasta `\ABCD\www\bases\copies\data\`, onde simplesmente o último número atribuído é armazenado.Sempre que as cópias são criadas, esse arquivo é protegido por gravação para evitar a duplicação do mesmo número por usuários simultâneos - para que outros usuários tenham que esperar até que esse arquivo seja gratuito para gravar.![](https://lh3.googleusercontent.com/Hpl24GzcIA7jYEUBUC7P41oEAd6nePawzewtXaWLiAmZr9_s-WI5ZYU9mzX4Ur5LfwWaluxKB2WVIW2x3U3011L96ocl3gyNid-B3NfhMgeoBivVweWAMXHLwDOmbFotkwZblv9L=s0)
