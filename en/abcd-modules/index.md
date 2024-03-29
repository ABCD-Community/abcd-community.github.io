---
title: ABCD Modules
description: This chapter deals with the main functions [!!] of the 'Central' module of the ABCD system.
lang: en
lang-ref: abcd-modules
---

# ABCD Modules

{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---



## Introduction and general configuration   

This chapter deals with the main functions [!!] of the 'Central' module of the ABCD system. As an integrated 'library automation software' the system offers tools for database management (both for bibliographic/document databases and administrative databases such as users, acquisitions and loans), data-entry, statistics, circulation, serials control and searching functions (OPAC in a 'portal' environment).

These functions are presented in different parts of a suite, which are relatively independent from each other but not fully. Parts are accessed by their own URL. Within one part several modules can exist which also cooperate. For example the pre-cataloging information produced for acquisitions will be re-used in the copies-database for the inventory and loan-objects database for the circulation module, which in its turn uses bibliographic information from the catalogs. Statistics can be applied to any ISIS-database, not only the Circulation databases, so this function will also re-appear at several instances within the software. The OPAC-technology can run on any ISIS-database, not only the own ABCD-catalogs, so it will be described as a relatively independent tool, as will be the case with the Serials Control.

**Important**
How to access the suite parts directly ?

-   The first six modules together constitute the 'Central' part of the ABCD-suite. It can be accessed by the [!!] URL http://[serverURL]:9090. The 'index.php' part is optional if the web-server (Apache) has been told that index.php is one of the default pages in the folder (as is e.g. also 'index.html').
   
-   The combined OPAC-with-portal (Site) can be accessed by http://[serverURL]/site/index.php, with the administrator page for this Site being http://[serverURL]/site/admin/index.php.
  
-   The Serials Control part should be accessed by the URL http://[serverURL]/secs-web/index.php.
   
-   EmpWeb can be accessed, if installed, by the URL http://[serverURL]/empweb/ (note the trailing for- ward-slash here !)
   
For all these parts or modules ABCD provides publicly available start login data, which need to be read from the 'leiame.txt' or 'readme.txt' files coming with the installation package. It is the responsibility of the system manager to take these login data out of the system and replace them by local - and locally controlled - login data.

ABCD manages the control of who can access the system and with which privileges through a system (introduced with version 1.0) of 'profiles'. Profiles are sets of allowed modules, databases and forms. ABCD users (not library patrons) then will be assigned to one of the defined profiles (see 'Users Administration' in the following section).


## Multilinguality configuration
    
ABCD is fully conceived as a multi-lingual software, allowing the creation and use of any language. All lan- guage-sensitive elements, such as screen messages and help-files, but for databases e.g. also display-formats, field- definition and -selection tables etc. are stored in separate subfolders for each language. These subfolders are named according to language-codes which are defined in the file 'lang.tab' of the 'bases'-directory. An example of such lang.tab file, in which two additional (non-Latin alphabet) languages have been added to the four original default languages, is listed here :

* pt=portuguese 
* es=spanish
* en=english
* fr=french
* am=amharic
* si=sinhalese

With this list all messages (the 'lang'-database) and database-structures and -printformats will (need to) have sub- folders pt, es, en, fr, am and si. The list of languages has to be repeated in each lang-subfolder, if so desired translating each of the language values (not 'keys' as the abbreviation codes need to remain constant !) can be translated into the underlying language and - if 'Unicode' is switched on (see infra) - even written in non-Latin alphabets. Beware of non-ASCII characters such as 'ñ' (e.g. in español) since these are coded differently in ANSI (Windows) vs. Unicode.

Since ABCD can deal with multiple database-folders (see infra), it will be necessary to define the path to the 'lang' database for the messages with the variable '$msg_path'. This defaults to the directory defined by $db_path in config.php but can also be defined independently to any folder in the system.

A special 'virtual' language with code '00' is used in ABCD to hold all messages from which the language transla- tions will be derived. These key-value pairs are mostly defined in English. The keys are the ones referred to in the PHP-scripts whenever displaying a language-dependent text on the screens, but will be searched for in the related table in the active language, unless it cannot be found there : then the '00' language acts as the reserve fall-back option. This means that if a message appears not in your own language but in English (supposing your language is not English), then that key still needs to be translated (added) to the corresponding table for your language and the message displayed is taken from the '00'-language.

Later in this manual a dedicated section will discuss how to create a mew language in ABCD with a Unicode non-Latin example.


## The main configuration files for ABCD Central

The main configuration of ABCD Central is based on the following files :

1.  config.php
2.  system_conf.php and abcd.def
3.  database_conf.php and dr_path.def

### CONFIG.PHP
This file contains the local variables which are managed by the system administrator. Currently the list of variables is as follows :
-   Date_default_timezone_set (the allowed values can be found at the URL [http://php.net/manual/es/time-](http://php.net/manual/es/time-) zones.php
-   $ Open_new_window : if set to 'Y' after logging in a new window with the main ABCD-interface will be opened in addition to the login screen
-   $ Context_menu : if set to 'N' the Central interface in the new window will not contain navigation elements (e.g. by 'right-clicking') - this is safer for keeping the ABCD work apart from other browser-activities and force the operator to use the interface elements rather than browser-elements e.g. to 'go back'
-   $config_date_format : defines the format of the dates used; to be given as DD for days, MM for months and YY for the year-display, each time separated by slashes '/'.

> Note:
>  If a field is defined as 'ISO'-date, the format will
> automatically be yyyymmdd; this can be automatically derived from a
> preceding normal date-field defined with $config_date_format

-   $Inventory_numeric : if set to 'Y'es leading zero's (at the left) will be omitted when reading the inventory number (or barcode) to make it a real numerical value
-   $max_inventory_length : a number defining the fixed number of positions in the barcode or inventory numbers; missing positions will become leading zero's. This parameter is taken into account in the processes related to the assignment of the inventory numbers of the database copies
-   $max_cn_length : same as $max_inventory_length but for the Control Number field : missing positions up to the number defined here will be filled with zero's
-   $app_path : the name of the folder acting as 'Central' with all Central scripts; best kept as 'central'; if renamed some scripts might fail.
-   $log : if set to 'Y'es 'and a subfolder 'log' exists in the database-directory, all calls to the Isis-executable 'wxis' will be logged in one file per day named according to the date and with the following information :

First line : 
```
** Friday 30th of November 2012 07:34:35 AM Operator: abcd Identifies the date, time, and operator executing the transaction
```

Second line: 
```
/central/dataentry/ini- cio_main.php/ABCD/www/htdocs/central/dataentry/wxis/login.xis IsisScript = / ABCD / www / htdocs / central / dataentry / wxis / login.xis ? Base = access & cipar = c: /bases_abcd/ bases/par/acces.par & Login = abcd & password = adm & path_db = c: / bases_abcd / bases / & cttype = s
```

where the following elements are identified: name of the php script that is running, name of the wxis script being invoked, parameters sent to IsisScript for the corresponding execution

> Note:
> In the future this log will also be made database-dependant.

-   $img_path : derault path where the images and digital documents linked to the records of the databases will be stored. This default directory can be modified using the dr_path.def file that provides more specific information about the storage of digital documents for a specific database (see infra).
-   $msg_path : path to the lang-database for the messages of the interface; this path can be in one of the defined database-folders but also outside any of them
-   $lang : default language used when opening Central
-   $lang_db : default language for the database administration module (can be different from $lang)
-   $change_password : whether 'Y'es or 'N'ot operators are allowed to change their passwords (in the login-screen)
-   $adm_login : an optionally built-in login-name to (temporarily) allow entering the Central system even if the access to the databases is not possible, e.g. for debugging/testing reasons; for security reasons : remove this login when not needed.
-   $adm_password : an optionally built-in password for the login with $adm_login;

> Note:
> remember this login/password acts on the full-administrator level and therefore is at a high-risk level !

  -   $dirtree=1: show (1) or hide (0) the icon or menu-entry that gives access to the exploration of the bases-folder; some network- or server-managers will not allow such function on their system !
  -   $MD5= When set to 1 (on) passwords will be encrypted with the MD5 encryption
  -   $fix_file_name = defines an array with substitutions of characters to be applied in file-names for uploaded files (in order to avoid complicated e.g. diacritical characters; the default values are :

```
array('Š'=>'S', 'š'=>'s', 'Ž'=>'Z', 'ž'=>'z', 'À'=>'A', 'Á'=>'A', 'Â'=>'A', 'Ã'=>'A', 'Ä'=>'A', 'Å'=>'A', 'Æ'=>'A', 'Ç'=>'C', 'È'=>'E', 'É'=>'E', 'Ê'=>'E', 'Ë'=>'E', 'Ì'=>'I', 'Í'=>'I', 'Î'=>'I', 'Ï'=>'I','Ñ'=>'N', 'Ò'=>'O', 'Ó'=>'O', 'Ô'=>'O', 'Õ'=>'O', 'Ö'=>'O', 'Ø'=>'O', 'Ù'=>'U', 'Ú'=>'U', 'Û'=>'U','Ü'=>'U', 'Ý'=>'Y', 'Þ'=>'B', 'ß'=>'Ss', 'à'=>'a', 'á'=>'a', 'â'=>'a', 'ã'=>'a', 'ä'=>'a', 'å'=>'a', 'æ'=>'a','ç'=>'c', 'è'=>'e', 'é'=>'e', 'ê'=>'e', 'ë'=>'e', 'ì'=>'i', 'í'=>'i', 'î'=>'i', 'ï'=>'i', 'ð'=>'o', 'ñ'=>'n', 'ò'=>'o','ó'=>'o', 'ô'=>'o', 'õ'=>'o', 'ö'=>'o', 'ø'=>'o', 'ù'=>'u', 'ú'=>'u', 'û'=>'u', 'ý'=>'y', 'þ'=>'b', 'ÿ'=>'y',' '=>'_' );
```

> Note:
>the last element substitures a space for an underline in file-names

-   $show_acces= When set to Y(es) the 'acces'-database with operators and their passwords (yes or not encrypted depending on $MD5) will be shown in the list of available database (if included there).
-   $EmpWeb= When set to 1 (on) the loans-system will use the EmpWeb Advanced Loans module and mecha- nisms e.g. in 'MySite' or availability-checks.
-   a new section can be optionally added to CONFIG.PHP dealing with the variables needed for the LDAP-au- thentification function, with example data given :

```
$use_ldap=false;
$ldap_host = "ldap://zflexldap.com";
$ldap_dn = "cn=ro_admin,ou=sysadmins,dc=zflexsoftware,dc=com";
$ldap_search_context = "ou=guests,dc=zflexsoftware,dc=com";
$ldap_port = "389";
$ldap_pass = "zflexpass";
```
  

-   finally also an optional section can be added to assist the configuration of EmpWeb (if used), more specifically to pre-define some variables and re-define some ports :

```
ProxyPass /empweb/ http://127.0.0.1:8080/empweb/ // to direct calls to empweb to port 8080 instead of 9090
ProxyPassReverse / http://127.0.0.1:8080/ // reverse of previous

$empwebservicequerylocation  =  "http://localhost:8086/ewengine/services/Empweb- QueryService";
$empwebservicetranslocation = "http://localhost:8086/ewengine/services/EmpwebTransac- tionService";
$empwebserviceobjectsdb = "objetos";
$empwebserviceusersdb = "*";
```
  

> Note:
> DEPRECATED VARIABLES : $institution_name and $institution_URL are no longer used but replaced by variables in abcd.def (see next section).

### system-variables defined in abcd.def

In the main bases-folder (in Windows e.g. C:\ABCD\www\bases, in Linux : /var/opt/ABCD/bases) a file 'abcd.def' defines system-wide variables. The main current variables here are :

-   LEGEND1= followed by the text to display at the second line of the Central footer
   
> Note: The 1st line of the footer is defined in the code of the script 'htdocs/central/common/footer.php. In this script also the following variables are arranged, so the administrator could envisage re-arranging them if so wanted by changing the (simple) script.

-   LEGEND2= follwed by the text to display at the header of Central (next to the ABCD logo)
-   URL1= followed by the text to display as the third footer line as a link
-   URL2= followed by the text to display as the fourth footer line as a link
-   FRAME_1H= a value (typically 100) defining the number of pixels for the height of the upper segment (mostly dark-blue background with ABCD logo) in the Central data-entry screens 
-   FRAME_2H= a avlue (typically less than 100) defininng the number of pixels for the height of the toolbar (with search-box) segment of the Central data-entry screens.

> Note With the variables FRAME_1H and FRAME_2H the administrator can adjust the interface to different resolution screens, however only at a system-wide level. Lower-resolution screens will require lower
> values.

-   MULTIPLE_DB_FORMATS=
 -   UNICODE=
 -   DIRTREE_EXT=
-   LOGO=[filename with logo picture] : reference to the picture file to be used as logo in the upper part of the
    
Central screen. The default logoabcd.jpg ![](https://lh3.googleusercontent.com/pz0ijzABDs0pzAV7feD4xFc4IDNCVCbayoU0n-v4TAQa7FP84yRWhYHcGLI443BbutsqMu0-R_TCLIsKn4vxkDg7gL5XC6YqJNXrRW0K4lDM64Cyj3yZap3ZgithA6CsXiejx4Jt=s0) can be replaced by any localized image here. Make sure the image is small enough (e.g. max. 3 Kb while the default is only 1,2Kb). Tools for re-sizing pictures are freely available for both Windows and Linux.

> Note The logo for ABCD iAH and Site need to be defined differently.
> E.g. for the OPAC (iAH) the image is defined in the file
> htdocs/iah/iah.def.php with the variable 'LOGO IMAGE=' ,

  
### database-variables defined in dr_path.def

In this file 'database-related paths definition', to be located in the base-folder for each database, some variables can be defined which re-define characteristics of the database. These parameters are ALL optional ! Currently the list of variables at this level is :

-   ROOT= defines the default path for this database where files attached to the record, e.g. images, PDFs etc. will be stored, e.g.
 ```
- ROOT=/var/opt/ABCD/bases/marc/dr/
```
-   IMPORTPDF = defines with Y or N whether documents (PDFs) can be imported into this database. if 'Y'es the PDF-icon will be shown in the Central toolbar
-   barcode = defines with 'Y' or 'N' whether or not barcodes are used in this database; this parameter defines whether the barcode icon will be shown in the Central toolbar
- tesaurus = defines the name of the thesaurus-database to be used with this database, e.g. tesaurus=agrovoc

> Note:
> the Spanish spelling of 'tesaurus' in this case

-   prefix_search_tesaurus= defines the prefix with which the descriptors in the database are indexed, e.g. MA_
-   COLLECTION= defines the path were digital library collections will be stored for this database. Such directory could be defined under the database-folder itself (e.g. /var/opt/ABCD/bases/dubcore/collection/) or as a collec- tive directory for all databases in the system (e.g. /var/opt/ABCD/bases/collections).
-   UNICODE= defines with '1' or '0' whether the database uses utf8 or unicode encoded content. In fact any value greater than 0 can be used, e.g. 'Y' will simply indicate 'yes, use unicode', '1' but also '2' etc. will also indicate 'yes use unicode' but at the same time identify Unicode character-subsets to be used, e.g. '1' includes Amharic, '2' includes Sinhalese, '3' includes Arabic etc. These codes are relevant for the OPAC where the alphabets will be shown in clickable icons.
    
### Defining different database-directories : db_path.dat

The file 'db_path.dat' in the bases-folder allows to define several directories (or folders) to be used as bases-folder, not only the current one (defined in CONFIG.PHP). The lines in this optional file contain the path, followed by a column-separator `'|'` and a description as shown in the selection-menu.

E.g. to define 2 database-folders, one with operational and one with test-databases, the file db_path.dat would be (example for Windows) :
```
C:/ABCD/www/bases/|Operational 
D:/databases/|Test-databases
```
These two options will appear in a list in the login-screen of ABCD Central and the $db_path variable will be substituted by the selected one.


## Login configuration of ABCD Central

The most important configuration file for ABCD Central is the file 'config.php' in the /www/htdocs/central folder. We discussed some general parameters earlier on (in the section about installation) as they deal with installation paths and default language to be used, but at the end some parameters are introduced which provide a recovery solution for the case when the general System Administrator login data have been lost (meaning the system cannot be entered by anyone anymore !).

These parameters are :
```
//USE THIS LOGIN AND PASSWORD IN CASE OF CORRUPTION OF THE OPERATORS DATABASE OR IF YOU DELETED, BY ERROR, THE SYSTEM ADMINISTRATOR

$adm_login=""; $adm_password="";
```  
```
//USE THIS PARAMETER TO ENABLE/DISABLE THE MD5 PASSWORD ENCRYPTION (0=OFF 1=ON)
$MD5=1;
```
By manually editing (e.g. with Notepad or another flat-ext-ASCII editor) the $adm_login and $adm_password parameters one can create temporary login data, which will allow to create real logins again (using the database administration tools for the USERS-database). It is strongly advised to immediately thereafter again remove the login-data from this file config.php - for obvious security reasons.

The $MD5 parameter will invoke password encryption (using the MD5 algorithm) when put to '1' or not if put at '0'.

## Administration of the ABCD user profiles.

From the main Central menu option 'Users Administration' one can enter the 'Create/Edit profiles' option in addition to create/edit/delete system users.

Some profiles come with the ABCD installation as examples, e.g. :
-   System Administrator
-   Database Administrator
-   Database Operator
-   Operator LIS
![](https://lh6.googleusercontent.com/we6opfWnYf-8n_b1lhuqxlCJuXuCwry7J7qqxIWQ8C4De6rGRtjzPSqc9aLRV-1O-G_wKFCo5_x37SbMLFcEhqY-5wak5o8mpvKjGnXFETGrh2JQi9AesI-35PryH8bPKG9fptoZ=s0)
    

As can be seen from this screen, the administrator has to enter the following data :

1.  profile name : any (short) name for the new profile to be created
2.  profile description : any description describing the profile
3.  for each database listed : whether or not access is granted and which data-entry forms of that database can be used by this profile. If all, 'All' can be checked for simplicity.
4.  Permissions : for each module (Cataloging - Circulation - Acquisitions) the menu-option (or function) to which this profile should have access should be activated (in the small box).
    
> Note:
> The list of profiles is kept by the Operating System in the file
> 'profiles.lst' in the bases/par/pro- files and for each profiles the
> characteristics (databases allowed, modules allowed are kept in a file
> named after the profile (without extension). Privileges not granted in
> the profile are assumed to be  'not' allowed. The privileges have
> brief but mostly self-explanatory names, e.g. 'delrec' for deleting
> records, expimp for exporting and importing records etc.


## Logging in into the system
    

After profiles have been created (or adopted from the default ones) and have been assigned to system users, any of the system users' logins can be used to enter the system. Unlike in previous preliminary versions of ABCD, it is obviously no longer necessary to select an authorization level when logging in, since this is now coupled with the login itself. Therefore in addition to login-name and -password only the language to be used is to be selected (this list is taken from the file 'lang.tab' in the bases-folder of ABCD (default : /ABCD/www/bases).![](https://lh4.googleusercontent.com/2ZyI0IeAoy6CyZGF8xtW16RYHd_9jh7g-AK6F-oshgPdBMUlrNef3piVWKj3K3x9mAjxsqvUHVg837ECB_pTIiaFhKeYgb3RJp2mLqmox-MU4RVUeq2GuToD_KdCp8feBAkfVDXh=s0)
 
As from ABCD 1.5 and 2.0 on the login-screen also provides a link to change the password, which gives a dialog to enter user_ID, old password and the new password twice, as illustrated here :
  
![](https://lh3.googleusercontent.com/MIVslA5az-6SPXmXrnrfTLPvaoDsEzVmcm1-XuOlyCMuWjg5IklAsVe0VbwcLlNYQbM_n0erw1D7bhrtK8wQbMniz48hq5Qe4prdZLQb579NPPj9ksmOIMp88tYSabqsspGHjgBQ=s0)  

This login-screen has one option 'Open in new window' ![](https://lh6.googleusercontent.com/NOO262msBChAvhySwoftlShZTmKmEhtgbqSIbG1_I7oimt9TGi25YraXZnHQc5zFwGUS6H_Rpohq642tQL9XmBMU2gwAwW2ofubnOiKw_jKrAk4EOg8cpSlOIYFnVX3dWAU0RKnz=s0)as a 'tickbox' for which the de- fault value is defined in the general configuration file 'config.php' of ABCD-Central with the parameter-name '$open_new_window' which can be set to "Y" (meaning after login ABCD will use a separate window, which avoids interference with other tabs or wrong use of the 'BACK' button of the browser) or "N" to simply open the ABCD window in the same area; the other parameter linked to this behaviour in 'config.php' is '$context_menu' which also can be set to "Y" or "N" to resp. allow or not the window-menu invoked by right-clicking on the page - again this can avoid wrong use of the 'BACK' button as this going back should preferably be performed through ABCD-interface buttons, not the ones of the browser who has no control on certain necessary ABCD- navigation issues.  
  
  
By clicking on the arrow ('GO') ![](https://lh3.googleusercontent.com/IdcZJXwvLz7q9ffvgfqwMqsIq0so55S4mLn1WHzi2nL4c10G1f5WyDfmAkc5N0lIv7Zl67Vz2bp-XXpziJaCWrPbVzzia4zPW1unNpQumXi8lDZ_9VfAQ882FfvT8YyAkkBF00U7=s0) the user will enter the main Central menu - adjusted to the profile granted. All options of this menu are discussed in the next sections of this manual. This includes the administration of users and linking them to a profile, since the users-database can be seen as just another ABCD-database for which general Database Management tools of ABCD are to be used.

## Using LDAP authentification
    
The use of an LDAP authentification server is a new feature in ABCD 2.0 . The acronym stands for "Lightweight Directory Access Protocol" and in practice for ABCD means that you can use a dedicated, mostly institution-wide server which holds records of all authorized users. E.g in a university a 'registration office' could manage such a centrally co-ordinated list of students, which the library system consults whenever a user wants to login. This means that no longer the library itself is responsible for the up-to-date keeping of this list. E.g. when a student would be 'expelled' from the university, no longer the library needs to know this immediately in order to prevent such user - often quite frustrated ! - to enter the library(-system) and abuse it. 

This LDAP functionality can be activated for the following ABCD-parts :
-   Central login for operators
-   Site : login for end-users in MySite
-   Secs-Web : login into the Serials Control module.
   
The logics of using LDAP in ABCD is as follows :

-   in config.php the parameter is switched ON or OFF (actually : true or false), so the use of LDAP is completely optional;
 -   whenever an operator (librarian) wants to log in into ABCD Central, or an end-user wants to log in into the 'MySite' module, the login-data entered are first checked against the LDAP-server; if that one responds 'clear' the login is granted, if not the login is rejected;
-   if the LDAP-server does not know the login (which is different from 'rejects the login'), the login is subsequently checked against the local login-database ('acces' for operators, 'users' for patrons);
    
A pre-requirement for LDAP to work in ABCD is to have the extra PHP-library installed for LDAP : sudo apt-get install php7.0-ldap [substitute 7.0 by '5' if using PHP 5.x] and restart your Apache with a command like in Linux : 
```
sudo service apache2 restart
```

Other newly required files (as compared to versions pre-ABCD2.0) are :

-   the ldap.php script to be copied into htdocs/central/common directory
-   a dedicated IsisScript 'loginLDAP.xis' to be copied into the directory htdocs/central/dataentry/wxis
-   new versions of inicio.php and inicio_mysite.php (done already by default in ABCD 2.0) with the following changes :
-   at the beginning (e.g. after the line require_once ("../config.php"); ) add a new line with the following in- struction : require_once ("ldap.php");
-   at the end of the script change the part 'VerificarUsuario();' as follows, so as to use the new authentification if LDAP is used and the old one if not :
```
if (isset($arrHttp["login"])){
	 global $use_ldap; 
 if($use_ldap) VerificarUsuarioLDAP(); 
	 else 
 VerificarUsuario();  
```
  

-   three new functions added : VerificarUsuarioLDAP(),LeerRegistroLDAP(),LoginNLDAP(), and Ses- sion($llave).
-   a new CSS-element defined in the CSS htdocs/central/css/layout.css at the very end before the closing '}': .dl- horizontal { float: left; width: 45px; overflow: hidden; clear: left; text-align: left; text-overflow: ellipsis; white- space: nowrap; border-radius:150px; display: block; margin: 0 auto; margin-left: -50px;
-   for the ABCD Loans module : a new version of the script htdocs/central/circulation/usuario_prestamos_presen- tar.php with
-   in the initial 'include' statements section, include ../common/ldap.php
-   on line 627 added code : 
```
if($use_ldap){ 
	if(!Exist($arrHttp["usuario "])) { 
	ProduceOutput("<h4>".$ms- gstr["ldapExi"]."</h4>",""); 
die; 
	} 
}
```
-   for reference purpose we also note the additional changes for the Secs-Web module if LDAP is to be used :
-   in htdocs\secs-web\index.php add : require_once(BVS_DIR. "/htdocs/central/config.php") after re- quire_once("./common/ini/config.ini.php"); so as to check whether or not to use LDAP in Secs-Web
-   new version of class htdocs\secs-web\common\class\session.class.php : a new function $misession->check- LoginLDAP()is implemented which will be used if LDAP is found to be active in config.php (previous lis- titem), instead of the default $misession->checkLogin() function.
-   in htdocs\secs-web\common\class\session.class.php the SessionManager has added instructions at the very beginning to include the LDAP script and note its ON/OFF setting :
```
require_once(BVS_DIR. "/htdocs/central/common/ldap.php"); 
require_once(BVS_DIR. "/htdocs/central/config.php");
```

The LDAP configuration is to be defined as follows in CONFIG.PHP of the Central directory :

-   $use_ldap : true or false, sets or unsets the use of LDAP;
-   $ldap_host : the name or server-IP of the LDAP-server;
-   $ldap_dn : the LDAP domain data in comma-delimited format;
-   $ldap_search_context : additional data used by the LDAP-server to specify the use-context;
-   $ldap_port : the port used by the LDAP-server;
-   $ldap_pass : the password needed to access the LDAP-server;

In practice you will get all these standard-data from the LDAP-server manager.
An example configuration in the ABCD-Central config.php script for a free test-LDAP server is given below :
```
$use_ldap=false;
$ldap_host = "ldap://zflexldap.com";
$ldap_dn = "cn=ro_admin,ou=sysadmins,dc=zflexsoftware,dc=com";
$ldap_search_context = "ou=guests,dc=zflexsoftware,dc=com";
$ldap_port = "389";
$ldap_pass = "zflexpass";  
```

This example configuration is taken from a free LDAP server which can also be used for testing, see the URL : [http://www.zflexldapadministrator.com](http://www.zflexldapadministrator.com/) . Sample users available are 'guest1' (password : guest1password), guest2 (password : guest2password) and guest3 (password : guest3password).

Please note that for your own ABCD LDAP you will probably work with the administrator in your organization or institution to define the correct configuration and do the testing.