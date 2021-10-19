---
title: Módulo central - entrada de dados (catalogação)
description: Nesta seção, discutimos brevemente as principais técnicas de uma das funções mais "centrais" do ABCD, criar registros em um banco de dados (em aplicações bibliográficas, em sua maioria referidas como "catalogação").
lang: pt
lang-ref: abcd-modules/data-entry
---

# Central module : data-entry (cataloging)

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---
 
In this section we discuss briefly the main techniques of one of the most 'central' functions of ABCD : creating records in a database (in bibliographic applications mostly referred to as 'cataloging').

These frequently used operations for catalogers are grouped into one 'toolbar' on top of the screen - in this way ABCD tries to imitate a 'local desktop software' behavior.![](https://lh5.googleusercontent.com/enveLRJHTkYBpkH9l5-M2uukoUjLbxv5ZVxrgmXGlueoXpyAYMxmiS4Mxm6FwRBr3ZhurqrxtQjP9LzcF7n8zC8BPiVthiVAP8wtfUHBLnbkQ1hSz3dXakOS6c8UxGlRXa53nrqD=s0)  

  
The above shown toolbar is related to the database. Whenever a record is shown, a second smaller toolbar will be shown which contains the buttons related to the current record :![](https://lh3.googleusercontent.com/mwCcNvQpHOJjtbkMpbdtHYY_sggNPv4alQ-XqDrLZl9D8AAtgoWr0xom1WxpxND_WIgKq0lSuuHK_c5s6HJDJ3COnDZYVQmRuZSdKlSdeaKbnE-jZhiMybW2MpgEhaxoyNk9ucOW=s0)

We will discuss all functions of the toolbars here briefly, going from left to right.

## Browsing records
    
There are 2 ways for browsing records :

-   either by entering the record number (MFN) in the dedicated box![](https://lh6.googleusercontent.com/emHTVDt5x4-uJO7zO-ZostzW1A9NIrHv6CmHIZrP_OwPvHjHlCC6leDtnkvnB2y5MP1Lt3OCenm9QIvSk3gODJWBuDA_DN7Wiqf49GuqrYi_NN3QQ_Jfv6FY4heuF-E9rlsU3FVn=s0)
    Here you have to simply enter a number from 1 up to the highest available MFN in the database.

  

-   or by clicking on one of the 'navigation buttons' to go the the first, previous, next, or last records![](https://lh6.googleusercontent.com/Bq7AHS3i_J-z7nvVjxBi6krrRMHK098i4WUd2NoHII05Yiq4xp8nzjpwNhapLowWY2eejYfuO_-Cq7Ws8P9UmGH-2SXcNjeJhojRaCgunkWG4aTTkX4QG5L-zNU-EHpfoY5ob1aa=s0)
    This navigation will be done either in the full database or in the search result set, according to the selected option in the adjacent menu.

  

## Searching records
    

As with browsing, ABCD offers 2 main approaches to identify a specific records for catalogers : by either searching or by selecting records through an alphabetic listing (AtoZ)
 ![](https://lh4.googleusercontent.com/6vDCBNQDd_4KLuaDHC7Y9kVPO41KuM66_SXtkgapa2E0DQCR753dXmVwFb15l7jnRMdxFfuTTu_1sttx1Q9UYYx-tdmweEcKqsmU7XKRH3fLwbdQektmwMM-6RivGzi9P3kxzMnr=s0)

by performing a search with a powerful search-function built-in into the database administration module, re- sulting in a real search-form presented (as defined in the 'define search form' function in the main administration menu) :
  
![](https://lh4.googleusercontent.com/kgo0wI_oIKFxaFkIXCqdxObFTdd6t-emz7mbx-p9nmZ_NPvCX8bcjzUJfNpp67USFjSBZVocYnNQFo9EN-1vQx0qN24GaRJRgWADaC8gwCLk14Cj_wZOPVU01WBcmDXlNg86sLFC=s0)

Searching this form is done as explained in the 'advanced search interface' section of the OPAC, which indeed uses the same form.

-   the A to Z selection tool  
    

![](https://lh3.googleusercontent.com/FoQsNh_sPLJF2DOEq4CHIj3UgWCL-yW3Yt37-ERX7fYjyiirdDlLmiHCGxsotbFi7F4I_sJCdi3Ut1AcIf8iHjC8wUzgLJXrOlcf0XuKbLgmr9MmNIgtfebXYYOh21h8GKzATTd9=s0)

 Clicking on this button will display another, small window in which all records of the database are listed according to the field identified as the 'Identifier' field in the database definition table (3rd column 'I'), mostly the title field

e.g. in bibliographic databases. In this list each alphabetic section can be clicked on, and after clicking on the relevant line, the record referenced to by this line will be automatically presented in the main window, ready for

e.g. editing. This nice tool extends, as we could put it, ABCD all the way up to Z !

![](https://lh4.googleusercontent.com/Gah_hVp-dQNlBTyE7NQTPSmjBmjNZTx-vDV3o9o_DYZecgGxbrhQkrk0SwJRppdkSdXhk4h_k35_IIGuC3KNYn0ilT3iuQ4W6qQ3EfYEvhHK2cVoLfpwIG91MqN4HjvslNhxQ3GU=s0)

  
## Using the editing forms
    
[!!] When clicking on the first icon of the record-toolbar, the record will be presented in an editing form. The same form - but empty - will be used for creation or copy of a new record (from the database toolbar).

> Note:
> In the case of MARC21 and CEPAL databases, whenever editing a new
> record, first a selection has to be made from a list of possible
> record types :


![](https://lh6.googleusercontent.com/Rq4b3rvw_kAR24UPoYfKVwIkE4Pxvx6iMPTEsfU7nvaxcKJ7OGNGLZhrE-NT_ZXk88qEVFn0OpjUjYRCj0dEq0Q9q4amNYaAgLsh3Yr-qvVNfT1wzIAP-J3wxaKgsFHm_PgyiHBZ=s0)

  
Selecting one of these (i.e. clicking on their link) will subsequently invoke the right worksheet with some pre-defined values (e.g. for the 'fixed format' MARC fields).

[!!] The MARC-21 edit form, with its long and complicated structure, will be presented in a special way : form sections can be 'collapsed' or 'unfolded' by clicking on the +-link of the according section. The details of the section will be shown or hidden. ABCD implements only MARC21 at the 'minimal' and 'national' level, by doing so it provides suitable levels for both larger and smaller libraries.
  
![](https://lh4.googleusercontent.com/2CRPS_C0nr9d487Ebh2kipuBszK2oOvooi2fME6M9GEzBCZTidNCwWQRqfVCL0Jl0HBgKBit-LhUa9JBNiUfe-DNGdQGliY4A_lhK2RcZKdyBNXeGmRSC-tcpAXsBd3BQ1axlWgL=s0)

General remark : depending on how the Field Definition Table of ABCD, which in contrast to the one of WinISIS also defines worksheet features, was designed, the worksheet can appear as divided into sections with direct-access links (buttons) and buttons to return to the beginning of the workshe et for faster navigation within the worksheet.

Fields for editing can have one of the following formats, each with their own way of dealing with them, briefly explained below as follows :

-   a simple editable field, [!!] as in the ISBN- field below, where you can only type in a value (e.g. ' ^a8570251270') yourself

![](https://lh6.googleusercontent.com/qnKWTeD2qEEyTkIq6NdoXrQsk3NoIrhY3f156kfGI6JCWV131aRCIg09vBrgaWG1pgzoNHNgZkkSycdtnKkkQJQrKZNEvKnHTWQXAq5TiuvVSUUAgi9ObAd6X-hKWXiRwUtiXq-6=s0)
    

-   a field with a menu from which a single option has to be selected, as e.g. 'monograph' as the bibliographic level :
![](https://lh4.googleusercontent.com/Tir3_VlQN45zaM3W9GBYD_mIZKA9dzdFycUqDnT1jtMJqlta8Ta9WWl9K6b4dCdDHmGiOcdl0tiIHFJlAfntu-oeNlD1QZkd_Adtayns8qRgOlDqnWVVViYk-Y8hkiaDIAAlyzr_=s0)  
   
![](https://lh4.googleusercontent.com/fXYfQSsVCHkeFDjz8etxLm9dO61cn_7koiobm7Dd-8FEVa5I9wIt4oT4XGzgAusKNzEnxqy8zynVJpSA2dvyfo2DNd48_23AjB7KBua-yCYiWLURSLGt4eGkCFxD48wpQLCCmc7a=s0)

a substructured field, with a button  to give access to a separate window in which all substructures (e.g. subfields or parts of the MARC-fixed header field) can individually entered.![](https://lh3.googleusercontent.com/CTpA_WhA4hH4DctcDwf5g9KULP7-ZLRdzrrj4csK0Jf67ijCMTM-nzZ6yVi6rNaVZ44DoydATXSibbgWMHjZbNUYtT9m4CJUhWX0gtSiBHbZlb5boUDThrIE_YvbzWVqj7D2yxgw=s0)

Clicking on the icon![](https://lh4.googleusercontent.com/fXYfQSsVCHkeFDjz8etxLm9dO61cn_7koiobm7Dd-8FEVa5I9wIt4oT4XGzgAusKNzEnxqy8zynVJpSA2dvyfo2DNd48_23AjB7KBua-yCYiWLURSLGt4eGkCFxD48wpQLCCmc7a=s0)

will invoke a new window in which all substructures are presented individually, e.g. in the for MARC field 'Edition' (250) there are subfields for the edition 'info proper and one for the 'additional information' :

  
![](https://lh4.googleusercontent.com/oXgEPHOkg8F8XMvF9V3gCSlrpcvdJioQgqJ75XEPXADo4olqMVYE2eYUnPYVn-eszmofCMZg5vJFv174DJ6mX0XMNUn6jUAz03iDGwECf17TRVK0_luuMrJmPkB6fqT1MCzip9Fi=s0)  

In this window each substructure value can be entered into its own edit box, repeats can be added with the 'add'

option and the whole 'group' of substructures can be repeated by pressing the ![](https://lh3.googleusercontent.com/KTz_LfSbCMlNi5VAlUfmiBeZTSxzGQRArPxdvh5uFVHafBPTjxhZcKheIjg1q3N1nE5UT8Xgzp-jJeDYNsLH1PXTUAZ2n7vFXOBTBTtCMQF_ZtFvqxyqllzJBdGelGA4lSf5altL=s0)button, which will add one series of substructures as a new occurrence of the same field.

[!!] The 'ADD' option at the right end of each subfield allows to create another occurrence of the same subfield. Beware : if you need to create a new occurrence of the field rather than the subfield, use the '+'-sign at the left top as mentioned above.

By clicking on the button ![](https://lh5.googleusercontent.com/5sJ0Fjl4CijxzEDy5GiCsSuKCAu8AUMYa4GGRmFvsxHxxZVLJRr37g4Izp4FL3gOvNPx2XS41s6VqeWdvQlEaHcCXX5zGgXwlNUNzG6vSq2DF6UIfoYp-WE2Bp_OLUl3N_e5PXiU=s0)the values will be placed into the field box with the proper substructure delimiters added.![](https://lh3.googleusercontent.com/PgLERHmFznvRqVapaWT3lwp5XX_3Q8kEPubXS4pQc-SjJRibyZUmgu6k-Hxi7q7IXoQtd9qUrUT3SXtgs7oYw9f4r6WQBL5Wm1gryT9yZnBfLJ34pIH8wbZWwS39GqJ35uVfoUv1=s0)
By clicking on the button  the edited values will be entered in the field box of the main editing window. Needless to say that the 'Cancel' button will just close the 'substructure' window without adding any values into the field.

It is possible to change the sequence of the repeats of substructures by using the 'up' and 'down' buttons ![](https://lh3.googleusercontent.com/lx6KHUQ9E2bDQr12qcKmlji2cu75RYgB3UlPYi98DGmXGJnlFiFJdpxBZKoa8xpZCGUpjxQeIxeS2mqW8gi5hdVhBv2Eibdp49iaj4D6lHWj_zqxKxFIYJIyo80jnuEXWOxi0_ER=s0) to move up resp. down the actually selected occurrence  

Finally one can also delete one occurrence of a substructured field by clicking on the button ![](https://lh3.googleusercontent.com/PikJVTAlv1fPvohI8Bd7TQshFzUyLYOKxIgKHmM-Jag2gTOQbLLFMmu10NFrJVpKplTjP9JWTXxLvz8_pQ6wD7L7huPv31KwO-6FL6gFMKrWNEfKYOH0Bq6XzULyx0B_Etfpt5g3=s0)

Experienced data entry experts will often by-pass this additional support from the ABCD-interface and type in the substructures of the field with their appropriate delimitors directly into the main worksheet editor, which is perfectly possible : the extra window is just an extra support indeed !

![](https://lh4.googleusercontent.com/ZRz9ASbmiTOM1gKYY0oGtb_PMiwNXv3GT1ypMICpS03quhmW6Ay7fco7fZDAcUww-DvTbxgEB5MP9AitFrhMm-vZl0Ly5ZU4eKzbYs0zgwC6hJoOfFlJV_l0FeqDD7nssm7NBygj=s0)

a field with a picklist, indicated by the  icon :

In a field with 'authority control' by predefined terms listed in a separate box, clicking on this icon will open the list in a smaller window :

![](https://lh4.googleusercontent.com/2koGGBfKwLjVDIGI06ImlpRyfJN4wn7HQB7TH_gtCh1-0S9d5xmCFuh4oPl59kjvlgMSzxY6JkqwBdaVb0YyoszU2lWyfcjvajeJhwyYVu2uclF-EDg8pDW_OblGiTaT5F9semzw=s0)  

Depending on the definition of this picklist (see the dedicated paragraph in the section on picklist definition of the database definition functions), only one or more items can be selected. Needless to say that the items listed will be precisely defined as well in that Field Definition Table set of colums on picklists, e.g. by defining a common prefix with which the terms have been indexed.
![](https://lh5.googleusercontent.com/wl7cVId_CAyinOal8GisdXNj_5XYLDK-UpJ4ksH5RiPL1hNnrujZ83FLos-TZQ0-TlJTtSkM7NiW-D5004yQiAJdhDAbKWyE1mSRSIkVXIDU_0fxCpQqAFPdJOrpA60E83wUV7P_=s0)

  

In this list you can navigate by using the alphabetic control or select one (or more) items from the list by clicking, Shift-clicking or Ctrl-clicking (or dragging the mouse) for multiple selection.

  

After you are ready with selecting one or more terms, click on 'Continue' (below within the picklist window) to transfer your selection to the main edit form.

  

-   a very special, interesting field is a 'Rich Text Editor' field, which shows up as follows :  
    
  
  

As can be seen, the field is a larger editing box with a series of icons above as in a real text editor with many text-editing features, such as itemized lists, boldface or italics etc. Such a field in ABCD is edited with a special add-on JavaScript tool, i.e. 'fckeditor', which allows to use the icons in order to create the according HTML- tags in the text of the field value. Whenever this value is shown in a WWW-environment (as ABCD itself, or![](https://lh3.googleusercontent.com/RTjq7sXJY_6MlrGHjbQsP5KBw6kl8tsfDkos67JXF1lVCD0p5Vp6tByafO6Io3dB_qd0c82dPz3_uC6CcLCcvt02VzVMg_JUUN3hiFKohJcOGWMFYDg9jx77mtpDNmoUdnYIXUdb=s0)

e.g. in J-ISIS), the HTML-tags will be interpreted as such and result in graphical effects, as this is the meaning of HTML-tags.

It is also possible to 'paste' into such a field text obtained from another document (e.g. a Word-document), using a conversion mechanism (to filter out all non-text elements) provided by ABCD.

## Record and field validation
 [!!] ABCD allows the system manager to design and implement validation statements for quality control at data entry stages. Such statements are written in the ISIS Formatting Language - we would say 'of course'..! See the section on this topic above - as it is an option of the main Central 'Update Database Definitions' menu. In the record- toolbar this function can be executed to actually check the current record according to the validation defined. The resulting messages will be shown in a small separate window.

## Shared cataloging through Z39.50
Z39.50 is a protocol which allows 'sharing' records (especially in the MARC-format) by first identifying them through a search with one of a series of Z39.50 servers - like Library of Congress in Washington or British Library in London - and then downloading the records into the local system. Here is how it works in ABCD :

### Configuring the Z39.50 of ABCD
Before you can use this function, some configuration has to be set in order to define the Z39.50 hosts you can or want to use and how to reach them. ABCD provides a menu option (main Central menu) for this configuration.

### Using the Z39.50 tool of ABCD
The following steps have to be taken for actually using the tool :

1.![](https://lh3.googleusercontent.com/mYLyc9UE5nFRpHNEhFnQkiGjSXQsBPJfsdpYH-gKdVT7OZbqMXt3WqFwIm4B6Ha6B8AazmWjmTBPke8lJIPJ3cey4ya1ZkXWFMV_PMOt1GRa6Ajt4zj1WbW7_fY1VgwU4CsObgAC=s0)    Click on the Z39.50 icon  in the cataloging toolbar, invoking a screen allowing the selection of a Z39.50 host and either a search statement or one or more ISBN's to be sent as to identify records for downloading :  

  

![](https://lh3.googleusercontent.com/4cqkJQAoYNkknLVBCBw810c4gJwEuxhnTsJZbQX93ZnT6-zyO2NYI5-8MrCF9SJPbP66j0UDZcxhrKWMajNviFCuuUPBQRPyhnpQTc6ARttoff8T0FUJvVNwRJTiPgVsFdRSBSnQ=s0)

2.  After having clicked on the button 'Buscar' (or search), if the submitted request is successful (meaning : the server accepted your request and identified one or more records indeed, complying with your search criteria), a new browser window will present the list of results with a 'copy to database' icon ![](https://lh3.googleusercontent.com/TpZsyfpKVlkL1bvjT2U8TUJDTqtnEpcD_20R61aCYDziT56gOy1QE7mMXku1-mEqpbF4i0BnxRa9j9YGAx-lgL-slzc5lIvHb95pCwWnJhstXp0p0OatRNomF2I9Q2cJ-H-J3nB4=s0)for each individual record :![](https://lh3.googleusercontent.com/xGZViNSp-WYv1rBFE0jYmVQaE7zjaO95CM3lMf_R4RVAMyMp0pkykniaC7H5NBF5D0wKvUaxkJiXSoHM2sDhJoAfjX2SVB4KIDDMwqN7-ziNGGeUyJjJOeN_J-xV_djapGtzg1Fb=s0)

  

3.  When clicking on the 'copy-to-database' icon, the selected record will be transferred into your ABCD cataloging screen as the actual record (a new MFN will have been granted), where it can be edited with the edit button if necessary.
    
Needless to say that in most cases such records are high quality MARC-records, so this shared cataloging has many advantages, e.g. saving time (if sufficient bandwidth for the communication with the server is available)  

and improving quality of your catalogue. If your catalogue does not use the MARC format however you might need to first prepare a conversion mechanism before loading records into your own database. This technique is discussed elsewhere in this document.

4.  [!!] When the Z39.50 icon is clicked not from the database-toolbar but from the record-toolbar, the behaviour will be slightly different : select the actual record (preferably by its ISBN) and when available from the selected Z39.50 server, only the missing fields in the actual record will be added, in order to complete the bibliographic record.
    
## Default values
    

This is a simple function of the database-toolbar : the edit-form will be presented and if so desired default values can be entered (or deleted) into this form.


## Reports (printing)
    
As explained earlier, ABCD reports are generated by ISIS Print Formats and therefore the interface for the creation of PFT's is re-used here. In the future ABCD will probably offer some pre-defined frequently-used or typically PFT's, e.g. for listing of overdue loans etc.

## Utilities
    
The utilities offered in this Data-Entry module from the database-toolbar are the following :

![](https://lh4.googleusercontent.com/zW30yuC8T2m3RIK22yfxyN5AM6veR_1uiZD_CkYiv6dQJLMFlTwz2S-ZzZGuOnMP7AlYL4TKnZdGwf3rgkW13h6VQLzWmfz97y34vCVU8iuCMvxCGgW-htcYcT8dL-01gb08DWsL=s0)  

1.  Import
2.  Text Import : text-based structured files can be imported by defining a conversion table, which will take the label for each (sub-)field (or the literals used to separate subfields) in the input-file, the 'repeat-separator' used within one field for different occurrences and the extraction format in ISIS-Formatting Language. :![](https://lh6.googleusercontent.com/qc5XZnGE3tuQg35BFgdGwyxP6KW0Gdrzwx_FS0vMKirZPRLhCLdEiFHLisGrETOXcbJfCV7--7ujQDyMW7XDc8lEVMKg-kqMvUv61obSl0Zj_eJ5khZn17gwJwM755OL5w2Yng9f=s0)
    
If the text-input file is actually a 'TAB-delimited' file (a 'comma-separated values' file with TAB's in stead of comma's), activate the button and ABCD will simply - without a need to identify each field or column
- import each value into a separated sequential field (meaning : the first value or column will go into field 001 etc.).
3.  ISO Import
    
ISO-files can be imported into an ABCD-database in 2 steps : first the ISO-file has to be uploaded by browsing to it :  

![](https://lh5.googleusercontent.com/uhygoC1DmMxYY3jV6iEBotnwgFvlC2FqaRIf_n9FU1iOssVcKwo0734OFqKYvhGymnhBvfb5Sgu0Q-JIWPqGCzJ5K0_-zLiUXiGAj1Uj9xU1pNs2fZMdUrNlZ1dFy8GMEN1wIdn4=s0)

  
Then the uploaded ISO file will be listed and can be actually imported with the green 'activate' button, after which ABCD will actually import the ISO-records into the actual database (using the CISIS tool for this pur- pose), meaning that in case of high volumes the Apache webserver might issue a time-out error - then use the command-line tool for this ! :![](https://lh6.googleusercontent.com/YR_prDLfJjpCKHXjTJKCl7fHgnotjbFVtLLAImuNxP54owkA8ZSzrgJQ41uL2BA47tGDuyzE61BO1zWeKOKgJV9P6GCi5o1TbXfjKsqratfH5wbJ7owv8mYhUg_OkpXcP2Wwf5Xi=s0)

4.  Export
5.  Export to ISO
This function simply asks for a selection of records (by MFN-range or search-expression) to export and a name of the export ISO-file :

  
![](https://lh3.googleusercontent.com/2J4DnZ_NtHRSXlYHgZadVupb0saBl0kFNcp9ImMBqMB3fyO8wzULWqTezY5T5A57vHt5ZAQYsK_eCHQSFaU9P4bTubsdwu0JgL9PHDLAAXt3j_BK0TJ-JKA2turJjW6MQ7rsUTKp=s0)  

6.  Export to TXT  
This is the reverse function from the TXT-import, using the same conversion table format, but logically doing the reverse operation on fields. By activating the 'delimited by tabs' option the export will be actually a CSV file which can be imported into spreadsheets etc.

7.  Other database utilities
In addition to importing and exporting databases from and to different formats, ABCD also needs to provide some tools for the database-administrator, which we will briefly discuss here :
  
![](https://lh4.googleusercontent.com/zW30yuC8T2m3RIK22yfxyN5AM6veR_1uiZD_CkYiv6dQJLMFlTwz2S-ZzZGuOnMP7AlYL4TKnZdGwf3rgkW13h6VQLzWmfz97y34vCVU8iuCMvxCGgW-htcYcT8dL-01gb08DWsL=s0)  

-   unlock the database : in case a database got locked (as part of the multi-user protection) without having the chance of being unlocked, e.g. in the case of a sudden power-cut, the database can be manually unlocked. ABCD will simply report on the status after unlocking.
  
-   List locked records : ABCD will list the records which are locked (if any) with their status :![](https://lh6.googleusercontent.com/izVayTT0xR2vCzBqH3hIveTcm_VOYShDlU80sbxLoDavXkBvlAGT2aF862nqott20-43nD-l4hOAzAefbx7HnPyfDWNhwEpI4D9DEukbHUzHkh3XL_kd8tMf1mxi2H10Wz8YOwCF=s0)
    

-   Inverted File generation : in case structural changes have been made to the FST, the system administrator should re-index the database to apply the new FST-definition onto all the records of the database (not only on the newly edited ones, which will be done automatically). If the set of records is not too large - to be seen in function also of the complexity of the FST and the average size of the records - the full Inverted File generation can be done from within ABCD here. In case of larger databases this should be done by a command-line operation with one of the CISIS tools, e.g.
```
mx MARC fst=@marc.fst fullinv=marc now - all tell=100
```
-   Global changes : as in WinISIS (and even provided in the old days of CDS/ISIS for DOS with additional ISIS/Pascal programs) changes can be edited semi-automatically over the full database or a range of records (identified by range or search-expression). The following interface illustrates the possibilities here :  

![](https://lh3.googleusercontent.com/XEUfl6-CDIMoQyC6WzP4_t7h7EuQRW-1_Y2-UvmRdI_UtreJDM3Qu4PSAeGNIoz52H-huEpLvKS5PZX7lFKO6hlCwUEzV6RbjFiNTz0bA5cxWcazH9HGEE9AyKy5_zbbXFqrR5oS=s0)

-   select field : which field to operate on
-   type of global change : either the 'new' value will be added as a new occurrence of the field, the existing field will be modified within or deleted.

-   scope of the field : the complete field has to be matched or any substring within the field
-   content to be located : the string of or within the field to be changed
-   value to be added/changed : the new string which will overwrite the located string
-   split field : in case a delimiter - as given here - is met in the field, the section before or after the delimiter (as checked) can either be deleted or moved into another field (to be selected from the list).
-   finally the operation can be executed or the form can be reset.
 ABCD will show the result of the operation. Extreme caution should be applied with these operations as they can be irreversible and affect many records. Taking a backup (export to ISO as explained above) is a good idea for sure.
-   The dedicated HELP-file for these utilities can be edited from this option. The existing text will be given in the HTML-editor and can be edited and/or translated.
    


## Statistics
This remaining database-toolbar option (since we don't have to discuss the help- and home-options as they are quite self-explanatory) is the one on Statistics. This option is explained in its own section but can be accessed also from the cataloger's toolbar.

## Barcodes
    

**Introduction**

ABCD (as from v1.5) has a function to assist in the production of barcodes. Earlier on ABCD-administrators had to rely on external - but existing and freely available - tools to produce their barcodes, but now ABCD has its own build-in option.  

Only databases which have been configured to use barcodes (as this is not a mandatory option in ABCD) will

show the barcode icon ![](https://lh4.googleusercontent.com/ac4m0TThbI9oN16h-JHNzK569lgh_JDNMYC5dn75XMihdiaHj8e8bgB749j4xpWvr10Se3YiByWUVu9vNsZNU8N69nFiQaDSFn-HrHIvp56hVJh-Wv9mZ-CK25BNcQ73K-sBGDhv=s0) in the toolbar. To activate this option for a database add the following line into the file 'dr_path.def' of the database concerned :

    barcode=Y

To access this option the operator must either

-   be System Administrator OR
-   have all the cataloging permissions on the database OR
-   have permission to print labels and bar codes (in the permissions settings of the related database).

This function will help to print labels that identify the physical objects in the circulation system or other data- bases with barcodes. A configuration file needs to be edited, where - among other variables - the dimensions of the labels or barcodes are defined. The results can be sent to the screen, to a txt file or to a word processor. At this moment barcodes can only be applied when the inventory information is stored inside the bibliographic records (the catalog-database, e.g. MARC).

Labels can be produced by
-   Classification numbers : a range of record classification numbers is provided and a report with barcodes is produced for all inventory numbers stored in the record
-   a range of inventory numbers : instead of classification numbers a range of inventory numbers needs to be indicated; insert the inventory numbers for which you want to print barcodes in the corresponding box and separate them by comma's (,)
-   Mfn range: a range of MFNs is provided and the report with barcodes is produced for all inventory numbers contained within each record of the requested range

The option 'barcodes' with the above mentioned barcode-icon when clicked will show up as follows, together with the option 'stock-taking' (which will be discussed in the next session), with the three main formats, resp. 'barcodes, 'spine-labels' and '(normal) labels' :

![](https://lh6.googleusercontent.com/tY80-1x5VoajM_0iIra1nCbELxFg-IhL-ErAMbIxPgruH75_GnrT3lZQverwI0qCmW1KyyKYloFaluPcdokqhhm_TJtrC4pywS3eOtwGpLKzT9svkQL-FkrFeQjmlfCqFxV1oELO=s0)

  

**Configuration**
    
This section defines the parameters that help to extract information from the database, prepare the presentation of the label and inform its dimensions. The following information is requested:


Table 2.1. Barcode parameters

|Parameter|Explanation|
|---|---|
|FST classifica- tion number prefix|Preliteral used to identify the classification number in the FST. Example: ST_|
|Format to locate the classification number|Format that will be applied to the database to extract the classification number. It is preceded by the previous prefix to present the list of classification numbers in the process of selecting the records. Example: if p (v82 ^ a) then v82 ^ a, "" v82 ^ b "." V82 ^ c, "" v82 ^ d, "" v82 ^ e, else v82 ^ b, "." v82|
|Prefix of the inventory number in the FST (edited)| Preliteral used to identify the inventory numbers in the FST and present them properly organized for the rank search, for example, to add zeros to the left even if it has not been entered that way.<br />Example: NICLA_<br /><br />Note:<br /> It is recommended to add this field to the record indexing table (FST). Example:<br /><br /> ```(if p (v900 ^ n) then 'NICLA_', If f (val (v900 ^ n), 1,0) = v900 ^ n then replace (f (val (v900 ^ n), 5.0), ``, `0`), else v900 ^ n, Eurlex.europa.eu eur-lex.europa.eu fi) ```<br /><br />The script in this format:<br />• Determines if the field is numeric (if f (val (v900 ^ n), 1,0) = v900 ^ n), which verifies whether the value of the field expressed in numerical form is equal to the value of the field;<br />• If so, the field is converted to a number in a fixed format of 5 characters by filling in spaces on the left which are then replaced by zeros:<br /><br /> ```replace (f (val (v900 ^ n), 5.0), ``, 0 ');``` <br /><br />• If it is not numerical, no change is made to the field. Note The value 5 shown in the format must be adapted to the number of positions currently held by the major Barcode entered in the database.|
|Format to locate the in- ventory number (edited)|It will be applied to the database to locate the inventory number and present it in the record selection window in order to issue the labels by a range or by a list of inventory numbers. In this example, zeros have been added to the left of the inventory number to ensure that the sequence presented and subsequently retrieved is correct.<br /><br />Example:<br />```if f (val (v900 ^ n), 1,0) = v900 ^ N then replace (f (val (v900^ n), 5.0), ``, `0`), else v900 ^n fi``` <br /><br />This script above:<br />-   Determines if the field is numeric (if f (val (v900 ^ n), 1,0) = v900 ^ n), which verifies whether the value of the field expressed in numerical form is equal to the value of the field;-   If so, the field is converted to a number in a fixed format of 5 characters by filling in spaces on the left which are then replaced by zeros:<br />```replace (f (val (v900 ^ n), 5.0), ``, 0 ');```-   If it is not numeric, no changes are made to the field.<br /><br />Here is the list presented for inventory number ranges when zeros are added to the left:<br />![](https://lh4.googleusercontent.com/WW2n1RGH42qo5aABD8d17omcsT491G5aM-8XDyQuUwPf3ZazcsEvedjbQSkioIZOuMLHfCCJxwJPuE75VoG69rV6zdRTNmkexKmnk693JIVbkIiHZND25C4Xg2VY53erLAkzHtLH=s0)Remember that you must create in the FST the NICLA_ recovery key with the inventory numbers with leading zeros:<br /><br />```900 0 (if p (v900 ^ n) then 'NICLA _', if f (val (v900 ^ n), 1,0) = v900 ^ n then replace (f (val (v900 ^ n), 5.0), ``, `0`), else v900 ^ n fi, '%' / fi)```<br /><br />See the difference if this method of left-filling with zeros is not used :<br />a. The normal indexing in the FST would be ```900 0 (| NI_ | v900 ^ n |% | /)```<br />b.  The prefix "NI_" would be used to retrieve the inventory numbers<br />c.  The extraction format of the inventory number would be v900^n<br />d. The list of inventory numbers would be displayed as follows, but making it impossible to establish a continuous range of inventory numbers.![](https://lh4.googleusercontent.com/4smbl2Df6zQecLxZQBhC3Z3quxVPrEuNWGGonxHaPtGTLFtjvi8jivjIQYD_dv3i_bW07LHuhxmtSPMENcnHqzUZ2r_l_2g13RTSt1gOdcqLjeeOxUTOHdc6WkAd9zN5xB6L80fj=s0)
|Prefix of the in- ventory number in the FST (unedited)|Preliteral used to identify the inventory numbers in the FST respecting the way they were entered. Used when printing is requested through a list of inventory numbers since it is necessary to compare the list supplied against the value entered in each of the records. Example: NI_|
|Inventory number format (unedited)|This format will be applied to the database to locate the inventory number as it was entered into the database. It is used to determine if the inventory number of the repeatable field of stock-items corresponds to the range or the requested list. <br />Example:<br />```v900^n```|
|Print Format (PFT)|Format to use to print the selected label or label.<br />Example of barcode label:<br /><br />```proc ('a1000 ~' if p (v84 [1]) then v84 [1] else v82 [1] fi '~'), (If p (v900 ^ n) then, 'INV *', </ Span> </ span> </ span> <span style= "font-size: V1000 ^ a [1], v1000 ^ b [1], v1000 ^ c [1], v1000^ d [1] '%%%' / fi)```<br /><br />Note: to understand the example PFT above :<br />a.  the use of to correctly encode the PFT<br />b.  the inclusion of the selected font to generate the bar code:<br />c.  the inclusion of the literal * INV * before and after the inventory number ```(v900 ^ n)```. This is essential because if you request the printing of a range or a list of inventory numbers ABCD you must have access to this value to compare the information extracted from the registry against the requested values to determine if an occurrence of the stock- items will be or will not be included in the requested output.<br /><br />d. line breaks were added to provide better visibility to the format. The configuration file should not have line breaks because one parameter is interpreted per line.If desired the format can be supplied as an external pft using @format_name .pft|
|Print Format (PFT) to send to TXT|Format to apply when the result wants to be sent to a TXT file in order to be processed by a special printer. You can enter directly in the text box or provide the name of an existing format or to be created in the same process. Use the edit-icon to edit or create the corresponding format.<br /><br />Example of the format to be used to generate a TXT file for printing barcodes on a printer of type Zebra:<br /><br />```proc ('a1000 ~'```<br /> ```if p (v84 [1]) then v84 [1] else v82 [1] fi '~'),```<br />``` (If p (v900 ^ n) then,```<br />``` 'INV *' , (2-methoxyphenyl) -2-methyl-2-oxo-1,2,3,4-tetrahydro- '^ XA ^ LL0203', / 'PW831', / 1, 1 H-NMR (DMSO-d 6):? 1, 1 H-NMR (DMSO-d 6):? 1, 1 H-NMR (DMSO-d 6):? 1, 1 H-NMR (DMSO-d 6):? 1, FT97,165 A0N, 25.43% FH + FD + FT97.134% A0N, 25.43% FH + FD + If a (v900 ^ m) and a (v900 ^ e) then | | V900 ^ l, else If a (v900 ^ m) and p (v900 ^ e) then | T. | V900 ^ e, | Ex. | V900 ^ l else If p (v900 ^ m) then | Vol. | V900 ^ m, | T. & lt; / RTI & gt; Ex. Fi, Fi, Fi, '^ FS', / 1, FT97,166 A0N, 25.43% FH + FD + FT97.165% A0N, 25.43% FH + FD + If p (v1000 ^ f) then v1000 ^ f fi '^ FS', / 1, 1 H-NMR (DMSO-d 6):? 1 H-NMR (300 MHz, CDCl3):? (1) 1, FT498.36 (M + H), 22.28 (M + H) + = 1, 1 H-NMR (DMSO-d 6):? 'PQ1,0,1, Y ^ XZ', / '%%%' Fi /)```<br /><br />If desired the format can be supplied as an external pft using @format_name.pft<br /><br />Note<br />• the text 'INV *' must appear at the beginning of each occurrence because this way the process can identify the inventory number Corresponding to determine whether or not it is included in the listings by rank or by inventory number<br />• the classification number is added to field 1000 and then that label is mentioned in the repeatable group using always the first occurrence of the same field<br />• / ' %%%' : this is the marker, on a final new line, to separate the different occurrences generated by the format|
|Tag height|Height in centimeters of the label. This value will be converted to em , multiplying it by 2.37106301584 for the purpose of fitting in the frame in the printer.|
|Width of the label|Width in centimeters of the label. This value will be converted to em , multiplying it by 2.37106301584 for the purpose of fitting in the frame in the printer.|
|Number of labels per line (columns)|The number of barcodes/tags, for pages with more than one barcode per line|

**Output examples with the following configuration file:**

• Example barcodes

![](https://lh6.googleusercontent.com/N58gdJQYOf2nT18k0seatyR488k2wrxcjRBbMiMJn5vuxkUHoJkYtUX_EoKL1sSCOlJZ-YIkblTu92S74XpQNZc94b80oskhWPlsgfxOYBj5aintpeKP6ofPJGjG_CABEThMrl1x=s0)

**Example configuration :**

Classification_number_pref:
```
ST_ V82 ^ b, v82 ^ b, v82 ^ b, v82 ^ b, "v82 ^ b," v82 ^ b,
```
The components of formula (I) 


Inventory_number_pref:

```
NICLA_ (V (v900 ^ n), 5.0), ``, `0`), else v900 ^ n 
```

Inventory_number_pref_list:

```
NI_ 
```

Inventory_number_display:

```
v900^n
```

Label_format:

```
@barcode.pft
```

Label_format_txt:

    @barcodetxt.pft


Height: 4 
Width: 7
Cols: 3 

• Example spine labels 

**Configuration:**

Classification_number_pref:

```
ST_ V82 ^ b, v82 ^ b, v82 ^ b, v82 ^ b, "v82 ^ b," v82 ^ b, 
```

The compoments of formula (I) Inventory_number_pref = ```NICLA_(V (v900 ^ n), 5.0), ``, `0`), else v900^n``` 

Inventory_number_pref_list:

```
NI_ 
```

Inventory_number_display


```
v900^n
```

Label_format:

```
@lomos.pft
```

Label_format_txt:

    @lomos_txt.php

    Height = 3
    Width = 5
    Cols = 4


Sample PFT : 


```
(if p (v900 ^ n) then 
'INV *' V900 ^ n '* INV *' 
'<center> <strong> <span style = "fontsize: 20px; font-face = arial">'
if p (v82 ^ a [1]) then V82 ^ a [1], v82 ^ b [1], v82 ^ c [1], v82 ^ d [1], " 1], 
else V82 ^
b [1], v82 ^ c [1], v82 ^ d [1], v82 ^ e [1], Fi '' ',
if a (v900 ^ m) and a (v900 ^ e) then Ex. | V900 ^ 1, Else If a (v900 ^ m) and p (v900 ^
e) then | T. | V900 ^ e, | Ex. Else If p (v900 ^ m) then Vol. | V900 ^ m, | T. & lt; / RTI
& gt; Ex. fi, fi, fi,
'%%%', fi /)
```


 Example output :![](https://lh5.googleusercontent.com/FG50ihhpXOJCgVCvVAYmbezkoDCk5mqtVNWIvIVoFI_C4A0YUPIPgr_FctE8g6YvR8ZxazajKtrEd9TVdVKBIzLTASIMu-sSLE5r9dzzzWXRs31SKgmCuhYkunnI5sSms3YyTvrX=s0)



-   Example labels
    

  

#### Example configuration :

Classification_number_pref:

```
ST_ V82 ^ b, v82 ^ b, v82 ^ b, v82 ^ b, "v82 ^ b," v82 ^ b, 
```

The components of formula (I) 
Inventory_number_pref:

```
NICLA_ (V (v900 ^ n), 5.0),``, `0`), else v900 ^ n 
```

Inventory_number_pref_list:

```
NI_
```


Inventory_number_display:

```
v900^n
```


Label_format:
```
@eags.pft
```

Label_format_txt:

```
@etiques_txt.php
```

    Height = 5
    Width = 10
    Cols = 2

Example PFT for labels :

```
('<Table> 
    <tr>
        <td valign = top align = center width = 50>' 
            'INV *' V900^n '* INV *' 
                if a (v82[1]) and a (v84[1]) then '' fi, 
                if p (v82^a[1]) then V82^a[1], v82^b[1], v82^c[1], v82^d[1], ''1], 
                 else 
                v82^b[1], v82^c[1], v82^d[1], v82^e[1], 
                fi,
                '' '
                if a (v900^m) and a(v900^e) then |Ex.| V900 ^ 1, 
                    else 
                    if a(v900^m) and p(v900^e) then |T.| V900 ^ e, | Ex. 
                        else 
                        if p(v900^m) then |Vol.| V900^m, |T. & lt; / RTI & gt; Ex. fi, 
                    fi, 
                fi, 
                (v100^a[1]) then '' '', v245^a, 
        '</ Td> 
        <td width = 50 valign = top align=right>' 
            v900^n'
        </td>
    </tr>
</table> 
%%%' /)
```
  
  

#### Example output :  


![](https://lh6.googleusercontent.com/NhW7CnlSLG9183c9gk5PEW4VJHsNCBb9x7ongyH2JhutZdw55_9O-tGODA4zZf__s9ycrbfGV9ODjrIR9LOBqSWJrYQAAxleDgMGiciY8LnmUmjsDPlo5m2sEcD-oCad7IQw8WLA=s0)

  

#### Output destination : Send to
The medium to which the issued labels are sent according to the following possibilities :

screen : Sends the generated output to the computer screen. You can use the Print option in the browser menu to obtain a printed copy; In this case you must configure the printer to set the margins and remove all page headers
MsWord Document : Send the output to a word processor. It has been tested successfully in OpenOffice. Once the document is displayed in the word processor, you must set the word's margins
Txt Use this option to generate a temporary file with other software that you want to use to print generated tags. In this case ABCD will use the above Display Format (PFT). Send to TXT in the corresponding configuration file.


#### Selection of records

The following methods are provided to define the set of records on which barcodes will be produced :

-   By classification number : uses the parameters 'Prefix of the classification number in the FST' and 'Format to locate the classification number' to display the list of classification numbers. Select from that format also the range 'from' and 'to' which you want to extract. A tag will be generated for each inventory number contained in each record in the selected range.
-   By range of inventory numbers : this method uses the parameters 'Inventory Number Prefix in the FST' and 'Format to locate the inventory number to display the list of classification numbers'. From the same PFT, the range 'from' and 'to' to extract will be taken. A tag will be generated for each inventory number contained in each record in the selected range. Remember the considerations already explained above to present a list of properly ordered inventory numbers, left-padded by zero's.
-   By list of inventory numbers : this method uses the parameters 'Prefix inventory number (unedited)' and 'Inven- tory number format (unedited)' to construct the search that locates the list of inventory numbers.
-   By range of MFNs : this methods will read each of the records of the requested Mfns range. A tag will be generated for each inventory number contained in each record in the selected range.
    
 

## Stock-taking tool
    

[for future use, to be added]

As an alternative to the ABCD-interface for stock-taking, a simple 'manual' method can be used, which will allow to produce reports on which barcodes found on the shelves are missing in the loanobjects or copies-databases, but also vice-versa : which existing loanobjects or copies cannot be found on the shelves.

To this end the following elements are needed - which can all be created using the standard ABCD Central tech- niques discussed earlier on in this chapter :  
-   a dedicated database 'stock' (already included in the databases directory as from ABCD 2.0), which will only serve to store the barcodes found on the shelves. This database has the simplest possible structure (FDT) :
```
F|1|Barcode|1|0|||X||10|||||||0||0|0||| 
F|2|Date of checking|0|0|||OD|||||||||0||0|0|||
```
where even the 2nd line is optional to store also time and date. So in essence only one simple field is necessary to store the barcodes. These then can be easily stored by scanning the barcode of the books when browsing the shelves with one single click into the data-entry form for this database and another click to save the record. As an alternative one can also store all barcodes as lines in a text-file and convert that file into an ISIS-database with the command :


    mx seq=mybarcodes.txt create=stock now -all

and in the FST one single instruction to index the barcode in v1 with prefix 'BC_' :


    1 5 '/BC_/', v1

-   a print format (PFT) to produce a report from the 'stock'-database checking the presence of the barcode in the copies-database (or loanobjects-database if that database-name is referenced to), which essentially should contain the following code :


```
if (ref->copies(L->copies('IN_'v1),v30)='')
then  'book with barcode <b>'v1'</b><font color="red"> is missing in COPIES database </font><br>'
else 'ok book with barcode 'v1' found in copies inventory' 
fi,
```


-   a print format (PFT) to produce an 'inverse' report, meaning : from the copies database checking into the stock database to see if the actual barcode is found in that database, so exists on the shelves :


```
if (ref->stock(L->stock('BC_'v30),v1)='')
then 'book with barcode <b>'v30'</b><font color="red"> is missing in STOCK database </font><br>'
else 'ok book with barcode 'v30' found on shelves' 
fi,
```


> Note:
> These are basic PFT's which can be elaborated for more decoration
> or inclusion of more data, e.g. the title of the book, for which
> another REF(L()) construct, referring to the catalog database this
> time, will need to be added.


The `REF(L())` function actually checks whether the barcode field, found when locating `(L())` the bar- code in the alternate database, remains empty, formulated as '' (two single quotes without anything in between, or an 'empty string') indicating absence.

The actual production of the stock-taking reports will be done - as can be expected - from the 'reports' menu-option or toolbar-icon. When producing the report, select the PFT's mentioned above, with the following reasoning : if the existence of a barcode, found on the shelves (and thus included in the STOCK-database) is to be checked in the ABCD-system, use the PFT with `ref->copies(L->copies('IN_',v1) ='')` statement, if on the other hand you want to check whether a barcode (or item) existing in the ABCD-system was indeed found on the shelves, use the PFT with the statement `if (ref->stock(L->stock('BC_'v30),v1)='')`.

Such reports can be conveniently sent to the screen, to a text- or word-processor file or, mostly probably the most handy option here, a spreadsheet, which then can be added to the stock-taking report of the library.

