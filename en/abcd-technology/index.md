---
title: ABCD technology
description: This topic talks about the technologies used to develop ABCD.
lang: en
lang-ref: abcd-technology
---

# ABCD technology

{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## ISIS databases

ISIS databases are files in which information is contained in sequentially numbered records (MFN's or Master File Numbers) with values (mostly textual) stored in fields with a 'tag' (or numerical identifier) and subfields (with a one-character identifier). Subfields, fields and records all are variable-length and 'variable occurrence' varying from 0 (not present) to any higher number of occurrences, with a maximum depending on the ISIS-technology used but in the newest generation (in J-ISIS or Alpha-ISIS) without limit.

Records are structurally described in a 'header' for each record itself, instead of the usual table-header in relational databases. By doing so ISIS reflects more the concept of each record being a 'document' in its own right with its own document structure, like e.g. books, articles or web-pages indeed. Therefore we prefer to call ISIS a 'documentary database' in which documents are stored as a record with variable structure and length. This avoids complicated structures of 'normalized' relational structures, which are very efficient in storing highly structured data but less so for semi-structured textual data.

This means that the records themselves can be quite polymorph, meaning structurally different with any combi- nations of fields. In principle ISIS can handle bibliographic records along with user-data and transactional data (e.g. loans) in one single database, but because of 'semi-relational' capabilities (fast retrieval of any part of a record in any ISIS-database at run-time, i.e. by the Formatting Language creating the output without the need for these 'relations' to be pre-defined) typically ISIS-applications will use some few databases, e.g. in ABCD only 3 or 4 databases (one for bibliographic entities, one for users, one for transactions and possibly one for items) can allow to run a full library.

In the 'classic' ISIS technology 1all variable-length records (with (sub-)fields containing the values) are stored in a 'Master' file (.MST) and record-positions are kept track of in the 'Cross-Reference' (.XRF) file, which can be seen as a 'first-order' normal index on the records in the database. New or even just edited records are always appended at the end of the Master file and references in the XRF are updated accordingly, necessitating some 'compacting' at times to get rid of deleted and/or inactive (versions of) records.2 All values specified by a 'Field Selection Table' (which uses the Formatting language, therefore allowing very flexible and powerful definition of selected elements), are included into a B-tree 'Inverted File', which can be seen as a 'dictionary' of terms with the exact 'address' (record, fieldtag, occurrence, position within occurrence) attached to them. This allows very efficient retrieval, including full-text based, of any element defined as being 'retrievable'. ISIS was one of the first databases to offer full-text, which became only popular decades later. This 'Inverted File' (or IF) has several components (with nodes .N01/.N02 and leaves .L01/L02 files) for efficient organization - because in certain applications with intensive indexing the IF can be even larger than the database file itself ! So typically ISIS-databases exist of some 10 files : a MST with XRF, the B-Tree Inverted File files and some definition tables for the fields, the data-entry form and the indexation. Due to the memory types used in the 'XRF'-file, which is a fixed-format table acting as a list of all MFNs with their ID and location into the MST, the maximum number of records which can be hold in one ISIS-database is slightly over 16 million. On the other hand within this limit the software performs remarkably well without almost any noticeable performance loss at higher numbers. All this is changing with the new database technologies introduced in 2009 with e.g. J-ISIS : Berkeley DB uses a different storage in separate files with the definitions incorporated into the main data-files. But basically the concept of 'tag-value' pairs (an identifier and a content), on which a powerful Formatting Language and fieldbased plus full-text indexing is applied, remain the core of ISIS-databases.

## CISIS - Utility Programs 

CISIS - Utility Programs is a set of software developed by BIREME to handle ISIS databases from the Command Line in UNIX/Linux or DOS/Windows. This sofware has been written in the C-programming language and hence the name of this ISIS family member. CISIS mainly exists of a series of 'utilities', i.e. command-driven executables which perform all types of functions in ISIS-databases, like creating records, updating and searching them, updating the Inverted File, import and export and many other functions, sometimes unique in the 'ISIS Family', e.g. joining records from different databases according to common keys, indexing and searching from different Inverted Files for one database.

Actually CISIS as a set of utilities contains more than 25 different tools or executables. 

To know all the tools, go to the C[ISIS - Utility Programs page](/en/abcd-technology/cisis-utils/)


### The Master / Xross-reference tool : mx

The mx tool is the main CISIS utility, it could easily be baptised as 'CDS/ISIS for the command line', meaning most things which can be done with (M)asterfiles and (X)rf-files - therefore 'mx' indeed - with ISIS can also be done with MX. Just to give an idea we give the list of parameters mx accepts (as this list is given when invoking the command in a command-line environment such as the CMD-window in Windows or a terminal-window in UNIX/Linux. As one will see, too many parameters are available, meaning mx is an enormously powerful tool for ISIS-database management, but it deserves a manual and training in its own right !

**![](https://lh5.googleusercontent.com/Onej8W2i6TGtd-ETfna8h0s3fvwzcspGkYwtHX-srEdQpo_Yadp41zI0Spis6Z31o5i3aYGo-PIu1qfmJ6L4RiuvPbElZA7L_TrRxEVcJ-PIu86gVhzvuB4nO1tYmfZPXjBJPgda=s0)**

A glance at the many parameters show that mx can not only search ISIS-databases (bool=) but apply on-the-fly GIZMO (string-substitutions) and ANSI-conversion (ansi=), join fields of records from different databases but identified by their IF-entry (join= and jchk=), apply data-entry processes (proc=) and inverted file operations.

  As CISIS comes in several varieties, according to the capacity of the databases and Inverted File keys intended, we need to specify that for ABCD we will only use the '16/60' variety of mx and other CISIS-tools. This can be verified from the information mx gives when invoked without any parameter as illustrated :![](https://lh5.googleusercontent.com/0AvWw9FZmlv63nUjXS52-vb1P-FNLTMuWm-4EB871bhv3jZNiOvjwgon4BIQX9v1RrnesyPoOCkXFlZgGZ69PnZCk3ofRODNGhXwOInlggaXOPaFPjdGM1djTe667ByL008WRiaL=s0)


The most relevant uses of mx in this context of ABCD are :
- import of ISO-records into an ISIS-database, e.g. the command : 

```
mx iso=myISOrecords.iso create=mydb now -all tell=100
```
    
will read the file myISOrecords.iso and create an ISIS database 'mydb' without waiting for any user-input ('now'ait) and without showing any information on the screen (-all) but showing progress after every 100 records imported.

  
> Note :
> In ABCD we use this to import a larger quantity of ISO-records
> into a database, as a high number and therefore long processing time
> would invoke the time-out of the web-server to stop the process.

  

- index an ISIS-database, e.g. the command :
 ```
mx mydb ifupd/create=mydb fst=@mydb.fst stw=@mydb.stw now -all
```
will create an 'Inverted File' named 'mydb' using the mydb database with the indexing specifications given in the FST 'mydb.fst' and omitting the stopwords listed in mydb.stw, again without interactive mode or output (now -all).


> Note:
> In ABCD we use this to create an index off-line in case - as is
> often the case - the database is r


### Inverted File tools : mz, ifupd, ifkeys, ifload, ifmerge
  
These are more specialized tools to generate/update the ISIS Inverted File with its B-Tree technology and parts (leaves and nodes) from the command line with some more optimized speed and more options. E.g. MFN-ranges can be defined, keys can be taken from the previously created LK (link) files (ifload) or nodes-files (ifmerge) of the B-Tree, which can be balanced etc.

We don't normally need to use this with ABCD, but knowing the possibilities exist, especially in the case of very large databases, is certainly useful.

### other CISIS-tools

Other tools to be briefly mentioned only are e.g. :

1.  retag : this tool will change the tags of the fields according to a given specification - which can have instructions on many fields in one run
2.  mfcrunch and ifcrunch : to convert the ISIS-files (resp. MST and the IF-files) from DOS/Windows to Unix and v.v.
3.  mkxrf : to re-create the XRF-file for a given database, in case this is lost or got corrupted - the tool will analyze the MST-file and assign XRF-records into the XRF.
4.  ctlmfn : to edit the values of the 'control-record' of the database, in which the maxMFN and other very technical values for the database are stored - for experts only !

## ISIS Formatting Language

The ISIS Formatting Language (FL) is one of the most important parts of the software because it gives ISIS- managers the possibility to exactly define what ISIS will produce out of the databases at many stages of the software, e.g.

-   what ISIS will show on the screen, i.e. 'present (defined in the Print Format Table or PFT)
-   what ISIS will use for the creation of indexing keys (defined in the 3rd column of the Field Select Table or FST)
-   what ISIS will use for sorting the records
-   what ISIS will use as exported values (defined in the reformatting FST)
-   what ISIS will use as values to validate input in fields (given in the validation tables).

### The FL for presenting values

This is by far the most important function of the Formatting Language : specifying which data exactly need to be taken and how they will be 'displayed' or 'printed' (to the screen, to a printer, to a file, to a webpage...).

Separate documents exist to deal with this extensive language, e.g. the dedicated chapter in the ISIS Reference Manual, published by UNESCO (June 2004, chapter 8, p. 94-122).

Basically there are three types of statements in the ISIS FL :
1.  values from fields, given as : Vx, where 'V' denotes the value (or 'contents') of a field with tag 'x', Vx^a is the value of the subfield a (^a) of field x and (Vx/) is the series of all occurrences of field X separated by a 'new-line' (/) since the parenthese embrace a 'repeatable group' of statements to be applied to all occurrences (repeatable fields are a strong special feature of ISIS).

2.  literals or quotes strings, which can be 'unconditional' (single quotes), |conditional| (pipes indicate the string will only be produced if the related field is present) and "repeatable" (double quotes will only produce the string at the first occurrence of a repeatable field).
ISIS-applications on the web, such as ABCD, create web-pages with HTML-tags using this method of adding literals to field-values, e.g.

```
'<table><tr><td>' Vx '</td><td>' Vy '</td></tr></Table>'
```

will display resp. the fields x and y in two columns of a table in HTML. Note that all HTML- codes are quoted (as unconditionals) and the values taken from the fields in the database are inserted by referring to them with the V-statement.

5. commands, which can be of different types, e.g. :

-   mode commands : mhl/u (mode heading lowercase/uppercase), mdl (mode data upper/lowercase) or mpl/u (mode proofreading upper/lowercase)

-   (in Windows-environments) : commands defining screen attributes (colors, fonts, boxes) or links (requesting the operating system to open other data, e.g. multimedia data referred to in a record), e.g.

LINK('click here for tull-text', OPENFILE Vx) will request - when the user clicks on the hyperlinked text 'click here for full-text', Windows to open the file of which the name is in Vx, with the Windows-application associated to the extension of that file.
-   the REF-command, which can retrieve data from other records (in the same or another database when ex- pressly referenced to), allowing semi-relations setups in ISIS-applications (but with the advantage that the relation is followed only at run-time when requested). e.g.

```REF(['users']) L(['users']V2),V1)``` 

will retrieve the value from field 1 in the database 'users' if the L(ookup) function has found the value of field 2 (in the actual database) in the index of the users-database, so that the MFN of the record can be identified.

-   conditional routing statements : e.g. 

```'IF...THEN... (ELSE....)FI'```
or even the 

```SELECT [case1 case2...] ELSE- CASE... ENDSEL```

construct can be used to apply formatting statements only to database values which comply with given conditions.

-   in the CISIS-environment extra FL statements are available, the most important one being a command which will actually **PROC**ess a record to alter the contents of the fields. The general syntax is :
```
    proc(x|y...) 
```
where x or y can be any of the following : ```'Dxxx' ```(to delete field with tag xxx)
- ```|Axx#|value|#| ``` (to Add value into field xx)
-   functions, mostly for string-operations (e.g. substr, size, val) or numerical (e.g. rmin, rmax, rsum...)

Full documentation on the CISIS Formatting Language is available on [this page](/en/abcd-technology/cisis-formatting/)


### The FL for definition of indexing keys
  
The same formatting language, but of course without any appearance-related effects, can be used to exactly define which values should go into the Inverted File of ISIS. This will be defined in the third column of the 'Field Select Table' where the extraction format using the FL is to be used. See also the discussion of the FST definition in the chapter on database definition and management of this manual.

Since the full formatting language - except graphical elements - is available, the REF-function e.g. can be used to take into the Inverted File values different from the actual field contents, even from another database. This can
e.g. be used to substitute codes for their full explanation or v.v.

### The FL for definition of sorting keys
    
The same reasoning can be applied for the definition of keys which ISIS will use to sort records : again the actual sorting values can be processed values derived from the actual field values, by using the FL.


### The FL for conversion during import/export

During import/export of records, most ISIS-applications will allow the use of a 'reformatting' FST, which has in its third column the exact definition of what to export/import, and in the first column (the 'IDentifier') the tag to be assigned to this value.

### The FL for validation statements

The Formatting Language can also be used to create error messages in case defined conditions are (not) met. These conditions will be checked when passing data entered into a data-entry form into the record for storage. ABCD provides this technique by default as explained in the section on record validation. An example again can clarify this easily :
```
if a(Vx) then 'This field is mandatory, please check again !' fi
```

This statement will produce, on the screen, the message 'This field is mandatory, please check again' if the value of the field with tag x does not exist or is A(bsent).

More sophisticated statements can be used for more advanced quality/consistency checking, e.g. using a 'SELECT' construct, or even checking the value in another database (with the earlier discussed 'REF'-function) to see whether it is a valid entry.


## ISIS Script

ISIS Script is a scripting language developed by BIREME in order to make stronger functions available to the ISIS webserver 'WWWISIS' for creation of pages with elements from ISIS-databases. ISIS Script in fact was one of the main elements in the stepping-up from WWWISIS to 'WXIS' which is the underlying web-server for ABCD.

ISIS Script scripts are stored as files with an extention .XIS. ABCD uses more than 100 such scripts, most of them in the php/dataentry/wxis folder but also iAH (the OPAC) makes extensive use of such scripts.

Obviously we cannot discuss the whole power of the ISIS Script language here. As a longuage it uses XML-like statements, e.g. in between the tags ```<pft>``` and ```</pft>``` a print format can be given and this format can be displayed by putting it in between ```<display>``` and ```</display>``` tags. All WXIS parameters can be defined within the ```<parm>``` and ```</parm>``` tags and fields can be defined with values, e.g.
 
```
<field action="replace" tag="6000">ValueOfField6000</field>
```
will put the string 'ValueOfField6000' into the field with tag 6000 (such high-value tags, in fact all tags above 999, are mostly used within ISIS-applications for temporary internal values which are not really stored in ISIS- records but rather 'virtual records'.

ISIS Script allows more flexible manipulation of data-elements, taken from ISIS-databases, in web-pages. In com- bination with PHP (see the dedicated section on PHP), which is a language for creation of web-pages powerful results are possible and this certainly adds to the general advanced functionality of ABCD.

Of course more details on the ISIS Script language can be found in the dedicated documentation.

## J-ISIS

J-ISIS or J(ava)-ISIS is the current new technology in the ISIS-family, based on Java.

Longer ago a first attempt to create a java-based ISIS version was done by an Italian team. The result was a working solution to consult ISIS-databases remotely using java, although not very highly performant. This effort has stopped development after some years and is no longer maintained or available.

As from 2005 the UNESCO software-expert, mr. Jean-Claude Dauphin, mostly responsible for the IDAMS soft- ware maintained by UNESCO (for statistical management), started developing a fully new ISIS-version, no longer based on the until then unique 'MST/XRF' approach, but storing the data in a schemeless key-value database 'Berkeley DB' (see e.g. [http://www.oracle.com/technetwork/products/berkeleydb/overview/index-085366.html](http://www.oracle.com/technetwork/products/berkeleydb/overview/index-085366.html) ), available still as FOSS from Oracle. For the search-engine and indexing the proven technology of Lucene was used from the Apache Software Foundation.

The real ISIS-technology of the concepts of variable-length records, fields and subfields with the ISIS Formatting Language (PFT) used not only in the output-presentation but also in the Field Selection Table (to define the exact string to be taken into the index) is still present and actually makes J-ISIS still being ISIS. J-ISIS by the way is the first version which contains a PFT-parser for grammar-checks and assistance.

The use of Berkeley DB means that no longer any limits are imposed upon record lengths (in traditional ISIS up to 32Kb with an extension possibility in CISIS up to 1Mb) or database-sizes.

The use of Lucene indexing technology means that not only all previously indexing techniques remain available but also 'ranking' now is added, making J-ISIS more suitable for e.g. full-text applications. A 'digital library' demo-database, based on the concept of using the TIKA-library for text-extraction of document formats by simply loading a document into a text-field, is included with the distribution package of J-ISIS.

At least once a year a new update is made available, before through kenai.com, nowadays (as from April 2017) at the URL [https://github.com/J-ISIS/J-ISIS](https://github.com/J-ISIS/J-ISIS ).

The 'new generation' ABCD (version 3.x) will be based on J-ISIS and is currently being developed by a team at 'Universidad de Ciencias Informáticas' (UCI) in Havana, Cuba.

## PHP
    
PHP is a 'Hypertext Preprocessing' language, which means it is a programming language for web-pages. As one of the successful 'FOSS' products it is nowadays very popular and wide used, often in combination with Apache and MySQL databases. This has even lead to packages such as 'EasyPHP' and 'WAMP' (Windows, Apache, MySQL and PHP) which allow to install these often-combined softwares into one package.

As usual there are some criticisms on PHP as a language, but a fact is that it is very popular and getting more powerful with each release. ABCD uses e.g. also 'controls' or ready-available modules for specific functions, which are freely available.

ABCD 2.0 is compatible with the current versions of PHP, i.e. 5.x and 7.x. No longer - as in ABCD 1.x - the parameter 'short_open_tag' needs to be switched on, but a few non-standard 'extensions' need to be activated (in php.ini) : gd2, xsl, yaz, xmlrpc, and if the related functions are used : ldap, mysqli (for EmpWeb) and mbstring (for Unicode).

## JavaScript
    
The official name of JavaScript is 'ECMA Script' but JavaScript is the popular name of a technology which is nowadays used in many web-pages : relatively small programmes embedded into the HTML-codes of the pages. Contrary to the name the language is not really linked to the JAVA Programming Language. JavaScript nowadays is supported by all up-to-date web-browsers and does not need any extra software or configuration. However it remains to be an option which can also be switched off (in Firefox e.g. : **Tools -> Options -> Content**, where both JavaScript and Java can be disabled), so make sure that the JavaScript option is enabled for the use of ABCD.

ABCD uses JavaScript 'scripts' inside its pages in very many instances, one reason being that by doing so the local computer can process data without a need for high traffic in between the server and the client (which is important in slow connectivity conditions).

As an example of a simple JavaScript we can refer to the script 'lrtrim.js' (in the ABCD-folder `\ABCD\www\htdocs\php\dataentry\js\`) which is called upon from several ABCD-PHP pages. The script trims white-spaces at the right or at the left side from strings. This can be easily done locally, no need for sending the string to the server together with the request to trim it and then having it returned from the server. Therefore the script is loaded into an ABCD page and executed locally.
Also generally available JavaScript existing modules are being used, e.g. for the calendar function in the Loans module or for the 'HTML Editor' (FCKEditor.js). Under here the calendar example is shown, based on the JavaScript 'popcalendar.js' which can be found e.g. in the folder php/loans/js of the ABCD home-folder (/ABCD/ www/htdocs). 

This little tool displays any month of the calendar and allows marking the holidays to take them into account when calculating the loans period !

  
![](https://lh6.googleusercontent.com/Mnn3D39lRsOzRc4pYefnVMSjV8Xg7d6yAIuKN7cqWRUR2GAhG8NKlE875jD7DJCnHTvewPZbYKkXASR5Er_YrKs6acSpIb9X-SU-IXgkgLF_RTOrHSi3Nel7C-OUGEBcZaDWJfyc=s0)  
  

Most JavaScript functions however are not visible on the screen, but perform useful functions within the web- pages of ABCD. So even if tools like the above mentioned (the HTML editor or the calendar) are considered unnecessary, still it is important to keep the option to run JavaScript within your browser 'on'. As with Java, this option e.g in Firefox can be checked in the `Tools|Options|Content` tab (in Internet Explorer one has to activate 'Enable for Active Scripting' in the Scripting section of the security zone 'Internet' under `Tools|Options|security`).

## JAVA, Groovy and Jetty
    
JAVA is at the same time a programming language (like e.g. 'C++') and a 'runtime compiler', which means that programs written in JAVA need a 'RunTime Environment' (RTE) version of JAVA which will compile the program for the given Operating System and CPU combination at run-time (i.e. when the user executes the program). By doing so the JAVA programs are completely 'multi-platform' (Windows, UNIX, Linux, OS/X...) because such RTE's exist for all platforms and are freely available for installation. So make sure your computer has its own JAVA RTE installed ! Both Sun (the real Java promoter) and Microsoft offer free versions of Java (e.g. at http:// java.com/en/download). JAVA is not only free but also 'Open Source' and therefore can be reported as being fully 'FOSS', as is ABCD.

ABCD uses JAVA only for the 'advanced' loans module, which comes as an extra option (see the chapter on the Circulation module). This advanced circulation management module is intended only for larger institutions with more complex circulation rules and multiple branches with their own loans policies or with user-databases in other formats (e.g. SQL). Also more interactive 'MyLibrary' -style functions can be offered. In order to allow such more complicated software-combinations, ABCD calls upon JAVA to provide web-services and links with other database-models.

Groovy is an object-oriented programming language for the Java Platform which can be used as a scripting lan- guage for the Java Platform.

The advanced ABCD Loans module (EmpWeb) also uses Jetty-technology, which is aHTTP Server and Servlet container written in Java.

Jetty can be used as:
-   a stand-alone traditional web server for static and dynamic content
-   a dynamic content server behind a dedicated HTTP server such as Apache using mod_proxy
- an embedded component within a java application


## MySQL

MySQL is a relational database developed as FOSS but with a 'dual license' scheme, allowing both commercial and free applications. Currently MySQL has been taken over by Sun Microsystems, a strong defender of FOSS software, e.g. JAVA. Recently Sun Microsystems has been taken over by Oracle, so the future is not so clear.

As a database MySQL has become incredibly popular because of its ease of use and combined packing with e.g. Apache and PHP for easy deployment of database-driven websites.

Examples of such pre-packaged combinations of Apache/PHP with MySQL are : EasyPHP (http://www.easyphp.org) and WAMP for Windows or XAMP for Linux (http://www.wampserver.com). Both are Open Source and free to use (GPL license).

Critics claim its 'relational' qualities are still lagging behind - even if improved a lot since the earlier days - as compared to e.g. PosGreSQL or of course the major relational databases like Oracle or IBM DBII. Some other library automation packages are completely using MySQL for the databases, the best known being KOHA (albeit that KOHA currently envisages adding/changing to another type of database, i.e. 'Zebra', exactly to avoid limita- tions of MySQL for library purposes.

The 'SQL' part of the name means 'Standard Query Language', denoting a standard grammar for retrieving data out of relations (related tables), heavily relying however on its relational structure. For this reason e.g. ISIS is not using SQL as it does not store its data into tables with fixed cells and structures.

MySQL will only be used in ABCD within the 'Advanced Loans' module, which is a non-standard extra (see the chapter on the loans module in this manual). There it will be used to store the transactions of the loans system, as these are administrative data which can be more efficiently handled by this type of database as compared to ISIS with all its - in this case unnecessary - flexibility and text-oriented features.


## YAZ

YAZ is a freely available software for embedding the Z39.50 protocol in applications. Z39.50 is used as a protocol to retrieve data from other catalogues, mostly in MARC-format. ABCD uses YAZ for its 'Z39.50' function in the cataloging module.


## Apache
    

Apache is the name of the webserver software very frequently used in 'open source' webservers. In fact we are talking about a software called 'HTTPD', which is only one product of the powerful 'Apache Software Foundation', which also provides other interesting products such as e.g. Lucene indexing (also going to be used in the next releases of ABCD), TomCat (a Java Servlet and Server Pages server) and the Derby DB.

Apache as a webserver seems to be the most widely used in the actual Internet, which is one of the (few) examples where FOSS dominates over the commercial solutions offered. All information on the Apache web-server and download files can be found at the URL : [http://www.apache.org.](http://www.apache.org/)

In many cases the Apache webserver software will already be installed on the server where ABCD will reside, as is probably also the case with PHP (and MySQL). For this reason ABCD came as a package both inclusive of Apache and PHP and another one without these, but in ABCD v2.0 only the non-inclusive package is available, leaving the Apache and PHP installation apart - good installers like WAMP and XAMP exist anyway also as FOSS. In the case of an existing Apache webserver, expertise on Apache should be available in order to integrate ABCD with the existing Apache-based applications. E.g. a virtual server for ABCD could be set up with 'aliases' specifically for the ABCD system (htdocs home) and cgi (scripts folder). In the case of the full package, as it came for ABCD 1.x, the latest 'stable' Apache httpd-version was included, pre-configured to work with ABCD as 'localhost' (which means : the PC itself runs both the client and the server). A small script launched the httpd (or Apache) service based on that configuration, so that installation and configuration efforts in principle could be kept to a strict minimum. Since nowadays too many different versions (32/64 bits, thread-safe or non-safe, MS VC10,12,14...) exist we think it is better to leave the installation of Apache and PHP to specialized packages such as the above mentioned WAMP and XAMP or, in the case of Linux, the 'server-versions' of the Linux-distributions which come with their own Apache and PHP pre-installed. In case of additional configuration still to be necessary, the user should be fully aware of the fact that Apache, as a Linux-based software, is case-sensitive for its parameters and file names (with path information) !

*In the case of webservers, we should mention 'IIS' (Internet Information Services) of Microsoft, free software but not open, which is the webserver coming with Windows. Differences are mostly in the way how it should/can be configured and managed, rather than performance, security etc... The terminology is a bit different (e.g. 'aliases' are called 'virtual folders' and there is no easily approachable ASCII-configuration file as with Apache and its 'httpd.conf'.
ABCD runs perfectly with IIS, as with other web-server software (e.g. Xitami), but this manual does not support the implementation on IIS. Dedicated manuals on configuring IIS for ABCD exist.*