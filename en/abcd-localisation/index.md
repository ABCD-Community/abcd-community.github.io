---
title: ABCD Localisation
description: This section deals with the techniques and steps needed in order to create a 'localised' version of ABCD.
lang: en
lang-ref: abcd-localisation
---


# ABCD Localisation

{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---
    

This section deals with the techniques and steps needed in order to create a 'localised' version of ABCD.
Localisation refers to the idea of presenting the software in a way suitable for the local users, i.e. using a language and alphabet but in some cases also 'style' of wording and presentation which is most suitable for the targeted audience. E.g. for a children's library one could imagine that all the mentioned elements : language, alphabet,  

wording and presentation, are adapted to the main characteristics of the target users, being children who have another vocabulary, their own preferences re styling (e.g. more colours and funny icons) etc.

As an extension of this idea also the concept of a 'responsive' interface could me mentioned : the interface adapts to the device of the user. Generally this boils down to using other style-sheets when the user-device is a mobile phone with much more vertically oriented and smaller screens as compared to computers. Not everybody is fully happy with this concept, some even stating "don't do it", so we will refrain from going into this technique all the way. Let us simply refer to the idea that a lot of such 'responsive' behaviour can be facilitated by the creation of several style-sheets sets. For ABCD this has been done as a matter of fact.

Here we will focus on creating a new interface based on the existing one but using a different - possibly new

-   language, if necessary written in a non-Latin alphabet. This not only needs to be done for the ABCD Central module but in fact more relevant for the other main end-user oriented modules iAH and Site. So when we 'localise' ABCD Central we consider the operators (librarians) also as end-users with their preference for a specific language, alphabet and vocabulary.

Since ABCD is a very much 'modular' system, each of the main modules has its own requirements and techniques to translate the interface to any other language. These modules operate independently (however accessing the same ISIS-databases) with their own software technology and also use different ways to display texts on the screens.

E.g 'Central' uses text-files .tab with simple key-value pairs in the language-database-folder whereas 'Site' uses HTML- and XML-files. For the iAH OPAC a single text-file with most messages can be used with available scripts to immediately create (most of) the necessary text-parts in the required files (mostly php and pft scripts).

## Localisation of Central
    
Except for some texts which could contain language-dependent elements, e.g. in the header and footers, like the institutional name, version, website links etc., all language-sensitive elements for messages are in 'tables', i.e. text- files with key-value pairs (key=value) saved by submodule (e.g. administration, cataloging, circulation…) in a file '.tab'. E.g. the file 'admin.tab' contains the messages of the Central-interface to deal with database-definitions. For each language these files are stored in a sub-folder of the 'lang'-folder in the bases-directory. This is not a real database-folder with ISIS-database files, like for other databases (e.g. MARC, CEPAL, USERS), but just the store of messages for each language used.

Under here we show how the same file admin.tab above will look like accessed from within the interface of ABCD Central; for illustration purposes we included a non-Latin entry (Sinhalese) already for the 3rd value (acquisitions) :![](https://lh6.googleusercontent.com/pIHhCVbVEbFErJDurRdNLow9fIaOaM0nUmHpEymKXTZmVK-mdaQuSU47atdLd34bXGv5orNAAMGZvMvBbxqMhULYICmIKVwaz129zQqc48bHwlPElSzt4sGRUjB1axyQ30nf4hI=s0)
The first use of this interface therefore is to 'adjust' messages according to local taste or individual preferences. However the same technique can also be used to create a new language as follows.

### Create new directories for a new language
    

Using the file-manager of your OS (either Windows or Linux) and navigate to the bases-folder, i.e.  

-   for Windows :

    \ABCD\www\bases

-   for Linux : 

    /var/opt/ABCD/bases
    
and locate the 'lang' sub-directory in the list of databases (each database has its own folder/directory). Enter into that directory and copy the one folder with the language you want to use as the 'from' (origin) language to be translated into a new one. E.g. if you want to create your new language based on the English, copy the folder 'en'.

Paste that folder back and (re-)name it with the code for your language, using preferably the ISO-codes for lan- guages. E.g. to create a Sinhalese interface we will use 'si', so the original folder 'en' is copies and added as a new folder 'si'. In there all text-files still are English, by definition.

### Add the new language in the languages lists

Still in your file manager, locate the file 'lang.tab' within your language folder and manually – e.g. with Notepad or Gedit – add your new language in the list, e.g. with Sinhalese the new list would look like :

```
en=English
es=Spanish
fr=French
pt=Portuguese
am=Amharic
si=Singalese
```
So if you use English as the default language for Central (see the file htdocs/central/config.php,in the line where the default language is defined, e.g. $lang="en"; for English), you have to edit the file bases/lang/en/lang.tab and add the new language as a new entry.

In Windows please check, esp. when using Notepad as the editor, that the extension of the file is maintained as '.tab' whereas Notepad will try to add .txt' to it as a new extension. ABCD will not recognize your languages list if it is not stored as lang.tab !

Now, up one level in the 'bases'-folder, another file 'lang.tab' is present which is used to list the available languages in the Central login-screen, where the previously edited file 'lang.tab' (in the language-specific subfolder) gives the display values (not the codes) for each language, so 'en' becomes 'English' etc. So here you simply have to list all language-codes you want to use, e.g.
```
en
fr
es
pt
am
si
```
If you want users to be allowed to switch languages within Central, you should also add the new language in the 'lang.tab'-files for all active languages, so in their own sub-folders.

### Translate all messages for all Central submodules using the interface

Now enter the ABCD Central interface into the language for which you have added the new language in the list. So the new language should appear in the languages-selection list of both the main login-screen and the language-selection list within the Central interface. Either way : make sure your new language is the active one. When then selecting the option 'Translate messages' and choosing one of the submodules, you will be looking at the 'origin'-language (e.g. English) at the left side fixed, and their values editable in boxes at the right side. So this is the big and main job : translate/transliterate all values to reflect as much as possible the correct language equivalent for the given message. This might require checking official glossaries e.g. maintained by your Ministry of Science and Technology, esp. for IT or even 'library science' in order to get the most appropriate authority files.


In the screenshot above one can see how the 3rd entry (no. 2) for 'acquisitions' has been translated into the Sinhalese word (and alphabet) '#############'.

Once the table is saved the next time (after refreshing the screens) the word 'acquisitions' in the interface will show as '#############' :  

  
  

![](https://lh4.googleusercontent.com/zmY-3GVoL-UVo7ASMvZdSedQR9zD03t6_DGbAKCSwt2T7nCvQfbr_kMAtpBLTvkI7uJuHA7b4HCeQYuaanWUBoX15mAlumzVTtOfFJXozBcDOsMtmnwcR0_lcN_1zsOCWV4Ir5Y=s0)

E.g. for the 'Amharic' interface (for Ethiopia) the same list of first few 'cataloging' interface messages will look like :
 
![](https://lh5.googleusercontent.com/GZP6UnHWGilHfOaA7X-KbL5VlFsjYlzOfNzE0kOBI6L3aXHr75H8cjv6qH92Zd7DNHpz3PVTGrrnWNrOXq5cDPd9OKo4Vq45s8RsjEP9FFXItaA-nJ2Smzr5uG2g76QKL2hreJk=s0)  

One can also, with an extra option in the ABCD Central main menu, 'compare' the existing translations in different languages to make sure the real correct meaning is taken. E.g.![](https://lh6.googleusercontent.com/GV4yMiMm5NCXvtykif-qia63hactYCeGWrzUm5oQM6IsEbJVH6YFEl8FB4FCyGh_VcQyxUC8Q-yCuE38iZEBDFNIL_RSPqC1AteYWUgu91WxrQUNltGiMRtHyZHhm7MP4JUdHWE=s0)

The list of languages displayed in this overview should be manually edited in the script 'compare_admin.php' in the htdocs/central/lang sub-folder. Look for a section like :

```
if (isset($msg_path) and $msg_path!="")
$a=$msg_path."lang/am/$table";
else
$a=$db_path."lang/am/$table";
```

and change '/am/' (Amharic) for the language you want to see – at the right-most side – instead of Amharic, or any other previous language if so preferred. E.g. '/si/' .

Alternatively, once this mechanism with the underlying system of files and (sub-)folders is well understood, one could also directly edit with a text-editor all .tab files immediately within the file-system, without using the ABCD- interface. ABCD indeed is nothing more – but also nothing less – than an 'interface' to the multitude of files, scripts and databases of which the system consists.  

> Note: 
> when saving text files with non-Latin scripts, like in the
> examples above, make sure you save the text-files as UTF-8 files, not
> the mostly default 'ANSI' characterset. In Windows there is an
> additional complication : some software will want to add a hidden
> 'BOM' (binary order mark) as a few characters to indicate that the
> file is of Unicode-type. Since there has never been reached a real
> agreement on this – and quite some experts do not accept this to be a
> good solution – it is better to avoid this BOM additional code. If
> present the file won't be correctly processed by e.g. JavaScript or
> PHP as in ABCD.

When all messages of all modules/functions of ABCD Central have been translated, one can open the related language-version and the interface would look like for instance :![](https://lh5.googleusercontent.com/Px_MqV3jtD_B1ZnwdlLcVfl_8sCDZBq7O9y7l0A796uCGm9QOZv0y9WxiJh4XD1OOfXXSGzttUieGY9Z74IeMxvFXyvePmt0fq-Aem8_9AAB_ztRAksqe7A1rikArEOA6QK3f7w=s0)

  

### Translate all help-messages for the new language/interface
    

The ABCD Central help-pages are located as HTML-files in the bases-directory named 'documentacion'. For each language used a subfolder needs to exist.

So in the case of adding a new language (e.g. Sinhalese), copy the folder 'en' to a new folder 'si'. Then inside this new folder you will find all English help-files in their original English version.

> Note:
> There exist sub-directories for some specific interface parts :
> acquisitions, circulation, copies and stats. All other helpfiles are
> directly positioned into the main subdirectory.

Then, using a suitable text-editor - try to use one which is more powerful than the dreaded Windows 'Notepad' but e.g. in Linux the basic 'nano'-editor will do well - translate the visible text-contents of the HTML-files. In case a good text-editor is used, these parts will have their own colour so as to make them quite easy to distinguish from other parts which should be left untouched as they constitute HTML-codes. Be careful ! As an illustration we show how the help-file 'alfa.html' for English is displayed in the Linux nano-editor : the while-coloured texts as the ones to translate into the new or local language.  

  
  

![](https://lh4.googleusercontent.com/4Y9Q-tEjpq-sMdCx8vTha3wCKRm50uD7zcjZzaltayXtG7pXmlNzLum86i18vaWLMTdewaF_BsEW01Pw6jpq6gN7p82NNG14RUFgd6FPzE6v63NBFtOIF2bNIal6qp_Kun4-Wic=s0)

  

### Create language folders for each database
    
Since each database you want to use in ABCD also contains some language-dependent elements, e.g. the names of fields in the 'Field Definition Table' or in the display formats (PFT's), you should also copy/paste and rename an 'origin' language-folder to a 'destination' (your new language) folder in the bases-folders. Once done, editing the 'database definitions' in the ABCD-Central interface will be done on the correct language version for that database. E.g. for the MARC-database, the default catalog database for a library in ABCD, and a new language 'Singalese', do the following :

-   copy the folder bases/marc/def/en as 'origin' to 'bases/marc/def/si as destination
-   copy the folder bases/marc/pfts/en as 'origin' to 'bases/marc/pfts/si' as destination.
    
Then when in the MARC-database in the new language (Singalese) and using the ABCD interface to create/edit database definitions, you will be actually editing the files in bases/marc/def/si and bases/marc/pfts/si, so all lan- guage-dependent parts like field-names can be translated into Singalese.

As mentioned above, it is also possible to edit these files directly with a text-editor within the file-system without using ABCD, but then be careful because some understanding of the file-structure is necessary. E.g. deleting a pipe `'|'` - which serves as a 'column' separator in ABCD Central – by accident might spoil the whole file.

## Localisation of the iAH OPAC
    
When checking the folder 'htdocs/central/iah', which contains all Central iAH scripts, one can see that again each language has its own sub-directory.

### The general language elements in the subfolders of htdocs/iah
    
These are mostly html-files, e.g. for the help related to searching the database 'lilacs', there is a file note_for- m_lilacs.htm with contents :

```
<hr>
<font face="verdana" size="2">
<b>Notas :</b><br>
<ul> 
<li>
<font face="verdana" size="2">
This option re
<font color="Navy">title words</font>, 

<font color="Navy">words from the abstract</font>, 
and <font co
</font></font>
<li><font face="verdana" size="2">Use the truncation symbol <font color="#FF0033">$</font>(dollar sign)
to search words with the same root. Example: 
<font color="Navy">educ</font><font face="verdana" size=
retrieves educaci&oacute;n, education, educa&ccedil;&atilde;o, etc.
 </font>
<li>
<font face="verdana" size="2">Do not type boolean operators (AND,
 OR ou AND NOT) between words. </
<li>
<font face="verdana" size="2">
Select the option 
<font color="Navy">
All words (AND)</font> to link the words (reduce the scope of the ret
<font color="Navy">Any word (OR)</font> to add words (enlarge the scope of the retrieval).</font>
<li><font face="verdana" size="2">
To search over other fields or to specify the field of the search use t
</font> </ul> </font><hr>
```


If one understands HTML-coding it can be easily seen where are the HTML-codes in between brackets < and > and where we have pieces of text to be translated.

If you want a new interface in iAH in another language, copy an existing 'origin' language folder and rename it under the new language-code. Then simply edit with a text-editor the pieces of text in your desired language/al- phabet. Again when using Unicode scripts don't forget to 'save as' UTF-8 encoded file or use the 'encoding' or 'charactersets' option of your editor to assure the characters can be correctly stored.

### The script-generated language elements

Within the htdocs/iah/scripts folder one will again note the existence of language-coded subfolders. In here iAH stores the HTML- and PFT- files or scripts it uses, with at many instances small language-related entries. While it would be possible to translate all such files in the same way as above, after having created a specific sub-folder for the new language by copying an 'origin' language folder, there are some scripts available in the folder 'htdocs/iah/ scripts/translate', which works as follows :

-   the 'translate' folder contains all the HTML- and PFT-templates used, as well as
    
-   a simple key-value list for each language saved under the language code with .txt extension, e.g. en.txt contains all keys and values for English.
    

For creating the Amharic scripts of iAH the file 'am.txt' contains sections e.g. like :

```
database=### ##
database_search=### #### #####
config=###
```
again stored in UTF-8 format.

From the 'model' translation script 'translate2en.sh' (or translate2en.bat in Windows) easily a dedicated script can be generated for the new language, in the case of 'am'-haric it became :

```
#!/bin/sh
./mx seq=am.txt= "proc='d*a1~{{'v1'}}~a2~'v2'~'" -all now create=to_am
for i in *.pft
do
./mx seq=$i£ gizmo=to_am lw=9000 pft=v1# now > ../am/$i
done
for i in *.htm
do
./mx seq=$i£ gizmo=to_am lw=9000 pft=v1# now > ../am/$i
done
```
where basically the string 'en' was changed to 'am' and 'to_en' was changed into 'to_am'.

When running this script in a terminal (or CMD in Windows) some smart use of the CISIS mx-tool will read in the key-values text for your language and process the lines to add special brackets {{ and }}. Then these will be replaced, with a gizmo-parameter using the database created in the previous step, in the existing script-templates by their actual values, both for the PFT and HTM extension files.

The resulting scripts then are stored in the language-specific subfolder one level up in the file-system (from the 'translate' subfolder).

Some manual checking might remain necessary after this process, but most of the cumbersome work has been done intelligently by the above scripts using mx, the main CISIS-tool. So in ISIS-environments many problems can be solved by using the power of the software itself, albeit good understanding of the command-line tools will be necessary to create such solutions.

The list of languages to be used in the interface is derived from the file 'iah.def.php' in the folder htdocs/iah/scripts. There is a line :

    AVAILABLE LANGUAGES=pt,es,en,fr,am

clearly listing the codes for the languages (and their sequence, which is quite important as it needs to correspond to the list of subfields in the iAH-configuration files for each database !). In other words and in this example : since we added 'Amharic' as the fifth language for the OPAC, each configuration line in dbn.def needs to get a subfield ^5 added with the appropriate term for the language.

With the parameter

    MULTI-LANGUAGE=ON
one can also switch if 'off' so as to only use the default language, set in the line

    $lang = ($_REQUEST['lang'] != '' ? $_REQUEST['lang'] : 'en');

of the file 'index.php' in the folder htdocs/iah.


## Localisation of the ABCD Site
    

The ABCD Site again uses a different mechanism of using language-dependent elements. When one checks the folder 'htdocs/site' it immediately becomes clear no separate language subfolders are present as in iAH. Rather as in Central a 'database'-folder will be used, named 'site' even if as with Central there is no real (ISIS-)database involved : rather this base-folder contains XML- and HTML-files for each language.

So, as above with Central, one starts by copying/renaming an existing language-subfolder in the 'bases/site' folder, each for the XML and HTML-files.

Then inside the newly created folder each of the files – about 30 but small in size – need to be manually edited with a text-editor. This is a job to be done carefully so as not to 'touch' on any real XML- or HTML-tag.

The files are named with numbers, according to an intricate internal naming system managed by the Site-scripts.

E.g. the file '22.xml' has this contents :
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<warning id="22" lang="en" available="yes">
<item available="yes">Warming<description>This VHL is under development </description>
</item>
</warning>
```
If one understand XML one can see that only the parts 'Warning' and 'This VHL is under development' are to be translated, everything else is to be left untouched as it is actual XML-code.

A more illustrative file is e.g. 'metasearch.xml' which contains all labels used in the 'metasearch' interface :

```
<?xml version="1.0" encoding="iso-8859-1"?>
<metasearch id="" lang="en" available="">
<text id="search_title" available="yes">ABCD Search</text>
<text id="search_entryWords" available="yes">Entry one or more words</text>
<text id="search_submit" available="yes">Search</text>
<text id="search_howToSearch" available="yes">how to search?</text>
<text id="search_allWords" available="yes">All words</text>
<text id="search_anyWord" available="yes">Any word</text>
<text id="search_error" available="yes">Please use a search expression.</text>
<text id="search_advancedSearch" available="yes">search filter</text>
<text id="search_freeSearch" available="yes">by words</text>
<text id="search_results" available="yes">Result</text>
<text id="search_method">method</text>
<text id="search_demo">demo</text>
<text id="conceptSearch_title" available="yes">by relevance</text>
<text id="conceptSearch_entryWords" available="yes">Search documents more related to the concepts</text>
<text id="decs_mesh" available="yes">Search by DeCS/MeSH terminology</text>
</metasearch>
```

Here it should be clear that again not the parts inside `<` and `>` can be changed, only the actual texts as displayed outside the brackets.

Using a 'better' text-editor than the very basic **'Notepad'** in Windows, e.g. **Notepad++**, or in Linux : **Gedit**, one can easily benefit from the syntax-recognition features of these softwares : whatever is plain text will be shown in a  black color whereas anything 'code' (e.g. XML, HTML, PHP…) will have colors. E.g. in the following screenshot we show the same file 'metasearch.xml' for the ABCD-site when opened in such a richer editor, now all text-parts to be edited shown in black colour :
  
![](https://lh6.googleusercontent.com/24zm6BV_6z8Wqj1miCiVRfzO8nvQaylhTK__UaoTBKCNkiatJC-QIIziClcH580AoiY7wx3xNXmgfE3tdAR9DsE-RImVgUDtJkjNs9JSDXizNpOTRQX3KD1ddq9jpntMk77f5ow=s0)  

Finally some buttons which are really fully embedded in the Site interface need to be edited for your language using the 'Site Admin' (the CMS part of the Site) interface, selecting the option 'texts' from the main menu of the Site Admin module :![](https://lh4.googleusercontent.com/eccq-2l4UiJjoOQugnWFR-tWYVEbmRm3jkEwl-oZKQvVfibr4P3cguXKOC5HwJhYDevDx9o3DMItYYm_7QKHNOWI8vt05A7x_JKHMEi64bSQ7W4FpO18fKZdNevBheSGwYzxB8Q=s0)

After selecting 'Texts' one can simply translate the option into the desired translated term :

![](https://lh6.googleusercontent.com/eeI61I7gTmSHmM1PAVa15ryO6Hr-BzuUZTCAb2A_xRSmo1SiD11A6h_BLiUQkSu58hNAfc2uSE3-OGXqi3xl44o-7cqT4q4YldtAlUxefTcwZNNjvxk-ZGNeaRLZ4U567UymOuU=s0)

Here the element 'contact' (the part of the screen where the Site will display contact-data) is simply translated as 'contact' but this could be done in another language/alphabet as well.  

Within all other ABCD Site Admin editing boxes there are still many more elements which can or should be translated, like each 'structural component' (the 'components' option of the main menu) when created also gets a name which could be yes or no translated into a specific language.

The list of languages in Site is derived from the script `functions.php` (in `htdocs/site/adm/php`), where the following section contains the list of languages to be used :


It is easy to see where to add/delete languages as listed by their codes in the array.

Additionally, ABCD needs a stylesheet named as 'style-xx' where xx is the language code, in the directory ht- docs/site/css/public/skins/classic (which is the default 'skin' for the ABCD Site, but as in the VHL Site this can be changed so as to create 'local' or 'regional' skins). A dedicated language folder also needs to be created even if it only contains one empty file 'redefine.css'.

In `htdocs/site/admin/defaultXML` for the new language a new folder needs to be created and the texts in the file 'texts.xml' also translated with the new language added. However as this is really administration domain translation of all terminology might not be opportune, necessary or even possible.