---
title: O Serviço de Entrega de Documentos Online (ODDS)
description: Este serviço é adicionado na versão ABCD 2.0 para facilitar a organização de um serviço de entrega de documentos elec- tronic para documentos. A idéia é que os usuários finais, a partir do link no site do ABCD (agora parte do site de demonstração), tragam os dados bibliográficos que conhecem de uma forma como uma formulação de pedido. O formulário, quando submetido, torna-se um registro no banco de dados ODDS que é atendido por um funcionário especial da biblioteca - bibliotecários, tendo frequentemente melhor acesso e conhecimento sobre como localizar documentos eletrônicos, identificar os documentos, colocá-los em um servidor de biblioteca e enviar - semi-automatizado - um e-mail para o usuário final solicitante notificando-o sobre a URL do documento e o tempo necessário para baixá-lo.  
lang: pt
lang-ref: abcd-odds
---


# The Online Document Delivery Service (ODDS)

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---

 
This service is added in version ABCD 2.0 to facilitate the organisation of a document delivery service for elec- tronic documents. The idea is that end-users, from the link on the ABCD Site (now part of the demo Site), bring in the bibliographical data they know in a form as a request formulation. The form, when submitted, becomes a record in the ODDS database which is attended by a special library officer : librarians, having often better access and knowledge about how to locate electronic documents, identify the documents, put them on a library server and send out - semi-automated - an e-mail to the requesting end-user notifying her/him of the URL of the document and the time-span to download it.  

We discuss this process in this section but will have to start with some few configuration issues.

## Configuration of ODDS
    
The ODDS module is integrated into ABCD as from version 2.0, but can also be installed as an add-on in an existing ABCD-installation by unzipping the ODDS.zip archive and by doing so adding new files but also modifying existing files in your system. We explain these here.

### new files
    
The following files are newly installed into ABCD for the purpose of the ODDS-module :

-   the directory `htdocs/central/odds`, which contain the main scripts and files needed; 
-   `htdocs/central/css/estilo_odds.css` : a CSS style-sheet used in ODDS, needs to be available in the Central stylesheets directory
-   `/lang/odds.tab` and `bases/lang/odds_help_info.tab` : messages and help text to be copied into the related lan- guage-directory of your ABCD bases/lang directory.
-   /odds datase as a folder in your ABCD's database-directory; this is the database to store the requests. The database may have some test records which should be deleted ('initialize' database) before starting to use it locally
-   `/par/odds.par` file to be copied to the directory bases/par and edited if necessary to indicate the correct path to the ODDS database for your ABCD installation
    

### modified files  

The following files exist in ABCD but have new contents added on behalf of ODDS :

-   central/iah/ver_documento.php 
-   central/iah/configure.php
-   central/iah/ver_documento_ex.php
-   central/iah/view_document_ex-ODDS.php
-   central/iah/ver_documento_ex-WEBEX.php
-   Iah/scripts/`<lang>`/ahhead.pft
-   Iah/scripts/`<lang>`/ahfoot.pft
    
### Structure of the ODDS-directory

After installation of ODDS, the following structure will exist in your ABCD Central odds-directory :
![](https://lh3.googleusercontent.com/Jt9okORMtmdkBEX5bmdMaGLRQtL75i3L7o2xY4XEr0yW0EDI2WdhLKMmkQFc5kjj1o-6gziwJJSd_74o_OkIAwYAClsq7gIC-jRBTA-3mtrU93Hkt6qnI_E8Ty-tTyQKBUtmnmyS=s0)

in which the following files side :
-   Form_odds.php : the ODSS home-page which contains the code to display the main ODDS request-form.   
-   Process_odds.php : The data loaded in the form of the previous item are sent to this script for validation, pro- cessing and storage of the data in the ODDS database.  
    
-   index.php : test examples for invoking the form with parameters and without parameters. The directory odds/lib/ contains the following files :![](https://lh6.googleusercontent.com/iHidAcGoGJFSn-qtNaAILWIqownUxbcN3jbZ_L9GxShuRAFNgqB843JtrNZxX4alBUMzZUebQ_UK2R3Cm0TGxz7iEbsY1pOSt9hUHyr3_p8yakFgtHqF4YaXEMNjzxBrkQpjbGiB=s0)
    


where these files implement various functionalities, needed by the ODDS module, more specifically :

-   Blat.exe Binary used to send emails (from ABCD) to the Windows operating system.
-   Footer.php Foot of the pages included in the ODDS module.
-   Header.php Head of the pages included in the ODDS module.
-   Header-ODDS.php Head for the box in which user validation is requested (from iAH or Site).
-   Header-SA-ODDS.php Head for the frame in which user validation is requested (from Alert Service).
-   Library.php Set of functions used to load messaging dynamically. The text of the messages are read from files with an extension tab. For details please see below.
-   logo.jpg Logo sent in the head of institutional emails.
-   Odds_title_back.png Background image for the title of the form.
-   SendMaiLinuxl.php Implements the functionality of sending emails (from ABCD) to the Linux operating system.
-   SendMail.php Used to centralize the sending of emails (regardless of the operating system). Validate the data required to make the sending and upload the text templates for the subject and the body of the mail according to the email to be sent (satisfied or canceled order).
-   SendMail.php Implements the sending of emails from ABCD (via Ajax). Validate the data required to make the shipment and upload the texts according to the email to be sent (order satisfied or canceled).

In order to send mails, the ODDS module is provided with the getOutput function implemented in the JavaScript language and located in the central file /odds/js/lib.js To be able to send (using a call to Ajax built by the getOutput function) must be invoked using the following parameters) if not used send empty strings) :

    getOutput(email,email_proxy,date,name,status,uploadFiles,notes,title)

where :
-   Email: is the email of the recipient (can be sent to several separating the addresses of mails with a comma).
-   Email_proxy: if there is a proxy to which you want to send mail.
-   Date: date of application.
-   Name: name of the applicant.
    
-   Status: status of the request, used if the request corresponds to a satisfied request (2) or a cancellation (3).
    
-   UploadFiles: uploaded files separated by the pipe character.  
-   Notes: additional notes.
-   Title: title of the work being served
-   Show_controls.php : Implements the load of the controls dynamically according to the option chosen in the "Bibliographic Level" combo. In other words, it dynamically determines what data will be requested at the time of making the bibliographic request according to the type of bibliography chosen. To load the controls, this file is invoked via Ajax, thus avoiding reloading the page.
    

In the```base/odds/def/<lang>/odds_show_controls.tab``` file, the blocks of controls to be set corresponding to the option chosen in the "Bibliographic Level" combo box are configured. That is, each block of controls maps with a combo option "Bibliographic Level". For example, the control block started with "as" ("as" ignores serial analytics) is loaded when the "magazine article" entry is selected in the combo. This link between the value "as" and the entry of the "magazine article" combo is done in the file levelbiblio.tab (under bases ```/odds/def/<lang>/```).

In show_controls.php, each line in each of the blocks specifies which field to display and with what character- istics :
```
<tagXXX> | <label_to_show> | <input_type> | <length> | <validate_method_1 validate_method_2>
```
  

where :

-   ```<tagXXX>```: XXX is the field number defined in the FDT file
-   ```<label_to_show>```: Text to be displayed accompanying the input for data entry
-   ```<input_type>```: type of input for data input, for now we only have two possible values: text or textarea
-   ```<length>```: length of the input (only applies to input of type text)
-   ```<validate_methods>``` Methods that apply to validate the data field. The methods must be defined in ```htdocs/central/odds/js/JV.js```
    
The directory odds/js/ contains the following files as javaScript functions :

-   jquey.min.js General javaScript ibrary jquery
-   JV.js Validations and messages for all elements of the forms
    

This file provides a list of validation methods provided by ODDS. All validations can be used by simply in- cluding the name of the validation function in bases / odds / def / <lang> /odds_show_controls.tab. In case you want to add or modify validations, as well as the messages they deployed, you must modify this file.

-   Lib.js Auxiliary functions for sending emails and calling Ajax to sendMail.php
    
-   odds.js Validations and call to show_controls.php The directory htdocs/central/iah
    

The files listed below should be overwritten should they already exist. These files implement the functionality to request identification from the user. Configure.php

-   View_document.php
-   View_document_ex.php
-   View_document_ex-ODDS.php
-   View_document_ex-WEBEX.php  
    
Clarification The parameterization of this functionality has not yet been completed; Therefore, some code fragments must be modified to be able to use it. See below.

Text and configuratoin of ODDS summarized :  

Table 2.3. 
|FUNCTION|RELATED FILES|
|-|-|
|Text and subject of the e-mails that are sent for the no- tification of orders ODDS (accessible from the ABCD)|In bases/odds/def/```<lang>```/ : odds_success_mail_sin- gle_file.tab odds_success_mail_multiple_file.tab odd- s_cancel_mail.tab|
|Miscellaneous texts: Below the title, on the top bar Noti- fication text of success or failure of the order (after com- pleting the form), section REQUEST_MESSAGES La- bels of the fixed controls, that is, they do not vary ac- cording to the "Bibliographic Level" chosen (for exam- ple, ID, name, email, etc.)|bases/lang/```<lang>```/odds.tab|
|Configuration of optional controls (those made visible according to the option chosen in the combo "Level Bib- liographic")|bases/odds/def/```<lang>```/odds_show_controls.tab|
|Text of the help box, on the right, in the main form|bases/lang/```<lang>```/odds_help_info.tab|
|ABCD Text for ODDS Notification E-mail Buttons (Or- der Completed and Order Canceled)|bases/odds/pfts/```<lang>```/odds.pft|
|Options in combos (whether or not visible) "source" "Bibliographic level" "category"|bases/odds/def/```<lang>```/source.tab bases/odds/def/```<lang>```/nivelbiblio.tab bases/odds/def/```<lang>```/categoria.tab|

  

## The workflow of ODDS
    

The workflow or 'how to use' of ODDS in ABCD pertains to 2 parts : the request by the end-user and the processing by the 'information broker' or librarian. The idea is that an end-user creates a request to get an electronic document which is not already available and which cannot easily be retrieved directly, e.g. because of licensing issues. A librarian would offer the service of locating the document, creating a local copy of it (given that the library is authorized to access the document) and alert the end-user by e-mail about the temporary availability of the document.

  

### The request created from ABCD Site (or iAH)
    
The process starts when an end-user creates the request through a form, to which a link exists in ABCD, mostly from the ABCD Site (as that is exactly the idea of the Site). The ABCD 2.0 demo site already has such a link in the 3rd column. A component of type 'XHTML' was created there, and in the component (as can be verified using the ABCD Site Admin or CMS) the following code was entered, in this case referring to the PHP-script for the form on a 'localhost' server, obviously needing adjustments for other server-URL's :
```
<p>Online Documents Delivery System 
<a target="blank" href="http://localhost:9090/central/odds/form_odds.php">Odds
</a>
</p>
```
  
This is nothing else but a simple HTML link to the ABCD Central script : http://localhost:9090/central/odds/ form_odds.php

and showing up in the ABCD Site as follows (example taken from the default demo ABCD Site) :
![](https://lh4.googleusercontent.com/gtyRIocAppdIyIaXuovTYterlO08TnPy2b2LuaX_v53W1WYWyJn2rMXHm4mXnN-yrfr5BxI7YQWrxSOP473GJFBhFtePHEczYNHZFRhT0uG7dkVQDz0zom0L-L7W6BQaSPIjS3-r=s0)  

Creating the same link in the iAH OPAC is also possible, but requires quite some more skills in locating the right spot for such link. Most links (e.g. the 'shortcut'-links) in iAH are repeated for every single record of a result-set, which does not make sense here for a document request.


> Note:
> The ODDS module is not a 'document request' feature for e.g.
> creating photocopies and having it physi- cally sent to the requester.
> Such feature are however also quite possible in ABCD iAH by e.g.
> creating an ISIS PFT as a 'shortcut' which sends a request to the
> library's e-mail address requesting such copy. The initial developer
> of iAH (BIREME/PAHO) uses/used this service a lot as it was/is their
> main service.

When clicking on the link given, a page will open in the browser with the request-form, which looks, with some demo-data already filled in, as follows :![](https://lh5.googleusercontent.com/3szfpD-HjZOJEGNc9B9d2fOLwyWvxfoRlPfYwuSg02zMDf38IJz1grNNu3eW4e26g4erISTdgjztWGjzx2Z_I848d40gj2IQhyHbjCT5_Uzcgrfuh0MrODCJiIyNeHn8y4Y_9jM7=s0)

One important observation here is that by selecting different 'type of documents' (here a 'journal article' is selected), the form will display and gather different fields to identify the bibliographic data of the document.

The picklists for this form are resp. 'categoria.tab' (for request categories, e.g. by library branch), 'nivelbib- lio.tab' (for the bibliographic level of the requested document, changing the fields involved in the form), 'source.tab' (where did the user learn about the document), 'status.tab' (status of the request process), 'tipoliteratu- ra.tab' (type of literature, e.g. book, article...) and finally 'topicarea.tab' (topics). All of these can be edited directly (n the directory bases/odds/def/lang/) or from the worksheet-editor as 'picklists' for the ODDS-database.

The requester, after filling in the mandatory and as many as possible the available fields, clicks on 'Send' and will then receive a confirmation :  


![](https://lh4.googleusercontent.com/Jaqrjl7kiDwUWHtgw3STUYsTcosEIOkQZNcb4n691kCMtyNpbAL7N37ID5V0ZyXdt7AqBPaR_6qzECA4le3Yxhmi3Yb06N-rMrhGuKtkwpQg6_G9pl4Y4QaDr8cXiNCOq0AeyXAM=s0)
This ends the first phase, the 'end-user' request. The user now has to wait for an e-mail to be sent by the ODDS- responsible librarian about the availability of the document.

  
### The ODDS processing by the library
The requests created by end-users are actually sent, by 'sending' the form, as records stored into the dedicated 'odds' database of ABCD. This means that the responsible officer or librarian needs to have administration access to this database in her/his profile. The database also needs to be included in the list of available databases (bases.dat in the bases-directory).

So in reality the ODDS-officer will check - on a regular basis, e.g. daily - whether any new incoming requests have been stored in her/his database. By opening that database and navigating to the end, the last submitted request e.g. can be opened and will be displayed with the default 'odds.pft' (which can be adapted if so desired), e.g. :![](https://lh6.googleusercontent.com/bmvTjxxtffwY6rWRew6s1qY5zQjogwE85pCg3R7m-ru3mZ1M6-b_FLW9lsOhmHePE-TDaJovcdhbcGmyXU266Pekpf7HB9NDjWNcfthTRyZWV8U-ol-Hr2mBf11-GWDLwEi7bfhp=s0)

which then can be opened for editing, with an 'editor'-form, just as any other database record can be edited in ABCD Central :  

  
![](https://lh3.googleusercontent.com/lztzuIaI90g9qaXgcljedIdNvPczZjP8zJXnV2FEg3BWGooJdvDOHyZhTj8eXUamUGvarY_mHQJCsNhzstd1x3Q5yP4TZKflgghYhZO2oBEg632U_c0ddUBgtBvcU4kDhSI_iao4=s0)

The data in the record will hopefully allow the officer to indeed locate the document and download a copy on the local server. This is the main job of course and the responsibility of the ODDS-officer, who has - in principle - more or better tools available than the end-user to perform this service.

When done, the officer would then change the 'request status' from 'processing' to 'served' (or 'ready', the pick-list values of this field can be locally adjusted as with any other database-field in ABCD). When the 'request status' field is changed to the value '2', the PFT presenting the record will now show at the bottom an extra button, which actually will trigger an e-mail sent out to the requester (whose e-mail needs to be known from the user-database !).  

![](https://lh3.googleusercontent.com/1hF1BRUWdyLCcbx1s5eMd6rxMSDGqsKAAjvVlp8ZQkJrnD2OFvGHIb1y5flaITmddBV4oLz9QBYCUoKV_30KjJGLhsfiZUBt3vum1YaGT5sCdX3grtj16pH-gIkj5KXX_mM92sVz=s0)

  

The 'notification of successful request' will actually, when clicked on, pass on the field-values to the JavaScript performing the e-mail client command as defined in the PFT,
```
<a href="#" onclick="return getOutput('`,v528,`','`,v828,`','`,v100,`','`,v510,`','`, v94,`','`,v1938,`',
```

The javaScript 'getOutput' with its proper sequence of variables is included in the script 'sendMail.php' described above in the configuration section of this chapter. It is the responsibility of the system-manager to make sure the e-mail send-function is well tested and working. The sendMail script checks the configuration scripts either for Linux (senderMailLinux.php) and uses that configuration to send out the e-mail, or in case of using Windows, the executable 'blat.exe' (which is included in ODDS) will be executed by Windows with some e-mail fields pre- defined in the script itself, e.g. 'sender' (the name of the library), 'from', with possibly an embedded logo

The exact wording of the e-mail letter sent out is defined in either the file 'odds/def/$lang/odds_success_mail_sin- gle_file.tab' or 'odds/def/$lang/odds_success_mail_multiple_file.tab' ($lang being the code of the language used) depending on whether just one or more documents were requested and uploaded. The format is given as follows :

subject = Reference service - Reply to your request.
```
<html>
<head>
<meta http-equiv=Content-Type content=text/html; charset=iso-8859-1> 
</head>

<BODY>

<p>Dear <b>|name|</b>.

<br/>Your request dated |date| for the document |request_data| is available for |number_of_days| days at the following URL: |url|</p><br>

<p>Sincerely,
<br> Library Administration<br>
<font color=red>Dept.</font><br><font color=#555555>ADDRESS:<br>Tel.: Fax: <br>Address/Country</font><br
<font color=green>www: [http://abcd.netcat.be](http://abcd.netcat.be/) </font><br></p>

</BODY>
</html>
```
As can be noted, the file uses 'variables' like |name| and |url| which will be substituted for the real values by the software.

If the e-mail wording needs adjustment, it can be easily done here by editing the text-file itself.

When a request is cancelled, the file 'odds_cancel_mail.tab' in the same 'def'-directory of the odds-database is used to define the contents.