---
title: Central utilities
description: The Central module, being the 'administration' module of ABCD, has a menu 'utilities' which is probably the most dynamic part of the system. More and more utilities have been and keep being added as needs or possible uses arise.
lang: en
lang-ref: abcd-utilities
---

# Central utilities

{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---
   

The Central module, being the 'administration' module of ABCD, has a menu 'utilities' which is probably the most dynamic part of the system. More and more utilities have been and keep being added as needs or possible uses arise.

Utilities are special scripts which serve a purpose of more advanced, non-daily use functions mostly related to manipulating and managing databases. One example has been discussed already above : the creation of a collection of digital library records in a database from a batch of documents.

In this section we will discuss the most important utilities. Some of them however are very simple and obvious in their use (e.g. initialize database) so they don't need a lot of explanation.

## The main utilities menu
 
From the main Central page, after logging in and having selected a database (because most utilities require a database to be active), one can select the main utilities menu :

Figure 2.1. Main Central Utilities menu  
![](https://lh5.googleusercontent.com/yojHqXcOqiMYGHREPSGx8e036s5P2a_iB_N-7XRpugD5jB1P46nRnkhAi7KPE3tSk3kNrjDrHiCQdAgeJzjX4FR8rZocBbhY7UaPNerSE-hApOW-F8427EIaT2tS1onPt43osiPn=s0)  

> Note:
> This menu can be different depending on the database selected or
> the Central configuration. E.g. the 'explore databases directoy' can
> be dis-allowed. Also utilities can have been added or re-arranged.

We give some brief explanation now for each of the utilites.

### Inverted File generation
  
Normally ABCD indexes immediately and automatically any edited or newly created record , but often it is desir- able or necessary to have a database fully re-indexed. In ISIS-technology this is called 'Inverted File generation' since a special index is created which has more features and power than normal database-indexes (which are more like sorted pointers). An Inverted File provides a dictionary of searchable terms and - in the background when a term is selected - all information necessary to provide the related record, field, field occurrence and in the case of full-fledged (or classis ISIS-)indexing also the position of the term within that field occurrence. CISIS is extremely fast in creating such indexes, so running the process over a full database typically takes seconds or some minutes at maximum. Typical usage cases are when the FST has been changed (then full IF generation is mandatory to reflect the changes) or when a batch of records has been added into the database e.g. by ISO-import.

In the Central data-entry toolbar also Inverted File update is an available option under the utilities-icon; depending on the option chosen there, either the same utility as the one currently discussed is invoked or an older version running over the HTTP-protocol and using wxis (instead of mx) is used, resulting in the same index but (much) slower. This utility in fact creates a command-line command and sends it to the server OS to run as a batch-process, only returning to the interface (the ABCD screen) when the process is finished with some result information.

The interface of this utility is quite simple :

-   a selectable list of available FST's for the given database
-   whether or not to use the special /M parameter, which means that if used (default is NOT) no proximity para- meters are included into the Inverted File; this speeds up the process a lot, results in smaller index files but disallows the operators of 'distance' in between words, rarely used anyway. 
-   The 'START' button to launch the actual process.
    

An example here is shown for the special 'Digital Library' database 'DUBCORE', where the special `'FULLTEX- T.FST'` has been selected and the /m parameter is indeed used :![](https://lh6.googleusercontent.com/aP1NR5FZgTWgkoX-pPIaZeVephzCZGoezler7zDVEwZg9ekbr5Ih8PM0XYv5kDSuWcsUVsmy8UCVAx6IbdaMaYu9JR05ij_Qy7D0FvrZEP5yBCMhspOUQuqgif6a92bccEAHyafW=s0)

  

The result is given in detail, including the actual parameters used in the command. This might allow you to find out what went wrong if the process was not successful. For example one can copy/paste the command-line to the terminal of your server, run it there and probably get more feedback on the problem.

The process finishes when the following feedback is shown :![](https://lh3.googleusercontent.com/eW350R_GPsc7KRKS9kHs1PuiBS0KphNRdu_jkxXp6hMUZx7iyBRIC43HA6bl0r0FsPHG4tr2UAHsFM-dHxBJS5yRoHMngTClfUD8nG_gMkAbJSsFkJL2h9M3RWvcZ4FQJ38j7-Y-=s0)

 In this case of the Dubcore database, we note the following :

-   a special version of mx has been used : `/opt/ABCD/www/cgi-bin/utf8/bigisis/mx`, which is the 'Unicode BigISIS' version as that is the one used (and this has been indicated in abcd.def and dr_path.def of the Dubcore-database.
    
-   a stopwords-file was found in the Dubcore data-directory and therefore used :
 `stw=@/var/opt/ABCD/bases/ dubcore/data/dubcore.stw`  
 
 -   since the database is identified as being Unicode, the special actab and uctab tables for UTF8 were located and found and also used :
    
    uctab: /var/opt/ABCD/bases/isisuctab_utf8.tab
    actab: /var/opt/ABCD/bases/isisactab_utf8.tab

-   The full command used to generate the Inverted File is given, so the preceding elements can be recognized again in this command :
    
```
/opt/ABCD/www/cgi-bin/utf8/bigisis/mx /var/opt/ABCD/bases/dubcore/data/dubcore fst=@/var/opt/ABCD/bases/dubcore/data/fulltext.fst uctab=/var/opt/ABCD/bases/isisuctab_utf8.tab actab=/var/opt/ABCD/bases/isisactab_utf8.tab stw=@/var/opt/ABCD/bases/dubcore/data/dubcore.stw fullinv/m=/var/opt/ABCD/bases/dubcore/data/dubcore -all now tell=100
```
  

> Note:
>  The FST used in this command is not the default one
> 'dubcore.fst' but the special one which loads the HTML-text files for
> inclusion into the Inverted File, allowing 'full-text' searches.

For very large databases it is advised to run this process only when necessary and preferably run the same command on the server itself, securing the database to be locked because the process might take long enough to disturb users.

### Copy the database to another folder
  
This utility will copy all the files of the active database into a named other folder, e.g. as a backup of the database.

One extra option here is to 'reorganize' the database, which means logically deleted MFN's (records) will be left out in the copy to make it a 'clean' or compacted database.

The utility's dialog only asks to identify the folder with the explore-function (allowing to create a new data- base-folder if it does not exist), the name for the copy and whether or not to 'reorganize' the database while copying :

  
![](https://lh5.googleusercontent.com/OmykiJJByPVmqtGkrjvm0HTmVP2oIEay8DjSFjX44CX794iPEu-1lztD96cxsKrE0qbBVkjrO0z9oV9OMSM_oUfXOm7VOcoDnlRTue8DOFfU1fGacFkuU7roTi8wM0ml1-zrxQcY=s0)  

After clicking on 'Execute' the next screen will ask to confirm for continuation and then the last screen will - if everything worked out well - confirm the copy, show the executed command and offer the option to read the database contents as a final check - which is actually running the next utility described under here :

 > Note: 
> This procedure will NOT add the database in the list of
> available databases, as opposed to the 'create new database' option
> which also allows to copy a database.

  
![](https://lh5.googleusercontent.com/Q0LPdZxKkZQ2fTAwxSR3IoKXaPYyeAidPDXjaNGt1fIajdPxapOzfXu1zK_R7H67IEdS46x5I_XhQVL4AYYcz2a6rve4IEZjophejE0BIiz4GohSejsabwnpFsxTVyCo9EsIG69y=s0)  
  

### Read database/ISO file with mx
This utility is a simple one : it allows to view the contents of a database quickly, e.g. before using the database for other purposes (import e.g.) in ABCD. The CISIS-utility 'mx' is used to this end. The dialog will invite to identify the database to be viewed with the 'explore'-function to select a folder. All 'MST' files of the selected folder will be shown so as to select the one to be printed on the screen. Actual printing is by batches of 20 records with the option, at the bottom of the records listed, to continue to other parts of the database.![](https://lh4.googleusercontent.com/3TpxBQuJGaDF_n1FzfWhIlHmuEP9WozT8XNbcsX5uh3jTaQnAEv93T3Cu1Ud7DUtqMRWSkm_lUxszI-6hQAiKBRkWNHOU_3G4hz5mZdcx64iZ0T_UNoOgoTFdpXW0pDKMWWjmqUO=s0)

  
 ### Restore database
Restoring a database means to load a database with the records from a copy of the master-file (.MST), e.g. after such copy has been created with the utility 'copy to another folder' as a backup. In that case 'restore' means to restore a backup. If the backup MST was a 'reorganized' one, the resulting restored database will be a clean copy.

The dialog is again very simple : using the 'explore'-function select the .MST file to be used as 'origin' and after clicking on 'execute' that master file will be loaded over the currently active database. So be careful and make sure you have the correct database as the active one.![](https://lh5.googleusercontent.com/jfECc-HKjMnR9P_I1R9PKZmujdr4SwWJFpjvoUemGHiHLwfdX4PcDQGOJXAbwTFLqUXCqQMGf5MaJsa9myPyQocttzOggvzxeQP0_BRlUntXfLuHWwG1hTSyjaVcXUZ0uVA5f9_v=s0)

  

After the restoring the dialog will also allow to re-generate the Inverted File (= re-indexing the database).![](https://lh3.googleusercontent.com/Y2kSfOk8Q0AME2TfekDOrSRnCRfItiaUDLXp0lM5-PNV4rVxtyzMu4gocBUAXtZnzHJa-7ns6Pr5V9EqV4XDa6DdBKZYMSpCZo3TaD4K0-pOYzDKkn5NoJ9nC-S5txk_pjzPknIO=s0)

  
### Initialize database

Initializing a database re-sets the existing database to 0 records without changing anything in the structure. So it is equivalent to making the database empty and literally 'restart from zero'. Since this is a non-reversible action a confirmation will need to be given while showing the actual number of records, even twice to avoid doing it by accident.![](https://lh4.googleusercontent.com/FgLVdHPn3WcvzX8b6a6OigwgGDq85xTAwP59GUtLlFmIM87JRQMINzeS9SYXvQaC5zT2uktv-39sTC0fvjinklriFvOZagfZSk-YYeUAFye7Pn7VxzQ7SZiA8XnaRNWXMzm3FLx5=s0)  

  
### Delete database

With this utility the active database will be deleted and no longer be available (removed from the list of available databases). Since this is a non-reversible action it will ask for confirmation followed by a 'confirmation of the confirmation' dialog to avoid any accidental action because 'canceling' the action is still possible at this stage :![](https://lh6.googleusercontent.com/cxG-uoMJU3mw1_DX1dnD69q3DjREhXrFl5n2UNRNw4DNRlUhOTir0zb1ojkpYoX6M9db0rMTs8o9c4SG_JTkNzoYCecxfyzE0jf6Twt1qTz1yI9J1sAKgSjme49A_-rmkEFhlXc4=s0)

### Protect database from initialization or deletion
In this utility the active database can be either protected or 'unprotected' from deleting or initializing, in order to secure a really important database.

As a consequence of protecting a database, trying to initialize it will result in the following error message :

  
![](https://lh4.googleusercontent.com/c17hGge8wLlFyPXMVruSbTO8BJPhBoFob_aDVUC88_TCDc37nqqV3sxZw-ZcCSs3Sn5IWWsqHoEcxcVN7vFoGtpVI2OqtMigPSYKEbCdzRle1oF3-ZV8Xg5hHqbH2BjIMv6P-lJE=s0)  

### Unlock database
In certain uncontrollable conditions, e.g. an unexpected power-cut, a database can end up being 'locked' at either the record-level (meaning a record was still open for editing at the time of the condition's appearance) or as a whole when e.g. the database was being fully indexed. Whereas the data-entry toolbar already provides the option to list and unlock one or more records (a range), in the case of the whole database being locked, another approach is necessary because no longer the operator can enter into this database to use the toolbar on it. In such case the database needs to be unlocked first.
![](https://lh5.googleusercontent.com/IJcpdKTsJquYxIjsl5T-aMMXRRlN4uDxEfCKjyd6wIUyoEMMXhtomEHnGheNSUB8BzKOqOKIFAlQLEqp0Me-43aFerL4wI8ZoCv3Rk4q8Iit9r5782ai5HKr8ssjLll2dQBM6Cio=s0)

  

The resulting screen shown above confirms that the database was unlocked with the CISIS-utility 'retag' from the non-unicode (=ansi) version of CISIS.

### Assign control number
In ABCD, each database to be used in a multi-database environment, such as a library catalog in a loans system, needs a 'Control Number' field as a 'primary key' or real identifier of each MFN. The MFN itself can NOT be used to this end since it is not a fixed element : it can change e.g. when exporting/importing (or 'compacting, reorganizing) a database.

  

This 'Control Number' (or CN) preferably is assigned automatically (meaning : defined as 'auto-increment' in the FDT) so that the software itself controls the assignment of control-numbers, based on the file 'control_number.cn' in the data-directory of the database which contains the last assigned number. In the edit-form for such a field a link is always given to allow manual assignment of the control number, overriding this default 'auto-increment' mechanism. However at times it is desirable or necessary to assign consecutive control-numbers, starting from the existing 'last assigned number', for a range of records. That is what this utility is for.

The dialog asks for the MFN-range (first and last) to be defined and allows the CN range to be reset to any other number to give full control.  

![](https://lh5.googleusercontent.com/e4P8ZZpzk9mCTpAx6oraLThXiJGbUe5kBoYqKJEe3HKXnmZZXV1Rgc2SqHZkU5_61YLMaXNgkdCAEmU2xTFGFt07QOEpdYsFGkHiCfjVgv3bFHG30kc4f4cjeOmKZmsRh76jSru5=s0)

After running the process the result is shown, e.g. in the case only MFN 1 and 2 were to get new CN's :![](https://lh4.googleusercontent.com/21sjJ5Nko0dFrcrQWvgc2SBEsyD6ThhYbhUEiJgcZK0zIaYT7TnbV9s-xADWW9BUv2TbnEg9fbLPdRj3nbREPN8UZin8QO5EAlR-sQml3KDnB07btqH0ksPjxWRaOGcEuCWyL7YP=s0)

  

### Create DSpace 'bridge' database and load repository into ABCD


This new function in ABCD 2.0 allows to copy the metadata and documents from an existing DSpace repository into a dedicated ABCD-database ('dcdspace', using the Dublin Core metadata-set). For this ABCD uses the DSpace REST-API in a 'web-services' approach. The DSpace community is changing a lot in this respect, mainly shifting more functionality to this REST-API, so this solution will need to be adjusted whenever DSpace has finished their process of maximizing their REST-API approach.

The automatically (i.e. by script) filled database can be made available, like any other ABCD database, in the Site and included into the ABCD Site Metasearch configuration, to allow users to search the DSpace repository along with the library catalog or any other ABCD-resource. The update of the repository in ABCD will need to be done by putting the update-script into a scheduler, e.g. to perform the update every night.

The script uses the CURL functionality, so this needs to be installed on the server. In Linux (Debian) it can be installed easily with the terminal-command :

    apt-get install php7.0-curl

 (or change php7.0 for php5 if your server uses PHP5.x)

The following steps need to be followed in order to use this DSpace-bridge functionality :
-   get the DSpace REST URL and test it directly in a browser to verify its accessibility;
-   [only the first time] create a database 'DCDSPACE' using the existing DUBCORE database as the model; this is very easy as all DUBCORE structures will be copied into a new directory bases/dcspace and all files renamed accordingly in an automated script;
-   create the extra option in the UTILITIES-menu : htdocs/central/dbadmin/menu_mantenimiento.php by inserting the following code in the function 'EnviarForma', as one extra 'switch'-option :

```
switch (Opcion){ 
case "DCDspace":
document.admin.base.value=base
document.admin.cipar.value=base+".par"
document.admin.action="dcdspace.php"
document.admin.target="" 
break;
}
```

> Note:
> This has already been done for the Utilities-menu of ABCD 2.0, so
> only needs to be done when building upon an older version.

-   Only when the 'dcdspace' database exists and has been selected (!!), the Utilities-menu will show the extra option :
    
![](https://lh6.googleusercontent.com/36zdeFgepT856VdQ0T4xfdDy8W7NY4_3-aqOZeYVCprZmkOAbXPbYj1XUp_zq4P89qF38SVTSJke6HZwoX75j217YEk7ZegjIku5nuUhyjQABrW85bjmJ9_yNZQOYctJwuJArxzQ=s0)  

The interface for this DSpace Bridge function is rather simple :

-   First a screen is presented with some basic explanation, the URL defining the source (and if necessary the proxy- settings) and an option to 'clean' the database before loading new records, followed by the 'fields mapping' area, in which the Dublin Core fields can be 'mapped' to the fields of the local database, which by default is the very simple straightforward list of fields (1-15) of the Dubcore demo-database; but note the non-standard fields v97-v98-v111 to store e.g. the source-URL for the full-text PDF - note that this is not always available in the source records :![](https://lh4.googleusercontent.com/w7526zqQnoiuOKsC3dEJq0l5dfnwyUvPvUAPIQ_BOtplQaMlV9G1IQisCsSRh_LNFWkSnz_gVCgYNbAliDI9F-SqfDfrjEKcPSdIMl0UFMdXWbPeAUYXeusTvYY3kaydVnAY97wM=s0)
    
-   When in the first interface screen 'Run' is clicked, the second screen will show the progress and a listing of records with their fields,  
    

![](https://lh5.googleusercontent.com/swvHiC5ywzun4gEWSTheDWfR6EGGya3KF1If-mWWRVj0-M1dU8lE_SjqYZfvcXvl-qVFjIShbGupGJQ3fv5Dujw4kmpkGBkTNV-KXkZzNEDsGFlGWcn8aDnWTxDkikZ23M6teXPn=s0)

This process can be stopped by clicking 'Stop' at any time. Depending mostly on the connection and server-re- sponse speed (which can vary a lot even during the same process) this process can take some time.

-   At the end of the record-loading process the interface returns to the first screen from where also the 'BACK'- button can be used to return to the main ABCD menu. Entering the DCDspace database from there will show - in the usual standard way - the records downloaded, including the hyperlink to the full-text if that was available. An example record is partially shown here :![](https://lh3.googleusercontent.com/MW1nDK_0IEGYHEC53WWfnW6_48CF81S2ABBqGbnjHTyJxvsqzX05QkJoHwKFcVX8wlxucVp74iw8zCUigZImggU-IEYmIW4LsJfl83TFsi0evWmKsUMnVcQ0eqV4JTYLgXC8K-ha=s0)
    

As mentioned before : this database can further be processed like any other ABCD-database : indexed, creating new/other display formats, inclusion into the metasearch of the ABCD Site etc.

### Explore databases directory
    
If in the Central configuration the option 'dirtree' is 'ON' (or '1') and the operator has administrator rights, this option will appear in the utilities menu. There are some security issues to be taken seriously here because the dirtree- script (which is not an original ABCD-script) allows text-files, such as configuration-files etc., on the server to be deleted and edited ! This is a very advanced function with many possibilities, including uploading files, so to be used very carefully.  

First of all, the utilities-menu entry allows either to open the whole 'bases'-directory (highest risk level...) or either the special system subdirectories par, wrk or [www.](http://www/) Only the contents of the selected directory (or folder) will be shown.![](https://lh5.googleusercontent.com/tndv9sYNqM9--qGb4GwilcZ2Z-K06A0xw1H6VstuZdwVRoBAYNnF9a094pnhQm_f7b13eX6C-L-PznvTfogt-o-WMatqGODrhwZmyDjxt08vh_MYp9YnSuqy_iQGpYYnOefxdUMh=s0)

  
Depending on the link clicked, a file-browser will show all files which are not filtered out by their extension. The list of extensions can be edited as well within this utility. The illustration below shows a segment of the file- browser at the level of the 'acces'-database, inside the English definition directory where e.g. the file 'acces.fdt'

has an icon to download it or to view ![](https://lh4.googleusercontent.com/KquKoYU1h7aHn3Xd93sjvqbOWYqWdpfg_2EsXcpi3wQyz1cKxeyrbHsc6Xnv_bjFhOjlK4EeomotVP0rexy6ti_B56L7Grp3R471EqD-kvlxBDpXE6nZdi2JW_MLfESVhcK6CcQk=s0) it - from where then also an 'edit'-link will be given.![](https://lh4.googleusercontent.com/C0x-B5BoSGD6pFA8a3yv1FJFOYYt6kHNACXLCxDcv1foQ_YfvW9vEnDcQILbzXgcTIWthUxbnhZVjwG_DCBXdI6J1jhdiYMwahCAEiHQ21a0wbKbo5QnjQCbPEsObSJU7rIdog54=s0)![](https://lh3.googleusercontent.com/5faDAeFvSxlS0epLq3zm-WeDVuNy4yHjorWRc3ZCwNdeZWb1Xe7zbDRZoNWkvx3peuCvulesBj04DLJ91brlYySfKgmF4VtIeomtM_EP9aEU-ML2Cqu1Pp1Dk_Qo4mFUaEHVdw9O=s0)

At the top of this file-browser there is a link to edit the extension-filter, meaning only files with the listed extensions will be shown.

![](https://lh5.googleusercontent.com/8i8DfVO3-bvuqN2sik6IykJx7YsYKhoBzadRTAAvyMYHBU0LhgMGkHv7NuKLMPQh2PIhwzaQU5QdonORdKClk8v4abuqWWOmDSE6uyOtIR6NlYosl4EaOP9CrdOZGgeyc9kLk_2-=s0)

Clicking on the link for 'File Filter' will give the dialog below, where the list of extensions can be re-defined.![](https://lh6.googleusercontent.com/ZEKv3oiusQkVYLUgxPJr3ign4jMJKCWYKeGq0n63DlrFTfccoo28Ks5rtYbPNl93JFtKSgYmhbViBTFSQhHwR80yTvmgnAOQXeNk75yJBUH52IMazsMdGcgiOBws6Ma_g4-KIMiz=s0)

  
### EXTRA UTILITIES

Since ABCD v2.0 another batch of utilities have been presented separately in an 'extra' submenu for utilities which we will discuss subsequently.

## The extra utilities menu

Less frequently used or more specific utilities are listed in this sub-menu :

Figure 2.2. The exta utilities menu
![](https://lh4.googleusercontent.com/tGUJ3lIdZhiYOstAHj2admE5wwb4kGTrQnMefZ3vZ0huOHcppg4bYyRICVsYe9FiJoyZw7EkfiyU6m9imdsFEE_7SO6XCWJErrS04-fxmvYaOvTgkOQpd0mZA2bswkfpq6UBT6-2=s0)  
  
Let's look a bit closer to each of these.

### Documents batch import
    

For this utility we refer to the more detailed discussion on 'Digital Library' in ABCD (section 9 of Chapter 2) since this is the main script used to create databases with a 'digital library' concept to use full-text indexing and original-document linking. Together this script and the utility 'Upload/Import document' (see later in this section under 1.2.7) constitute the ABCD 'Digital Library' feature.

### Add to loanobjects from catalogue

There are actually three similar utilities addressing the batch-creation of loanobjects, this one (1.2.2) and the subsequent two ones (1.2.3 and 1.2.4). They partly overlap but have different 'optimal' use cases, depending on the exact situation of the initial records from which the loanobjects need to be created.

With this utility it is possible to create a series of loanobjects directly from a catalog-database in which the nec- essary fields are available, with the special option to create a fixed number of loanobjects.

All three utilities assume that the information on the loanobjects, which are physical units contrary to the catalog records (which are intellectual units according to the FRBR-model), is available somewhere in the catalog records.

E.g. when you create a catalog from a '.mrc' (marc21) export, like from a *KOHA-library* catalog, the data to identify the loanobjects are in some extra fields of the marc-records. The assumption is that the current active catalog-database still has these fields present in the records, e.g. these fields were used in the ABCD system set up for operation without copies/loanobjects - which is exactly the idea of having the copies-data in the catalog-records.

For this utility, the first screen, shown below, deals with a series of parameters to be checked by the operator of the utility. These parameters will define the range and from where to get the information to put into the ABCD Loanobjects records' fields :![](https://lh5.googleusercontent.com/pB_BOUr-LIJcR-S0QaGDoyxnnq-wen-EO817-bvkP-iOP1QzlsYG3DRd59j426T1TaXU2JtdslMlyE2keS-lEp5qYv2fi-Rz8QdpRMyhOnPeRGF5EM6AoMXeSkUcXZmmshK-iQI5=s0)


-   From : the first MFN from which to create a new loanobject
-   To : the last MFN from which to create a new loanobject, with the last available MFN in the database shown
-   Field for barcode : the field in the catalog-records which contains the unique identifier of the loanobject
-   Subfield : if that identifier is in a subfield, identify the subfield identifier to be used (without the caret ^)
-   Control Number field : the field which contains the Control Number of the catalog entry
-   Number of copies : the maximum number of copies/loanobjects to be created from one record (which supposes each copy is identified in the catalog as an occurrence of the field)
-   OR : if the number of copies are given in a field, the field-tag (and if applicable the subfield identifier) are to be identified, so the number will be taken from the value of that (sub-)field
-   Type of object : the 'loanobject'-type (as defined in the circulation system) to be used for this range of loanobjects
-   Main Library : the main 'location' information, mostly the name of a library or library branch
-   Secondary Library : the location within the main library to more exactly specify the object's location, e.g. a shelf no. or classification code

It is very important to have made - in advance - a very good analysis of your original 'incoming' data, in order to know in which exact fields and subfields the copy-data can be found. In general there will be two different 
'models' : one with the copy-data repeated in a repeatable field of one record, and one with each copy in a different record. We give examples of both situations under here.


1.  copies repeated in one field : e.g. exported from Mikromarc software : in the one record shown there are 3 occurrences of v99 which has the copy-informaiton in subfields (in which exact subfields comes which exact information is to be checked in the original software !) :![](https://lh5.googleusercontent.com/jjmnAO0fUQiMEJwVf29rBnpgNVDk-mqZPYfHqRETbfb1_bXWjBTJiPRufaEQWn1R_6xZFMzD4IwywZyAgjserw2ufV8tiZT2CmmpQnxoeiHhRgfAzJgWHgHAkGu4CKC7Y72PWlk6=s0)
    

2.  copies repeated as subsequent records, e.g. export from a *KOHA-catalog* : the example shows two different MFN's in which each a v952 contains the copy-data in subfields and `v999` contains the `CN` in both `^c` and `^d` :
 ![](https://lh4.googleusercontent.com/dW6IsLOPARFgFCPoXrKwAubGL2qHmKa9yvJ3QUeiUD6qaFC8D8vbWQ57-PqUneCCoXLO6WOCVxYS9nFWc47-iULLn8XDSjBf-0OJnl5zYkYcHoYukZpIwo-WGN1Mq9csnyFn57f0=s0)
    

> Note:
> The previous illustrations were created in a 'terminal' window
> with a CISIS-mx command which converts the typical '.mrc'
> subfield-characters to the ISIS-subfield character (a caret or ^) with
> a gizmo-database 'sv' and in addition specifies that the
> 'leader-fields' should be presented in the tag-ranger of 3000 :


    mx iso=marc=koha.mrc isotag1=3000 gizmo=sv

  

If everything was properly identified, the script will run over the range of MFNs of the catalog database and report the number of loanobjects-records created. In this case 3 MFN's were created since the 'number of copies' was fixed at 3 - of course a more interesting approach is when the exact number of copies is noted somewhere in the catalog-record, so no fixed number needs to be created.  


![](https://lh4.googleusercontent.com/oCeqh-yJ-VL5mShRTvKLqROa4Ab-78EHgdiiGPS9pcy0v3qDTYT6uC3x5DNhfzoJAND7RvsNn_Fwc7Y4DGxSkvp6VvRDWVlAbVU_5hfb0HphrxSNpe9YKmDsI7TpCznzim7ZtTeB=s0)

 

### Add to loanobjects from catalog (not using copies database)

This utility is a more general one without fixed number of loanobjects to be created, so the related 'addloanobject- copies' script is meant to create the loanobjects records stored in the catalog database without using the copies database. Let's look at the dialog to be filled in before running the process :![](https://lh5.googleusercontent.com/5CEu1ieTj9msSaY302v46ykK9UYThljkhqJp_PYbyN6KsZOZrjRmLLkqUr4HEUtn6ny5m62_POMV5IHGu2FNLQyGGW2jMGvIVR-oxj0vscHFlug1MUOBcxxzmss4KXGkMQE_hbVH=s0)

  

As can be seen, information needs to be specified on the range of MFN, the (sub-)fields for CN and Inventory No. (barcodes) and, if from the 'ADD' menu an extra value needs to be added to the loanobjects (main library, branch, tome and volume/part), for each of these also a value can be given. For the 'loanobject'-type either one of the system-defined values can be selected from the menu, or if 'use a (sub-)field combination' is chosen, the field (and optionally subfield) which defines the type of loanobject can be given by its tag.

Clicking on the 'UPDATE' button will run the process over the selected range of MFNs and report the result.

  

### Add to copies and loanobjects from catalogue(Using copies database)
    
When a library prefers to first create all 'copies' (or acquisition/stock) records for its catalog, at some moment it needs to also create the corresponding loanobjects in ABCD, which are differently organized (as explained supra) by having all physical units (with their barcode or identifier) repeated in one field (v959) rather than having one individual record per unit as in the COPIES-database.

This script allows to create a batch of loanobjects from an existing copies-database, in addition to allowing to create them directly from the catalog (as in utility 1.2.2). The interface is similar to the previous one (1.2.3) but the built-in options 1 and 2 are rather different :
1.  Create both copies and loanobjects records from the existing data in the catalog database : fill in the inventory number field
2.  Create the loanobjects for a range of existing copies-records : don't fill in the inventory number field

The 'ADD' element of the interface now allows to additionally also insert all standard fields of the COPIES- database and define from where in the catalog-records to take the value. So this is optional and depends on the availability of such information in the catalog records.  

As in the previous tool, also the loanobject-type can be either defined as a fixed value selected from the system-de- faults, or taken in a variable way from a field/subfield of the catalog-records. Again it is important to carefully analyze the information available in the catalog records !![](https://lh5.googleusercontent.com/Ae9HOl9sWQ9xTDFaqn6JrMCDkPp2JX12LJMkbGeHSdQ7tX_lxRX5J1TBJQD8023h5iJ8zyEOae-_StHBXT9It5yZyT7R5Gz4ZqPDGuXIh01-leYSet_xiHkEGhp6eftA7EI-IK0m=s0)


This utility, as does the previous one, uses an 'mx'-command sent to the OS of the server, so it will perform its task very quickly but without client-server communication and protection, meaning that if the process takes long or hangs for some reason, no feedback will be given. So use this type of utilities carefully, i.e. after first testing with a very limited range of MFNs and checking the results, before doing the full range. However once carefully prepared and run, it can save an immense number of work-hours for the manual alternative.

### Import ISO with mx

As a faster alternative to the ISO-file import in the Central Data-entry toolbar (utilities icon) here is a tool to quickly import large numbers of records. In view of the HTTP-protocol interaction in between server and client, the dataentry toolbar option needs to do this in limited batches (of 200 records e.g.), here there is no such limit but one has to ensure the server and database is ready for the job. Taking into account the fact that mostly this process just takes seconds, even for large databases, it still can be a very handy tool.![](https://lh4.googleusercontent.com/7YZq35RN3HfiTtBRLV6OeRiVIe0vbvooy0CjmX37HemdAXPAESFHpdKDXfOd2jHLi6-agrd4uCdq0xL21cnWfUOV1Z-wcWBU2zmj7VAEU2OTcMgnKAs8gkTH3u21Mr-jg6MtnbWE=s0)

The utility requires to select (with the default ABCD file-browser) the ISO-file to serve as input, to specify if the incoming records should overwrite the existing database (create) or be appended at the end of existing records, and finally whether or not the ISO-records need converted from Windows to Linux. The ISO2709 format is a text- format and in Windows uses different end-of-line markers.

### Export ISO with mx

This utility is very simple : a command will be created and run on the server to export your database to ISO2709 format. This utility simply takes the active database as a whole.

The only additional option here is 'use MARC format yes/no'. If yes is selected, the MARC leader will be exported to the 3000-range of tags so as to be included in the ISO-records.  

![](https://lh4.googleusercontent.com/0JxsKAYxqiv7GbXTpLdh1CgC9UaIDYhh7FZ_V-w5n9Tabx1GOwIvpg1aUay351FSmFJ5pgnF4V5TUI0c6lx_jZjzZrF2cALQDYXNmnmH-hHr7Dd_BZbdzgv7zv_fp6VfuDiWlnB_=s0)

  
### Upload/import document

When your database has a 'Digital Library' style, e..g the 'DUBCORE' demo-database, documents can be uploaded and linked to the automatically created metadata-records. This principle and technique is described in detail in the section on ABCD Digital Library (section 9).

In fact there are 2 utilities used to implement this 'Digital Library' feature in ABCD :
1.  a batch-tool to convert the typical document-formats (.docx, .pdf, .odt etc.) to HTML-text-format and load all words of the text into the Inverted File; see the discussion in the Digital Library section (no. 9) of this manual. With this tool a digital library database or repository can be created from scratch, but also a batch of new incoming documents can be added to the existing database. New records will be created with both metadata, full text and the link to the original document;
2.  this 'interactive' tool which allows to select one or more documents individually to be added into existing records or at the end of the database. If selected from the Central Data-entry Toolbar (the icon appears as part of the toolbar ![](https://lh3.googleusercontent.com/oG7Fmq7G1SDh8_rGMV_PDT9UCFC-8Bpzo5idcxx_h-Rx8MJgOveMV2lkUufTlyZ7xQVlqVmqFWi3_iNTpOBuCxgSycfFwCuLyaAkN15x0Q7AwG99XLk5V3rf-R77gb1qpQ_2rb03=s0) if the database has the parameter 'IMPORTPDF' set to 'Y'(es)) this utility will add the document to the existing active record, otherwise the new record(s) will be appended to the database.

The interface runs in several steps, in fact only adding one step for selection of documents to the batch-import tool :

![](https://lh3.googleusercontent.com/zsa_roWj0FhJ5r1_IgIzqoNrmxRPX01cyG42CQ5hBP6mxpfvHMPaxXd56nZ8VmJvgWpEvTZ6z3jAI8r8Ux294Qd19A67op0REuKFd3pW7sLq13I1ZhTUZ0HbMOaWe4uJWzANvvgy=s0)  

1.  First the defined 'collection' directory for the active database will bes shown and the documents to be uploaded will need to be identified with the default ABCD-filebrowser (more than one file can be selected). The COL- LECTION-parameter in dr_path.def defines the destination directory.
2.  After having sent the documents to the server (3 selected in the illustration above), the 2nd step will ask to 'map' the metadata and text-fields, exactly as described in the discussion of the batch-import tool above.
3.  Finally - again exactly as with the batch-import tool - the process progress will be shown with the final infor- mation about the result.
    
### Clean/compact database
Cleaning or compacting a database is the process which gets rid of logically deleted records (or MFNs in ISIS). Whenever a record is edited, the reference in the XRF-file to the old version is deactivated and a new one added to the new version of the record, so after some time lots of records remain in the MST without actually being used. To recover this space, the tool will quickly export and re-import the records.

This is the simplest possible tool with no interface at all, except for the result screen which shows the two com- mands executed on the active database on the server :

1.  the export command
2.  the command to re-import the export created in step 1.  

Note that the temporary export-file is created in the 'wrk' database-directory as we need to ensure there are writ- ing-rights for that directory.![](https://lh5.googleusercontent.com/THYSSPIHRm0yikifSdJHtxSqWaKqoG4rfYXD3PVytdZlqUM26wsib_RZLXkXTzLBJTTsGXOh1RJfiWIbYiIF5pp_qSRitHAo62eOyw79f6K5soC0FmyW-64-QTMw-lE68bwmxbjs=s0)

### Barcode check
    
This tool is supposed to run from the LOANOBJECTS database in order to check whether the barcodes of the loanobjects-records 1) exist in the copies database and 2) the related title exists in the catalog. So this option will only show up when the active database is named 'loanobjects'.

The idea is to simply scan (or otherwise 'enter') the barcode of a book in the first box and - given the name of the catalog-database and the CN-field - click on 'SEARCH' to see if the result appears in GREEN (=OK) or in RED (not OK). So this tool can assist a 'stocktaking' effort but in an interactive way : librarians walking along the shelves and checking each individual book and correcting when e.g. a copy or title is missing for an existing object in either the loanobjects, copy or catalog-databases. In this sense this is different from another procedure for 'batch' stock-taking which is described in another section of this manual. In that procedure reports will be produced for all existing loanobjects to see if they exist on the shelves (as noted in a database with barcodes) or - vice versa - a report listing all inventoried barcodes (in a very simple dedicated database) with information on whether yes or not this barcode was found in the loanobjects database.

  
![](https://lh3.googleusercontent.com/ClgBpA-YnDFMIojiRVXfQm6Ob3YGf3ze7anH2_ffWEX-ULXqWDoH6423cSdzrzKQWDVQwFyCVhqRyoUSbn9moH66LXTXG-KXlhsf7eduivGg40zHzCFQxovNYl_5pyV9-TgTVe8n=s0)  

The illustration above shows the result for a barcode 'x12345' which was NOT found in the LOANOBJECTS database. Since it was not found there it can also not be located into the COPIES database or MARC-catalog. Once created in LOANOBJECTS, the check can be repeated to see if a corresponding record exists in the COPIES and MARC database.

### Convert ABCD to Unicode

To assist migration from ABCD1.x to ABCD2.x with the Unicode capabilities, two additional utilities are avail- able, to convert from ANSI (the 'old' classic ABCD) to UTF8 and vice versa. The interface is the same for both scripts but the 'direction' of the operation is the opposite.

  
![](https://lh6.googleusercontent.com/upDp23kYWhyk1tXWNE4ZFMluuG4fmWZZCgKSP6rBZn6C6N4a-VUWfLl1Oa9e8Hwh2lCfF_TAkR-f2abgkoH98oRF_flA3_fYWNw1EUeX17amsdVqXEBfsUBjGzZ55lAyCNFc5SyL=s0)  

Beware : this conversion does NOT convert databases, only the text-files of the system. So the first option 'Convert base marc' of the illustration above means to convert the text-files of the database, i.e. the files with extenstions FDT, FST, PFT, STW, DEF and TAB in the 'def' and 'pfts' subdirectories of the database. This operation will allow to use non-Latin characters in e.g. print-formats or field-names, which would otherwise completely disturb the display if kept in ANSI.  

A separate option is available for doing this specifically for the 'operators with passwords' database 'acces'.

The list of extensions allows to select/deselect specific file types. In most cases it is best to leave them all selected, as there should be specific reasons to leave out one or more from this process.

When selecting the 'htdocs' folder the whole series of text-files with the selected extensions will be changed from ANSI to UTF8. For instance help-texts in iAH in HTML-format can be changed to UTF8 to allow non- Latin content etc. An important folder here is probably the htdocs/bases/documentacion folder with help-text ('documentation') for the databases. They can then also be written in the local alphabets of the users.

### Convert ABCD to ANSI
    
This utility 'undoes' the previous action and is indeed converting all UTF8-marked text-files, with the selected extensions for the selected system-part (bases-folder for the active database or the whole htdocs-directory) to ANSI. This procedure will only be needed in very rare cases and assumes all non-Latin contents have been removed (or were absent in the first place).

The tool has the same interface as the previous one and results in the same detailed list of the file-names of files which were not-converted, which were converted with unknown previous encoding and converted with known previous coding.

Be careful, e.g. lots of .HTML files exist in htdocs (e.g. plugins for Secs-Web, so it can take a while.
