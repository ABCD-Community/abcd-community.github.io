---
title: Colaboração
description: Veja como colaborar com o ABCD
lang: pt
lang-ref: collab
---

# Colabore com o ABCD
{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---


O ABCD é um software livre em contrução, por isso toda a ajuda é bem vinda. Não é necessário ser programador para ajudar no desenvolvimento do sistema, às vezes, uma simples correção de tradução já é de enorme valor, portanto, veja abaixo como você pode ajudar:


# Documentação

## Corrigindo a documentação

Ao lado de todas as páginas da documentação existe um botão ao lado que permite a edição. Você pode clicar, editar e enviar. Para isto, basta ter uma conta no Github.

> Dica:
> Para editar os arquivos Markdown, você pode utilizar o edito [Stack Edit](https://stackedit.io/){:target="_blank"}. Com ele é possível sincronizar no Google Drive.


> Dica2:
> Leia este tutorial [Começando](/pt/getting-started)


## Criando uma nova tradução

Para criar uma nova tradução você precisa baixar este projeto para seu computador. Para isto além da conta no Github, você precisa instalar no seu computador:

- Git ou Github desktop
- Jekyll [Leia as intruções de instalação](https://jekyllrb.com/docs/installation/){:target="_blank"}


### Primeiros passos 

O processo de criação de tradução para um novo idioma é simples, porém exige atenção.

1 - copie a pasta "en" na raiz do projeto com a sigla para o idioma desejado. Exemplo: "es"

2 - na pasta `_data` copie em todos os arquivos tudo que estiver dentro de `en` e cole abaixo.

Exemplo:

```language
en:
  label: English
pt:
  label: Português
es:
  label: Español
```

Faça isso com todos os arquivos, mas sempre conferindo no terminal se não houve nenhum erro. É muito fácil cometer erros nesta etapa.


3 - Entre na pasta criada para o idioma na raiz do projeto e vá localizando os arquivos. Faça as alterações, mas oberve que no cabeçalho de todos existe a sinalização de idioma. Não esqueça de trocar.

Exemplo:

```language
---
title: Collaboration
description: See how to collaborate with ABCD
lang: en
lang-ref: collab
---
```

Troque para:

```language
---
title: Colaboración
description: A continuación se explica cómo colaborar con el ABCD
lang: es
lang-ref: collab
---
```

Observe que o campo **lang-ref NÃO deve ser alterado**.


4 - Antes de submeter sua tradução para o Github, crie uma branch com um nome claro explicando o seu trabalho. Exemplo: "spanish-translation"


Se você estiver usando o Windows, é possível baixar o Github Desktop que facilita muito este processo. Caso esteja utilizando outro sistema operacional você terá que ter um conhecimento maior sobre Git.



# Sistema

O processo de submissão para o desenvolvimento do ABCD é bastante similar ao processo da documentação, no entanto é importante observar que dentro do sistema existe muito trabalho a ser feito.


O desenvolvimento do ABCD fica localizado neste repositório [ABCD-DEVCOM](https://github.com/ABCD-DEVCOM/ABCD2) e você pode colaborar:

- Em bases de dados:
	- Ajustes nas bases de dados;
	- Desenvolvimento das ajudas nas bases de dados;
	- Tradução de base de dados;
	- Correção de bugs;
	- Criação de uma base para um fim específico que tenha alguma relevância.

- No sistema:
	- correção de erros;
	- melhorias no código;
	- implementação de funcionalidades.

Estes são apenas alguns exemplos.