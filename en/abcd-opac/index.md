---
title: ABCD OPAC
description: ABCD Opac allows up to 3 levels of search - Metasearch, Search on a specific database, Search on a subset of records in a database
lang: en
lang-ref: abcd-opac
---

# Features

{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---


ABCD Opac allows up to 3 levels of search:

- Metasearch
- Search on a specific database
- Search on a subset of records in a database (material type or other classification defined by an FST prefix)

## Metasearch

Applies the search expression to all databases defined in the file bases.dat contained in the folder "opac_conf" of the bases folder. The Start option in the menu bar activates the meta-search by displaying this box:

![](https://lh4.googleusercontent.com/LP69w4E576tCSQwv0ERfFbzVqAjDWO4JUGLYxDZRTR62DIZfEEXdBxB9TGuOoENmVG-lXAaDtD89-lBhwmo7izjmIJiSq1BkgNWyVOZDngEmyFIyEy5sG0_5Xtz6VJBhFpVjzGH6=s0)

If one or more words are put in the **search box**, the prefix **TW_** is added to construct the search expression and apply it to all databases. This means that the databases must use this prefix for word indexing. As a result, a summary of the located records is presented:

![](https://lh4.googleusercontent.com/y43MEXZ2UvV814d2nE86YxAwQ4WqwRg6V3xJDmlBmDYK5aSsoSlnmEjm4iCnQZfDjDisgQErWTbZlNxXomGMPfL8Cc_r7gs-BR8wKwf7dCuRInXuDhEXySKUCWGmw1w4tUezDtd6=s0)

with the list of results located in the first database. If you want to change the database, click on the corresponding name.

To consult the dictionary of retrievable words, click the **Show Dictionary** button. As we are at the metasearch level, the dictionary displayed is a consolidation of the terms located in the individual dictionaries

# Searches

## Free search

## Advanced search

## Dictionary of terms



## Alphabetical indexes

The ABCD Opac can be placed in any folder under the directory WEB directory as long as the following structure is maintained

![](https://lh3.googleusercontent.com/HI_rd4hdZuVng3-iqihKalDa7smrwCdUhkDlEskQxsa3MU_oKcqYpOWahnjYyQ0aXRfTiZxMPA2g-j0jvTlK3HWNJeanJC7GfROTkBvawyrmEQg5cd4_l6QHGun9fHqyyu5oD-3S=s0)

|||
|-|-|
| **config**  | contains the configuration module scripts |
| **images**| contains the graphical elements used in the presentation of the interface.| 
| **images\_config**| with the graphical elements used in the configuration module|                                                  
|**js**|the javascripts used in the pages|                                                  
|**php**|the scripts used in the query interface|
|**index.php**|home page which redirects to the index.php placed in the **php** folder.
|**styles.css**|style files used|                                             

To install it, unzip the compressed file in the corresponding directory and proceed to directory and proceed to prepare your installation by following these steps following these steps:

# Installation

1. Create the folder where Opac is to be installed and unzip the downloaded opac_dist.zip file. This folder can be in ABCD or anywhere within the web directory and for the purposes of this explanation we will call it opac_abcd (see Folder structure)
    
2. Move the opac.xis folder to `central/dataentry/wxis/` and rename it to `opac`.

3. Copy the files contained in lang/00, lang/es, lang/pt and any other updates to the language folder of the database folder (Ex: /bases/lang/00). This file contains the OPAC messages and account status, renewal and online booking

4. Modify the first few lines of the script `[opac-directory] /php/config_opac.php` to put the path to the ABCD `config.php` which is located in the central folder.
      
Ex:
```
include ("/abcd/www/htdocs/central/config.php"); //CAMINO DE ACCESO HACIA EL CONFIG.PHP DE ABCD
```
         
If you are installing OPAC with version 1.6, modify in `php/config_opac.php` the following parameters  
          
```   
$ABCD\_scripts\_path="/abcd/www/htdocs/"; //path donde están
        instalados los scripts de abcd
        $server\_url="<http://127.0.0.1:9001>"; //El url que se usa para acceder al módulo central
```          
by setting the values corresponding to your installation
   
5. Add a new subfolder called **opac\ _conf** to the **bases** folder established in **config.php** of ABCD. The **opac _conf** will be used to store the database configuration files. These files are created from the configuration module contained in the OPAC **config** folder.

6. Under **opac _conf** add a subfolder for each language you are going to use (for example: es, fr, pt, en ...)

7. Run the configuration module from where you installed OPAC

ex:
http://localhost:9091/opac_abcd/config/

At this point, the access path to ABCD config.php is checked (see point 4)

## Configuration module input

1.  Provide the ABCD administrator's login and password. The language table used in this entry is the one defined in the central ABCD module. If an error occurs, check that point 4 of the installation has run correctly.

2.  If your login and password are correct, the main main menu with the configuration options will be displayed.
3. When the configuration module is accessed for the first time, with each menu a screen is presented with a help window from abcdonline.info.

You will also see 2 links:

- Show/hide help
- Translate help

The first link temporarily hides the help page from you and the second link sends the help page to the Google translator and opens a new window with the English translation. You can permanently hide the help by using the **Parameters** option in the configuration menu and checking your preference in the corresponding **Show help pages** parameter. You can then use the Show/Hide Help link to view the help when you need it.e.

### General configuration
Execute the options found under **General Settings**:

- Parameters
- Available languages
- Available Databases
- Records Toolbar

The explanation of each is shown in the corresponding registration form

### Database configuration

Select the database you want to configure. This list is generated from the `base.dat` file created in the ***Available Databases*** option of the ***General Settings***.*

> Important Note: 
> this setting corresponds to the selected language. Therefore, the generated files will be stored in the folder corresponding to this language.

#### Basic Setup
You must fill out the forms:

- Free search
- Advanced search
- Display formats
- Check and update dbn.par.

This option checks if the defined formats are included in dbn.par and, if not, adds them.
Note that to add a format in dbn.par, you must follow the following scheme:

```
format.pft =%path_database%dbn/pfts/%lang%/format.pft 
```

where: 
- **%path_database%**: is the name of the parameter that will be replaced at runtime by the path to the bases folder 
- **dbn**: is the name of the data base 
- **%lang%**: is the name of the parameter that will be replaced at runtime by the active language


You can use the **Copy Setup Files window** to replicate the setup in another language, so that you only need to modify the table titles and formats.

### Meta Search

- After completing the basic database configuration, you must configure the **meta-search** by filling out the advanced search form. Remember that for a field to be part of the metasearch it must be indexed in the FST of all databases with the same prefix.
- Once the basic configuration of a language is ready, log in to Opac and run the tests.

### Advanced Configuration

## Modify the opac start page and the start pages of each database
