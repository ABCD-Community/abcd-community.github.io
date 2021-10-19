---
title: ABCD OPAC
description: ABCD Opac permite até 3 níveis de pesquisa - Metasearch, Pesquisa em um banco de dados específico, Pesquisa em um subconjunto de registros em um banco de dados
lang: pt
lang-ref: abcd-opac
---

# Características

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---


O ABCD Opac permite até 3 níveis de busca:

- Metasearch
- Pesquisa em um banco de dados específico
- Pesquisa em um subconjunto de registros em um banco de dados (tipo de material ou outra classificação definida por um prefixo FST)

## Metasearch

Aplica a expressão de busca a todos os bancos de dados definidos no arquivo bases.dat contido na pasta "opac_conf" da pasta bases. A opção Iniciar na barra de menu ativa a metabusca ao exibir esta caixa:

![](https://lh4.googleusercontent.com/LP69w4E576tCSQwv0ERfFbzVqAjDWO4JUGLYxDZRTR62DIZfEEXdBxB9TGuOoENmVG-lXAaDtD89-lBhwmo7izjmIJiSq1BkgNWyVOZDngEmyFIyEy5sG0_5Xtz6VJBhFpVjzGH6=s0)

Se uma ou mais palavras forem colocadas na **caixa de pesquisa**, o prefixo **TW_** é adicionado para construir a expressão de pesquisa e aplicá-la a todos os bancos de dados. Isto significa que as bases de dados devem usar este prefixo para a indexação de palavras. Como resultado, é apresentado um resumo dos registros localizados:

![](https://lh4.googleusercontent.com/y43MEXZ2UvV814d2nE86YxAwQ4WqwRg6V3xJDmlBmDYK5aSsoSlnmEjm4iCnQZfDjDisgQErWTbZlNxXomGMPfL8Cc_r7gs-BR8wKwf7dCuRInXuDhEXySKUCWGmw1w4tUezDtd6=s0)

com a lista de resultados localizada no primeiro banco de dados. Se desejar alterar o banco de dados, clique no nome correspondente.

Para consultar o dicionário de palavras recuperáveis, clique no botão **Show Dictionary**. Como estamos no nível de metasearch, o dicionário exibido é uma consolidação dos termos localizados nos dicionários individuais

# Buscas

## Busca livre

## Busca avançada

## Dicionário de termos



## Índices alfabéticos

O ABCD Opac pode ser colocado em qualquer pasta sob o diretório WEB, desde que seja mantida a seguinte estrutura

![](https://lh3.googleusercontent.com/HI_rd4hdZuVng3-iqihKalDa7smrwCdUhkDlEskQxsa3MU_oKcqYpOWahnjYyQ0aXRfTiZxMPA2g-j0jvTlK3HWNJeanJC7GfROTkBvawyrmEQg5cd4_l6QHGun9fHqyyu5oD-3S=s0)

|||
|-|-|
| **config**  | contém os scripts do módulo de configuração |
| **images**| contém os elementos gráficos utilizados na apresentação da interface.| 
| **images\_config**| com os elementos gráficos utilizados no módulo de configuração|                                                  
|**js**|os javascripts utilizados nas páginas|                                                  
|**php**|os scripts usados na interface de consulta|
|**index.php**|página inicial que redireciona para a pasta index.php colocada na pasta **php**.|
|**styles.css**|arquivos de estilo utilizados|                                             

Para instalá-lo, descompacte o arquivo comprimido no diretório correspondente e prossiga para o diretório e prepare sua instalação seguindo estas etapas:

# Instalação

1. Criar a pasta onde o Opac deve ser instalado e descompactar o arquivo opac_dist.zip baixado. Esta pasta pode estar no ABCD ou em qualquer lugar dentro do diretório web e para os propósitos desta explicação a chamaremos opac_abcd (veja Estrutura da pasta)
    
2. Mova a pasta opac.xis para `central/dataentry/wxis/` e renomeie-a para `opac`.

3. Copiar os arquivos contidos em lang/00, lang/es, lang/pt e quaisquer outras atualizações na pasta de idiomas da pasta do banco de dados (Ex: /bases/lang/00). Este arquivo contém as mensagens OPAC e o status da conta, renovação e reserva on-line.

4. Modificar as primeiras linhas do script `[opac-directory] /php/config_opac.php` para colocar o caminho para o ABCD `config.php` que está localizado na pasta central.
      
Ex:
```
include ("/abcd/www/htdocs/central/config.php"); //CAMINO DE ACCESO HACIA EL CONFIG.PHP DE ABCD
```
         
Se você estiver instalando OPAC com a versão 1.6, modifique em `php/config_opac.php` os seguintes parâmetros  
          
```   
$ABCD\_scripts\_path="/abcd/www/htdocs/"; //path donde están
        instalados los scripts de abcd
        $server\_url="<http://127.0.0.1:9001>"; //El url que se usa para acceder al módulo central
```          
colocando os valores correspondentes a sua instalação.
   
5. Adicionar uma nova subpasta chamada **opac\ _conf ** à pasta **bases** estabelecida em **config.php** do ABCD. O **opac _conf** será usado para armazenar os arquivos de configuração do banco de dados. Estes arquivos são criados a partir do módulo de configuração contido na pasta **config** do OPAC.

6. Em **opac _conf** acrescente uma subpasta para cada idioma que você vai usar (por exemplo: es, fr, pt, en ...)

7. Execute o módulo de configuração de onde você instalou o OPAC

ex:
http://localhost:9091/opac_abcd/config/

Neste ponto, o caminho de acesso ao ABCD config.php é verificado (ver ponto 4)

## Entrada do módulo de configuração

1.  Forneça o login e a senha do administrador do ABCD. A tabela de idiomas utilizada nesta entrada é a definida no módulo central do ABCD. Se ocorrer um erro, verifique se o ponto 4 da instalação foi executado corretamente.

2.  Se seu login e senha estiverem corretos, será exibido o menu principal com as opções de configuração.
3. Quando o módulo de configuração é acessado pela primeira vez, com cada menu é apresentada uma tela com uma janela de ajuda do abcdonline.info.

Você também verá 2 links:

- Mostrar/ocultar ajuda
- Traduzir ajuda

O primeiro link esconde temporariamente a página de ajuda de você e o segundo link envia a página de ajuda para o tradutor do Google e abre uma nova janela com a tradução para o inglês. Você pode ocultar permanentemente a ajuda usando a opção **Parâmetros** no menu de configuração e verificando sua preferência no parâmetro correspondente **Mostrar páginas de ajuda**. Você pode então usar o link Mostrar/ocultar ajuda para visualizar a ajuda quando precisar dela, por exemplo

### Configuração geral
Executar as opções encontradas em **Configurações Gerais**:

- Parâmetros
- Idiomas disponíveis
- Bases de dados disponíveis
- Barra de Ferramentas de Registros

A explicação de cada um deles é apresentada no formulário de registro correspondente

### Configuração do banco de dados

Selecione o banco de dados que você deseja configurar. Esta lista é gerada a partir do arquivo `base.dat` criado na opção ***Bases de Dados Disponíveis*** da opção ***Configurações Gerais***.

> Nota importante: 
> esta configuração corresponde ao idioma selecionado. Portanto, os arquivos gerados serão armazenados na pasta correspondente a este idioma.

#### Instalação básica
Você deve preencher os formulários:

- Busca livre
- Busca avançada
- Formatos de exibição
- Verificar e atualizar o dbn.par.

Esta opção verifica se os formatos definidos estão incluídos no dbn.par e, se não estiverem, adiciona-os.
Note que para adicionar um formato no dbn.par, você deve seguir o seguinte esquema:

```
format.pft =%path_database%dbn/pfts/%lang%/format.pft 
```

onde: 
- **%path_database%**: é o nome do parâmetro que será substituído em tempo de execução pelo caminho para a pasta de bases 
- **dbn**: é o nome do banco de dados 
- **%lang%**: é o nome do parâmetro que será substituído no momento da execução pelo idioma ativo


Você pode usar a janela **Copy Setup Files*** para replicar a configuração em outro idioma, de modo que você só precisa modificar os títulos e formatos das tabelas.

### Metapesquisa

- Após completar a configuração básica do banco de dados, você deve configurar o **metasearch** preenchendo o formulário de busca avançada. Lembre-se que para que um campo faça parte da metasearch deve ser indexado no FST de todas as bases de dados com o mesmo prefixo.
- Uma vez que a configuração básica de um idioma esteja pronta, faça o login no Opac e execute os testes.

### Configuração avançada

## Modificar a página inicial do opac e as páginas iniciais de cada banco de dados
