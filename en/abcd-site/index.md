---
title: ABCD Site
description: ABCD-Site administration
lang: en
lang-ref: abcd-site
---

# ABCD-Site administration

{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---



# Objective of the chapter

ABCD-Site is a customized partial version of VHL-Site, produced and maintained by BIREME. The full package of VHL-Site can be downloaded from: [http://bvsmodelo.bvsalud.org/php/level.php?lang=en&component=27&item=10](http://bvsmodelo.bvsalud.org/php/level.php?lang=en&component=27&item=10)

This manual has been written to provide information to ABCD-Site users in the software operation and configuration.

This document provides an overall description of the components that make up both the administration site and the public site, going more into details about the former, describing the operations that may be accomplished in systematically organized topics and following the same hierarchy as the stages.

The ABCD-Site is assumed to have been installed and configured in compliance with the readme file in the setup.

The manual also comprises a section on the methodology’s bibliographic references and a glossary of the ABCD model, in addition to three attachments with additional information for Metasearch, search field acronyms and tips to create search strategies in databases with the iAH search interface.

A Virtual Library is a model for the management of information and knowledge, which includes the cooperation and convergence between institutions, systems, networks, and initiatives of producers, intermediaries, and users in the operation of networks of local, national, regional and international information sources favoring open and universal access.

ABCD-Site organizes information in a structure that integrates and interconnects reference databases, specialist directories, events and institutions, a catalogue of the information resources available on the internet, collections of full texts.

The space of the ABCD is, therefore, a dynamic and decentralized network of information sources based on which it is possible to retrieve and extract information and knowledge to support decision-making processes.

# Introduction

The ABCD-Site is an integral tool of information sources which enables you to create, manage and publish your site.
Information source is any entity that responds to user demand for information. These information sources are generated, updated, stored and operated --through the Internet or intranet-- by information producers, integrators and intermediaries, in a decentralized way and according to common methodologies for ABCD integration.

ABCD-Site Main Features:

-   management of ABCD structure and contents
    
-   integration to ABCD with internal and external sources
    

The public site is configured using CSS (Cascading Style Sheets) and XSL(T) (eXtreme Style Language Transformer) technologies for presentation of its contents.

# General features of the system

## Access

The administration area is available through the main address of ABCD-Site. Therefore, if the address is http://localhost:9090/site/php/index.php/, all you have to do is to modify the URL to enter to the ABCD administration area, according to the example:

http://localhost:9090/site/admin/


**Initial Screen for the ABCD-Site Administration System**

**![](https://lh6.googleusercontent.com/nG6703_3wNktO-mihl_x5GyRQYONM7L5NMuQSWOCzrg5qyYIBkVGnJC5cMPcpUrpJwX2SZkE1HzTE_S7AvIUxEuus3U_w0hM_4CSrkgfJdygsDCPs0HLzJRhIQARma8MzoqBJ8bq=s0)**

Figure 1

To use the management tool, you must be a registered user and have an access password. The ABCD-Site currently has interfaces in 4 (four) languages and it is possible to work in any number or combinations of the languages. The content of each interface is managed separately with the use of a code and a password.

There are two types of users on the ABCD-Site administration system:

-   Administrator: with full access to all areas of the ABCD-Site
    
-   Content: restricted Access to Components area
    

At the time of installation of the system a set of _standard_ **passwords** is available to enable immediate access to the system, and which for reasons of safety **should be changed by the ABCD administrator.**

The passwords are:

    user: adm
    password: x

Note: The same password can be used on the interface of any language. For further information on user access and management, see item 6 – Management of the access area in this Manual.

## Main menu

The main allows management of the content of an ABCD-Site with identification of sources, topics, links with other sites, etc. It is divided into 3 main areas: Structure, Components and Access.

**![](https://lh3.googleusercontent.com/PrLM7VXSfMADkoke52ZescTM2zXN64qTmBDq8o1oJqRycNjpvlGyUBPTcg8GWusSFDAo51h-V9iucwrQa-EVk_nbzVbAqsPnwbxza0Gi3L_vdG9RXKHQtgeYutuv6CkKREZkQwab=s0)**
Figure 2

### Structure

Structure refers to the management of the ABCD elements : nomenclature, labels, languages, content access control (information sources, topics and communities) and to annexes (highlights and notices) etc.

### Components

Components refer to content management (information sources, topics and communities) which will be available in the ABCD interface.

### Access

Access refers to the access mode of the producers responsible for information, updates and validations of the content of the site.

## Main functions

After entering the user and the password, the administrator views the screen of the General Administration System, where it is possible to access: structure, content and access (users registration).

The main page of the administration system has three main functions located on the top of the screen.

**![](https://lh3.googleusercontent.com/PrLM7VXSfMADkoke52ZescTM2zXN64qTmBDq8o1oJqRycNjpvlGyUBPTcg8GWusSFDAo51h-V9iucwrQa-EVk_nbzVbAqsPnwbxza0Gi3L_vdG9RXKHQtgeYutuv6CkKREZkQwab=s0)**

Figure 3

### Preview

It shows a preview the ABCD site. The purpose is to facilitate the administration job by enabling immediate preview of the changes made without having to resort to the public stage.

### Exit

A feature used to exit the current screen and to return to system’s access page. If the user is on the home page of the Administration System, this option will return to the page to enter the system.

## General tools

These relate to features available in any ABCD content management window, whether in STRUCTURE, COMPONENTS or ACCESS. In the example below, we select the **SERVICE** box.

**![](https://lh6.googleusercontent.com/uAVOHZ8E0_bWh6K5_lLx22hiugFKF2s9iGjAfjPGYI6tS0o0VHIM3iwURB8jpm9nzz-t9aIRnisGa9cvCAssQPFRInTHxmZoeVGwFbglAp2C-Jl4kAF3pHGcGBmDMbmY9cpmRKm6=s0)**

Figure 4

### Save
Saves the changes made in the current section and records them into the interface files.

### Add

Adds data items according to the type of content existing in the section.

### Modify
Edits content data items existing in the section.

### Delete
Deletes content data items existing in the section.

### Exit
Returns to the main menu.

### Items list

Lists data items according to the type of content existing in the section. It shows the information on a hierarchical level determining how it is displayed in the ABCD interface.

### Move up
Moves up the selected item, enabling to change its order/sequence.

### Moves down
Moves up the selected item, enabling to change its order/sequence.

### Specific tools:
Features that vary according to the type available for each component of the system. In the example below we have selected the SciELO element of the first column

**![](https://lh6.googleusercontent.com/SDmhfxD_VYp2waCsklbRQptCqPbupr69us5MQFmAauVMU6yflrGGf0-JpU5YjO3tLmZ02eD0IZvPtKvL_c00AGJKdmQ-7N1gZCCacjvx5Nh6ACnp4HNAHk-jl1EZYTse3QMwTygB=s0)**
Figure 5

### Area identification
Name of the section to be changed (in the example, we have _Connection with other sites_).

### Status
Current status, which may be defined as Available or Unavailable.

**Available:** data are stored and available on the ABCD public interface.

**Unavailable:** data are stored and visualized only by the system’s administrators.

### Modify

It saves the changes made in the current section and applies them to the interface.

### Exit

It returns to the main menu.

# STRUCTURE area management

**![](https://lh3.googleusercontent.com/PrLM7VXSfMADkoke52ZescTM2zXN64qTmBDq8o1oJqRycNjpvlGyUBPTcg8GWusSFDAo51h-V9iucwrQa-EVk_nbzVbAqsPnwbxza0Gi3L_vdG9RXKHQtgeYutuv6CkKREZkQwab=s0)**
Figure 6

Features available in the **STRUCTURE** area:

## ABCD Logo

URL of the logo and URL for the responsible organisation providing ABCD (ABCD-Father).

**![](https://lh5.googleusercontent.com/Y2hiylkb6MAbobfDTjYe7gSdJnf_1nELwdO_44_ComGgGqnAgq2yHD9iUFazK_wSaXbDdC_Trwr9GcMTQ2zZt8o-C37G6caEuSUUSqwSujzLiV-qwiuG_DcwCwbzqblnBOQym7Xc=s0)**
Figure 7

-   **Label**
    Identifies the logo name available at the ABCD.

-   **Image**
    URL of the image that will make up the ABCD banner (or logo)

-   **Link**
    Inserts the link to the ABCD home

## Identification

Identifies the ABCD name that will be displayed in the banner and at the top of the administration system page.

**![](https://lh5.googleusercontent.com/ncuyoqqsqZ6YvgTr5xXgkQOnjLQOgorgmDy9wiblK8ea6MhdhpQXtjIbA7TIEaMbBZ6RniETj2PdQ_mSk0Cm03mga4z3p3yPTQ-QtZU3ulAEePAN1amjnW9p-du3pX1HNvD0f9eR=s0)**
Figure 8

-   **Label**
    ABCD name.

-   **Image**
    Site identification image

> Note: 
> In ABCD identification the user must choose between the label or the image, never use both at the same time.

## Contact

E-mail to contact the person(s) responsible for ABCD. More than one address can be registered, which in the public interface will be selected via a box, in the form.

**![](https://lh3.googleusercontent.com/RAcmWfQoF1XojZ2_UXClug_k5Cevrk2Zt36mfkR4ff7hT4sfkuOhGQdPbBTppHni3GAi_bitNNZojkoklZ-Sbs7hgUx30E1QWk9U8qxRwdDbKznnA8VW6cJv-l9t8dRerhWV5Yik=s0)**
Figure 9

-   **E-mail subject**
Indication of contact name. We suggest that personal data should be avoided.

-   **E-mail**  
Corresponding e-mail address.

> Note: 
> Personal addresses may be used as contact as these data are visible for the user of the public interface.


## Versions

Makes available public interfaces in other languages. These currently can be: English, French, Spanish and Portuguese, available in the administration module, depending on the work language. Example: for the Portuguese work language, other versions available are English, French and Spanish.

![](https://lh3.googleusercontent.com/I1qlg5lxIyvkcTQKw_tSEm5RMxC0INmMeaf8fAxms8lQx7Dc-QR5XLYtILKV8bCFl9KUYnHSLzvKo_2yM6sjdMZ1_vGNeVIu5Zd8cctxBw0YQmUI0Q_btGnssz8rtkQxAo8gMlO4=s0)

Figure 10

-   Name
    Identification of the version made available or not.

-   Link
    Identifies the action in the system that will make the public interface available.

## Institutions

Name of and link to institutions responsible for ABCD, displayed on the top right hand corner of the public site. This area enables the separate registration of image links and logos’ links.

![](https://lh5.googleusercontent.com/V-r3BYY_ijiLuAzKCCwkokPEFomtqK-sCc-nfNRPRRDKsfPJTS8XoTrvPa0nTNboONm9Q5coGk-DbpR8Vn9RZp4ez8JL6N5cQpatp_DHQMaZStBcrXW1qTPKiCxKO8EtfiVttdlK=s0)

Figure 11

-   Name
    Identifies the institution.

-   Image
    URL of the logo image (if there is a logo )

-   Link
    Link to the institution website (whenever available)

## Metasearch

Identifies and enables changing labels of research services available on the public interface.

![](https://lh5.googleusercontent.com/rCQu6tHW98iYXe5iZFD4X5P0FslvpDl1_ZK2Taig4Vrk5tKfCLGKvejhhnaV6dJ3dOnftLhRWuhwnqXd07OrJ9S9QDKk3gCd3crBSy6y0QvjbZymIge1AvEmQh7BFiWN0bd3Q8tb=s0)

Figure 12

-   Text
 Changes the text of the metasearch labels

The labels can be modified using the option “Metasearch” of the structure column, or directly editing the file `…/bases/site/xml/<lang>/metasearch.xml`

The last 5 rows grayed are implemented in the full version of this Site editor, because are related with special search features using the Thesaurus MeSH/DeCS of BIREME.

|Meta label|Text to display|
|-|-|
|search_title|ABCD Search|
|search_entryWords|Entry one or more words|
|search_submit|Search|
|search_howToSearch|how to search?|
|search_allWords|All words|
|search_anyWord|Any word|
|search_error|Please use a search expression.|
|search_advancedSearch|search filter|
|search_freeSearch|by words|
|search_results|Result|
|search_method|Method|
|search_demo|Demo|
|conceptSearch_title|by relevance|
|conceptSearch_entryWords|Search documents more related to the concepts|
|decs_mesh|Search by DeCS/MeSH terminology|

## Responsible Institution

Information on the site’s footnote. Describes data for contacting the institution in charge of the ABCD, as address, phone number, etc.

![](https://lh3.googleusercontent.com/85RZOciBOisYtO1J0zR5eFeXVypW2cmM428xRE1Lm2xd39ep-DcCcGp5h7Scv85xIRiOOP5y77p4DBaEFlzQIiXApd0SrnHV1Dz5gDJ-RpnULlp4ZyzCU03VqdsjiLz9IBX70XZ1=s0)

Figure 13

-   Name
    Indicates the institution that will have its contact data published at the page’s footnote.

-   XHTML Editor
Enables the creation of the welcome text to be made available at the public interface (for more information about he text editor in XHTML see item Sources Collection).

## Meta information of the site

Space for a ABCD’s brief description, which will allow the ABCD to be indexed and retrieved by web browsers. Enables description by author, keyword and description, etc.

![](https://lh4.googleusercontent.com/wSIjjgLMGSDGTR2hYV35w6I4bepKYZ9l7rL0QDQOaoXcgwXKVcJKVyRQ69A42maAGsjbKLbBfL8AKpIyVbfiedkMrECmDrdHR1pQoO5_ZZChlbpHMYX3l7T471el0nEns1lLBPv6=s0)

Figure 14

-   Element
    Indicates the field to be indexed by the Internet search engines. These may be:
	-   author: Institution’s URL;
	-   keywords: key words, describing the site’s content;
	-   description: site identification
    

## Texts

Manages the list comprising all labels and image URLs that identify common actions and areas of the ABCD site, other than the search services.

The labels can be modified using the option “Texts” of the structure column, or directly editing the file …/bases/site/xml/<lang>/bvs.xml

Meta label|Text to display|
|-|-|
Button_moreInformation|More information|
Default_print|print|
Default_close|close|
Home|home|
Contact|Contact|
Contact: subject|Subject|
Contact: name|Name|
Contact: email|Email|
Contact: message|Message|
Contact: send|Send|
Contact: error|Please fill in the fields:|
Contact: response|Your message has been successfully sent|
topic.expand|show subtopics|

![](https://lh6.googleusercontent.com/anr60MER2b3YL78gjS9SOgN5ML0c1-HJ9J0vId8VAV0jrozeg57XZUAEMhbKyysIUgYSlGsGwjnSTegQq8ILWS7Glek7qpob-jFicgopXDjUB6cR2bgGAYwK_VcTRh0nf_HJDTlc=s0)

Figure 15

-   Identification
    

Indicates the corresponding label

-   XHTML Editor
    

Enables the creation of the warning text to be made available at the public interface (for more information about he text editor in XHTML see item Sources Collection later in 3.10.3)

-   Image
    

Image URL.

## File manager

Allows the uploading of local files to a dedicated area of the server. ABCD Site is configured to load files under /abcd/www/htdocs/local. The administrator of the Server should give read/write access to the folder.

![](https://lh3.googleusercontent.com/RmQ4XNvuQm7afPiqYODo6aW_rX9-J_i2eEHu0JkmXjEyX5IYp23aZugcik3z9ZdctnDb9Va19I763sXjUBNMDKzWvpOH_zjsaqCtgLph4rByjEkAlmgOfsHOOGD04RyJ8c23BgPt=s0)

![](https://lh3.googleusercontent.com/wa4_rsMLvTdl-Y9k4egEr_LfDdoWuyPFoFQK-VOlPQoKkI2FklCjU9GRV2XDLJxaI3fqHyz-gY2oOnGW5GUFc7s9pP_bg142a8aYxqhvKgwKx05JbHW038wH_km-bVd--da4o34u=s0)

The administrator can filter the type of files admited to upload, modifying the variable in the configuration file:

    /htdocs/site/admin/fnow/include_config_system.php
    
    $cfg["allowed_extensions"] = "(gif|bmp|png|jpg|jpeg|doc|txt|xml|pdf)";

It is recommended to design a clear strategy of filing archives in this area classifying them by type. If there were a lot of files of the same class, it is recommended to prepare a balanced hierarchical structure, so that there are not too many files in a folder at the same level.

Opening a decimal tree is recommended, as shown in the figure at the right.

## Components

Version 4.02 of the ABCD Site enables administration of the system via “columns” subdivided into components (or boxes) displayed in up to three (3) columns, with no limits as to the number of component inside each one of them in that:

Column 1 – links to other Libraries or related portals.

Column 2 – collection of ABCD information sources.

Column 3 – space available for highlights, news, etc.

![](https://lh3.googleusercontent.com/b-Jk9WEw6XFaMXmC9V80Ukr5r8UgOxV2iUpcuCf6y_iI8Ml67WGPk1iHOVrmKnWnUl-ILQk5Z0QMPWPgURgQ7yCqGjKrZF0tLKTyF4tyRzDylskeE2UHvPD89j0X56jhCUI5iHj7=s0)

Figure 16

The order of each component, as well as that of the columns (depending on the ABCD scope) may be changed from the COMPONENT administration, where we have the columns as well as each one of the components (available or not in the public interface).

![](https://lh3.googleusercontent.com/7B5nFnm_WxdJPY3DdyNvtBPZ4t9NStUPqgKAiIEiXKi1JyZvDPooviflrc0HGz2SqaC1WgRq-CNzey9JOZ0qwE7CysLir0_mC9Ebm-B9aiLHIxodh-OVwMb1d9UJgwt7P70mG8gM=s0)

Figure 17

Each component of the column is represented by a title with the type of function that will make working on the content:

![](https://lh4.googleusercontent.com/LxMSIw8ZrFagvw76phE_WYdeTznCZvyPY0BNBvTxujB4dagGUyvHli82xqPJ6PHhy4v6ULXuIPL9bBq8DDfO6fXRzdCEj9c3MjiQBoHtOdM1g7DMvSzUo9J0Z0I1jO01pyE1Z1q5=s0)

Figure 18

### Types of Components

In addition to the structuring in “Columns”, version 4.0 of the ABCD Site also works by using some types of components that may be distributed along ABCD.

![](https://lh5.googleusercontent.com/ssnbueCcErC53P1mKtvpvUEQPuSmD9Ij08htXz2E_5-tJviOYxrZ6IfG2hkAXURz6sgptONPLRnftDdpsQFvzx_o-z_ePBOzAIRFSPC4MQFzbjGK8-hDkU-Umsf9lRM8UDdTpAab=s0)

Figure 19

Types of components may be:

### Warning

Enables insertion of warning messages relative to ABCD : site under maintenance, site for demonstration only, etc.

![](https://lh3.googleusercontent.com/7hY4hzt2iUsbrs4_U50vtMRchwL0cD3yCJDfRObjAp-POC7MVtJNvKdb3uy8hNINCzbU98mbQZdgPbhenaQjge05rae6yDmLcPukmCON47IdZ2EhMSi1WjXCCr6D9Do1VM4zOTmP=s0)

Figure 20

-   Name
    

Indicates the title of the warning (only for the administration module. Not published).

-   XHTML Editor
    

Enables the creation of the warning text to be made available at the public interface (for more information about he text editor in XHTML see item Sources Collection).

### Sources collection

Enables registration of each information resource, as well as its configuration, to take part in the Metasearch.

![](https://lh5.googleusercontent.com/yHzGAXK-SaCMbzX7Pz2c7ux-M_ZA-iZyibyOAdmMI9ldcRE34eji1-DqetOY0vqJsWpnoxpcCZpkMrUMRA9t3xgHDIXrbgH3Mlwm2krQVNeVn_fZtvAm-eLyVEaBXXNsQXRzXEKX=s0)

Figure 21

-   Name
    

Source identification.

-   Image
    

URL of the source image.

-   Link
    

Link to the search area source of the information resource.

-   XHTML description
    

Reserved for a brief description on the information resource and its contents.

Example of XHTML Description usage.

![](https://lh4.googleusercontent.com/Yxpeknf61g2_XEakB4DR1jVhqjy67bL9JXqOkaUdhSL3ultIaqXoXNkdPdgDHSSw1Gy8KNpfbZANYgPdZ72go2qzzAUIM8chfZVseQndFVa51czgyZ975yD4gnUKebEAe17jCqdJ=s0)

Figure 22

-   Portal web page (XHTML)
    

When used, the content of this field generates a second level page (portal) in ABCD. Follows the same editing rules as the description area, but the link field must not be filled out.

Example of Portal web page use (XHTML)

In order to active a second level page, the first LINK box should be empty, otherwise the first XHTML page will be displayed. The link to the external site should be included in the text of this web page.

![](https://lh3.googleusercontent.com/KxuLLgp99uD89fapssrZQDgZAQJzcO50N4w0l1tQpLdDWud3vXazvwguxneQF-ehSQauxVuaAg1JwY26ifTmCO5uXNE0N6wQp6BUpq7bl4g1CuDayb7ULZu_lFW6LfpTvu-7AQPr=s0)

Figure 23

-   Metasearch
    

This mechanism enables the user to conduct a free query or a query by subject over different information resources included in the Site. Some Metasearch configuration is required so that the resources operate with this search system.

Information on how to configure the search system is explained in topics “Configuration parameters for Metasearch” and “Topics” in this manual.

### Communities

Enables the registration of a specific Community information resource such as virtual communities, forums, etc.

![](https://lh5.googleusercontent.com/Hr2pDo49V9zQmZbR7jaHPg2KqU2CkyBnUENV8fHEpysFxAl3OkOUl546PmpbLzKjVNc8IbA2NMTnQwYRuhASisjAleNYZOgWWW3aAJCRl5ojwlGxxfQ9NPCSnClc-QBM3qwQP54W=s0)

Figure 24

-   Name
    

Resource identification.

-   Image
    

URL of the resource image.

-   Link
    

Link to the search interface of the information resource.

-   XHTML description
    

Reserved for a brief description of the information source and its content

-   Portal web page (XHTML)
    

When used, the content of this field generates a second level page (portal) in the ABCD. Follows the same editing rules as the description area, but the link field must not be filled out (for more information on the XHTML text editor see item (Sources Collection).

### Highlights

Collection of records highlighted in the main page of the ABCD.

![](https://lh5.googleusercontent.com/hTnvZxoex-8CRRgG8pBDjq9rwRHrjOgLZajq8cOwIwBYBQIhFfvl23ofBdn7hlD_Y1oe7aAL_wrcPk_kHY0LOka7Cb6GFzasFa0GY_kSa-CUYkn9Q7vlz3Lc0zRvb6AJ7RWo2tuz=s0)

Figure 25

-   Name
    

Resource identification.

-   Image
    

URL of the source image.

-   Link
    

Link to the search interface of the information source.

### Portals

Collection of links to other web portals related to ABCD.

![](https://lh5.googleusercontent.com/dRHyeXDthzMtQvbo8DNaFrWd54kibJMMLj_TVI6yS3ehcE-xxSXPSVLUuQ6HM_XjiUDLGALns4LxajP6weJQ9ZmE1funNIsbS2zBURAOqDYR9kidz4bOMoeA5nPDH_a7m0nyNHzV=s0)

Figure 26

-   Name
    

Resource identification.

-   Image
    

URL of the source image.

-   Link
    

Link to the search interface of the information resource.

### About

Enables registration of information on ABCD such as objective, reach, etc.

![](https://lh3.googleusercontent.com/IruSjJq0uydwnjPVA9vybDF5dBrRkaW2h4oE6E8E61Y7zJnNyyqKvL_AMGBJWzcNvseM1uXlKhqyf5VsrDdz_ZVxlyo3U5tfBzCzz5fy8WYIlk_HBTySIS_rdXcMqwMjAKSpMujW=s0)

Figure 27

-   Name
Resource identification.

-   Image
URL of the source image.

-   Link
Link to the search interface of the information resource.

-   XHTML description
    

Reserved for a brief description of the information source and its conte

-   Portal web page (XHTML)
    

When used, the content of this field generates a second level page (portal) in ABCD. Follows the same editing rules as the description area, but the link field must not be filled out (for more information on the XHTML text editor see item (Sources Collection).

### Topics

Collection of related topics that enables an automatic metasearch in a set of sources previously configured to offer this feature. This service requires a controlled vocabulary to be efficient.

Information on how to configure the search system is spelled out in topics “Configuration parameters for Metasearch” and “Subjects” in the full version of the BVS Site manual.  [http://bvsmodelo.bvsalud.org/download/bvs/Manual_BVS-Site4.0_en.pdf](http://bvsmodelo.bvsalud.org/download/bvs/Manual_BVS-Site4.0_en.pdf)

### HTML

Use of the HTML editor page to publish information directly on the ABCD main page..

![](https://lh5.googleusercontent.com/8TDLybDPszqiDgyZ3AVg71uNKcHLsSQPC0GyzLFpsvUoWo071iK-3IspSy9HOWgTlr8Gez_lVP8bG731xrqwDOxlXwV6g6eAGtaWAdpE0eNeZVQl_oY0kUZinqcf0MQzbUR3kbBQ=s0)

Figure 28

### RSS

Creates a link with news agencies that make the RSS feature available to users.

![](https://lh3.googleusercontent.com/vGQixwHVhc5kM_nEG-N8etapOOnZ94zWstBl0kAkOV3o58R9dh6FvxirIksLfv0iKBGzJwSEoWFEcbcQqL7ww_lOb71V-NJCTIw1zmjPgX6x3k1hqXfKiLmSmO6FTbznxZwMKq-5=s0)

Figure 29

-   Link to the RSS file
Indication of the URL corresponding to the RSS service.

-   Check
Checks if the RSS address is correct. Checking will be made in the box below, named RSS.

-   RSS
- Box to check the RSS feature indicated.

# COMPONENTS area management

![](https://lh3.googleusercontent.com/PrLM7VXSfMADkoke52ZescTM2zXN64qTmBDq8o1oJqRycNjpvlGyUBPTcg8GWusSFDAo51h-V9iucwrQa-EVk_nbzVbAqsPnwbxza0Gi3L_vdG9RXKHQtgeYutuv6CkKREZkQwab=s0)

Figure 30

Once the components of each column are defined (item 4.10), its content must be managed via the COMPONENTS area, depending on each component selected.

Detailed information on how to work with each type of component in the system is provided in the item “[Types of Components](https://docs.google.com/document/d/13kW8gJdtY0rSvjYdMlF0-pcGTaVnzIyv3zhU01vsiyk/edit#heading=h.vx1227)”.

## Metasearch

Configuration of the Metasearch (which is done in free search or search by topic) is essential for effective search of information resources within ABCD, and the parameters must be correctly filled in and the resource correctly registered so that Metasearch works.

![](https://lh3.googleusercontent.com/huLkWCa7aNLN9-fM4HvIrAcyXs3i7hgAETfR6vQ2IJqTX-nP4WnvGzzvhk_FWwjNy1Vm5tiY9IL25w9iU8vIhpE9KhXlF_y-BSf81e0UVvUpymtTc2mq_ux-maxlixJEq21K_wxM=s0)

Figure 31

-   Search link - fixed part
    

A set of parameters that determines the information resource that is being queried.

-   Free search parameters
    

A variable that receives the argument of the search on the information resource to be queried.

-   Show result link - fixed part
    

Set of parameters that determine the visualization of the search results.

Note: In the standard installation of a ABCD some information sources are already configured, but when inserting a new Source the fields mentioned are empty and have to be set up.

### Configuration parameters for Metasearch

Configuration of the Metasearch engine is always based on the Information Resources URL and should be adjusted according to the type of information source.

Example of URL from the DBLIL database in ABCD demo.

With the full path:

[http://<my-host>/cgi-bin/wxis.exe/iah/scripts/?IsisScript=iah.xis&lang=es&base=DBLIL](http://localhost:9090/cgi-bin/wxis.exe/iah/scripts/?IsisScript=iah.xis&lang=es&base=DBLIL)

Using a relative path if the database is in the same host of your ABCD Site.

/iah/?base=DBLIL&lang=es

in this case, you could refer to the server as %HOST% in the metasearch parameters.

In order to conduct a search, configurations of links and parameters must be entered correctly.

Notes: The methodology used for configuration of the Metasearch engine in this manual is based on the use of ABCD applications in its standard model. Adjustments may be necessary in specific cases or at the time of customization of applications. In this case, the help of the ABCD system analyst/developer is important to identify the parameters required for the Metasearch engine.

### Parameters for configuring DATABASES available with iAH

We have taken as an example the DBLIL database from BIREME included in the ABCD package as demo. This database that has the following URL:

[http://localhost:9090/cgi-bin/wxis.exe/iah/scripts/?IsisScript=iah.xis&lang=es&base=DBLIL](http://localhost:9090/cgi-bin/wxis.exe/iah/scripts/?IsisScript=iah.xis&lang=es&base=DBLIL)

In this URL we have:

Term

Description

http://localhost:9090

name and address of server where search is started.

    /cgi-bin/wxis.exe/iah/scripts/?IsisScript=iah.xis

search mechanism to be used (in the examples we have iAH), where wxislind.exe is the executable file that may also be found as wxis.exe, wxis1660, etc.

base=DBLIL

name of database where the search is performed

lang=e

language to be used in the search:  
pt = Portuguese  
en= English  
es = Spanish

Table 1

Once the URL of the base has been identified, one needs only to add the parameters below at the end of each field for the Metasearch to work smoothly.

-   Search link - fixed part:
    

&nextAction=xml&count=1[&fmt=citation]

  

parameter &fmt is optional, if you don’t declare it the result will be displayed using the default format of the database as declared in the <base>.def file

-   Free Search parameters:
    

exprSearch=

  

-   Show result link – fixed part:
    

&nextAction=lnk

  

Following the example above we have:

-   URL of the source

     /iah/?base=DBLIL&lang=es
  
-   Search link - fixed part:
    http://%HOST%/cgi-bin/wxis.exe/iah/scripts/?IsisScript=iah.xis&base=DBLIL&lang=en&nextAction=xml&count=1

-   Free search parameters (here there is no variation):
    exprSearch=

-   Show result link – fixed part:

    http://%HOST%/cgi-bin/wxis.exe/iah/scripts/?IsisScript=iah.xis&base=DBLIL&lang=en&nextAction=lnk

  
  

![](https://lh5.googleusercontent.com/0TKZAd8lWomvxI00--4dwDkYpi5jQKqs99jRZAGfImsE0gf3vuBmNgw_-GmyO3e82VfJe_FkJtuUcuTapB_SDjAi0tqjd-tVH0N6YKun_V9y9RgDeelW_l7Vi1-g_BjCfdFPhrde=s0)

Figure 32

> Hint:
> in Parameters for free search of database, the standard variable used by iAH is exprSearch=, which will receive the expression used by the user in the free search (typed by the user in the search box) or by topic. However, it may vary from source to source.

# ACCESS area management

![](https://lh3.googleusercontent.com/PrLM7VXSfMADkoke52ZescTM2zXN64qTmBDq8o1oJqRycNjpvlGyUBPTcg8GWusSFDAo51h-V9iucwrQa-EVk_nbzVbAqsPnwbxza0Gi3L_vdG9RXKHQtgeYutuv6CkKREZkQwab=s0)

Figure 33

It refers to the management and control of users, passwords and those responsible for the administration of ABCD. In this section, one may add, edit or delete the registration of users and passwords to limit the management of the Interface.

Features available in the **ACCESS** area:

![](https://lh4.googleusercontent.com/4CSNEjdr8uYX1sDvsjjGFysRXpIzzROA_5VYn4aVBgz37-BDYJ8LqmdvxUVZy3gBeW6k8AhUKj7A-M9-ZTFxADbbl-ylFG3JXbKXnYXIggyDZT4bsvoi_ZIb3zmUGmteMpKEA1mH=s0)

Figure 34

-   Name
    Identifies the user’s login access

-   Type
    Identifies system’s user permit for site management.
    There are two types of permissions:
    * Administrator – the system administrator, who has access to all modules (structure, content, access)
    * Content – Access permitted only for management of content and of some structure items
    

-   Password
Identifies the user’s login access
	* ABCD-Site Administration menu, with administrator’s permission displays the full standard menu.
	* ABCD-Site Administration Menu with content permission
    

![](https://lh4.googleusercontent.com/lzsQ1ifAcwwbpKju0DipLN-mYUffzO1xN5L4g6XOa_2YhEysF_KB92u5omF9sLAAH9utPugdVLmHFe9PGVSTPbRcOjcazwUNbWXdqXXoQcN5hnONiYP2FyMhAQ2bywepnzOL94wC=s0)

Figure 35

# ABCD Site - tips

## BVS-Site & Google Analytics

This section explains how to add to ABCD Site the script of Google Analytics to keep statistics of visits.

## Activation of the function step by step

Step 1: Register the Site in Google Analytics [https://www.google.com/analytics/](https://www.google.com/analytics/).

More information about registration and how the sytem works can be obtained in the support page of Google: [http://www.google.com/support/googleanalytics/?hl=en](http://www.google.com/support/googleanalytics/?hl=en)

Step 2: Add your Site to be monitored by Google tool. This step should be done using the control interface of Google Analytics. After the completion of this step, you should receive an ID (tracking code) which is an unique autogenerated code for each site being monitored. You should write down this code in a safe place.

Step 3: Edit the file ../htdocs/site/bvs-site-conf.php of your installation of ABCD Site, adding the following lines:

    [ANALYTICS]
    GOOGLE_ANALYTICS_ID=XX-99999 (code received in step 2)

## ABCD-Site in multiple languages

ABCD Site works in 3 languages by default: English, Portuguese, and Spanish. This section describes the required steps to add new languaes to the system.

> Note: 
> The present version uses character encoding ISO-8859-1,
> therefore only languages that can be represented by this encoding will function correctly. In version 4.1.x and better of the system (not yet released) the encoding is changed to UTF-8 with the objective to increase the numer of supported languages.

## Steps to add a new language to ABCD Site

Step 1: Create directories for the new language using the two-letter language notation of ISO (pt-Portuguese, es-Spanish, fr-French, en-English, etc.) below the ../bases directory of the installation of ABCD Site.

Example: adding support for French (assuming ABCD Site is installed under /ABCD/www/)

    cd /ABCD/www/bases/site/xml/

    mkdir fr

    cd /ABCD/www/bases/site/html/

    mkdir fr

    cd /ABCD/www/bases/site/ini/

    mkdir fr

When finished this step, the directory /bases will have with the following structure of directories

    xml/
        pt/
        es/
        en/
        fr/
	ini/
        pt/
        es/
		en/
	    fr/
    html/
	    pt/
        es/
        en/
        fr/

Step 2: copy all XML directories of an available language in ABCD Site into the directory of the new languages

Example: copying English files to French language

    cd /ABCD/www/bases/site/xml/en

    cp *.* /ABCD/www/bases/site/xml/fr

Step 3: edit the file bvs.xml in the folder /xml/[new_language] replacing the two-letter code corresponding to the source language with the two-letter code of the new language.

Note: use the text editor of your choice (Notepad, Textpad, Vi, etc.) and check that the file is saved as plain text.

Example: change the code “en” to “fr” using the editor Vi

    :s/\/en\//\/fr\//g

Step 4: edit the file adm.xml in the folder /xml/[new_language] replacing the two-letter code corresponding to the source language with the two-letter code of the new language.

Note: use the text editor of your choice (Notepad, Textpad, Vi, etc.) and check that the file is saved as plain text.

Example: change the code “en” to “fr” using the editor Vi

    :s/\/en\//\/fr\//g

## ABCD-Site: adding your own java scripts

This section explains how to add to ABCD Site other javascript functions to be available in different places of ABCD Site.

Step 1: create the folder 

    ../htdocs/site/local/js

Step 2: create in this folder a file named function.js  and include there all your javascript functions

Step 3: declare the use of the file in ../htdocs/site/php/head.php  including the following line:

    <script type="text/javascript"
    src="<?php echo $def['DIRECTORY']?>local/js/functions.js">
    </script>




