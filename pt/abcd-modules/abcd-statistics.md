---
title: Módulo central - estatísticas no ABCD
description: O módulo de Estatística pode ser invocado a partir da Administração principal
lang: pt
lang-ref: abcd-modules/abcd-statistics
---

# Módulo central - estatísticas no ABCD
    

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---


O módulo Estatísticas pode ser invocado a partir do menu de administração principal ou da opção da barra de ferramentas de catalogação:  

![](/pt/images/abcddoabcd1_html_cfa08dca0bc74fd4.gif)


A tela de Estatísticas oferece três funções principais:

1. Usar uma tabela existente
2. Criar uma nova tabela
3. Gerar saída
  
## **a. Usar uma tabela existente**
   
Tabelas existentes são listadas na lista de opções pelo seu critério de linha/coluna. Na versão ABCD demo, uma tabela foi pré-definida: uma tabela “código de classificação por data de publicação".

> Nota
> A lista de tabelas disponíveis é obtida a partir de um arquivo de texto “tabs.cfg” 
> na pasta /bases/[dbname]/def/[idioma]/. Este arquivo contém, para cada tabela pré-definida, 
> três valores separados pelo caractere “|”:

 - o nome como exibido no menu de tabelas (que por razões de clareza pode ser uma menção de ambos os critérios);
 - o campo para as linhas;
 - o campo para as colunas.

Por exemplo:
  
    Número de classificação / Data de publicação|Classificação LC|Data de publicação
       
![](/pt/images/abcddoabcd1_html_74661ef69844666c.gif)

Após a seleção da tabela, simplesmente continuar usando a opção “Gerar saída”, veja abaixo.

## **b. Criar uma nova tabela**
    
A tabela tem que ser definida, identificando quais os valores (como contidos em um campo da base de dados ISIS) serão utilizados na direção horizontal (linhas) e quais na direção vertical (colunas). ABCD irá mostrar uma lista de variáveis de critério disponíveis (ou campos) para selecionar a partir de ambas – linhas e colunas.


![](/pt/images/abcddoabcd1_html_212f1cff531bdd69.gif)

  

> Nota
> A lista com os campos ou critérios disponíveis é obtida a partir do arquivo textual “stat.cfg” 
> na pasta /bases/[dbname]/def/[idioma], que contém em cada linha um critério, 
> especificado como um nome de campo  e uma PFT para definir exatamente como os valores 
> devem ser extraídos do campo.

O exemplo demo da base de dados MARC é:
  
```
Classificação LC|v50^a
Data de publicação|if val(v260^c)<2000 then '1900-2000' else F(val(v260^c),1,0) fi
```

A segunda linha mostra como ela pode ser mais do que apenas um simples valor de campo, usando condições, etc.

Uma vez que ambos os critérios: linhas e colunas foram definidos, a tabela pode ser usada para gerar a saída como explicado abaixo.

  

## **c. Gerar saída**
    
A geração de saída no ABCD envolve duas etapas: a criação da tabela com os valores e - se assim for  desejado - a criação de gráficos de saída ou exportar a tabela para outros formatos de documento externo (por exemplo, para o software de planilha eletrônica tipo Excel que oferece, em geral, possibilidades mais avançadas/detalhadas de produção gráfica).

Antes de criar a saída é preciso definir o intervalo de MFN’s (de registros ISIS), para ser utilizado ou uma expressão de pesquisa para aplicadas às estatísticas apenas a um determinado sub-conjunto da base de dados. Na caixa “pesquisa” (ou query) pode-se usar a Linguagem de Pesquisa ISIS com qualquer expressão válida.

![](/pt/images/abcddoabcd1_html_44510d97236fbd1c.gif)

  
Critérios de linha e coluna (por exemplo, os documentos publicados em uma determinada data de publicação, pertencentes a um dado código de classificação LC). 

Tenha cuidado para não calcular tabelas com valores individuais de intervalo estendido (por exemplo, todos os anos ou códigos LC), mas sim usar a linguagem de formatação para combinar os valores em classes, uma vez que isto, provavelmente, faz muito mais sentido, no seu relatório estatístico. 

O exemplo acima dá algumas dicas sobre como obter essas classes, usando uma condição a ser aplicada aos valores de uma data, assim o usuário pode derivar mais classes deste exemplo básico. Neste sentido, o seguinte trecho de uma tabela dá um MAU exemplo, pois os valores das células são em sua maioria, se não sempre, “1”, devido aos critérios de linhas e colunas serem muito detalhados:

![](/pt/images/abcddoabcd1_html_959ff37ab6c3c758.gif)

As opções de saída dadas pelo ABCD são os seguintes:

![](/pt/images/abcddoabcd1_html_bc2b7d4c2fd8565e.gif)


- Saída para uma planilha irá transferir a tabela para uma planilha eletrônica para posterior processamento;
- Saída para um documento irá transferir a tabela para um documento de processador de texto para posterior processamento – isto pode ser prático para incluir os resultados em seu documento de relatório anual, etc.;
- Saída para impressora permite a impressão direta da tabela, usando uma impressora disponível em seu Sistema Operacional.
- Existem duas saídas gráficas fornecidas pelo próprio ABCD:
    * Gráfico animado: esta é uma forma fantasiosa de mostrar os gráficos, adequado principalmente para apresentações de monitoramento de atenção (mas que requer software Flash instalado no computador);
    *     • Gráfico não animado: a exibição dos gráficos, mas sem a fantasia de animação.
Em ambos os casos diversos estilos típicos de saída gráfica (barras horizontais ou verticais, linhas, barras tridimensionais, etc.) estão disponíveis e podem ser selecionados. 

![](/pt/images/abcddoabcd1_html_66aff427c54cdae3.gif)

Se você não estiver familiarizado com esses estilos, porque não experimenta apenas e decida por si mesmo qual apresenta a mensagem das estatísticas da forma mais clara? Lembre-se que a transmissão de uma mensagem é a coisa crucial com estatísticas aqui, não impressionando o público ou o leitor com uma montanha de dados – como é frequentemente o caso com as ferramentas de estatística. Muitas vezes quanto mais simples mais convincente!
Um exemplo de saída em forma de gráfico parece como este:

![](/pt/images/abcddoabcd1_html_84f5e1bd59fe5345.gif)