---
title: Introduction - background information
description: General introduction to ABCD as a software suite
lang: en
lang-ref: abcd-introduction
---

# Introduction: background information

{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## General introduction to ABCD as a software suite
    

ABCD is the acronym for a software suite for the automation of libraries and documentation centres. In Spanish this is, in full : 'Automatisación de Bibliotécas y Centros de Documentación', which keeps the same acronym valid also for French (Automation des Bibliothèques et Centres de Documentacion) or Portugese (Automatização das Bibliotecas e dos Centros de Documentação). Even in other non-latin languages, with some slight but quite acceptable variations, - e.g. Dutch : 'Automatisering van Bibliotheken en Centra voor Documentatie' - the acronym can still be maintained.

  

The name itself already expresses the ambition of the software suite : not only providing automation functions for the 'classic' libraries but also other information providers such as documentation centres. Flexibility and versatility are at the forefront of the criteria on which the software is developed. This flexibility e.g. is illustrated by the fact that in principle, but also practically, any bibliographic structure can be managed by the software, or even created by itself. Even non-bibliographic structures can be created, as long as the information is mainly 'textual' information, as this is the limitation put by the underlying database technology, which is the (CDS/)ISIS textual database. Good understanding of some basic ISIS-related concepts and techniques, e.g. the Formatting Language, is crucial for full mastering of the ABCD-software. For this reason some sections of this Manual will also deal with the underlying ISIS-technology.

  

ABCD is called a 'suite' of softwares for library and documentation centres automation because it exists of some relatively independent modules, which can fully co-operate but also can exist without each other. In fact some existing advanced softwares, mostly having already shown their potential in demanding environments in BIREME- applications (within the Virtual Health Library context), were adopted and adapted into ABCD - that is why the original names such as iAH, SeCS (both developed by BIREME) and EmpWeb (Empréstimos en Web) developed originally by KALIO ltda. of Uruguay and amply tested in Valparaiso at the University) are maintained. These main parts are shown, with their hierarchical relationships, at the second level in the following picture and subsequently discussed briefly :

![Slide2](https://user-images.githubusercontent.com/20482054/137317883-75797ad3-47d5-43f0-b3b7-7c405f646236.JPG)


### the ABCD Central

The 'Central' module of ABCD comprises modules for Database Administration (creation of databases, edit- ing of database-structures, database utilities), Cataloging, Acquisitions, Circulation/Loans and Statistics. A thesaurus management module is also being prepared as part of the cataloging module for a specific the- saurus-structure database with consistency control of the hierarchical levels. As part of this 'central module' we would also like to mention import- and export services, printing and database-tools like blocking/unblocking and 'global changes' to fields in records. This 'Central' part in fact represents the 'back-office' part of ABCD, end-users will not be confronted with this but what they will see and be offered is fully defined in this central management part of the software !

 Any ISIS-database structure can be defined and managed, with currently records of 1Mb maximum size and 4Gb max, databases (but these restrictions will be made obsolete by the NBP-based next generation of ISIS and ABCD). As compared to 'normal' ISIS-technology ,60-character (as compared to 30-character) indexing keys are used, there are much stronger authority control features available (picklists based on tables or authority databases such as thesauri) at the data-entry stage with flexible validation formats) and all interaction is based on WWW-technology of course, allowing e.g. HTML-coded text-strings for full-text indexing, hyperlinks to help-pages etc.

It is perfectly possible to fully automate a smaller library with mostly internal users with all necessary functions, only using this Central part, as e.g. an advanced searching option is built-in, so that all functions are covered with a minimum of technological complexity (i.e. only ISIS and PHP).

### the ABCD OPAC (iAH)

The public search interface (OPAC) is an adapted version of BIREME's general 'advanced interface for Health information' (iAH). It allows meta-searches on not only the local catalogs but also many other information resources.

The iAH interface developed by BIREME is currently being upgraded to iAHx, ensuring it will align perfectly with modern Information Retrieval concepts and techniques (e.g. clustering, relevance ranking based on Lucene indexing).

### the ABCD Site

The search function is offered as part of an 'end-users' portal page, presenting the own catalog(s) in a much wider information context by providing access to other information resource.s (e.g. Google, Medline...) and communication (announcements, alerts), also paving the way for 'Web 2.0'-like functions.

The Site Administrator actually is a specific Content Management System which allows designing the structure and components of the portal page of ABCD.


### the ABCD Serials Control System (SeCS)

This module offers an advanced management tool for serials/journals (classical and/or electronic) of any pub- lication type (referring to periodicity). Serials as such but also issues of a serial and all types of publication patterns can be managed by this module. BIREME uses this technology e.g. for its products 'Portal of Scientific Journals' (see : [http://portal.revistas.bvs.br/main.php?home=true&lang=en)](http://portal.revistas.bvs.br/main.php?home=true&lang=en)) and SCAD (see : http://scad.bvs.br/php/index.php?lang=en) which is the Brazilian union catalog of over 12.000 journals (with millions of issues) of more than 50 libraries.

### the ABCD Advanced Loans module (EmpWeb) 

This module offers advanced loans management with some more extra features for larger and more complex organisations. It offers a 'MyLibrary' function to end-users through the OPAC and is based on 'web-services' technology. It can be used to replace the integrated loans module of ABCD in case of a need to cope with multi-branch/policy and very high transactions volume situations.

The 'suite' idea reflects the fact that ABCD has relatively independent parts - as is the case with office automation suites (e.g. Open Office, Microsoft Office) - but with obvious links to co-operate. The Statistics module e.g., as part of the Circulation/Loans module, can work on any ISIS-database, while the iAH-OPAC also can offer advanced web-based retrieval in any (set of) ISIS-databases, not only ABCD-maintained ones. The Serials Control System (SeCS) manages ISIS-databases for serials within or outside the ABCD-context. But together, we believe, these parts constitute a very powerful suite of tools, and as an integrated part we hope 'the sum is more than just the parts added up' !

## The ISIS software family (history and overview)

In this paragraph we want to briefly introduce the wider 'ISIS software family' to which ABCD belongs. As with all 'families', members share a lot of characteristics but not all.

The common characteristics of the ISIS family relate to the way how information (of textual nature) is stored and managed by putting it in repeatable fields of variable length with the possibility of subdividing fields into subfields. Fields are in fact couples of a field-ID (a 'tag') combined with a field-value (a text, or in newer ISIS generation, any object, like e.g. 'binary large objects' or blobs).

In addition to technological common characteristics, most if not all ISIS family members share also 'social' char- acteristics, e.g.
* being mainly used in Developing Countries or 'the South', with e.g. a very strong presence in Latin-America, but also - more than can be 'measured' in all kinds of small, often deprived non-connected (no Internet) information centres in Africa and Asia.
* being promoted by many United Nation members and projects, of course first of all in UNESCO-environments, but - as shown by the BIREME example - also WHO and FAO (the AGRIS and ASFISIS systems of FAO can be given as examples here, but also the origin of the WEBLIS library system). The United Nations IFAP and 'Knowledge Society' programmes should not underestimate how much real impact comes from the UNES- CO-promoted information tools like ISIS, IDAMS, Greenstone etc. - sometimes even indicating that the impact can be the reverse of given financial input or publicity.

The following illustration summarizes the full family up to now.

![Slide1](https://user-images.githubusercontent.com/20482054/137317911-2d69015b-5c84-4aaf-9004-58b6546ec262.JPG)


One could summarize the history by claiming the 'family' now has 4 generations while the 5th generation is being prepared :

* The first generation : CDS/ISIS and Micro-ISIS
* The second generation : enriched ISIS/Pascal interfaces, CISIS-tools
* The third generation : graphical, multimedia and multi-database : WinISIS, ISISDLL 
* The fourth generation : WWW-enabled versions (wwwisis, isis3w, openisis…) .

In view of some major technological changes introduced in the newest generation as of 2008 one should perhaps consider the newest ISIS-members (J-ISIS and ISIS/NBP) as representing yet another new 5th generation.

Some highlights of each generation is given below.


#### 1975 - The first generation 

CDS/ISIS at the International Labour Organisation (ILO) Centralised Documentation System merged with Integrated Set of Information Services Running on VAX OS on mainframes


#### 1985 - The second generation

Micro-ISIS G. Del Bigio joins UNESCO and creates PC-DOS based version and integrates separated functions into one general customizable, multilingual menu-based interface with full documentation as version 2.3 Version 3.0 - 3.8 : networked multi-user, ISIS/Pascal UNIX-version for Intel-based UNIX OS World-wide distri- bution and huge success in Developing Countries


* ISIS/Pascal programmed add-ons (e.g. Heurisko, ADEM, IRIS and ODIN, LAMP) create rich tools; e.g. IR- BIS (Russia) for libraries, FAO uses ISIS for its AGRIS-system and ODIN/IRIS extensions for its ASFISIS- system
* Bireme/OPS (WHO Brazil) creates CISIS-tools suite for command-line database management, uses it for its huge health information databases on the Internet; these are multi-platform (run on Unix/Linux and DOS)
    

#### 1995 - The third generation
   * UNESCO produces Windows version : WinISIS, with many graphical, multi-media and multi-database fea- tures
    * Full library automation systems can be and are developed, e.g. PURNA (India)
    * other libraries start using ISIS for full library automation, e.g. SNAL (Tanzania) uses networked ODIN/IRIS based library system for its university library
    * Bireme distributes a web-server version of ISIS as ‘wwwisis’ running on both DOS/Windows and UNIX/ Linux; many applications are developed JavaISIS (Italy) and isis3w (Poland) added to the family
      

#### 2005 – The fourth generation
* Advanced web-based tools spearhead further developments : GenISIS (France) allows easy creation of web- based search interfaces
* WEBLIS (Poland/FAO) is a full-fledged advanced web-based library automation system
* Bireme develops WXIS and adds XML to ISIS
* WXIS-based library systems are developed in Latin-America (e.g. OpenMarcoPolo)
* OpenISIS (Germany) creates first fully Open Source version (webserver, PHP-library) but goes its own way (Malete, Selene)
    
#### 2008 - The fifth generation
   *	UNESCO developes a completely new Java-based graphical interface 'J-ISIS" using not only JAVA-technol- ogy but also the embedded Berkeley DB for the storage layer. This project is a fully FOSS-oriented project.
	* BIREME developes ABCD and - at the same time - a fully new technology for its future ISIS-products : ISIS/NBP. ABCD is meant to be the first applcation to be migrated into NBP.

NBP or 'Network Based Platform' is the new ISIS technology with as the main characteristics :
* flexible archtecture in which 'ISIS-cells' will communicate through known protocols with several plat- forms and interfaces; ISIS-cells will also allow to use different storage models as these will be contained within the cells but they behave in the same standardized way towards the external technology used;

* ISIS databases will no longer have out-dated limitations re database-, record- and field-sizes;
* ISIS databases will be UNICODE compatible
* Indexing will be done by using other FOSS full-text indexers such as Lucene (from Apache Software Foundation).  

ISIS is being used by ten-thousands of users, mostly in the Developing Countries where it is promoted by UNES- CO and BIREME (for mostly Latin America). In Latin America ISIS is very strongly represented in libraries and documentation centres (it has a 'dominant' position even here), in Africa and Sout-East Asia there are an unknown but high number of users, many of them often non-connected to the internet and therefore still using older tech- nology and with relatively poor ICT-skills. This creates a special challenge to the support of the users-community.

At the 3rd World Congress on ISIS (Rio de Janeiro, Brazil, September 2008) the Users Community decided to make ISIS fully 'FOSS' and co-ordinated by an 'International Co-ordination Committee on ISIS' (ICCI), see : [http://www.unesco.org/new/en/member-states/single-view/news/3rd_world_congress_on_isis_to_focus_on_latest_developments_o/](http://www.unesco.org/new/en/member-states/single-view/news/3rd_world_congress_on_isis_to_focus_on_latest_developments_o/)

Summarizing the long history of ISIS, one could say that ISIS combines very sound basic 'textual database' princi- ples, a strong tradition and a world-wide but insufficiently co-ordinated users' community with still modern state- of-the-art technological development.

## From 'free' to 'FOSS'

> Tip:
> You might be interested to read the full article on this topic, published at : 'Innovation', no. 36 June 2008, p. 39-47.
> CDS/ISIS as a software has been 'free' and 'open' since its early days, long before 'FOSS' (Free and Open Source Software) became a known software model (or should it be put in the reverse way : long before 'commercial closed software' became widely practised' ).

### ISIS as 'open' software

Whereas ISIS, from the DOS-version produced and distributed by UNESCO as from 1985, always has been ‘free’
– i.e. without cost but with a restriction to the not-for-profit sectors only – the software was not ‘open’ in the strict meaning of the concept as nowadays known as ‘Open Source Software’ with its different definitions (see [http://www.opensource.org/docs/osd)](http://www.opensource.org/docs/osd)) and licenses (e.g. (L)GPL, BSD, Creative Commons..).

But in 3 meanings there were, already from this beginning - and therefore long before the FOSS movement began to become really visible –, elements of being ‘open’ in addition to being free(ware) :

1.  the standards were open and published. In the ‘CDS/ISIS Reference Manual’, written by its founding father Gi- anpaolo Del Bigio (working for ILO then UNESCO), the technical details were published in the annexes, allowing others to program their own versions of ISIS using the same compatible standards. E.g. in Slovakia Marek Smihla had programmed executables (e.g. ADEM for data-entry) which ran independently from the ISIS-executables from UNESCO and could write and read ISIS-records. Bireme in Sao Paulo, Brazil, did something similar : they pro- grammed writing, reading and indexing tools with lots of advanced features (e.g. joining databases, linking them as relations etc…) in the C-language (therefore CISIS) which are still the basis for their other ISIS-related software : the DLL and the webservers (WWWISIS, WXIS) and which now have expanded capacity, e.g. 4 Gb max. database size, 1 Mb record size, 60 character-index keys. Co-operation was then set up with UNESCO, e.g. allowing the ‘CDS/ISIS for Windows’ to become a mix of UNESCO-programmed and Bireme-programmed modules.

2.  an open, adjustable interface : the software itself was presented as a very flexible environment, with three main features which were used heavily all over the world not only to change its ‘interface’ but also the functions and features.

	* An open menu-structure : Micro-CDS/ISIS was fully based on menus which could be produced and changed by using the software itself, including the definition of ‘actions’ to be invoked by each menu option and allowing hierarchical sub-menus as well as dropping/adding options.

	* An open message system : all messages were/are based on small ISIS-databases which can be edited (each language having its own message-database) and expanded. This not only allowed (often together with the previous feature of open menu’s) creation of rather different conformations of the software – taking into account also colors and screen-features which could be changed – but also expansion and introduction of parameters (which could then be ‘read’ as messages) for additional software running inside ISIS (see further : ISIS/Pascal add-ons), as amply used e.g. by the cataloguing interface ‘ODIN’ and OPAC ‘IRIS’ (by the author of this article).
	* A programming tool ‘ISIS/Pascal’ which acted as an ‘API’ (with published calls for functions and their para- meters) inside CDS/ISIS. ISIS/Pascal programmes, varying from a few lines to thousands of lines for sophisticated applications, could be included into the program either as ‘format exits’ (to expand the functions of the already very rich Formatting Language) or as ‘menu exits’ to expand the functions of the menus, allowing almost independent interfaces to ‘take over’ the CDS/ISIS environment in the creation and manipulation of its databases. One feature illustrating the ‘openness’ was the possibility of adding a parameter in the ‘SYSPAR.PAR’ initialization file to automatically invoke a menu and its option, therefore allowing the menu-interface to be skipped and immediately presenting the new ISIS/Pascal interface. In this way full OPAC (e.g. IRIS using a welcome-screen which could be invoked by a time-out mechanism after a previous session was left) and CD-ROM search modules (HEURISKO is an example) were written, loan-systems for libraries and thesaurus-management tools were produced.
    
	* Last but not least : the ‘open character’ of the Formatting Language. The Formatting Language is a grammar used to define in a detailed way how elements of the database-data, taken from repeatable fields and subfields, also from other records in the same or other databases (therefore resembling relational approaches) and with navigation links, will be ‘processed’ in some output (for display, sorting, printing, exporting). It was largely expanded with graphical features in the Windows version (RichText but also images and extra text- and image-boxes). Together these strong ‘data-processing’ and ‘presentation’ features of the Formatting Language have allowed the production of rather new ‘identities’ of the software, e.g. as a Library Management software with OPAC and Loans System (e.g. PURNA from India). In current applications, based on web-technology, the Formatting Language is still gracefully used to produce HTML-elements (e.g. links but also tables), even if more dedicated tools for that, e.g. PHP, are now added to the power of the own ISIS Formatting Language.

### ISIS as full open source software
 
Already in 2001 UNESCO decided to embark on this relatively new approach of not only providing the software for free but also making the source codes in principle ‘open’, i.e. publicly available (see : [http://portal.unesco.org/ci/en/](http://portal.unesco.org/ci/en/) ev.php-URL_ID=13803&URL_DO=DO_TOPIC&URL_SECTION=201.html). This has finally lead to a frame- work of its wider ‘Free and Open Source Portal’ approach promoting the idea and adding other softwares, e.g. Greenstone, into their ‘basket’ of supported and promoted softwares for better professional development also in the Southern and transitional countries. UNESCO’s FOSS Portal can be found at : [http://www.unesco.org/cgi-bin/webworld/portal_freesoftware/cgi/page.cgi?d=1](http://www.unesco.org/cgi-bin/webworld/portal_freesoftware/cgi/page.cgi?d=1), with interesting links to discussions of the FOSS history, li- censes and case studies. In reality however the source codes for existing ISIS-software are to be requested from UNESCO, but the new softwares will be fully available on public websites.

At Bireme/OPS/WHO a similar decision was taken in 2006/7. No longer would the institute charge a small fee for their software (as was the case before, e.g. 150 USD for official registration as a user with support rights) and therefore make it ‘free’, but also the sources have been and are still being prepared for publication of all their software, including the basic CISIS-modules. Their new ISIS-generation software, called ‘ISIS-NBP’ (Network Based Platform) will follow FOSS-methods (including a ‘community’ with possibilities to contribute, discuss and download sources at the URL http://reddes.bireme.br) to show their firm commitment to FOSS. As the newest full-fledged application, ABCD will be fully published as open source, even if the original development is still centrally managed by Bireme and its own programmers, as the project is now also supported by the Flemish Interuniversity Council (VLIR) with specific requirements to present it as a full competitor to other library systems (including other FOSS–softwares like KOHA and NewGenLib) and to this end needs some more central control for specific purposes.

The advantage of becoming fully open source – for all software - lies in the fact that users, certainly (programming) skilled ones, can fully check on the internal mechanisms and propose/make changes if so desired. One example: WinISIS has a slightly different way of sorting values taken by the ‘VAL’-function (i.e. removing padding 0’s first) which is not a bug as such and therefore does not ‘need’ to be corrected by the software provider; with access to the source codes one could change this however.

As is always the case with open source software, it would be best not to make such changes without consulting/in- forming the ‘developers’ community’.

## Aims of ABCD
    
ABCD aims at providing an integrated library management tool covering all main functions in a library, i.e. acquisitions, bibliographic databases management, users management, loans management, serials control, end- user searching on local and external bibliographic databases and library portal.

it is not the first time in the ISIS-history and -environment that such effort has been undertaken. Open MarcoPolo, Clabel and - as a more advanced effort - WEBLIS are predecessors to ABCD in this sense.

#### ABCD as a generic, flexible bibliographic tool
    
As the name itself suggests, ABCD however aims not only at providing a solution for libraries, but for documen- tation centres as well. These typically have slightly different needs, e.g. have more specialized collections, higher needs re contents disclosure (e.g. by providing abstracts, using thesauri etc.) and requiring more flexibility in the bibliographic structures. For this reason ABCD not only has tried to include full-text features but was principally conceived to offer a very open solution, allowing any fields structure to be created and maintained within the same software. By the database technology of ISIS itself, which is quite flexible and non-restrictive, bibliographic structures can be created without a need to 'normalise' all elements into a series of tables or relations (as is the case with relational database technology) and in most cases all bibliographic elements can be contained into one single database - only for optimization purposes ISIS would expect some semi-relational approaches to be implemented.

As a library system, however, ABCD comes pre-configured for some major bibliographic standards, i.e. MARC21, CEPAL and AGRIS. But we repeat : the same mechanisms, interface and forms can be used to create and maintain any structure, whether bibliographic or not.

So, to put the aims a bit more precise : ABCD aims at providing a very generic/generalizable tool for managing libraries and documentation centres.

#### ABCD as a librarian-oriented tool

Another specific aim of ABCD is to offer a tool for librarians, rather than ICT technicians. This is achieved by taking library and information science principles (rather than computer or programming principles) as the starting point, even in the design of the databases themselves. Typically a bibliographic record is one real entity in an ISIS database, not a complicated series of elements 'queried' or 'joined' together from many tables (as in relational sys- tems), however preserving criteria like efficiency (in space usage, speed of operation..). Each entity subsequently can be thoroughly 'moulded' by the librarians themselves with the use of the ISIS Formatting Language (FL), which allows dealing with all elements of an entity (e.g. a substring from a subfield of an occurrence of one specific field at micro-detail level) without real programming - even if the FL allows some degree of programming logics like loops and nested conditions - for the creation of any output format. This output can be anything like a sort key, an indexing key, a screen format or - as is the case in e.g. ABCD - ISIS-data embedded in web-pages or any other grammar such as XML. Lots of teaching experiences with ISIS show that librarians are perfectly capable of understanding and using all this, reaching advanced results without any real programming.

#### ABCD as a tool for developing countries

ABCD aims at providing librarians and information workers in developing countries a very powerful tool, which however takes into account some specific realities, such as :

-   low availability of ICT skills : as with previous ISIS-based solutions, librarians are - in principle - enabled to solve their problems by avoiding unnecessary software architectures while still allowing flexibility within the software (e.g. through the Formatting Language);
    
-   low availability of bandwidth and connectivity : by using modern web-techniques such as AJAX and JavaScript, data-traffic in between client and server is kept minimal, allowing the local computer (at the 'client-side') to process the data as much as possible without always referring to the server; also the graphical design is kept rather sober for the same reason.

## Actors and partners of ABCD

ABCD, as with all major software projects, is a conglomerate effort of several actors and partners. At the following URL a list of the main actors and partners is maintained : [http://reddes.bvsaude.org/projects/abcd/wiki/HallFame?version=20](http://reddes.bvsaude.org/projects/abcd/wiki/HallFame?version=20)

The main input, obviously, comes from the Brazilian BIREME institute (see http://www.bireme.br), which has availed all of its ISIS-based technology to be combined into one 'culmination' product which is indeed ABCD. In fact the original idea stems from its actual Director, Mr. Abel Packer, who has generously availed also worktime of his programmers and software managers.

A special mentioning certainly is appropriate for Mrs. Guilda Ascencio, Venezuela, who was the main programmer of the ABCD central part with its modules, based on her own 'Orbital Documental' software, in which she had proved that very advanced applications, combining library and other documentation management issues, could be built using ISIS and web-technology.

[!!] Programmers' generously availed by BIREME's director, mr. Abel Packer, have contributed since years to the development of ABCD iAH, Site and SeCS. These contributions represent uncountable and invaluable contribu- tions to the ABCD software - and moreover they will continue developing the software as it will now also be used for BIREME's own projects, adding significantly to the future 'sustainability'.

Both the author of this book and mr. Ernesto Spinak, co-ordinator of the BIREME-based team, have acted as coordinators of the ABCD development project, trying to assemble the many pieces of the puzzle - and to make sure the final picture of the puzzle not only is more or less correct but also somehow attractive.

Two more institutional partners have to be mentioned as well :
-   UNESCO : as explained above in the section about ISIS history, it is clear that UNESCO has an enormous merit in developing and promoting ISIS. ABCD will become part of the set of UNESCO-promoted ISIS products, but through a Memory of Understanding in between UNESCO and BIREME close technical supervision by BIREME will be assured.

- VLIR/UOS : the 'Development Co-operation' section of the Flemish Interuniversity Council (VLIR, Belgium, see http://www.vliruos.be), through a project 'Development Of and Capacity Building in ISIS-Based Library Automation Systems' (DOCBIBLAS) which is promoted by the Belgian co-author of this manual, has selected ABCD as the library automation solution it wants to promote with its partner university libraries in the South (Latin-America, Africa and South-East Asia).
