---
title: Digital library features in ABCD
description: In this section we discuss some features and techniques to create and use digital libraries as 'full-text' databases in ABCD.
tags: 
 - digital libraries
 - collections
lang: en
lang-ref: abcd-digital-library
---


# Digital library features in ABCD

{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---

In this section we discuss some features and techniques to create and use digital libraries as 'full-text' databases in ABCD.  

## The Digital Library concept in ABCD
   
In ABCD we simplify the meaning of a 'digital library' as a 'full-text' database, in which the records either containin addition to 'metadata' - the full-text of a document or have a link to the full-text document while the words in that full-text can be searched.

Since ABCD is based on the CDS/ISIS technology, therefore focuses on text-retrieval, images and other non-tex- tual elements of a document will not be processed but remain available of course in the original linked documents.

E.g. illustrations in a PDF will not be part of the ABCD-record but by clicking on the document-links the PDF, including the figures, will be opened in the browser.

An important limitation is the absence of 'relevance ranking' : the indexing engine of ISIS can deal with words (full-text indexing) but has no provision for relevance ranking, e.g. storing a 'weight' denoting the relevance of a document based on the (statistical) frequency of the word occurring in the document. In ABCD 2.0 a word is there or not, and this has certainly consequences for the search efficiency. For 'ranked full-text indexing' we have to refer to the new-generation version of ABCD : version 3.0, which is based on J-ISIS and therefore the Lucene- engine which has provision for ranking.

  

Another limitation is the size of the documents : if the special CISIS version 'BigISIS' is used, records can contain up to 1 Mb of text. In our tests most documents (PDF's) fit within this limit except for the really long textual documents. Most bigger PDF-files are big because they contain a lot of images or binary elements (BLOBs) but the extracted text will mostly fit within the 1Mb limit. Putting the document text inside the record therefore should be only used - it is an option after all - if most of the collection consists of not-too-long textual documents. The script generating the ABCD-records of a digital library database will warn for documents not fitting (or exceeding the PHP-limit set for upload_max_filesize' parameter - which by the way has very low correlation with the actual text-size of the documents.

However, despite the limitations, using a database for a digital library in ABCD also has advantages :

1.  The digital library can be managed like any other database, e.g. searching/editing in ABCD Central, including adding/editing metadata fields
    
2.  The database or digital library can be presented in the ABCD Site and searched along like any other database (e.g. catalog, serials collection...) in the MetaSearch option of ABCD
    
3.  If the document-text is - as an optional feature - stored inside the record, it can also be edited along with any other fields (metadata).
    
4.  Numbers of documents in the collection hardly affect the speed of operations, e.g. CISIS can deal with almost 17 million documents without any speed-penalty in searching.
    
5.  If the directories of the original files are structured into sub-directories, ABCD will generate and index these directory-names automatically as metadata in the 'sections' field of the records. This means searching can be based on these directory- or foldernames.
    

One special feature used by ABCD - as do many other similar dedicated digital library softwares - is to use the 'metadata'-extraction feature of the Apache Software Foundation TIKA library, which is a general-purpose text- extractor. This means that, provided (not obvious - most authors are not giving attention to this feature of their word-processor) that in the document properties the related fields were entered, available metadata such as title and author will be automatically entered into the fields of the database-record (see below for a sample record with such automatically extracted metadata). If defined in the Field Selection Table, these fields will also be searchable in both Central and the OPAC (or Site Metasearch).

A special instance of a digital library in ABCD would be a 'DSpace repository' created from an existing DSpace collection. For this we refer to the dedicated section in this manual.

## Creating a collection in batch-mode

The batch-mode creation of a collection refers to the possibility to add a set of documents, pre-organized into one or more (sub-)folders, into an existing ABCD-database. We suggest to use the 'Dublin Core' demo-database as it  

has already the basic Dublin Core fields available and the creation script presents these fields already as defaults (but they can still be changed).

A typical use case would be the initial creation of a collection of theses, where the theses as PDF-documents are stored in a folder, structured by e.g. faculty, department and year of submission. These folder-names will automatically be introduced as meta-data ('sections') in the database-records and can be used as search-criteria.

Another usage case is adding a series of newly arrived documents (e.g. journal-articles) into an existing collection. For additions of individual documents, either in a new or existing record of the collection, a different script will be used, see the next section 1.3.

### Preparation of your collection

The following are the pre-required elements in order to allow creation of a collection in batch-mode :
-   A database with pre-defined FDT, FST and PFT in which the documents will be added as records
-   A new parameter 'COLLECTION=' in dr_path.def file of the related database : this parameter indicates the full path to the collection-subfolder in which the collection files will be stored. This subfolder can be anywhere in your system, but typically will be either a 'collection' directory in the 'bases' directory of your ABCD-system (e.g. ABCD\bases\collection in Windows) or a collection-subdirectory for a specific database (e.g. /var/opt/ ABCD/bases/dubcore/collection in Linux). This folder will need full access/control for the script creating the document records.
-   Optionally : a field in which the document text will be stored   
-   A special PFT (to be edited manually or copied form existing digital library database PFT), in which two special instructions are given :
    
1.  instruction to display the text-contents of the document into an 'Iframe' of the window :

```
if p(v96) then 
'<tr>
<td width=20% valign=top><font face=arial size=2><b>Text- source</b>'
'</td>
<td valign=top>
<font face=arial size=2>
<iframe height=200 width=800 scrolling=yes src=http://localhost:9090/', replace(v96*1,'ABCD/www/bases/','collec- tion/') ,'>
</iframe></td></tr>' 
fi
```
  

> Note:
> This example works for 'localhost' with port 9090 since the
> 'source' of the file is referenced by 'http://localhost:9090', and the
> string 'ABCD/www/bases/' in the file-path and -name in v96 will be
> replaced by 'collection', so this supposes Apache has an 'alias' in
> which 'collection' refers to the real database-directory. The name of
> the database (e.g. 'dubcore') will need to be present as well as the
> 'ABCDSourceRepo' subfolder name.

  

2.  instruction to display the link to the original document file on the server :
   
```
if p(v98) then 
'<tr><td width=20% valign=top>
<font face=arial size=2><b>URL</b></td>
<td valign=top> 
<div id=divurld',f(mfn,1,0),' name=di- vurld',f(mfn,1,0),'>
<a href=javascript:DisplayURL(',f(mfn,1,0),')>DISPLAY</a></div>
<div id=divurl',f(mfn,1,0),' name=divurl',f(mfn,1,0),' style=display:none>
<font face=arial size=2>
<a href="',v98'" target=new>'v98+|<br>|,'</A>
</div>
</td>' 
fi/
```
  

> Note :
> This example is a bit more advanced since it includes the
> mechanism to hide the URL with only a link 'DISPLAY', which triggers a
> Javascript function 'Dis- playURL' which will invite the user to log
> in as a library user and only if correctly logged in will actually
> display the real URL. That URL is indicated by the value
of v98 in this example. As an alternative to 'logging in' ABCD can also use a check on the end-users IP-number (or range) and only show the URL to users within the accepted IP-range :

The login Javascript code, to be added on top of the PFT, is listed under here :
```
<script  language=javascript>  
function  DisplayURL(id)  {  
var  login- to=document.getElementById("into").value;  
if  (loginto=="no")  {  
var posicion_x;  
var  posicion_y;  
posicion_x=(screen.width/2)-(315);  
posicion_y=(screen.height/2)-(235); 
sel = window.open("/site/login.php?id="+id, "ABCD Log In Windows", 
"width=630,
height=470,
menubar=0,
toolbar=0,
directories=0,
scrollbars=no,
resizable=no,left="+posicion_x+",top="+posi- cion_y+"");  
}  else  {  
document.getElementById("divurld"+id).style.dis- play="none";
document.getElementById("divurl"+id).style.display="block"; 
} 
}
</script>
```
As an alternative the IP-range of the end-user can be checked to (dis-)allow the display of the URL, with the following code added into the PFT :

```
proc('<9000>',getenv('REMOTE_ADDR'),'</9000>'),
s1:=(left(v9000,instr(v9000,'.')-1)),
s2:=(mid(v9000,instr(v9000,'.')+1,size(v9000)))/, 
s2:=(left(s2,instr(s2,'.')-1)),
if p(v98) then '<tr><td width=20% valign=top>
<font face=arial size=2><b>URL</b></td>
<td valign=top>', if val(s1)=127 then if
val(s2)=0 then 
'<a href="http://127.0.0.1:9090//docs/dubcore/collec-
tion/',v98, '" target="new">'v98,'</a></td>' 
else 'IP not allowed' fi else
'IP not allowed' fi fi,
```

> Note This instruction has two separate parts : at the beginning of the
> PFT a 'proc' is used to store the IP-number in a virtual field v9000
> and then its parts into local variables 's1' and 's2' respectively.
> Then, at the location of the PFT where you want to display (or not)
> the URL, and if v98 (with the URL info) is present only, the value of
> s1 and s2 are checked to see if they are contained within the allowed
> range, in this case 'localhost' (127.0.x.x).

In principle the system manager (or librarian) needs to decide which method to restrict access to the original documents to use : either log-in based or IP-range based. However using normal PFT-instructions (e.g. `IF...THEN...FI`) one can combine them or simply use both, e.g. labeled 'Display after log-in' and 'Display within campus'.

-   A special FST, named 'fulltext.fst' in the database 'data'-directory, which contains an indexing instruction (line) which uses the document-text as input for the indexing engine with the 'cat' instruction, e.g. in the case of the existing Dublin Core database ('dubcore') :
   
        99 8 '/TW_/',if p(v96) then proc('Gload/99/nonl='v96) fi,v99

This instruction creates an index identified by '99', using the prefixed words-indexing method (8) of ISIS, by first creating the prefix 'TW_' (text-words, typically the index for the simple search of ABCD OPAC), then if the field 96 is present to indicate the path/name of the text- file, to load that file into v99 (without new-line characters) and use that text as input for the indexing engine. In addition to this special instruction all other meta-data oriented indexing instructions, e.g. to include title/author etc., can be used in this special FST.

-   A 'normal' FST, mostly meta-data oriented, to be used whenever the record meta-data fields have been edited and are saved.      
-   A fixed-named 'collection' subdirectory of the related database-directory
-   A fixed-named subdirectoy of the COLLECTION-directory 'ABCDImportRepo' in which the documents to be processed are located.

***It is of utmost importance that both the collection- and ABCDImportRepo- subfolders have full access (or in Windows 'Full Control') to the users, since files will be moved from there and new files will be written into the collection-folder.*** Make sure, using your Operating System's interface, that this condition is fulfilled. E.g. in Windows right-click on the folder and check if the 'security'-tab indicates 'full control' for the users. In Linux make sure the directory has '777' attributes (e.g. with the command 'chmod -R 777 collection'). Please also note that also higher-level directories or folders need to have full access since the OS will parse through all levels from the 'root' up to the related collection-directory and stop doing so if no full access it allowed.

A typical structure will look like the following, where documents are related to either ABCD, ISIS, Greenstone (GSDO) or J-ISIS, so inside the ABCDImportRepo subdirectory the original documents were stored inside sub- folders with corresponding names (ABCD, ISIS, GSDL, J-ISIS), except for a special document 'ISISorigins.pdf' which was left out of this sections-structure and therefore will end up in the 'root' of the collection.

Figure 2.3. Typical COLLECTION structure  
![](https://lh4.googleusercontent.com/PQFZshDsKeQgHWqg3KQJQtHAxt6rghclE-Oocr7XFxLeIrvGesQomgc9GSXGspQZUCQM_1-I1uXtagHYuPcYmnhLQWIlJL5QwTV1O1fTQ-wkMPpKbQM5xkC7k238VEO2E0cpSKE=s0)  

The ABCDSourceRepo subdirectory will contain all HTML-files with the extracted texts, all original docu- ments (e.g. PDFs, Word-documents...) will be stored in the corresponding subfolders as they were present in the ABCDImportRepo directory, but with some random numbering added to the file-name. This is to ensure that doc- uments with the same document-names still are individually identified. The resulting ABCD-record will have both the reference to the HTML-file (in ABCDSourceRepo) as the original document into its dedicated fields, in the demo DUBCORE database : resp. v96 and v99. In this example the'isisorigins.pdf' was not moved into a subfolder

-   only for demonstration purposes - because inside the ABCDImportRepo folder it also resided at the 'root'-level.
    

  ### Using the creation script

After you have ensured all preparation steps are properly dealt with, the use of the script to create digital library records is rather straightforward.

The script for batch-import of documents is the first one in the new 'EXTRA UTILITIES' submenu of the Central Utilities menu :

Figure 2.4. EXTRA UTILITIES menu
![](https://lh4.googleusercontent.com/HbIp-oJ7MU0pbCdUwPAylXr_k-YHkSxBk56VH6yAX7SA3XVmhm_I-va0BIT6xWaJOBUx-q75COsJbxiIv-svzrn09dwDStX5rr2vsup0MFy0VQ1XGvvsqP5T2wxyXVVrmiJg3jE=s0)  

After the 'Documents batch import' option is selected, the main screen is shown, in the case of the Linux version after a count-down to load the Tika-server into memory (since the server-version, not used in Windows) takes longer to load) :  

Figure 2.5. Main screen Batch Documents Import  
![](https://lh3.googleusercontent.com/3vgNTxShUJRVhdHVohjIycFHPKXHydrJ5F7TQ7LoNTkkMsh1HhveSSZKsxVTjWxrq5wNKM96ODpfNtllM0pTAVylxRptKB7qm3Yd3_-H2ICIMtpUs-tfBmXPVrptJ2jQpXKcppc=s0)  

In this screen the librarian has to 'match' the automatically extracted metadata (Dublin Core-based) to the fields of her/his database, along with some special fields : the field to contain the 'sections' (=subfolders of the collection), the document source, the document identifier and optionally the field to contain the full document text extracted by TIKA. Note that this is not used by default as it will require the BIGISIS CISIS-version in order to use larger records.

Clicking on the 'Update' button will launch the iterative script which processes all files in the ABCDImportRepo subdirectory and displays the progress on the screen until it is finished. The illustration below shows the last part of such listing when the script finished.

  
Figure 2.6. Results listing after running collection creation script
![](https://lh6.googleusercontent.com/oeMq4ObdTqwxsm6_KI4KGnjJq3YumujJAkEzY23sfUpIgHqS-v3KM_tSXOWFv4Dkl8DkdY4KfiWzTzQc_aXnM7E2wD5X6-5jp1RBPx6kBXBKYmfpofvnNwrRV9DZnPEYTdOOV9I=s0)  

Now entering (still within Central) into the database and navigating to the last record will show a typical record as follows :


Figure 2.7. Display DigLib record in Central  
![](https://lh5.googleusercontent.com/3SZi9Ww6HrOvKFmXRCUEEjGb9I6EwyVFCU4df5ZMdHtwZOa7969XSck-BzqRyHU1gbhManGNLNPBYcvvrFA7COfCYvvl9psrHBrokCq0RQMs2-P0S8gH_yiSfeWiJqaR8k5TTQw=s0)  

The database needs to be fully indexed ('full inverted file generation' in ISIS-vocabulary) using the earlier men- tioned special FST 'fulltext.fst', but also using the special parameter '/m' in order to avoid storing all detailed po- sition info into the index-postings :  

Figure 2.8. Full text indexing of Digital Library collection 
  
![](https://lh4.googleusercontent.com/t-EXYP1O9uwEvVQUCvfbZe3YgnksOCrjkgR_NpXSb8dykJ2X4n1iK_QwNArgPZw1GEivtflK177dj6pjEyKPJ5cmlKe3SIVLe7rbdE-c7_n-67NXQqUD1Y0cm7ycPDhc6aU8FdQ=s0)  
  

An example of - part of - a full-text index is shown in the next illustration :

  

Figure 2.9. Full text index listing
![](https://lh5.googleusercontent.com/Oi-1e6Lpk7x0CXxOw1vDATQAR0RT4uI8nPV8oeYNceH0mfzlZY8fqSRuz1rlMx8ldIUN03FzL3w_skJn3cQoFVfunDBhU-JS-_KJxdlOUBUeA2MSyRX7cUGXNZwcaRs_9127OR8=s0)  

Selecting one or more words, as is also done in any other Central search action on any other database, results in displaying the record(s) with highlighting of search-terms :

  

Figure 2.10. Digital Library search record display  
![](https://lh3.googleusercontent.com/QmOzgg-3Am4rhfEsGWk5OWWDnuxpCQ5jox4XY27IJUFsi6Ysk4-zHePLIspTecuz25z6-Ep816yO2i1QdRu8aXQ0kZLWnObFthLC2PVkXDO5TuX4FfzLIwCqDJg4IxpC0ksj-GQ=s0)  

The text-source is just shown as a first quick-check to assess the relevance of the document; this is of limited use but e.g. in the OPAC can help end-users to decide on whether or not they click on the URL-link to view the original document in full format.  

In order to illustrate the earlier mentioned 'sections' feature, where ABCD uses the pre-configured subfolders of the ABCDImportRepo directory to automatically assign 'sections' to the collection, here is the listing of the 'sections'-index in ABCD Central :

Figure 2.11. ABCD Digital Library Sections listing  
![](https://lh4.googleusercontent.com/BtVS6AiGpMAqOU69jbw5W_mtlDFKnSylzcA1Hx0MXX52p7rHY-1JhrJX47OZ0QAr6O_j5LyPyTl6i-fd8VAvTPvEG7DIA5N8SOyG6aOTjJESa6wx-JH5vlxepeed4GsuEFQD9P0=s0)  

This reflects the now adjusted folder structure of the collection-directory : subfolders from ABCDImportRepo were reconstructed into the collection-root folder with the original files moved there, and the ABCDImportRepo folder is emptied, only leaving unprocessed files there (e.g. too large) :

  

Figure 2.12. ABCD Digital Library new collection directory structure
![](https://lh5.googleusercontent.com/XJchXKfLypvlu2RfnnGQpoZLzQsLO_H8CXUhCeclnmsjGzZE1yv_DIHXjH2hPqaNy4qLa0p0bj6J4qztaJsedEOj2f1c98T9yWvNlkz8Crf89l-RGYaHUlCPwBvk-51E98SXdN8=s0)  

As one can see : in addition to the 'ABCDImportRepo' folder (now emptied) there is a folder 'ABCDSourceRepo' containing all html-files with extracted texts, and there are 'section-'folders for ABCD, GSDL, ISIS, JISIS and 'Various', while two PDF's were not part of the sections and therefore remain at the 'root'-level of the collection without 'section' information.

  

The digital library database can be included in the ABCD Site MetaSearch (as is the case in the demo installation) and searched by end-users like any other database. The result display is very similar to the one above in Central :  

  

Figure 2.13. DIgital Library search result in iAH-OPAC
![](https://lh6.googleusercontent.com/Y1XhawZUTMcJzw_p_RRcBxW1cGwa4-uA3wUrPvudm6M5iHUSzLtzfNzFx2IG-tnz1yJtSrPpHvsZ0kJwlGNMfu2YdyTtnNhO8ToMiLR9s9UaLpI71XA8ilmgVr9zjftZGm59xcU=s0)

This screenshot also shows at the right side the original PDF-document, after having clicked on the URL-link as a hyperlink.

> Note:
> The 'login'-based protection method using the javascript
> 'Display_URL' does not work from Central but works - as intended -
> from the iAH OPAC.
