---
title: The ABCD OAI interface
description: This section will present the ABCD OAI interface, which is an implementation of BIREME's 'ISIS-OAI- PROVIDER', a general tool for providing access to ISIS databases through the OAI-PMH protocol.
lang: en
lang-ref: abcd-oai
---


# The ABCD OAI interface

{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---


   
This section will present the ABCD OAI interface, which is an implementation of BIREME's 'ISIS-OAI- PROVIDER', a general tool for providing access to ISIS databases through the OAI-PMH protocol.

  

## Short introduction to the OAI-PMH concept.

OAI, or 'Open Archive Initiative' is a world-wide initiative in the information communities to avail information in an open, free way.

For more informaiton on this organisation, the 'Openarchives.org', see [http://www.openarchives.org.](http://www.openarchives.org/)

The Open Archives Initiative develops and promotes interoperability standards that aim to facilitate the efficient dissemination of content. OAI has its roots in the open access and institutional repository movements.

The three current main areas of activity are :
1.  OAI-PMH : OAI Protocol for Metadata Harvesting : a protocol to allow retrieving metadata on electronic documents with an open standard, meaning one does not need to use the software with which the metadata were/are managed.
2.  ResourceSync Framework Specification : a protocol to make it possible for servers to synchronize their refer- ences to resources which might move or migratie on the WWW so as to always remain updated (pointing to the correct URL)
3.  Open Archives Initiative Object Exchange and Reuse : a mechanism to allow 'rich information documents' (with images, movies etc.) to be presented as one 'aggregated resource' independent from the individual locations of the components. E.g. social media The intent is to develop standards that generalize across all web-based information including the increasing popular social networks of “web 2.0.  

In ABCD the first of these three features is implemented : the Protocol for Metadata Harvesting or OAI-PMH. The OAI-PMH is the main protocol developed and promoted by the OAI, and described as :

“The Open Archives Initiative Protocol for Metadata Harvesting (OAI-PMH) is a low-barrier mechanism for repository interoperability. Data Providers are repositories that expose structured metadata via OAI-PMH. Service Providers then make OAI-PMH service requests to harvest that metadata. OAI-PMH is a set of six verbs or services that are invoked within HTTP. ”

The idea is to provide access to 'open' meta-data based information in as much a 'generic' and open way as possible, meaning that any need of specific software should be avoided. For this reason the protocol agreed on 6 'verrbs' or commands which allow to identify properly the source of the information and retrieval of basic meta-data information of documents available, often in a 'repository', either in a list of document-identifiers or, based on one such identifier, a specific document. In order to facilitate easier update of repositories taking their info from other repositories, selections can be limited by dates.

## Implementation and configuration in ABCD
    

The implementation in ABCD is fully based on the tool 'ISIS-OAI-PROVIDER' produced by BIREME as part of their Virtual Health Library (see e.g. the website about this tool :[http://wiki.bireme.org/en/index.php/Isis-oai-](http://wiki.bireme.org/en/index.php/Isis-oai-) provider and for downloading the original software the GitHub repository : [:https://github.com/bireme/isis-oai-](http://wiki.bireme.org/en/index.php/Isis-oai-provider)  [provider .](http://wiki.bireme.org/en/index.php/Isis-oai-provider)

Since no ABCD or other ISIS-related software can be supposed to exist at the users' side, the mechanism is to provide a URL and present the interface as just a web-page which is freely accessible. Therefore no links from within ABCD (e.g. in 'Central' module) is provided but the URL should be entered directly in the browser's address bar (or referenced by a shortcut etc.). In the case of an ABCD 'localhost:9090' installation this URL would be : http://localhost:9090/isis-oai-provider/index.php.

The page opened by that URL should like like the following illustration:

![](https://lh5.googleusercontent.com/f1EYMwsBO1rReclD6jf-NCB0IKaarFg-mYaPDhikP964JQ4kTHP3YpEOte8zKnhgHuQKyhQ4e0qb980FJtvbN0OrkCxWfmnkyHJKYHBJxRFvCqpXCLB081DSmDvjIhhDGjPofXw=s0)

As can be seen, in the left part of the interface access is given to each of the 6 main 'verbs' or operators, with a short description of each verb after selection of one of them, while at the right part the user-interacion has two parts : the criteria defined by the user at the upper part and the XML-output (to be 'captured' with copy/paste, in some browsers from the 'frame source' if the full XML-code is needed) as the result of the harvesting action.  

We will first briefly discuss the configuration necessary to make this work for local ISIS-databases in ABCD and then discuss each of the 6 verbs with some illustration.

### Configuration of the interface

Configuring ABCD for the OAI-interface comprises two parts : a general configuration and a configuration file for all involved databases.

### The general configuration
    
The file 'oai-config.php' is located at the 'root' of the **isis-oai-provider** module in ABCD, which is stored, next to other modules like central, iah, secs-web and site, in the htdocs-folder of ABCD. A typical Windows file-manager view of this folder's content looks like this:

![](https://lh3.googleusercontent.com/7S58qqg99TZ3eMo4ikRuv8OWoNFdufxw6jigaiASdp-uX_yVx4XqTrUSCxaDAYry-oAP0z5WdnXU6KAf5iyMhtDcJY8ocLAuSx-7Lg7xDze5rLfbu_u9XhHil8_85lpCu-Kkl-E=s0)

So this module uses its own CSS stylesheets and images, allows for gizmo's to be applied and uses one JavaScript file with 'functions' called from the scripts. The most important sudirectories here are :

- **lib**: this directory contains the main PHP-scripts for the interface, partly taken - inherited - from the general PHP- OAI libraries (e.g. OAIServer.php) and partly dedicated PHP-scripts to deal with resp. ISIS-databases (ISISD- b.php) or one (ISISItem.php) or more (ISISItemFactory.php) ISIS records. The configuration parser-scripts are also here for resp. parsing the ABCD-OAI configuration or the 'mapping' of the database fields to the Dublin- Core standard.
  
- **map**: this directory contains at least one file for each database involved, i.e. following either one of the two allowed syntaxes : OAI_DC (files with the name of the database followed by the .i2x extension) or ISIS (more traditional ISIS PFT formats with th eextension .pft). This mapping will be discussed in more detail below.
  
- **wxis**: some ISIS-Scripts used by the main executable wxis (web-enabled ISIS). getidientifiers.xis, getrecord.xis and gettotal.xis. These are rather 'normal' ISISScript instructions, taking variables form the CGI-environment and then specifying the instructions to operate on the variables, e.g. printing the titles in a loop etc.
  
- In the main isis-oai-provider directory itself we find the opening PHP-script index.php (which contains the interface) and the sample and real configuration files as PHP-scripts.

For the configuration of the ABCD-OAI interface we need to consider two files : one for the general configuration, one for the databases.

A sample listing, as it comes with the demo implementation, is given here, where lines starting with ';' are comments, e.g. to illustrate the Windows-alternatives:

```
[ENVIRONMENT]  
; Set the directory of application. The effect will be [http://your-site.org/DIRECTORY](http://your-site.org/DIRECTORY)

DIRECTORY=/isis-oai-provider 
;Full path to folder 'site' in folder bases. Windows users must NOT put letter unit in path
DATABASE_PATH=/var/opt/ABCD/bases/;
DATABASE_PATH=/ABCD/www/bases/ EXE_EXTENSION=;
EXE_EXTENSION=.exe

;Set the directory configured to execute cgi-bin applications.

CGI-BIN_DIRECTORY=/cgi-bin/ 

;[INFORMATION] 
;Set the repository's name. 
NAME=ABCD

; Set the email of the system admin [EMAIL=egbert.desmet@uantwerpen.be](mailto:EMAIL%3Degbert.desmet@uantwerpen.be) 
IDPREFIX=be

IDDOMAIN=netcat 
EARLIESTDATESTAMP=2011-01-01 
MAX_ITEMS_PER_PASS=20
```

In the [ENVIRONMENT] section the following variables need to be defined :

- DIRECTORY : the folder of the module, starting from the 'ABCD DocumentRoot' (as defined in the webserver, e.g. Apache), so in the default case of ABCD in Linux where the document-root is defined as '/opt/ABCD/www/ htdocs', defineing the DIRECTOY as 'isis-oai-provider' means that the OAI-module is located in /opt/ABCD/ www/htdocs/isis-oai-provider.
- DATABASE_PATH : the directory where the databases are to be found
- EXE_EXTENSION : the extension to be added to the 'wxis' executable name, in Windows : '.exe', in Linux no extension is used.
- CGI-BIN_DIRECTORY : the directory as it should be recognized in the URL In the case of Apache the Apache- configuration explains which real directory corresponds with the URL-string '/cgi-bin/'.

In the [INFORMATION] section we define:  

- NAME : the name of your repository as you want it to be seen by the user
- EMAIL : the e-mail address of the administrator who can be contacted about the repository
- IDPREFIX and IDDOMAIN : together they identify the 'domain' of the server
- EARLIESTDATESTAMP : the starting data of the repository, i.e. the date of the oldest documents, in the format YYYY-MM-DD.
- MAX_ITEMS_PER_PASS : the number of records to be listed in the ListIdentifers or ListRecords verbs. At the end of the list a 'resumption'-code will be given which can be used to define the start of the next batch. Default here is 20 items.  
    
### The databases configuration

One or more databases can be used in the OAI-interface, where they are referred to, in the OAI-vocabulary, as 'sets'. The sample implementation in ABCD uses 2 such sets : MARC (a marc21 catalog) and DUBCORE. (a repository with papers, but this is just a sample full-text database which the ABCD-administrator has to implement !)..

#### The database definition :
Each database needs to be defined, but also will need at least one 'mapping' file which we will discuss after- wards. The parameters to be defined for each are rather self-explanatory, like name, description, path (to the data- base-files), database (the actual file.name to which '.mst' will be added to define the ISIS MST file), while some other parameters can be briefly explained additionally :

-   mapping : the file where the 'mapping' (the ISIS-fields corresponding with the related DublinCore elements) are described in either a very simple 'DC' format (.i2x) or a more sophisticated format based on the ISIS Formatting Language (.pft), see further;
-   idprefix : the string to be prefixed (added 'before') the actual identifier when listing the record-identifiers; this additional string is optional;
-   cisis_version : this is the identifer of the specific CISIS-version which is used (as from ABCD2.0 different CISIS-versions can be used, e.g. BIGISIS or UTF8/FFI etc. The version specified here should reflect the (sub-)directory structure naming into the 'cgi-bin' directory where the correct 'wxis' (or in Windows : wxis.exe) is located to deal with the database concenred. This can be different for any database defined.


> Note:
> We changed the original BIREME-name of the variable
> 'isis_key_length' (e.g. 1030, 1660...), but indeed in ABCD the CISIS
> version is to be referred to here. This is one real difference with
> the original default BIREME-tool.

  

-   identifier-field : the tag (number) of the ISIS-field which contains the identifier of the record;
-   date-stamp-field : the tag (number) of the ISIS-field which contains the datestamp of the record.

We use the earlier mentioned 2 databases or 'sets' to illustrate the configuration of a database (in this case for Linux) :

    [marc] name=marc

    description="MARC" 
    path=/var/opt/ABCD/bases/marc/data database=/var/opt/ABCD/bases/marc/data/marc 
    mapping=marc.i2x
    
    prefix=oai_date_ cisis_version=ansi 
    ; identifier_field=1 
    datestamp_field=980 [dubcore] 
    name=dubcore  

  

    description="DublinCore repository"
    path=/var/opt/ABCD/bases/dubcore/data
    database=/var/opt/ABCD/bases/dubcore/data/dubcore
    mapping=dubcore.i2x
    
    prefix=oai_date_ 
    cisis_version=utf8/bigisis ; dentifier_field=111
    datestamp_field=507

The database 'mapping' explains how the ISIS-fields correspond with the DC or XML-elements. It is best to illustrate this based on the samples provided, starting with the very simple example 'marc.i2x' :

  

    root=oai-dc 245 dc:title
    500 dc:description
    650 dc:subject
    001 dc:identifier
    980 dc:date

First the 'root' string is defined as it will be used in the interface records-display. In the case of the oai-dc prefix used (see the 'usage' section below) just put 'oai-dc.

This 'root' is followed by a list of fields, one for each line, consisting of the ISIS-field-tag folllowed by the Dublin- Core element-name, e.g. the MARC21 title field 245 becomes : 245 dc-title. Note that this list can be a selection of fields to be shown. Non-defined fields here will just keep the field-tag as the XML-element, without translation to a proper DC-eleement.

When more powerful formatting is desired, e.g. on the level of subfields, the alternative more complicated syntax of an ISIS PFT can be used, then referring to a file with the .pft extension. Such PFT 'prints' the necessary XML- tags, i.e. the XML-leader info, as 'literals (unconditional quoted strings) :

```
<oai_dc:dc
xmlns:oai_dc="http://www.openarchives.org/OAI/2.0/oai_dc/"
xmlns:dc="http://purl.org/dc/elements/1.1/"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="http://www.openarchives.org/OAI/2.0/oai_dc/ http://www.openarchives.org/OAI/2.0/oai_dc.xsd">'/
```

followed by the individual ISIS-fields in the Formatting Language syntax used to add literals for the DC-XML output, in the case of e.g. the 'title' (v2 in Dubcore) :

```
if p(v2) then
(| <dc:title><![CDATA[|v2^*|]]></dc:title>|/), 
fi,
```

or, for the title and authors n MARC :
```
if p(v245) then
(| <dc:title><![CDATA[|v245^*|]]></dc:title>|/),
| <dc:title><![CDATA[|v246^*|]]></dc:title>|/,
fi,
```

```
if p(v100) or p(v110) then
(if p(v100) then
| <dc:creator><![CDATA[|v100^*|]]></dc:creator>|/,
else
| <dc:creator><![CDATA[|v110^*|]]></dc:creator>|/,
fi), fi
```
which should be read as : if the title is present then print the XML tags `<dc:title>` and `</dc:title>` with the actual value of v2 (any subfield, indicated by the `^*` operator, in between the [CDATA[...] attribute.
Any more complicated PFT-statements can be used, e.g. for displaying the document-format, if it is indicated in
`v9` :

```
' <dc:format>'select s(mpu,v9,mpl)
case 'A':'text',if p(v8^q) then '/'v8[1]^q fi,
case 'MATERIAL TEXTUAL':'text',
case 'G':'video',
case 'I':'audio',
elsecase if a(v9) then 'text',if p(v8^q) then '/'v8[1]^q fi, 
else 'other' fi
endsel,
'</dc:format>'/,
```
Any sequence of ISIS-fields can be treated this way, but fields not mentioned here will be omitted from the output.
Instead of fields also subfields or groups of fields can be used, using the power of the Formatting Language.
Best is to re-use an existing model, as provided with the demo-installation, for a new different local database, mostly adapting the field-tags to the local structure of the database. One has to be very careful, as always with the ISIS Formatting Language : missing a quote or any other syntax mistake will  produce no output at all but some error messages in the XML-output !

## Using the interface

When everything is properly configured - a lot of preliminary testing is advised, after all OAI means exposing your database to the whole world ! - the following outputs can be obtained, presented by each one of the six OAI- PHM 'verbs' :


> Note: 
> With most illustratoins under here, the XML-output is
> incomplete, in other words : the actual output contains more data but
> only part can be shown here.


> Note: The illustrations are generated with the Firefox browser,
> immediately showing the XML-output because no XML-style being
> available ('This XML file does not appear to have any style
> information associated with it. The document tree is shown below').
> Other browsers might show just the text-output, the full- XML still
> being available by right-clicking and requesting the 'frame-source'.

  

### Identify

This verb returns the main protocol information. Compulsory parameters verb (automatcially entered by electing this verb).

The output contains all necessary information as agreed per the protocol, e.g. the 'name' of the protocol as indicated in the oai-config script.  
 
### ListMetadataFormats

![](https://lh3.googleusercontent.com/6f0E2NSTeGar6fjrd1bcAQeZYQHtzva_3wkuqxdLr7cH2AhUhehTCmeMWIzT6qQ7OEzPjcntEt6jp7cLRcKMHKYJDQ79JxOzv30AMn0GnCjGKMre-M10TpimikTVIj9IU0bW0Ng=s0)
    
This verb describes the metadata formats used in the protocol. Compulsory parameters verb In ABCD we use two different formats : oai_dc and isis. which will correspond with the 'mapping' file defined, either i2x (for oai- dc) or pft for isis.  

### ListSets

![](https://lh5.googleusercontent.com/noGNA6WpWzDJxl6TocVjIGVOqHIvH6TE0Ro8xvhUJ2QUV7sVVafS3BxxjpJ7fXltzKKoXG3oItP1Gv9aOWsffrrTBOtkypv-P97sgRfWOjfuMxkwe9HBKzJbmRsyMIC126_ozTU=s0)
   
Retrieves a list of all databases available on this repository. Compulsory parameters verb Exclusive parameter resumptionToken

> Note:
> 'exclusive parameter' means that this parameter is not allowed as
> it is incompatible with the idea of the verb itself. The interface
> will not allow to put an exclusive parameter.

In case of our 2 demo-databases here (marc and dubcore) the output will look somethng like :  
  
### ListIdentifiers

![](https://lh3.googleusercontent.com/wQz-eoTP6LfgmBsBfS5LOkwIYxbc9B5v5qbgeF_ELnZ8MYvXG5OVBFAVVgbhVV49Fw2POb-tmj9lnHKkRgJOAMk19X7Nx9MQSYIIdbbguixg_GHD8H543cwSkX1qj7CQgadwdo8=s0)
    
This verb retrieves a list with the single identifier of each document published. Compulsory parameters verb metadataPrefix Optional parameters from until set Exclusive parameter resumptionToken retrieves a list with the single identifier of each document published. Compulsory parameters verb metadataPrefix Optional parameters from until set Exclusive parameter resumptionToken.

Depending on the field given in the database configuration as containing the identifier of the record, the records will be listed with that field :  

![](https://lh6.googleusercontent.com/91zcJCxAgaa4bosa0f86nu4spU7pi8-u4yEWuEsrfWeC1NO64TgeBCvxpA4gAQC19JG0HrgGupXIq87AKwIUiZkrH-D1-ujis6oPuwNcHF7KdtJGJt52JgnA3sIpN5kh63Vp0hE=s0)

We are showing here the end of the output, because an interesting feature is visible there : the 'resumptionToken can be copied from there, to be filled in into the corresponding form-element in order to resume further listing with the given one as the first, so allowing subsequent batches to be retrieved (or 'harvested' in the IOAI-vocabulary).  

![](https://lh5.googleusercontent.com/C25Nq5y3MGwZVEA7wDJM1EbuiH8fYY4M3acSer7otCSUVTFUoeHTtFfbPoOaisLONg4GwPZbS6pesNUNg20QV4fDbDowQaxcpHtBlNT31Gdlg140RCVxsM1_XnOP81_1hZ1w5Jw=s0)

### ListRecords

This verb retrieves the list of documents. Compulsory parameters verb metadataPrefix Optional parameters from until set Exclusive parameter resumptionToken .  

![](https://lh5.googleusercontent.com/C25Nq5y3MGwZVEA7wDJM1EbuiH8fYY4M3acSer7otCSUVTFUoeHTtFfbPoOaisLONg4GwPZbS6pesNUNg20QV4fDbDowQaxcpHtBlNT31Gdlg140RCVxsM1_XnOP81_1hZ1w5Jw=s0)

As with 'ListIdentifiers' a resumptionToken can be used to continue listing more records starting from the last one shown before. Note that also 'from' and 'until' dates can be entered to limit the records listed to a given span of time.

### ListRecord

Finally, the last 'verb' is to retrieve the metadata of a specific record. Compulsory parameters verb metadataPrefix identifier. Shown here is one record form the dubcore demo-database, using the dubcore_dc.pft 'mapping file' which is also part of the demo.  

![](https://lh4.googleusercontent.com/14ZvlkoFGdbxtE8y1RxxOiA56KtM-91sVobilKzRbgSZ3eTm48vaS4FULlZRia7wxqYL1UekDhU7bkbJADaiHhEsJchq1pl--3lzBp7lQyb_DX-VQW_E5jP7C-CvLqdwMJ7SW_0=s0)
