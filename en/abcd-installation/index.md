---
title: ABCD installation
description: Available installation versions
tags: 
 - installation
 - server
 - apache
lang: en
lang-ref: abcd-installation
---

# ABCD installation

{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Available installation versions
    
ABCD version 1.0 came originally in three main versions :

1.  non-assisted installation package for Windows : this is a ZIP-file containing all necessary files, which simply need to be unzipped into the root of (one of your) harddisk(s), e.g. C:\. Since it encompasses both Apache and PHP, after simply unzipping it should normally work ! Here Apache comes with its own configuration file (httpd.conf) where port 9090 is activated to allow running next to possible other running Apache installations. Only for some specific uses, e.g. the use of Z39.50 which needs additional PHP-modules (YAZ), it will be necessary to do some editing (of e.g. php.ini).
 ABCD installations which will use the Advanced Loans module (EmpWeb) need to additionally unpack the most recent EmpWeb.  zip package, where an extra main subfolder in \ABCD will be created and some additional files will be added to the ABCD Central directory.

2.  assisted installation for Windows : this is a self-installing executable, which will first check whether Apache and PHP are already installed on the system. If so these installations will be skipped, if not they will be added to the basic ABCD installation. This requires mainly following the dialogs and instructions of the installer itself. At the end a similar directory-folder as with the package under 1. will be the result.
    
3.  non-assisted installation package for Linux : this is a .tar.gz archive for Linux systems which should be un- packed into the Linux file-system, depending on its organisation (definition on where such applications can be put). If the correct access-rights are granted (with the appropriate Linux-commands such as chown and chmod) ABCD can be installed, like in Windows, under the file-system root '/'. In Linux systems the assumption is that Apache and PHP are installed separately (e.g. with the dedicated tool like apt-get or Synaptic), so the package only contains the proper ABCD files in the 'www'-directory.
    
The new version 2.0 distribution is simplified : no longer ABCD comes with its own conifguration of Apache with PHP for Windows, since nowadays very good installation packages for these environments exist (WAMP, XAMP) but also these packages arein a better position to keep the different versions of Apache (ASF, Bauhaus ??) in thread-safe or not compiled with one of the many MS Visual C versions (9, 10. 14) streamlined with the correct
versions of PHP, again 32- or 64-bit versions etc.

So the installation for Windows is now very similar to the one for Linux : Apache and PHP are supposed to have been pre-installed and -configured. ABCD only needs a 'virtual host' configuration file to be added into the Apache-server in order to run from that pre-installed version. In e.g. WAMP the file - coming with the installation

- httpd-hosts-abcd.conf simply needs to be added into the 'alias'-directory and Apache restarted.


## Installation issues

This section deals with the installation issues for ABCD. Since ABCD has several totally different components, installation by definition encompasses quite some potential pitfalls. Three main reasons can be given for the in- stallation to be complex :

1.  ABCD is a combination of several software technologies : ISIS-databases, ISIS-scripts and ISIS-formats, a webserver, PHP-scripting, plus (in the case of the advanced Loans module) some JAVA and MySQL parts;  
2.  being web-based, which means a web-server has to be installed and special measures have to be taken about access rights and security : in principle the whole world - with access to the WWW - can interfere.
3.  ABCD will be installed in quite different situations, varying from a simple stand-alone (even non-networked) PC upto servers in big networks with a webserver and often also PHP-scripting services already pre-installed.

Previously the installation packages came in two types :

1.  a full package, containing all ABCD-proper files plus the Apache webserver and PHP-scripting engine.
In this situation an archive (.zip) needs to be unpacked into a root-folder of the file system (which can be any operating system in which Apache/PHP and ISIS can run). After unpacking there will be a dedicated folder for Apache, another one for PHP, a cgi-folder (to contain the web-accessible executables) and a 'documents' folder (in Apache called ' htdocs') which acts as the homepage of the ABCD-application.
	-   Apache comes with a pre-defined configuration file (httpd.conf in the conf subfolder of the Apache folder) which defines the following specific parameters :

|**Apache parameter**| **explanation** |
|--|--|
|ServerRoot "/ABCD/apache"| the directory from where Apache runs|
|Listen 9090|the port used by ABCD, the default http-port being 80, but in order to avoid interference with other ex- isting http-applications, if so desired, a different port can be used, e.g. 9090. In case of using a different port-number, some adjustments will have to be made in the ABCD_start.bat script and in some OPAC- URL's.|
|PHPIniDir "/ABCD/php"|The folder from where PHP is running|
|DocumentRoot "/ABCD/www/htdocs"|The root-folder for all the files which are part of the application itself, so the ' homepage'|
|ScriptAlias /cgi-bin/ "/ABCD/www/cgi-bin/"|The folder in which Apache will executables allow to run from instructions in the web-pages|

> Note: Make sure the 'cgi' module of PHP is installed into Apache,
> which is no longer the case (as before) in newer Apache installations.
> The command to install this module in Linux is :

```
sudo a2enmod cgi
```
-   PHP comes with a predefined configuration in php.ini.

#### PHP settings and php.ini

Since ABCD uses PHP throughout with some additional PHP modules (YAZ, XSLTProcessor...) Pears should be installed within the PHP-installation and some extra modules need to be copied into the PHP 'ex- tensions' folder : php_yaz.dll, yaz.dll, yaz3.dll (these two serve the Z39.50 function of ABCD cataloging), iconv.dll, libxm2l.dll, libxslt.dll (for the XSLT Processor). The PHP-extensions folder needs to be present in the system's path environment variable (in Windows e.g. : go to 'My Computer (right-click) `| Properties | Advanced | Environment Variables | System` variables and edit the Path variable by adding, if not present : ';C:\ABCD\php\ext'). Also make sure your php.ini (in \ABCD\php) has the extensions mentioned here com- mented out (i.e. remove the leading ';' to activate the extension).

* extension=iconv.dll
* extension=iconv.dll
* extension=libxml2.dll
* extension=libxslt.dll
* extension=yaz3.dll
* extension=php_yaz.dll

Be careful with possible other php.ini files existing, e.g. in \Windows or \PHP as these might disturb your ABCD-PHP. A PHP-test option is available with ABCD at the URL : http://localthos:9090/info.php. We are specifically interested in the following section below, where XSL and YAZ should be mentioned as running

-   if not check your path-environment variable and all paths again, as well as the 'extensions' section of your php.ini !
    
  
![](https://lh3.googleusercontent.com/pbkmTbhGVKMZUoDhfCpUtppoiU7g62SzdWYvph68NZ6bmxAk7jxFzqSCuuJOM1uw4zLhJclusfPHuLy2TkeeukzIDPnMZVm8PCXcMnCrS-v9HUwgEEO3hYrHLEF4_4EhhWFOfTgl=s0)  
  

The php.ini file contains a few more settings which need to be checked for ABCD to run correctly :
-   register_globals = On (default = Off)
-   short_open_tag= On
-   extension_dir = "/ABCD/php/ext" (or adjust to the real path to your ABCD installation)
-   default_charset = "iso-8859-1" (default = not active) or "utf8" if Unicode is to be used
-   extension_dir = "/ABCD/php/ext" => defines the extensions directory
-   extension=yaz3.dll and extension=php_yaz.dll are listed in the => are added in the 'Dy- namic Extensions' section in order to allow the YAZ-module for Z39,50 to work

Note
As from ABCD 2.0 it is no longer required to keep the setting for 'short_open_tag' to 'On' (which is contra-indicated anyway). All 'short open tags' ```<?``` have been changed to ```<?php``` .

2.  an ABCD-only package, requiring Apache (or another web-server) and PHP already being installed.

In this case the assumption is that at least some expertise is available to understand the existing web-server installation and PHP configuration. Using ' aliases' for the ABCD-installation and cgi-folder, which can be put in a virtual host configuration file, ABCD can be installed anywhere inside or outside the existing home-folder for the web-server. So only the cgi-folder and htdocs-folder is included into this package. System managers should refer to the Apache and PHP manuals in case they are not sure about how to proceed with this type of installation.

Alternatively one could also use prepackaged installations like EasyPHP or WAMP (for Windows) / XAMP (for UNIX/Linux). Again in this case Apache and PHP (and MySQL) will be automatically installed and the ABCD cgi-bin and htdocs folders have to be moved into the existing folder-structures (of Apache) and php.ini has to be edited.

As from ABCD 2.0 only the second type of distributions will be available, leaving the installation of Apache and PHP to other, more specialised packages such as WAMP or XAMP. Only a specific 'virtual host' configuration file for ABCD needs to be added to the Apache configuration (e.g. in WAMP : by putting it into the 'alias' directory) and some PHP settings need to be checked in php.ini to activate additional extensions e.g. for gd2, libxml, xsl, and if the related functions are used : ldap, yaz, mysqli (for Empweb) and mbstring (for Unicode).

A dedicated installation tool will be created as part of the ABCD-software, but in essence still doing the same as described above, only after collecting some parameters for installation (like which disk to use, which port etc.).

## Directory structure and access rights

After installation of ABCD the following folder structure will be created (in this case EmpWeb is included) :![](https://lh4.googleusercontent.com/qLB6IsXz6bzbMin7kOq6XtfMJUFdkHZUzMBv0eAOZHTTtrrgJZ1H0ziZM7xsbJnwdVeNzQ6gVg17NG-rhtiHqK3fiaWqYI-mpnzbDKzIzIXgbYXp_QAA5XRF1G00OmffiXQ9p5GP=s0)

As can be seen, 3 (or 4 if EmpWeb is included) sub-folders have been created in the main folder /ABCD. In the case of installation of the optional Advanced Loans folder one more folder containing basic technology for ABCD will be added : the Java Development Kit (JDK). The standard folders are resp. :

#### apache [ABCD 1.x only]

The Apache folder contains the Apache web-server software, which is in fact only of several important soft- wares developed by the Apache Software Foundation. By default Apache webserver is installed in another base- folder (e.g. in Windows : C:\Program Files\Apache Software Foundation\Apache2.2) and network-managers will probably have installed Apache on their server(s) according to their own preferences, but when installed from the 'full ABCD-package' Apache will run - with its configuration file httpd.conf adjusted for this situation from \ABCD\Apache.


#### php [ABCD 1.x only]

The PHP folder contains the PHP scripting software. Again, as with Apache, in many instances this software will be installed in its own right, e.g. in C:\PHP, or often also as part of a combined package containing Apache, MySQL and PHP, e.g. with EasyPHP or WAMP-server. When installed as part of ABCD however PHP will run from here with the necessary adjustments done in the main PHP-configuration file php.ini.


#### www
The www folder contains the whole ABCD system, which is subdivided in 4 folders :

![](https://lh5.googleusercontent.com/L8VMgbN73AAypaMHcVUEOHhI9UrXunKxtYtccKqiI-zlfep4M_mdguSBw7q0B8m3m94pCc5qhy5dZ41Ii-B4vEh9W9-btdHUw366bmpvEEc8FJeM5UzztH8Lso9mU7YeK9LGjVjx=s0)
	
* bases

The bases folder contains the databases of your ABCD installation, which one dedicated subfolder (with many subfolders in its turn) for each database. When an additional database is copied or created using ABCD, the system will create such a dedicated extra subfolder here. A typical list of database-folders in the /bases folder looks as follows :

![](https://lh6.googleusercontent.com/LabEXUm9-Q2wVGwdg5rAzOSpf1CFC9hIZOBrv5_8SV174Q6yrlT1u5GC1LgsSoYQ-i50enpQwQZDgG6rJfy80AI8LAHji71wZSGkOzke4_V8wxTGPwbHC5-Z9Ou2TLbLOXvkzqr7=s0)

  
[!!] As can be seen, many databases exist (but not as many as there are tables in a relational setup, since ISIS does not practice 'normalisation' into related tables), some of them - e.g. marc, biblo, dblil - are models coming with the installation of ABCD, others - in this case e.g. 'gemim' - are created by ABCD in the author's installation only, while finally others are serving specific modules of the library system, e.g. 'providers' and 'purchaseorder', are used for the acquisitions module, 'suggestions', 'suspml', trans and users are used for the Loans Module. 'recommend' and 'reserva' meanwhile are legacy folders to older ABCD-versions pre 1.0. So each ABCD-bases folder will be different according to the actual databases used.

Some essential configuration files to be located in this folder are :

-   bases.dat : the list of databases available to this Central-installation (i.e. a database-name, a column-sep- arator `'|'` and a description
-   lang.tab : a list of languages used as key-value pairs for code-full language, e.g. en=english
-   abcd.def : the main system-wide configuration file, see the configuration section
-   loans.dat : if this file exists, ABCD Central will use the copies/loanobjects directly from the catalog-data- base, not from the dedicated copies/loanobjects databases;
-   acquisitions.dat : a file listing the catalog databases to be used for acquisition of copies, e.g. 

    marc|Marc
    biblo|Cepal


Note that since more than one bases-directory can be defined (in db_path.dat), also different files abcd.def (with e.g. different LEGEND1 and LEGEND2 parameters to identify the base-directory on the screen in the footer) can be used.

A special database is the database 'acces' which holds the users (with their login data) and their access-rights (authority level) to the databases.

In the 'www'-folder ABCD keeps some small special files, e.g. the 'prolog' and 'epilog' html-codes which will be invoked resp. before and after the main page contents of each ABCD-page produced by an ISIS-PFT. This is where system manager could - if so desired - add code (e.g. JavaScript) they want to be executed at each page.

The 'LANG'-folder is also quite special : it contains, for each language used, the tables with messages used for each of the Central modules. E.g. the 'lang.tab' file contains the information on the actually officially supported 4 languages : pt=Portuguese fr=French en=English es=Spanish. This list of languages for each language is based on the basic language-authority file lang.tab in the bases-folder itself (where it resides along with the authority list of databases available : bases.dat).


> Note: 
> [!!] The '00' lang subfolder contains the tables serving as
> 'master' for the other languages. Whenever a message is not found by
> ABCD in the language selected, it will refer to these tables and use
> the messages contained there, to avoid missing messages in any
> language. This way one can also start translating into a new language
> without having to finish the full job before using ABCD, as the
> missing messages will be taken from the language '00'.

Finally also the folder 'par' is, like 'lang', not a database folder but it holds the .par files for each database known to ABCD. A .par file actually is a small text-file (so it can be edited by any TXT-editor like Notepad) with on each line the full path reference to parts of the database concerned. E.g. a typical .par file for ABCD looks like this :
  
```
marc.*=%path_database%marc/data/marc.* 
prologoact.pft=%path_database%www/prologoact.pft 
prologo.pft=%path_database%www/prologo.pft
epilogoact.pft=%path_database%www/epilogoact.pft
epilogo.pft=%path_database%www/epilogo.pft
autoridades.pft=%path_database%marc/pfts/en/autoridades.pft”
```
  
Each element gets, after the equation sign, its path in the file-system. As can be seen, variables taken from the Operating System's Environment can be used, in this case %path_database%, which is substituted by the real pathname as defined in the main configuration file config.php (see infra).

[!!] While normally all elements referred to here belong to the database in question, elements of other data- bases should also be added if they are used in 'REF'-statements of the formats used in this database, since ISIS will have to know where to locate such external database element if called from a format - and will look for its path here !

#### cgi-bin

The cgi-bin folder contains the executables which ABCD will call from its web-pages and which therefore should be authorized to run by the webserver (Apache) using the CGI-protocol. In the case of ABCD the main executable is the wxis.exe ISIS-server, which does the main part of the job. Some other CISIS-tools are however also included for specific tasks.

The wxis-modules subfolder here contains scripts (with .xis extension) for the wxis-server, while the 'gizmo' folder contains some small ISIS-databases which define strings to be substituted by another one, e.g. for changes due to different environments used (DOS/ASCII, Windows/ANSI, WWW/XML.

#### htdocs

The htdocs (we use the traditional Apache 'hypertext documents' folder name) is the 'home-folder' of the web-site served by the ABCD-Apache server. So therefore it contains all the software elements (except the basic external technology such as Apache and PHP) specifically produced for ABCD :

![](https://lh6.googleusercontent.com/sMJ-zXYZyOb7bqWiOXNhZrCwJcjDM4wMvDfQeBnPVvZNCQndBx7axGxsSj-RBXab_ZbqgtLplxoPpKSMcKaAfxK7zACGetmaU9_qmgbWQ9d_XcjFtdCZ440jyQI7DrxdZ7_SKn_7=s0)  

  
Two initial scripts are present within this homepage folder : index.php (which is the default home-page indeed, allowing the URL of ABCD only to refer to the server-part) and the [!!] 'what.php' script for including the footer info.

An optional file 'db_path.dat' can be located here to point to different (each on one line) database-folders.

Since ABCD is a 'suite' of different functions, each one has its own homepage, i.e. the 'index.html' file located in the appropriate subfolder.

The main folders of the ABCD-system are briefly described below here :

1.  **bases**
Here for each database (in a dedicated subfolder) external files linked to from the records in the database,
e.g. full-text PDF's or images, will be stored E.g. the user images can be stored here in a subfolder 'users', so the photos of the user will be shown whenever a loans-system user is presented. [!!] Don't mix this folder up with the 'bases' folder where the actual databases reside !

2.  **central**
This is indeed, as suggested by the name, the 'central' part of the system where most of the database administration and many core-activities of the software are included. We will therefore deal with the important subfolders contained in here :

![](https://lh4.googleusercontent.com/oAeaF6wjkV-srtvdNT7KsY7pnflDrxcCU7E-uN4E0v-GdTvGwGzEyQ1Fka6AJTAu_359kJoQSjhNNJ3aGbPKpB4ukRNKGZpfoevjmVursjPkc01DMh2s3vjhJ2icywVN-1arTz_8=s0)

Some initial scripts are located at this level : homepage.php and inicio.php are the starting pages, which read into memory the main configuration parameters defined in config.php (or config.loans.php for the Loans module). For the 'mySite' functionality, additional initial scripts will be found here too : ini- ciomysite.php, homepagemysite.php and availibility.php. These scripts now (as from ABCD2.0) contain both the code for EmpWeb (using SQL-queries) and Central Loans (using ISIS-QL), so e.g. 'empwe- bavailability.php' is no longer used since the code is included in 'availability.php'.

The basic configuration files CONFIG.PHP, SYSTEM_CONF.PHP and DATABASE_CONF.PHP, which are also found here, will be discussed in more detail in their dedicated sections on the ABCD- configuration.

The following folders here deal with one specific function or module of ABCD by storing the PHP-scripts with lots of additional elements (images and style-sheets for the webpages etc.) : acquisitions, dataentry, dbadmin, loans, statistics and usersadm.

The names of the folders are sufficiently self-explanatory in these cases. Here we would only like to underline the presence of a module 'database administration' which allows creation of any ISIS-structure  to deal with any type of textual data, allowing ABCD to be more flexible than most other systems and more than just a library system.


Special folders here dedicated to special functions in ABCD here are the following :

-   common : in here there are some crucial php-scripts which are needed by all modules, e.g. 'header' and 'footer', but also 'wxis-llamar.php' (which allows using either the cgi-method of calling executables (safer) or direct executable calls from PHP (faster). The instituational_info.php script defines the name of the resonsible institution of the ABCD-installation, which will be called upon in many pages.
-   documentacion : obviously this folder contains scripts to deal with the online-help functions of ABCD.
-   images : contains small images used in many pages (mostly .png and .gif)
-   css : contains the Cascading Style Sheets used in this central part of ABCD
-   styles : contains the basic main stylesheet 'basic.css'
-   lang : contains for each module a script to facilitate language switching or reverting to the default language
-   [deprecated] test : contains some scripts testing the ABCD-installation and access to the cgi-executable.

3.  **empweb**

This folder is non-standard and contains the subfolders and software parts used by the Advanced Loans module of ABCD, which is not further detailed in this manual.

4.  **iah**
iAH is the original name of the advanced web-interface for 'Health Information' of BIREME which acts as the OPAC of ABCD but also as a meta-search engine on other defined-as-relevant sources.

5.  **isisws**
This folder contains scripts for the SOAP-related functions of ABCD.

6.  **secs-web**

This module allows ABCD to offer advanced serials management tools within the web-environment :
Serials Control System. vii.site

Finally the 'Site' module combines advanced OPAC searching (with meta-search possibilities) with a 'por- tal' service, offering the search option within an environment of other networked information resources and communication with users. The structure and the contents of this portal can be edited online with a built-in ABCD Content Management System.

  

#### EmpWeb (only if installation of EmpWeb was added !)
    

This folder contains most but not all files necessary to run EmpWeb, e.g. the Java Jetty server and the scripts. EmpWeb however additionally needs also added scripts in ABCD Central (this allows the Advanced Loans to be compatible with the built-in Loans system of ABCD) and - since it uses an SQL-database for storing the transactions - an installation of one of the common SQL-databases (MySQL, PostGres, Oracle...), which needs to be done separately - use the installation instructions for the SQL-solution chosen. A separate manual on EmpWeb is available.
