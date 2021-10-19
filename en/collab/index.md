---
title: Collaboration
description: See how to collaborate with ABCD
lang: en
lang-ref: collab
---


# Contribute to ABCD
{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---


ABCD is a free software under construction, so all help is welcome. You don't need to be a programmer to help developing the system, sometimes a simple translation correction is already of enormous value, so see below how you can help:


# Documentation

## Fixing the documentation

Next to every page of the documentation there is a button next to it that allows editing. You can click, edit and submit. For this, you just need to have an account on Github.


> Tip:
> To edit Markdown files, you can use the [Stack Edit](https://stackedit.io/){:target="_blank"}. With it you can sync to Google Drive.


> Tip2:
> Read this tutorial  [Getting Started](/en/getting-started)

## Creating a new translation

To create a new translation you need to download this project to your computer. For this besides the Github account, you need to install it on your computer:

- Git or Github desktop
- Jekyll [Read the installation instructions](https://jekyllrb.com/docs/installation/){:target="_blank"}


### Getting started 

The process of creating a translation for a new language is simple, but requires attention.

1 - copy the "en" folder in the project root with the acronym for the desired language. Example: "es".

2 - in the `_data` folder, copy everything under `en` and paste it below.

Example:

```language
en:
  label: English
pt:
  label: Português
es:
  label: Español
```

Do this with all the files, but always check in the terminal that there was no error. It is very easy to make mistakes at this stage.


3 - Enter the folder created for the language in the root of the project and go locating the files. Make the changes, but oberve that in the header of all there is the language sign. Don't forget to change it.

Example:

```language
---
title: Collaboration
description: See how to collaborate with ABCD
lang: en
lang-ref: collab
---
```

Change to:

```language
---
title: Colaboración
description: A continuación se explica cómo colaborar con el ABCD
lang: es
lang-ref: collab
---
```

Note that the field **lang-ref NOT to be changed**.


4 - Before submitting your translation to Github, create a branch with a clear name explaining your work. Example: "spanish-translation"


If you're using Windows, you can download the Github Desktop which makes this process much easier. If you are using another operating system you will have to have a greater knowledge of Git.



# System

The submission process for the ABCD development is quite similar to the documentation process, however it is important to note that within the system there is a lot of work to be done.


The ABCD development is located in this repository [ABCD-DEVCOM](https://github.com/ABCD-DEVCOM/ABCD2) and you can collaborate:

- In databases:
	- Adjustments to the databases;
	- Development of database aids;
	- Database translation;
	- Bug fixing;
	- Creation of a base for a specific purpose that has some relevance.

- In the system:
	- bug fixing;
	- code improvements;
	- implementation of functionalities.

These are just some examples.