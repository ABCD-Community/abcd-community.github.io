---
title: Central module - database managementlation
description: In this section we discuss briefly the main techniques of one of the most powerful functions of ABCD
lang: en
lang-ref: abcd-modules/database-management
---


# Central module : database management


{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---



In this section we discuss briefly the main techniques of one of the most powerful functions of ABCD : creating new databases and modifying database structures. Since ISIS-databases don't require sophisticated 'normalized' re- lational structures and still can cope with elements in many-to-many relationships (like authors with publications), ABCD can be used to deal with any such 'locally' created database relatively easily. We recommend ABCD for environments where several such applications, like e.g. Institutional repositories, cultural heritage collections, vo- cabularies and ontologies or even just 'snippets' (loose textual information units), are likely to be created and used.

We discuss in the following sections each of the options given in the main menu of ABCD Database management :![](https://lh5.googleusercontent.com/BE-QOz1IhYm4yArieSfqJz9alwkHKd10jYQD4LP66teGuVQuIHGXClJn43ynGbjbiH9kaqHZ7QD1Hmo4fSH_N2w55zn578cLHjCCsGFEZn4KLqcq28Yu6gN8p9MQezE7t_BGDzHC=s0)

 
> Note:  
> This menu is created in the PHP-script 'homepage.php' in the
> folder '\ABCD\www\htdocs\php\' where each login level gets its own
> function to create the menu (e.g. function MenuAdministrador() for the
> system administrator), so if it is necessary to change the sequence of
> the functions of this menu, this file has to be edited by someone who
> understands the HTML-coding inside.
> 
> We prefer to discuss the options in this main menu in a slightly
> different sequence (which can be obtained also in the menu by editing
> the above mentioned 'homepage.php' script), because before doing
> anything else the Users Administration should be at least performed
> once to define a local System Administrator and probably (quite) some
> other system users.
> 
> [!!] In view of the importance of the 'Data Entry' menu option here a
> dedicated section of this manual will be devoted to it following the
> discussion of the other Central functions. Also the procedures to
> follow to create copies and loan-objects for the inventory resp.
> loan-databases will be explained there as they are part of the Data
> Entry function.


## Users administration

The Users administration option of the main ABCD Database Administration menu is a specific case of data- base-management, using mostly the general techniques discussed in this section, but for a specific database 'USERS' in which only the System Administrator can create profiles and ('register') new users or edit them.


> Note: 
> IMPORTANT ! Before doing anything else, ABCD should get, by
> using this Users Administration option, a new, local System
> Administrator with his/her own login data ! The default login
> 'abcd/adm' will be widely known as it is published, so doesn't give
> any security indeed !

  

The screen following selection of the 'Users Administration' on the main Central menu will show 2 options :
  
![](https://lh3.googleusercontent.com/-qWWxqxHbNDV4H_ckIFQLOUbEZ9EXq9ojXk7lVKkMva53tCRv10pW85-FXQ4ea13lvzgo_JfERlF-2-2bgjoSbDeK4MTgfAjhpoGHGmyC1Q-SxuKbG9Z5-CCcaMDDjcd0GAre2fA=s0)  
  

The second option of managing the profiles is discussed elsewhere. The option on managing users is presented by first showing the existing users (there should be at least one 'System Administrator' user !) and giving the options to either edit these, delete or add (create) a new user.![](https://lh4.googleusercontent.com/lCWxZcCRXs6_4aR2OcR_pHwg7eObQuLh0yC-kfCnu4sGWZ4R80BgZpNK1lg1vDMLut45QICuQgQ5PKYBvSu0SgJs9WttQ847dGnZNZLw9nR8JOduU5NV8hIt2MHmZZ3OOY-3mPEH=s0)

When clicking on the 'record edit' icon (first one of the three presented for each user : ![](https://lh5.googleusercontent.com/DLZoceS22SkSxwdb2bE953Hj5KcGdr2VHpPcF5KZC0UJ4EgvUBobWXfYFNH5G5iMN83FTYMF2o3mP-5VSTBXSqFq1SGpPP3ImvfvQi2TbjjSY4zC7pYMDmICA_Cxy-EbxOALmFAC=s0) ) the record with the user data will be shown in an interactive edit-form :

  
![](https://lh3.googleusercontent.com/dCeLrTK6NagnAkFlULrem84wwtHl5ZoI2xaQBLKtMj8bRaj6vUIY8bopj_Q37hKkqpwWUyk0SEvjb0tV6cyRObaewa0vBx87JZvbDC-Rope4vKxj-sSYjMM0nt7sErVtA5WtDUs9=s0)  

This edit form has the following parts :  

1.  the user name, which can be a full name
2.  the login to be used in the login screen, mostly a shorter name
3.  the password for this user
4.  The profiles which have been created and which can be assigned to this user. A set of demo-profiles is included with the ABCD-installation package.
5.  the 'expiry' date for the current user, in the 'normal' date-format (as defined in config.php) and the mandatory ISO-date format which will be created automatically by the software itself.
6.  After editing the new user the record should be saved and then will be immediately allowed to use the system.
    

## Creating a new database in ABCD
    

After selection of the 'Create Database' menu option, the following 3 elements need to be specified :![](https://lh4.googleusercontent.com/0kY0d4W0NeDCkRgbEspkVOaJ9f-5_YIUgeLVmhLAjSSXQ_nK3bkUOLZTmVmQBDjnz8I2WuhoSYyNXteNvvX-saKtrHpMcRVXUlMm7uLvYeoMibjM0LNNjBwh8yWph2Tly3_28uwm=s0)

In the first box the software asks for the 'name of the database', which will be the real internal file name of the new database. These names no longer are confined to the old-style '6 characters' name of CDS/ISIS or WinISIS, but short names are still preferable. The name as presented to the users will be specified in the 2nd box : the 'description'.

> Tip:
> Database names and descriptions can be approached directly in the
> file 'bases.tab' in the folder \ABCD\www\bases. In this file each
> database, provided to users, has one line with each two values : the
> 'name' and the 'description', separated by a pipe ('|') .

The 3rd box will always provide the options 'new database' - meaning creating a database from scratch - and 'WinISIS database' - meaning copying an existing structure of a (Win)ISIS database or in fact any ISIS-database with a FDT, FST and PFT. Then also the existing databases will be provided as models to be used as the basis from which to create the new database. We only deal with the first 2 options, as copying from an existing ABCD- database is quite straight-forward (ABCD simply creates the database by copying all necessary files into their appropriate folders and adding the new database to the list of existing databases).

The creation of a new database 'from scratch', meaning : not based on an existing model but starting from a zero-basis, involves understanding quite some ISIS-techniques, esp. the Formatting Language, because this will be used not only in the creation of the presentation format of the new database, but also in several ABCD-specific attributes of the fields (in both the FDT and data-entry worksheet) and the FST for indexing.

### Creation of a new database from scratch
    
#### Editing the FDT

[!!] Since version 1.0 of ABCD two interfaces are provided for editing the FDT : one 'full' and one 'abbre- viated'. The abbreviated form will not show the subfields unless the field itself is selected by its link in the first column - they will then appear in the subsequent form where all the details of the subfields can be edited, e.g. the width of the columns as 'no. of columns' in case the subfields are to be presented in a table rather than separate entry-fields (which is the default type of entry : Text/Textarea). This abbreviated FDT-editor is quite practical - and faster - in case of large complicated (i.e. using many subfields) structures such as MARC (even when only using 'minimal' and 'national' cataloging levels the number of possible elements is very high, p.e. there are 14 different record types with each their own 'polymorphic' field 8 and corresponding picklists, also for the MARC-indicators... resulting in more than 140 picklist-tables per language). For other, simpler structures the full FDT-editor can be used.

[!!] In the case the full FDT-editor is selected, or when in the abbreviated editor a field is presented in a detailed format, the link at the first column can be used to show the field in a 'vertical' detailed way, so presenting just the selected field in a normal form. This then again is more practical to deal with the individual elements to be defined.
  
[!!] The FDT-editor screen is probably the most complicated one of ABCD, as it presents an empty FDT, but since in ABCD this FDT also defines the worksheet for data-entry (or cataloging), unlike in other ISIS-softwares where a separate but simple 'FMT' (data entry worksheet) is defined, and since in addition ABCD uses quite some more advanced data-entry features such as picklists and validations, this step is rather demanding.

> Tip In order to 'edit' the form, double-click inside a cell of the
> table ! Simple-clicking will only select the row but not make the cell
> editable or invoke the menu attached to the cell.

We will deal with each 'column' of the table now, but for a simple test it could be sufficient to simply only use the first 11 columns and the 2 last ones, the remaining part being dedicated to the optional definition of picklists :

![](https://lh6.googleusercontent.com/kPazwK_Jv1KbLvSgrKNfdrxF8_JP_ZblxQFRtfj7C8599QfET0wftqNq2wmat-QWM3Re2yUJvAgWlQYzvD4tdrF-NeCCuU9esA2IenOppk8uZ65TZ7mhgHINzdjRgKoNhv12We8K=s0)  


#### A. Defining the fields
1.  The first column : this is only a number, assigned by the system. It can be used however, if so desired, to open the row in a separate window to present all columns as separate boxes to interact with, by clicking on the hyperlink of the number itself. Such an empty row presentation looks like this :  

![](https://lh6.googleusercontent.com/zN2AIz2DBmeqK6pNjYvtk0WyZjgAbr1AJ3jGhU_KvsbBO5YycCNhKqhwUTPqHFZRmXnGD6necfQ01tnjE0_8iJB23I703QXWaPPFrshOYjdztaJf83Ch5LJ32W6BGyVoy_Asci2g=s0)


2.  The second column is about the 'type' of the field, which can be one of the following types :![](https://lh5.googleusercontent.com/dRjJTJs8TLrPN6lfaXwf5IM899xU4IPEHbLLJ0pBGICZFPabenTtBv3wnSBQboBNLjcQqU2TtvSvvp_ISq8yBZOifEO1eO1-ZafzTLvRMqrIQKAgErXnWBkL9k2kWL21ux4Lj1NO=s0)
    
	* Field : the basic unit within a record, which should be used in case the element is NOT one of the following types : a subfield, a fixed field, a MARC-fixed field or -leader, or a 'group' which is a repeated field with subfields.
    *  [!!] Auto-increment : this is a special field which the system itself will normally manage, by taking the number saved in the small file 'control_number.cn' in the data-folder of the database, and adding 1 for each subsequent record using this field. When for some special reason this automatic numbering needs to be manually changed, the 'assign'-link will allow to do so.
    * [!!] A subfield : when previously a field was created with values for subfields given in the 'subfields'-column (see infra), ABCD expects subsequently ALL subfields to be described immediately following the field to which they belong. The subfield-identifier then has to be put into the column for 'subfields' and the sub- field-name as the field-name. Indicators as used in MARC-structures should be treated as subfields but with numerical identifiers.
    * A fixed field : allows to create a simple field with a fixed length  
    * [!!] Date (MARC 005) : this is the special date-field with tag 005 as used in MARC.
    * [!!] MARC-Leader : the fixed-structure MARC leader field. Dedicated support for all positions of this special field is given.
    * 'Group' : this is a subfielded field which is repeatable. As with a normal subfielded field, it should be followed immediately with the subfields belonging to the group, but each series of subfields will be repeatable. A typical example of a group is the 'author'-field, as an author definition contains mostly several 'parts' (or subfields) such as name, first name, role etc.. and documents in principle can have more than one author, therefore this field should be repeatable. The 'table' data-entry element is quite suitable to represent such a complicated field in a data-entry form : each row of the table will be a repeat of the field and the columns represent the subfields. [!!] Sizes of the columns can be set as the 'row' -parameter of the first subfield definition row. The number of rows in the table will define how many occurrences will be shown, but ABCD will always add one empty row to allow creation of additional occurrences.
    * A 'line' is just a graphical element to separate fields in the worksheet for data-entry. It doesn't need any further specifications.
    * A 'heading' is a short text which can define a 'section' in the data-entry worksheet in order to 'group' fields together; ABCD will automatically provide hyperlinks-within-the-form to navigate directly to any of the defined headings. In MARC a typical 'header' could be e.g. 'primary entries' or 'secundary entries'.
    * Operator and Date : this field will be automaticall filled in by ABCD with the name of the logged-in operator who edits the records and the time-stamp of creation.
    

3.  The third column is used to define the 'tag' or numerical identifier of the field, as required by ISO-2709. These numbers range from 1 to 999. ABCD (as does CISIS) uses many fields with values higher than 1000 for inter- nal, mostly temporary uses. Field-tags can be arbitrary (e.g. 1, 2, 3...) but often should comply with existing standards, e.g. MARC21 uses '245' for the main title field. It is the designer's (you..) responsibility to decide on a proper list of field-tags.
    
4.  Column no. 4 allows to identify the field with a 'name' or 'title' in order to explain the meaning of the field-tag. Here any - preferably short - indication can be used in the actual language.
    

> Note:
> ABCD, unlike WinISIS and other ISIS-variants, allows creation of
> FDT for each language used, so field names can be language-dependent !

5.  Column no. 5 allows to select one - and only one ! - field in a database to be used as the 'I'dentifier field on which the lists (see e.g. the 'A-Z selection tool') will be based. This is not the same as the 'primary key' field in relational databases, but indeed defines the field marked as being 'I' - since this column only allows to 'activate' or 'de-activate' - and hence being used to sort the records for direct selection.
    
6.  Column no. 6, as the previous one, only allows 'activating' or 'de-activating', in this case to denote whether a field is repeatable or not. This is an important decision to be taken, according to the designers view on the database structure, but different reasonings can be applied. E.g. in a simple structure the 'title'-field could be made 'repeatable' to also contain all types of titles (e.g. sub-titles, translated and original titles...) in order to confront the users with only one 'title'-field. MARC wants all types of titles to be in different fields, but still prefers the title-proper field to be repeatable ! We suggest to make fields repeatable in case of any doubt, as it is easier to use a repeatable field only once, rather than displaying repeats properly in a field defined as non- repeatable (in that case the field definition has to be changed in the FDT ánd the PFT's need to be adjusted !).
    
7.  Column no. 7 allows to define the single-characters (0-9 or a-z, case-insensitive) which will identify the sub- fields, if any. Remember that if subfields are given here, the subsequent lines or rows SHOULD deal with each of them individually, otherwise a logical error will be given. [!!] In the table-row defining the specific subfield, this column should contain the subfield-identifier.
    
8.  Column 8 allows to optionally define characters such as punctuation (,:: etc.) which will be converted - in the same sequence, so be careful and make sure there is consistency ! - into the subfield identifiers. This allows data-entry staff to use the punctuation instead of the rather less-obivous sub-field identifiers, but remember that ABCD also allows to deal with each subfield individually without having to bother about the identifiers (see the section on 'data-entry').

9.  [!!] Column 9 allows to define the type of HTML-input component the data-entry form will provide, where there are 15 possibilities :

![](https://lh3.googleusercontent.com/u-8-cS31wEnibu0cmG6cb4U-MMt4JTr2qBTU6PDZ11lL2kCspQZWFrhxLdDEn4GnuaYNHDPfYPbF34ODHAcP7GaJ5hewHhawkRZmM-j9sOxvvVAASgC16xBNuugb1iwfO827_pf_=s0)

![](https://lh3.googleusercontent.com/-TAFo7WPCWDZlR6kscNHtFIcWMNvjbgkt2z6HtElNTpzED2CQlXGupzO979kcGyYbOXPd91ezgznpLDeoUpmzXYxUTJ82J2TNOjgO1jX3u7PLcEEcu_xizVM9H-I3yQd-cI6NIz-=s0)

![](https://lh6.googleusercontent.com/MNRAKw2VaT_UMhQWbs8zFvrNMtjmsS2oPJCefLGn8IIky3Fk3B8puPvoz_h3gO8PnZqvN4EWkaD_XtGtUSnMDZfkkYB3MGpyzUJIGJRkmVg2rahGmbphLegPc92XHwbyeTgj1J65=s0)  

* Text/Textarea will present a text-box of variable length. The number indicated in the 'rows' column defines the number of lines which will be presented in this box.
* Text (fixed length) will present a text-box of fixed length. The number indicated in the 'columns' column defines the number of characters which will be allowed to enter in this box.
* Table will present a table in which, in the rows, occurrences of the field can be entered, and in the columns, subfields of that occurrence can be entered. The numbers in resp. the 'rows' and 'columns' columns define, as can be expected, the number of occurrences and subfields which will be captured for this field.
* The 'Password' option gives a text-box in which the box will be filled with * for each character typed, to hide the contents of this special field. If the MD5 option is activated in the config.php file, the passwords will be encrypted.
* Date is the option to capture a date, with the assistance of a JavaScript control to offer date selection from a calendar.
 * [!!] ISO-date is the ISO-formatted (yyyymmdd) date field, mostly filled-in automatically by ABCD for internal use.
* Select simple will allow selection of only one element from a list of pre-defined options.
* Select multiple will allow selection of more than one element from a list of pre-defined options.
* Checkbox is the option to allow one or more boxes to be 'ticked' (activated) in order to select them.
* Radio is the option to allow only one round button to be activated in order to select the related option.
* HTML area is the option to present to the user a full HTML-editor (JavaScript control, in ABCD we use FCKEditor) for editing, in WYSIWYG-mode, text with HTML-codes.
 * External HTML is the option to create, as in 10, a text-with-HTML-codes, but this will be stored not in the database but as an external file, with a link in the ISIS-record to this file.
 * Upload file is the option to present a JavaScript control for loading files to the server and create a link accordingly.
* [!!] Read-only is a field which will not be editable after it has been entered as it is read-only.
*  [!!] Hidden : a field which will not be shown after having been entered.  
 
10.  Column 10 allows to define the number of 'rows' the data-input HTML-component will offer. Depending on the exact type selected in the previous column, this means the number of text-lines which can be displayed in the box, or the number of occurrences of a field (in a table to contain a 'group') will be allowed etc.

11.  As with the previous column, this column allows to define a number, but this time for the number of 'columns' in the HTML-input component, which can be e.g. the number of characters (in a fixed-length textbox) or the number of sub-fields (in a table), or more generally the 'width' of the box.
    
In principle, after having defined these 11 columns and if no need exists to define 'picklist', what is remaining is to simply define, if wanted, a 'default' value for this field in the last-but-one column, and to indicate if a help- page for the current field is to be made available. [!!] These help-pages are to be referred to as URL's (local files or online webpages).

At the end of the table options are provided to save the table, but also to test and validate it![](https://lh3.googleusercontent.com/9HhAv5eLud0hhqtTRGEUkE1ZGL4Lf097h2CHHMjsbhK5LWtdpqPIQqttSBnATqbFTDCu-JyREbI5TEj6gd3rtNdL2fZXF3VUOOTkrlySKX37rZtcHFnsfFVFs0zSDHeqBS9w2nxU=s0)

Here the 'Test' and 'Validate' options will resp. display the resulting form for getting an idea about the result and display the table in a different window with a message indicating wether any logical or grammatical errors are present in the table. It goes without saying that such errors need to be corrected first before 'saving' or 'updating' the FDT with the last option presented here.

The 'List' option provides a listing of the table in a separate window, e.g. allowing printing it or saving it as a separate file.

#### B. The definition of picklists
    
We continue here discussing the columns of the FDT, this time with the columns 12-20, which (except for the last 2) deal with the definition of 'pick-lists' to be presented in the data-entry form in order to support terminology control, authority control or simply to facilitate the data entry by providing the options available.

12.  Type of picklist : here we define the type of the control list to be used, with the following options : [!!] Database, Table or Thesaurus.
    
A database is actually an ISIS-database with its Inverted File, so providing an almost unlimited number of possibilities, but being rather a complicated solution. [!!] A simple pick-list (table) will be based on an ASCII (or TXT-)file containing on each line one option. The 'Thesaurus'-option is in fact an (ISIS-)database again, but this time using a specific field structure with references to the different (and standardized) thesaurus hier- archical relationships, such as 'synonym', 'broader term', 'narrower term', 'scope note', 'use for' or 'used for'. Such thesaurus-database normally provides ways of 'navigating' to the related terms and therefore offers even a higher level of support for data-entry, by providing in such a scientific way descriptors of a given scientific field or topic.

13.  Name : here the name of either the database or the file on which the control list is based, is to be put. This can also be taken from the 'browse' option in the 15th column (see infra).
   
14.  Prefix : here the short prefix should be put in case a database is producing the picklist, as that list will be produced from the Inverted File of that database and that often will be divided in 'sections' by the use of a prefix
    

- this is the one to be put here to allow partial presentation of the Inverted File. If e.g. the control list is used to facilitate the entry of publisher names (as many come back often), probably the database publishers are indexed with a prefix such as 'PU=', then putting this prefix here will only display the section of the IF with that prefix.

15.  'Browse' : this is a link which, when clicked, will open the following separate window, which allows defining some information on the picklist-database in separate boxes, first of all the name of the database which can be selected form the ones already available.  
    
![](https://lh6.googleusercontent.com/PJZthcOQDtRu9jxxBxRaqW9DWs-ZVysRsC2sxAXkgMZ9mpIRjQ2cmdvFl-iMcFJ_VyBG4CT89a6qv7r0b1HuaIMgDBLY7v1KzL-bEmQu5rZiD5rL9xP_2kTd2NsLgxj4HwHJ5vzc=s0)

 16.  Display format (or 'List as') denotes the PFT which defines how the values in the list will be displayed with the Formatting Language. [!!] Here either an 'inline' PFT can be given, e.g. 'v11', or a reference to an external format can be given as '@myformat.pft'. This external format has to be written following a pre-defined pattern in order to be correctly interpreted.
    
See the example here used for the authority files of the MARC database : @autoridades.pft: select e3

```
case 1: v1
case 100: v100^a,`$$$`v100^a
case 110: v110^a,`$$$`v110
case 111: v111^a,`$$$`v111
case 245: v245^a,`$$$`f(mfn,1,0) case 260: v260^a," : "v260^b case 270: v270
case 340: v340
...
endsel
```
  

> Note:
> [!!] In case the PFT contains pipes (|) it CAN NOT be put inline
> into the FDT but has to be put in an external PFT referred to from
> this cell (this is because the pipes are also used as separators for
> the column values of the FDT table as stored in ASCII- format).

17.  Extract as : defines, again with the Formatting Language, how the contents of the field needs to be exactly extracted from the field values in the record to which the entry in the list (as an Inverted File posting) points. If this value is omitted, the values will be kept in the format defined as 'display format' in the previous column. If the display format is a pre-defined format (@xxxx) and follows the instruction to separate the display format from the extraction format by $$$, this part should be left empty.

18.  Default value : here the default value can be put which could serve for fields which often have, in the specific case of the database, the same value, which then will already be presented automatically.
 
19.  Help : this is a tick-box (active or not) to indicate whether a help-file for this field should be presented in the worksheet. The help-pages are stored in the folder bases/dbn/ayudas, where dbn represents the name of the database.  
   
#### The FST Definition

After having defined the list of fields (and picklists for them), ISIS expects the manager, who is creating a new database, to define not only which fields will be indexed, but also exactly how they should be indexed. That is what the Field Select Table (FST) is meant to do.

There are excellent documents available as 'help-pages' within ABCD on this complicated ISIS-technique (and included as annex with this manual), so here we only present the main purpose of the three FST-columns.

The FST contains 3 columns :

1.  The identifier
This is a tag (a number) which will be used as the field from where the index term was taken, e.g. to allow field- limitations in searching. Mostly this tag will correspond to the actual field from where the value was taken, but it can also be a 'virtual' field (e.g. to group several titles in one 'title-field' to simplify the structure for the search). For example, one could create the very popular 'ALL FIELDS' search (Google-users don't know anything else !) by indexing all significant fields with one and the same IDentifier, e.g. '999' to allow a 'non-fielded' search.

2.  The indexing technique
ISIS avails 9 techniques for indexing, but basically these can be reduced to two main options : the full field (abbreviated to the first 60 characters in ABCD) - called 'by line' - or a full-text indexing - called 'by word'. Indexing techniques from 5-9 are optimized for indexing using a 'prefix' (a short tag preceding the values to group the values in the same alphabetical section of the overall index or inverted file).

  

3.  The extraction format
 Here the actual format to produce the sting to be indexed is specified using the ISIS Formatting Language. All features of the Formatting Language (except presentation features) can be used, including REFerring to other databases.

  

The interface of ABCD makes the creation of such an FST as easy as is possible (but it isn't easy really, because of the advanced possibilities available!), by not only providing the FST in 3 editable columns, but also, as a reference, the FDT from which fields can be used with their tags, and also indicating whether they have subfields and are repeatable or not.![](https://lh4.googleusercontent.com/i5Vtr0vTJ6oJOQJfiU2Q3rg9LHa2Lk1qq-vjMxShCLhMFgoZssGo0Igo2GUjJ13FxTQk9c63bdnfyWxaWOzowQ8nwQMSc1S0hP7vcmm-HQumWuJMAMEZ1ay3o8ETkuZrOYNr4gzV=s0)  

As can be seen in [!!] this example, which uses very simple extraction formats, we always prefer prefixes to be used, e.g. 'ID_'. In view of some built-in options of the iAH OPAC interface for ABCD, we recommend the use of 3-character prefixes ending with an underscore ('_').

As the Formatting Language (ISIS' most powerful feature) can be used here in its full power (without the graphical presentation features), values can be processed before then enter the dictionary, e.g. 'N:', f(mfn,1,0) produces the recordnumber or MFN, formatted (f) as a string, but more complicated examples can be given, e.g. .

-   a combination of several fields or subfields with added punctuation
-   formats using the REF-function to refer to external databases to take values from there after locating the MFN with the L-function - doing so e.g. codes can be converted into values for the dictionary.
    
After having edited the FST, it can be tested with any record of your database to check whether the actual values which will be indexed indeed comply with what was intended.![](https://lh5.googleusercontent.com/FRA6Z4MDzsH4LSRB2h7RIix9nvptfcgKSDdIlqn-IaG-aaR0p39PQ1u_-C_NEWjqnbqJL7vgWWtWngDP4oimbX-JNSpuuBlKzYg2cAHsu7YZsKVmc7eVcyH4nRoPiXQbJ0SG5hGW=s0)


#### The worksheet editor

As in any ISIS-application, ABCD allows the creation of many different worksheets for different purposes, e.g. to deal with only a smaller subset of fields, or with the fields in a different sequence etc.

For that reason ABCD offers in this option an easy tool to select which fields to present in the (new or edited) worksheet and in which sequence to present them :

  
![](https://lh5.googleusercontent.com/PqifZQf5Z9eKjkYTnqvq1ADR1IzJ5m1rFtXJH3tweCdwJdpYgm841-pdb7Nf42SSB6UmNagSYyqlYM4UE6YN26NFGXFbAawHlEizFva2Okle6mEajqtcUE9Lj4s5SbT_kPXW5IdX=s0)

In case an existing worksheet needs to be edited, it can be selected (in the upper part of the interface) from a list

-   where possibly also an existing worksheet can be deleted is so desired. The main part of the worksheet presents
    

the list of available fields with possibility to copy any field ( ) or all fields ( ![](https://lh4.googleusercontent.com/6vcKUqy6njvqCh-qXnxOoyLtj3GZAZZqTXg3Mdh8jSduvP2J0YA74-YYtPw7mZ5pviDiG81r2u881hlODieyOFR2s6VI1NyDTQ--lmMOhXk7kKbcqcd9i6q6w7Wj29b9rQjWgYiV=s0) ) to the worksheet list at the right side.![](https://lh4.googleusercontent.com/F778ssiMh_7PggbelfwBKygL6CBhIaW-sp9UR4VueZ4oWdzhsjbKns-q0P74R3qD41xf8kYM4szlPq3TzCZzPT50nW4Db2DspeoWTlAeLX8MUG4_XQIfMG93Yt3MGdrjoEQMwRC4=s0)

Finally the worksheet can be saved into the system with an internal name (short and lower-case only) and a description for easy identification.![](https://lh5.googleusercontent.com/EWTCud_6-VyUNX6KsiOJiofV2-p_IsAbjUok0WZCOcLCNKmW4_HXkVXVGPpEiNE0Y_7MPR3Y8iH9-FKqqdRQHm_jlyZOWt6-SMiBZgqi76ffz7iyoyWFXPb2RJh2XzJAHgVE7oWk=s0)

#### The PFT Editor

Since the ISIS Formatting Language is a very powerful tool with many possibilities, a dedicated document on the (C)ISIS Formatting Language is added as annex to this Manual on ABCD, but it can also be consulted from a link provided in this PFT-interface of ABCD. Here we just briefly explain how the ABCD interface allows easy creation of either HTML-formats (for presentation on the web-pages) or 'delimited' formats (for export to a comma-delimited file).  


The PFT-Editor has 4 parts :
  
![](https://lh3.googleusercontent.com/opZKqWrBzBAbc0la7a43dghMs8Ctu736CiBaj17dgO12FwP0jnzPsKbmUGKyH_lgjIaxx_6eu3p12MCGliowkSez-1UwyJuat3DY6xg78WRGfqPnldYwpey5oobFN7mwufYxbC0H=s0)  
  

1.  Use an existing format : a list of existing PFT's will be available to select from. It can be also deleted or uploaded from an external file if not yet available. The format then will be presented with an editor to make changes into it.![](https://lh6.googleusercontent.com/LF03KbwiDfsg4x-hd5dB_vMNQ-KW-2VS45WWZFh3c8VutA53ycDhnk_DnJUDPq2hvJYTLRk4PiX4QlkpmCeDYKfwBnf-FYd7n_o8Qm-krFEy70bN2GrwYLYzarC0uU1pOlexeeEk=s0)
    

2.  Create a format : as with other table editors in ABCD, first a list of available fields is presented, which can be copied either individually or altogether into the format and then re-ordered.

> Note: 
> Windows list-selection tricks can be used here : Ctrl-click to
> add an entry into your selection or Shift- click to select all options
> upto the cursor position.

![](https://lh3.googleusercontent.com/7qv2pzwlhbLF8WyorU87BxnIB1S8pzPbwajUhTCFsYYWb9cc_xLOFMj0VYqppz7Q1Nhknu5_OyRqfqoPf9_NUwy2fzeYvWboFr4XxbhHr0-PlbKb8puDvu9yRR6SW1Z6MDeHdLW2=s0)

  

3.  Generate output
  As mentioned and shown above, generating output to test the PFT can be one of three pre-defined standard ways of presenting data from your database : either a 'table-formatted' web-page (in colums) or 'paragraph-formatted' webpage (no columns), or - alternatively for quite different purposes - a delimited format for export to other software. ABCD will immediately generate the necessary code, combining HTML-tags as quoted 'literals' with values from the fields (Vx).  

[!!] In case a 'column'-based format ('delimited' will allow export to softwares such as spreadsheets and statis- tical analysis tools) is selected, in the right square the (sequende of the) headers of the columns can be defined, by default they will be the field-names already defined.

![](https://lh6.googleusercontent.com/1o1GalJS8J492Mhe31NMGVJ22cUvr12wGCm_IsJUN_s_8spLVRe5SRfpptM-zWInOb4hay6lBJBNhnMZUYDEB_BIIllRWdqb-3gaTraJZsIsWEJmZ2urNNCUokN2qYOr9ZPFQknM=s0)![](https://lh5.googleusercontent.com/wsOwFpqXoqdibccoPmD8OErSxaVrWE4C3cGGWIyAnkfAgWUN24xG2EGpJjFJH4uD1YYsdYdQkor_IE7wTx-W8Q3tQPvMBcInU_RBiEANiOyFgQarl4T3iGAI0SmM6EeBZtC2sWrf=s0)

This format then can indeed be 'tested' immediately on either a range or records or a selection defined by a search-statement.

![](https://lh3.googleusercontent.com/ttX0fvJNFH2qqzxWuWc-Jvg-8Fp7PjOTcHjDtdxtzQvWJieZvpnTPJtO04YkFKWJUUDz_BN8I102VBc_o-98w9C_RdWtx77kR46C5uFZ3c0kQ6kY0NvK6VbQJSgYfi6gutu_Ko4u=s0)

This will result, when 'previewed' within the interface as opposed to 'sent to a document or worksheet' (this last option is ideal when outputting data as 'delimited'), into a display format like the following :  

![](https://lh5.googleusercontent.com/Qm5qO48Xk515yl75gC4B_A-1pAu95qto6F09C38JkeNO6pFjBrhCW9ewUEq-Dvyk8vzyPJvtKXskPJW164Y9y7j4xqHo8z3LR7LEHubA8qJIPVM4U-bGuzLcxK3tHTTXgQRmVlw5=s0)


> Note:
> In this example subfield codes are still visible, but with simply
> adding a 'mode' statement like 'mhl' into the format ISIS will hide
> them.

*The other functions of defining/editing ABCD-database definitions will be discussed below when dealing with the'Update database definition' section.*

### Copying an existing WinISIS database
For creating an ABCD-database from your existing WinISIS database, here are the steps to be followed :

1.  Export your existing records into an ISO-export file using WinISIS (or another ISIS-tool allowing ISO-export); remember where you have saved this .ISO export file, normally it will reside in the WORK-folder of your WinISIS installation. No specific parameters need to be set, unless of course you would only want to use a subset of the records in that database (by using MFN-range minimum and maximum or a search result) or you need to 'convert' (reformat) the records before entering them into ABCD by the use of a 'reformatting FST'.
2.  Assign in ABCD, after having selected the 'Import from WinISIS' option, a name and a description - as with a new database, see supra. Then select your WinISIS database using the list in the 'Create from' part of the dialog.
3.  Select the FDT belonging to that database and click on 'Upload' in order to have the FDT loaded into the ABCD environment of the new database.
4.  Select the FST belonging to that database and click on 'Upload' in order to have the FST loaded into the ABCD environment of the new database.
5.  Select the PFT belonging to that database and click on 'Upload' in order to have the PFT loaded into the ABCD environment of the new database.

> Warning:
> Most WinISIS databases use a default PFT (with the name of the
> database) which contains typical Windows (as opposed to HTML) codes,
> such as e.g. 'BOX', 'FS' etc. These will result in a 'grammatical'
> error when later opening this in ABCD, so it is better to avoid this
> by selecting a PFT without such

typical Windows-elements ! If not available, remember to re-create a HTML-based format within ABCD to replace the default PFT for your new database.

6.  Click on the 'Create Database' option in order for ABCD to start writing the necessary folders and files for your new database. A message about successful creation (or not, in case of problems) will be displayed on your screen. Also you will be reminded of the fact that without assigning this database as accessible to at least one user, you won't be able to use this database.

7.  Now you can open the new database, as it has become part of the list, in the main database management window.
8.  As the database can be opened but with 0 records, the first thing to do is to import the ISO-records created in the first step of this series. To this end, click on the 'Utils' icon in the main toolbar of this data-entry screen (as described in the section dedicated to this) and select the option 'ISO import'. This procedure further, as can be expected, involves the selection of the source ISO-file, which then should be 'uploaded'.
9.  Now, a bit strange, the ISO-file is ready for being effectively imported into the database. For this, click on the 'Utils' icon again in the toolbar and select 'ISO-import', where now the uploaded ISO-file is available for effectively importing (converting) into your ABCD-database. The software will now ask you if it is o.k. to indeed start importing the ISO-records from the selected file. The list of imported records will be shown on your screen to monitor its progress and success.
10.  If your newly imported records don't immediately show up in the database, re-open the database from the main menu, this will refresh the database parameters.
11.  Now the records should be visible and editable as normal records, only they have not yet been indexed into the Inverted File, so use the option 'Inverted File' update in the 'Other utils' section of the 'Utils' screen.

> Warning:
> If your imported series of records is quite large (e.g. above
> a few hundreds), it is possible, depending on the system you are
> working on, that the process will be too long for the web-server
> (Apache in most cases) and it won't be allowed to finish. For this
> reason it will be necessary in such cases to perform the Inverted File
> generation action not from ABCD (as a web-environment) but directly
> from the command-line, using the dedicated CISIS-tools (for which
> another section of this manual will give the details).

  
### Copying an existing ABCD database

This last option is the easiest to perform, as only a new name and description need to be entered, after which ABCD will simply re-produce all necessary files into a new folder structure for the new database. The source databases from which you can choose are the ones listed in the database-menu, in other words : the database descriptions listed in the file 'bases.dat' in the ABCD bases-folder.

The system will simply - as above - list all files copied and created in their proper folder-structure and that is it ! An empty database, as a copy of the existing ABCD-database but with new name and description, will be available for normal use.


## Update database definitions

From this option it is possible to edit all existing 'structures' or definition tables related to a database in ABCD. In comparison with 'normal' ISIS-databases, and in order to support some more advanced features in ABCD, there are some more of such database definition elements, as can be seen from the following 'database definitions' menu :  

![](https://lh4.googleusercontent.com/VbTg7M4vPqy060v0DLr5r5Hc1-iRsXj23Hk5fpsyxo9t3FsRnhpk9wqnJihtlUXgiSE6tAD2IX6NN7u3NOM5Kl_BgCdV8N9ErylXlzgobzFoBdIcVwQP5y2592pTznr4MASFd16p=s0)

In fact only the first four tables are used in other ISIS-environments : the Field Definition Table (FDT), the Field Select Table (FST), the FMT or edit-worksheet and the Print Format Table or PFT. Since we needed these also in order to create a 'new' database in ABCD, they were discussed in the according section above, the only difference being that instead of an empty table a pre-filled table with the already existing definitions will be presented by ABCD.

Let us briefly deal with the additional definitions for ABCD-databases now.

### Type of records

Some database-structures, such as MARC, require the 'type of the record' to be specifically coded into a dedicated field of the record. The software can then use this code to adjust many features to the specific needs for the type indicated, e.g. worksheets and print-formats can be different according to this type, or simply - as is the case with MARC - the format wants to be very detailed.

The 'type of record' information needs to be gathered at the beginning of the creation of a new record, so a list of types defined (and therefore 'available') will be presented as links, each one leading to the appropriate subsequent data-entry form, as can be seen from the MARC demo in ABCD.

[!!] In order to define such types, ABCD uses a table 'Typeofrecord.tab' - located in the 'def' folder for the actual language within the www/bases/[DB]/ folder. This file is - as is often the case in ABCD - an ASCII-file which contains, for each type defined, 4 values separated by a `'|'` (pipe-character), so this can be edited directly with an ASCII-editor (e.g. Notepad), but within ABCD an easier-to-use table format is presented :  

![](https://lh3.googleusercontent.com/vxYJnzAQtoYOlQ42XpphksTV7sTvdyZ_1x92W50iot6_PXKSqKe2ieDqglYgSlHcjQL-FCxZ9Sy5URXL6kCe-FWtzROKyDW0N4DZWiqfRvM9NLbrbV9dq82EoyhnDzlaG1brsT2r=s0)

 
The example above is the MARC record-type definition, which is kept in (internal) tag 3006 and has the following 4 columns, each containing values for each type :

-   the name of the worksheet to be used for the given type of record - with the 'edit'-link next to this first column one can also immediately edit the worksheet
-   the 'Tag1' value, which is in fact a one-character code to internally identify the type of record
-   the 'Tag2' value, not used in this case
-   the description of the type as it will appear in the list of available types. Clicking on 'update' below the form will save the table with any changes made.
    

### Record validation
    
[!!} Record validation allows the database manager to define criteria against which input for a field can and will be checked before entering it actually in the fields, or after registration of the record. Record validation in ABCD can relate to one of the following elements :
-   record validation : conditions can be given for each field
-   begin format : code can be given to be executed when a (new) record is created, e.g. the date of creation can be added with the date() instruction
-   end format : code can be given to be executed when the record is saved, e.g. the date of last update can be added with the date() instruction.

After selecting on of the three options above, clicking on one of the listed (as pre-defined) record-types will show the editor where the validation conditions can be defined.

These criteria need to be formulated into - no surprise ! - the ISIS Formatting Language. With the Formatting Language one can check a condition and if (not) met, an error message, which will be shown on the next screen, can be produced by the format. [!!] If the validation criterion was defined as 'fatal' however the record will not be saved and the error has to be corrected first.  

  

In this menu-option from the 'Update database definitions' menu each defined field will be listed with a box to enter the validation statement. E.g. :![](https://lh3.googleusercontent.com/oKu8hUaxkI7DKnHNYYzV2n78dodM6df_kALvB7fNV4OKE31M0dUFYVaXevZtFtmCYmpX0qoAxSYXSV5HXNMQt1IP506Wqan-MpU2LTJslPAJNd9jIP_YtbIcqzFNMWt5DJ9J0638=s0)


The format used here checks on the 'absence' of a value in field with tag 2 and if indeed absent will produce an error message that this mandatory field is missing. [!!] As stated above, errors can be marked as 'fatal' or not. With the 'ADD' link in the left-most part for each field. As shown in the illustration above, with the 'ADD'-link in the left-most column one can add more fields, even fields already used with another validation criterion to be applied.

When clicking on the 'edit' icon to the right of the edit-window for this field, the box re-appears in a separate small window for editing and the statement can also be tested on a record to see if it is doing the right thing. After editing one has to click on 'send' to put the possibly edited validation format back to the main table.

### Advanced search form
    
The advanced search form is the one used in ABCD at two locations : within the cataloging module to allow the cataloger to quickly and/or efficiently identify a specific record for editing (or duplication checking or copying) and in the OPAC as the advanced search form. Here ABCD simply offers an editor for the table which defines that search form with 3 columns :![](https://lh4.googleusercontent.com/SorkLWvyRODpnX8jui2-hUL_LhB6NpILr_Za1vwKLytNe_4RfO-Lwp_tYm_V2A7ocRQSTA3GAejqLNWjzSDtsMvC6Hd05vWxnahjyTw50Euss-dbJHbefvokq_5FyuW9jjxGPpFL=s0)

-   The first column is the field-name or 'index' as it will appear in the search-form
-   The second column gives the identifier used for the given field (or in fact combination of fields) in the FST
-   The third and last column keeps the prefix or fixed start-string which is used (if any) in the ISIS Inverted File for this index.

ABCD will also present, next (to the right) to this table, the existing FST to facilitate the identification of indexes (fields for searching) and the identifiers used.

Clicking on 'update' saves the table, which in fact is a file 'busqueda.tab', stored in the language subfolder of the 'pfts' folder within the database folder.

### Available databases list or table
    
Here simply a list is given of the databases being defined as 'available' in the ABCD-system. Actions allowed here are only changing the sequence (by moving up or down) of the databases in the list and saving the changed list.  

![](https://lh4.googleusercontent.com/ft7Snl4rGz9hwaRty5XTgrPAanSM3zHrlHabOyEuj_6mGagJThOV6Hgc51WR9IXzKukInGcRBM1n-7l_3KyXpcOY0W4TUEem3QaYg6km54S0Tq2MkaianL_pJ1g6UH6QhNmP_x3n=s0)

  
For adding or deleting databases one has to actually create the new database or delete the one to be taken out of the list. ABCD will take care of the changes in this list automatically. [!!} Databases can be moved up or down by selecting them and using the UP/DOWN buttons as in many of such controls in the ABCD-interface.

### [dbn].par
For each ISIS-database in a multi-database application such as ABCD, there is a file needed to tell ISIS where to find the constituting parts of the database-files - which then consequently can reside anywhere in the system. Such files are named after the database-name (therefore indicated here as [dbn] with the .par extension. Again this is a simple ASCII-file which can be edited directly or, as is the case here, from this ABCD-menu.

  
![](https://lh6.googleusercontent.com/sJjlKFYiUph88YKCmjJvYnTZSiNFZUPnpIV3_aoEu2dX2GZ7iQ4_z5U71JO6GeRYcCRvfVWIy14Ic34k6X2gZjs1dRVw7kkpQbf9xMsUYulJVbHaIDhR5YAhzQnNOhHgi5ubFvt4=s0)  

In principle ABCD will take care of this file and make sure that the necessary paths are available. The only special feature here - as compared to the same concept of dbn.par in other ISIS-environments, is the use of 'variables', taken from the operating system's environment variables, which can be dynamically substituted for their actual values. E.g.

    %path_database%

is a variable which actually will contain the database-path defined in the config.php main configuration file of ABCD.

[!!] In the example of the illustration above, the last line is an interesting one as it gives the path to the 'loanob- jects'-database for displaying copy-information (if included in one of the MARC-pft's) with the REF-function. In order to find the loanobjects-database for the use of REF->loanobjects, ISIS needs to know the path to this other database and therefore it should be included into the dbn.par.  

  

> Note [!!] For this last feature also to work in the OPAC (iAH), one
> has to add the path to the first section of the dbn.def file. E.g. the
> loanobjects-database should be pointed to by a new line there
> containing : 

    FILE loanobjects.*=%path_database%loanobjects/data/loanobjects.*

### Help files on the database-fields
    

For each field in the database ABCD can provide a help-page, which can be edited from this menu-option. To support the creation of such a page, ABCD will automatically put all known information from the FDT on the given field already available. With the built-in (JavaScript-based) HTML-editor a real nice help-page can then be produced and saved. The 'preview' link of course allows checking the result of your editing effort.![](https://lh3.googleusercontent.com/86HYiZn_9klIyIPWshK6DiZqkH2UUbz3FDsEAfldXlD_OaOAbmvNTq7tKWm9nDicDZo8eqSAK0WoFf2AhTvtNCaEWnWnXfdLLy120Yqt8LJ8RlCX_xLHWnz2ZjGfbeohmeKpynE8=s0)

  

### Configure database in iAH (or OPAC)
    

[!!] In order to be able to use a newly defined ABCD-database with the advanced iAH OPAC-interface (or in the ABCD Site), a special configuration file is to be edited : dbn.def. (where dbn has to be substituted for the actual database-name).

This file has the following sections to be edited :

  

1.  The FILES section : here the paths to the files to be accessed need to be given. In this path both the `%path_database%` and `%lang%` variables can be used to refer to resp. the actual database and actual language in use.![](https://lh5.googleusercontent.com/XzbGmhr000O_9jU0KhhbX-0UJLCR9zI0rLo-L_A0z13CZaPHFL6UbDRpB4-mwbuKLBq7ep2OfyAsBpTNPfhGjrU4ZYHDKPzqQXk-Z6ByNQIIuekR6Czye_oWsRW1jnZYh4VU6yHp=s0)
    
2.  The INDEX-DEFINITION section : here all the information for the active languages (numbered as 1, 2, 3 etc.) has to be entered (in subfields) to allow the interface to recognize the prefixes used for each searchable field and to name the field accordingly. The first line with prefix 'TW_' is the one used for the 'simple' search interface (Google-like) for searching words from the fields defined (by the prefix in the FST) to be included in this simple search. This is indicated by the presence of the subfield `^d*`.  

3.  The GIZMO section : here - if necessary in specific cases - gizmo databases for automatic substitution of strings by other strings (which can be used to change character sets, but also change codes and abbreviations into full values etc...) can be pointed to.![](https://lh6.googleusercontent.com/i3z71qKLcIxk8mqXAMyAccsJ2Hx1QG_uB2OvNG9nlLNCryQDE2QUmKbltjRbUYsjYLrA2Kgl1hD3RkO8NqA_30i9U9xZ2_WcrsnJIx99Y0NHHKhYuP-UO8avSXhZdu0H091ud26f=s0)
    
4.  The FORMAT section : here the display formats used in the OPAC should be defined, with for each language (in the numbered subfields) the label to be used on the screen. Remember that only formats (files with .PFT extension) can be used which are referred to somehow in the FILES section ! Also the default format can be identified here by simply indicating which format earlier referred to should be used as default display format.
    
![](https://lh6.googleusercontent.com/njC4b_3cU7HUeqbQOeT3bVrsJ7jbEngMbisQdVhUxB8g5FYzmUFkZJlS3ISRFVUA4VzKmcgYnMmKeC4S1DA-aUGa0AD-vWEgeh3cz7GIGIkfFLzrCTgykCUDhru5dhvsYScb6PeX=s0)  
  

5.  The HELP form section : here simply the (HTML-)files containing resp. the help-page and notes-page for the user of this database in the OPAC should be referred to.
   
6.  The PREFERENCES section : here the system manager can indicated which of the three search interfaces (simple, advanced and free) will be available for this database, and some other additional features of the inter- face : whether sending a search result to an e-mail will be possible, whether the results should be listed with navigation buttons, the number of records to be shown in one page and whether XML-export will be offered.  
  

![](https://lh4.googleusercontent.com/SUqlv_DS-5N3Kxc36LQEGCNl49_0RclTci9RUwEjAFbRTp6F3rm55qyt1apeIPfGjOi4985rdzkLB6gKnntkAsckRq8NX5AxOQoTndC8SeZZQj1iZnwto9U4jj5h32emFdv_LRgp=s0)

### Statistics : list of variables
    
This option simply allows quick definition of the variables from the given database with which tables for statistical analysis will be computed. For each criterion or variable (either as row or column for the table) a name and an extraction format has to be given. The extraction format - using the Formatting Language of course - exactly defines how the values in the field should be taken to compute the value in the table. By doing so it is possible

e.g. to define ranges of field-values to be combined into one table-criterion. The file at stake is actually 'stats.cfg' in the (language-specific) def-section of the database-folder.

  
![](https://lh3.googleusercontent.com/wC2Pm3_FdQWQeRseA-9bJvV9cek-D4kLLVBFCxGOiBsn1HP357CwdJfYTJmOMXU-96a4o38eL5Tim6ZbtxW3UaQ2mZBIdfbO0Z3elCOPoEKLu_d9OnmbOqdNYdqKhVnHKHPfY5H4=s0)  

The option to define a prefix is not yet implemented in this version of ABCD. The idea is that the values would be taken from the Inverted File, prefixed with the string defined here. By doing so the values would be computed while 'inverting' the record, not at the stage of producing the statistics table, and therefore allow faster production of the table.


### Statistics : list of tables
   
As with the list of variables above, ABCD also keeps a simple list of available tables, which have been defined previously, for the statistics module. This file 'tabs.cfg' equally resides in the def-subfolder of the database. Each line in this file contains three values (separated by the pipe-character) : the name of the table followed by the two criteria used in this table, e.g. :

Classification code / Publication date|Classification LC|Publication date  

![](https://lh5.googleusercontent.com/4Yz-wvMo6dXPEaPLOyoNg3QkqnJqEGBFyWf8_UA5gUKhPkSqtEF-8Gpnyawe6T1qzTzTYjtg0iihrGdCocgsiUnbthqSA0Z8AQ8c9EbXYfmOGC2xQuOu13xg5fCSrREfP1xE__W9=s0)

  

As can be seen from the example the editor in ABCD simplifies editing by providing each of the three values individually but also by providing lists of available row- and column-criteria.

## Reports
In fact creating reports in ABCD means creating ISIS Formatting Language formats (PFT's) with which the reports will create output, because with the F.L. any type of report can be produced and saved for later re-use. We therefore refer to the section on 'Display Format (PFT)' of the 'Update Database Definitions' Central menu option. Exactly the same interface is used here.

## Utilities
In this option ABCD offers some very basic operations on databases :![](https://lh5.googleusercontent.com/jHTrAoEZoonuu-fniMYnXtwtpKFWZ6iSyvT3yhksNy7-s0LYqs7QO2znmgtGZIcv0ZK6sRt04TJusqcNN0sYDMT4z5_Cr8dopMFvIUjDBqop84967SdUx8E4SeYZLSSSzE7zOLzo=s0)

-   Initialize the database means to delete all records in the database but without changing the structures of the database.
-   Delete the database of course means fully deleting the whole database with all corresponding files and folders in the ABCD bases/ folder.
-   Lock the database means to prevent any other users to make any changes to the records (data-entry), e.g. when a full Inverted File generation would be envisaged. 
-   Unlock the dabase of course then means to avail the database again to other users. Use these options with all necessary care and caution !
-   Assign Control Number is the option to automatically put sequential control-numbers in a series of selected records. Only a continuous series of MFN's can be selected here.
-   Link database with the copies database : as explained on the screen itself, here the option to activate the use of the copies database for the actual (bibliographic) database has to be activated.
-   Reset Control Number is the function to manually re-set to a specific value the numerical value in the file 'control_number.cn' of the database, in case for some reason the numbering has to be managed manually. E.g.  
setting this number to 1000 will make ABCD to assign from the next record on control-numbers starting from 1000. This could be useful in conditions where e.g. different cataloging centres are using different ABCD- servers but the resulting databases have to be merged into one catalog with control_numbers not interfering, so covering different ranges. By default however reset will revert to 1 as the basic control_number to start from.

## Z39.50 Configuration
    

Here the ABCD interface allows setting some parameters to define which servers for Z39.50 shared cataloging services will be offered in the Z39.50 list and some more parameters to ensure proper use of the protocol for the server. Such technical information can be mostly obtained from the service provider, e.g. in the case of the Library of Congress consult the following website : [http://www.loc.gov/z3950/lcserver.html.](http://www.loc.gov/z3950/lcserver.html)

Configuring Z39.50 has the following parts :

  
![](https://lh6.googleusercontent.com/ITrPEbvuGaSe7_zQeYSHHfBd8_KKHSWJsncTede3hrzK76SanHdAtZjXecP_pYxAyswJym0WD0ISJA6wUAyjsQnW6LLxVAtjEScBwW0oZzCsDfb_aeIeOPszhN3x5QAu_e6j1TEk=s0)  

-   Configure Z39.50 servers : in an interface similar to the one of users-administration, the defined servers are to be configured, with the parameters name, URL, Port, Database and UTF-8 (or not), see the illustration under here for Library of Congress. New servers of course can also be added with the 'Create'-icon.![](https://lh5.googleusercontent.com/7abTBVqO1hMgGJI9lE5T0J-uC7hF66DKPF5C6CeZRd_UNwgYg26RwJpWkQtqiLn5cexTN8GeCRpM_i5W2wmOblqxOE7LVLQM-Et_9rjWsje-gZ-KUg9SdWyQOmI9JUHnl94HGTaI=s0)
    
-   Conversion formats : when the incoming records (mostly in MARC21 format) need to be converted to the format used in the destination database, a form can be edited here to specify the conversion from source to destination. The name , subfields and tag of the incoming field will be listed and in the 'Conversion formats' column the ISIS F.L. defines how to extract values for this field in the destination database. ABCD comes with one demo conversion table to convert from MARC to CEPAL formats, with the following example for converting the ISSN MARC field to CEPAL.![](https://lh6.googleusercontent.com/NzKlW54uaVPpDnsfqjqhPihGxAj66yQpcXmYVXHYXu5M8vlScNcr5oPrnfojykpvvFvtsgN7pKjEJo7AgjPN5-rgnPcJU-ROa-Jr1gDy3R-h9eOrjkWjbNAV4ku1XRobgzBvN_I3=s0)
    
-   MARC-8 to ANSI character conversion table : this is a table which converts characters from the MARC-8 table (e.g. âa) to ANSI format (e.g. á). This table can be edited here if necessary.
    
-   Finally the Z39.50 can be tested from here, with the same interface as used in the ABCD Data-Entry module (see infra).
    

## Translate messages and help pages

There are two types of language-sensitive content which ABCD uses and which needs to be edited when creating or adapting new or other language versions : short messages and labels on the one hand, full help-pages on the other hand. [!!] These can be edited into other languages for each module of ABCD Central.

### Translation of short messages and labels
  Editing these is facilitated by presenting the default (English) language terms and phrases in a table in wich in the second column the new values should be put by the translator. For each of the main functions such a table is presented:  

![](https://lh6.googleusercontent.com/m1hz1TJkkEYhsRxPYlyht1xMnpY6J0i5-pz0mnnWpYx6X55NuFqRs1ImHIPUDEQRMqmdmn_d-E0A8mysiZdHBaxbXTo64z97dJiR8n2cgRGBg1yjG-rJaiUIfIl_YxkxeSo0eUX-=s0)


Here is a sample of some messages translated from English to Dutch for the loans module:![](https://lh3.googleusercontent.com/O0iI1_pPKlVklFOKS-sGzp3vgeYfzn3osmyn-TV6Q6TYBX1DrmZ1VSExhfOWIuH6KrS6FrRZcZJjnz-w-me5BVRgeZlGt4TscelQuLcCZXHKIh04XkhhyEqZACxI1miCqJyBBcA6=s0)  

This screen provides a 'save' icon ![](https://lh3.googleusercontent.com/dXAH4i_glKZgtTCotEYcefBtDLWMyqWrBU9S9YAu6qxRLhe8UD8VGqaIIYhqZKLcGCmLOQwwyO9HdFGU20PzL6iJjEbTIAMcnDH4Sg2AlZCGVOeqlUZh69EVziP-zzlx3StZuLNP=s0) for storing the table with new translations.

### Translation of help pages
Here the approach is different : a list of available help-pages is given ![](https://lh4.googleusercontent.com/W84ZVXybbCMZqEaGoEVBhZ0kEuuMULAumIlD2Fgkgi2Br3ZacVBgWZUtlxSXNVjYFkocdIrNEGOcNXzQUmMQmSskQ6vI_b58cOKlrD0zZFqOvqk9O0EVkyfbyOE0F8BC02bQRSmr=s0)

  
and for each help-file one can 'preview' or 'edit' the page. In the case of editing the built-in JavaScript-based HTML-editor will be provided :![](https://lh3.googleusercontent.com/6p6kLKxf78YCkDM7Agwx-OgiarG2cPyZ-SlpwoJnzqu6pZ2baVtKRuJiGGU1uEFyBMOLl1I09ulIJcq5c18t10V36CLKPQa3UEXd4hMs9TdodCmAR3FpGahQCngPuOTYnV_PCBAy=s0)  

  
## Explore databases directory
    
[!!] Exploration of the databases directory can be done (when the dedicated option variable '$dirtree' is put to '1' in CONFIG.PHP !) using a special display in the ABCD-web-page of the folders of the database-folder of the system,
![](https://lh6.googleusercontent.com/0aF6Wene-a2HY8S_9g8yTE19Qdn195lR3Dppjawr4Y0sLECjEl6fQuAkwgcXOPYQJb64s5Kd2yd7-DBp8IWQnFchTEvETm9VDo6XtuFdyvJ-_nmSac7u_r3PEOKRX4eOxL9PNZfE=s0)

with some possibilities to enter within subfolders and even editing, renaming, zipping etc. some of the text-files
in thereon by clicking on the 'details' icon ![](https://lh6.googleusercontent.com/auQdMSP6XtrDRMBZbxonDmbg01ii0m7BKIUjaxtxWEJK_CccgXfNI11wiSCVaXkrHF6a3dHiqe8OXB1HAz7FtiOKUAqQiLNjTKVEfuwFseFHKSPJNBmRycQ9NUWAFPWXBRmeAYSw=s0) , given e.g. the following options to apply on the selected file:
![](https://lh5.googleusercontent.com/7wIzZpzlZ9Yo7YsN4mLs1N3z7Iiw9Hduh8FhK6rPUtFK_X8GurPs6qCU-Ya9UyoYjEyKG0iRMWY0ExHQ8_E6-PkCQcKZH0BU4piwyH1bl9SZUID694XNos8my4iYpchMWXWoAmKb=s0){:class="img-responsive"}  

## Statistics

The Statistics module of ABCD also has a dedicated chapter, so here we just refer to this chapter, as this function can also be accessed from this menu but also from the cataloging toolbar and several menu's in the acquisitions and loans modules.