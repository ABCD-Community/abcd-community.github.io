---
title: Central module - loans/circulation
description: This section is about the ABCD basic loans module as it comes pre-configured with the system. Still, always following the ABCD philosophy of flexibility, the loans system can work with any bibliographic and objects database.
lang: en
lang-ref: abcd-modules/abcd-circulation
---

# Central module : loans/circulation

{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---


This section is about the ABCD basic loans module as it comes pre-configured with the system. Still, always following the ABCD philosophy of flexibility, the loans system can work with any bibliographic and objects database.

In addition, ABCD offers an 'advanced loans' module (EmpWeb) which can cope with much more complicated situations in e.g. multi-branch organisations with different loans policies etc. [!!] The transactions in this Advanced Loans module will be stored in SQL-tables and it can also access user-data (through WebServices) stored in SQL-tables elsewhere in addition to accessing the user-data in the ABCD-user database (in ISIS-format). This of course allows very advanced high-performance applications of the loans module. In addition EmpWeb or ABCD Advanced Loans will offer a reservation function and a function 'MySite' where end-users can check and keep track of availability of loan-objects in their personal (password-protected) account of ABCD-Loans.

[!!] This advanced module however requires installation of additional software (Java/Jetty and an SQL database) and is only offered as an optional extra module.

We suggest to check the following criteria in order to decide on whether you will need the advanced module or not :

-   multiple servers in your system ?
-   multiple users/copies databases in your system ?
-   high volume of transactions ?
-   any data source needs ODBC drivers ? (ODBC drivers are software to couple mostly relational databases or SQL-tables to software)

If you have a 'yes' with serious importance for your system, you will be better off with the advanced loans module. [!!] Most smaller libraries however, certainly where there is a lack of expertise on using Java and SQL-databases, will be better of with this ABCD Central Loans module as it is fully based on the ISIS-database technology and doesn't need any additional software to be installed.

## The ABCD inventory copies and loanobjects databases
  
ABCD uses two different databases to deal with information based on the physical objects in the library : the COPIES and LOANOBJECTS. Both databases have different purposes and scopes and therefore the data are kept separate. A good understanding of their different purposes and structures will help in understanding ABCD. Let's discuss each of them here.

1.  The ABCD copies database.
  
This database has the function of keeping track of all administrative data on objects in the library collections. These data in principle need to be kept for inventory and book-keeping reasons, whereas data related to loan- objects can be deleted when the loan-object is removed from the collection. Actually the record created at the end of an Acquisitions procedure (from suggestion to received item or anywhere in between) will be stored in this copies database. The copies field structure is as follows (field tags are followed by the field name) :

  ``` 
1|Control number
10|Database
20|Call number
30|Inventory number
35|Main Library
40|Branch library
60|Volume/Part
63|Copy Number
68|Acquisition type
70|Provider/Donor/Institution
80|Date of arrival
85|ISO Date of arrival
90|Price
100|Purchase order
110|Suggestion number
200|Status
300|Conditions
400|In exchange of
```  

The field 30 (Inventory Number) is created by the auto-increment mechanism of ABCD : the next number to be assigned is stored in a small file 'control_number.cn' in the data-folder of the database (in this case COPIES), as each record has to be identified by a unique value which can be used for linking from the other databases (as 'primary key').

Differently from the LOANOBJECTS-database the COPIES-database has one record per object. These records are normally created by the 'Add to copies' function of the cataloging module.or the Acquisitions module.

This database has to be indexed with 2 mandatory keys : 
```
1 0 "CN_"V10,"_"V1,
200 0 "STATUS_"V200^a
```

The first key here assures that the identifier of each copy can be quickly referred to by the prefix 'CN_' followed by the bibliographic database name V10 (because several catalogs can be combined into one copies-database) and the identifier in that catalog itself (V1). For an entry in the copies-database to be allowed to enter into the loanobjects database it needs such an entry in the Inverted File (and assumed the status-field is at least at level 2, which means 'verified and stamped', that is why the second FST-entry indexes on the status of each copy).

In the cataloging module copy records will be shown in a separate smaller window when clicking on the 'Add copy' icon of the record-toolbar and then on 'show copies'.

2.  The ABCD loanobjects database

This database has different goals from the copies-database : it's purpose is only to provide the necessary data about all objects which can be used in the loans-system. Its contents are quite limited :

```
1|Control number 
10|Database 
959|Copies subfields :
i|Inventory number
l|Library  
b|Branch library 
o|Type of Object 
b|Volume
t|Part
```

As can be seen from this very short list of fields (in fact only 3), each loan-object is identified by its con- trol_number V1, the bibliographic database to be linked to `v10` and the actual details on each copy as a repeat- ed subfielded field `v959` (this gives, in ISIS-technology, the fastest performance in case of high number of copies). The subfields allow to specify the unique identifier (e.g. barcode) of each copy, the main library and location within that library (e.g. shelving information), the loan object type (books e.g. will have different loan- parameters from video's) and in case of a multi-volume work the volume and part - identifiers.


The loanobjects database has to be indexed with at least the following instruction : 
```
1 0 "CN_"v10,"_"V1
```

because (as in the copies-database) the string `'CN_'` followed by the catalog-name and catalog-identifier allows each copy to be identified. If this entry cannot be found in the loan-objects database for a given book, it will not be possible to use the object in the loans system.

Loanobjects normally are created from the cataloging module after having created the according inventory copy with the icons in the record-toolbar of the cataloging module :![](https://lh4.googleusercontent.com/ebH3FxIFkYNd33i369lT3THlc09YBpK2rfnRVyX0dXK6ip_47_BEbMTnPYt9Bydfde94zRRI_TL2zlTNK2G4a8w7fh6xesi1u9UQ8KtH586nOumZCpzit89jR7jAouWGS35hRFTH=s0)

After having clicked on 'Add to loan objects' the record will have been created in the loanobjects database. If this database is to be edited directly as an ABCD-database, remember to include it in the list of databases (bases.dat, which can be accessed directly from the Operating System but also through the corresponding 'Update database definitions' menu in ABCD Central) and to the profile of users which need access to this database directly. There the loanobject records will be presented for browsing and editing in a table format (as explained in the section on the FDT-definition for 'group'-fields).
**![](https://lh5.googleusercontent.com/kGCCdxZMk5AkkHsZpOEWtuv7D6zocGllu-_hJZ3x85CX9BwTH8-yR8qOP2KR7IzRhCFHAfr_DIOrcudDcu9pGgX1PifR1xEGymxHSIQHUe2JaW7kirMS4migH5EuTQqVVLuLPSko=s0)**

## The basic ABCD loans module
    

### Introduction
    
This loans module is called 'basic' because it is fully integrated with the other ABCD Central modules, using the same underlying technology: ISIS-databases, ISIS Script and PHP. Looking at its functionality however one could hardly call this 'basic' : this module takes as its departing point the 'objects' created by the acquisitions module into the database 'copies', to apply rules on all kinds of 'transactions' on them : issuing to a user, returning, reservation, loans renewal. Rules for all types of transactions can be defined and will be applied according to the object category in combination with the user category. Categories for objects and users can be defined 'ad libitum' with specified number of objects, hours/days (taking into account a calendar specific for the library), fines and renewal conditions for each combination object/user.

The main menu of this loans module has three sections :  

1.  Transactions : here the real every-day loans transactions (loaning a book to a user, returning it, reservations etc.) are dealt with. 
2.  Databases : here the databases on which the loans system is based can be accessed and managed : the borrowers or users, the transactions, the reservations and the fines.
3.  Configuration of the loans system : here the 'rules' can be defined for combinations of object types with user categories, and calenders, currency etc. can be defined.
    
    
### General loans parameters and configuration in abcd.def
The file 'abcd.def' (in the bases-folder of the ABCD-system) contains the parameters applied to the whole system. Some of them relate however specifically to the ABCD Central Circulation system. A brief listing with explanation is given here :
  

Table 2.2. ABCD Central Loans configuration parameters in abcd.def

|||
|-|-|
|LOGO_OPAC|Url of the logo that is displayed in the key request, statement and online reservations|
|BG_WEB|Background color of the key request window|
|WEBRENO- VATION|Y / N to enable / disable online renewal option|
|RESERVATION|Y / N to enable / disable access to the reservation process from the loan menus|
|LOAN_POLICY|BY_USER to indicate that the object type of the item to be loaned is requested at the time of processing the loan. This option should be used when it is not provided from the database of copies and the inventory of the objects does not have a subfield with the type of object|
|ASK_LPN|Whether or not the option to request the return date is enabled, ie not calculate it from the policy|
|E-MAIL|Y / N to enable / disable sending loan reminder emails|
|AC_SUSP|Sets the date from which a suspension begins. The Y value indicates that it must start from the last active suspension of the user. The N value indicates that it starts from the day it is recorded.|
|CALENDAR|To establish the way in which the period of fines and suspensions is calculated|

As an example section of the abcd.def loans configuration parameters :
```
LOGO_OPAC = ../css/logo_opac.png
BG_WEB = #ffffff
LOAN_POLICY = BY_USER
WEBRENOVATION = N
EMAIL = Y
RESERVATION = N
```
### ABCD Loans detailed configuration

The loans configuration in ABCD allows to define which source bibliographic databases (catalogs) to link the loans system to - it can be any database indeed ! - and to define the parameters which will constitute the 'policy' on each object/user combination to be applied.

  
![](https://lh4.googleusercontent.com/sTSX8m20ZtRIqe_0xI2Aow6MCkzq2IKRgsez9Y1uFaMtPmzrP5T5vTr8I5Bj8yMcta0aDo-dtaM7Hi_x_MhzEnIeymKyERV_gq_i_y4BSN0iqk3qjJWMFEujxmNQUm5vufSLUtZF=s0)  
  

Since any database can be linked into the loans system as 'source', there is a need to explain to the loans system how values from these databases will be used in the loans system. We can best illustrate this by giving the example of the CEPAL-database of the ABCD-model application :
  
![](https://lh6.googleusercontent.com/h7xGmc7cp6O_342sS27bUebhaGIxmi4VKgkcklq-wToV2RPH3Va0u516LtoKGGGW9vrxNnojG4j1wj_FnM6DlrKYH-cef3nxDIqtvJyWH_RWtXYb22d1qIAYQYOhtCSKoYz8Fyir=s0)  

This form shows the information needed for the loans system, e.g. which prefix is used in the index for the accession number or which print formats (PFT's) to use to produce the data in the loans screens.
  
The power of the Formatting Language can be applied here, of course. For example, instead of the rather dumb example above here as the 'PFT to be used to extract the type of record', one could define a different type (with consequently different loan parameters for the type) according to some conditions, e.g. the date, the month etc. So an object which is a normal loans object could be changed into 'special material' during the exams period etc. The ISIS Formatting Language provides most necessary functions (e.g. Date() with substring extraction) for this purpose.

The same applies to the definition of the borrowers data :  
![](https://lh5.googleusercontent.com/wLOo5NOPZiHWg8B6Q_CjF0m9mR2RzeXUCLnVsq1tW0ZfAHMdc2fwA78d5O8Ru6jftpDJylLdO3Q9kSUdrbT5QHMkAUWP_OoV_04llaElodP34f2P85W5v-SBU_c6R2IJStUg_hH2=s0)  
  

Instead of simply taking the 'value of Field 10' (v10) to define the borrower type, one could put a more sophisticated Formatting Language statement here in order to make the status of the borrower even dynamically dependent on other conditions (again : date, but also other conditions can be defined).

  

Using a table ABCD will then present the defined borrowers types and allows to add any number of more such types :

  
![](https://lh6.googleusercontent.com/rvBEt9ZoDB4vhrenRG6GVP_Y6qrhT50iL2aEPYiQ6jn08m1lDIZX4wgr651YWZ7VCTx5CRRMietK4pOn70_EqXwuKpWuwkIx8WnGmn5TNQj3POl9vpQpWXb-Nbnu8_hhSNALD7od=s0)  

Here we only show part of the table, but in fact the interface will always offer a few more empty lines to add more types, and lines with a type can also be added in between existing rows.
  

The same approach is used for the definition of the objects types :

  
![](https://lh6.googleusercontent.com/9ZQuOp9pys-PFpi8L6PsUNltDDpNeCybMppbHj7FAwmInaCgk7Uve8lr9W4xv1G0o4YKeGi0RxQX5NJzhUHuT7-_H8EZl7mm5XpT8riELdt3FViKkMPHYkz-1IgtnN5QTW4HRX0T=s0)  

Needless to say that each time a 'cancel' or an 'update' button is provided to either cancel the editing of the table or to actually store it again.

From these two types (users and objects), ABCD then creates the 'loans policy table', which lists in a matrix all possible combinations of user types and object types, and parameters can be entered for many aspects of the loans policy :  

As can be seen, lots of parameters are stored and used in the decision-making process of each transaction (e.g. is this user allowed to loan this type of material, how many of them, for how long, what is the fine for late return etc.). Units can be either days or hours and the calculation of 'number of days elapsed' will be based on a calendar function (see below).![](https://lh3.googleusercontent.com/68czHaXI1MwuSNOueTQ1Hz50sP4MUFXCPzyaXHNHxkj5RNSC6ORJrtAWCwlPaLFpYqUvt4I0keY__bzVRiSRzB3yqgZdknJ0IiSov8_xc17mTndZnW9Mb0poqriCx-RhXGwI6-_U=s0)

A special (new as from v1.5) feature is to allow the librarian to divert from the stored 'duration' parameter : at the time of lending out the number of days or return date can be changed manually, making it different from the official calculated duration according to the defined policy. For this a new parameter is to be added into the file abcd.def : 

    ASK_LPN =Y/N.

Configuration of the loans system continues with two more options :

-   definition of the currency , fine unit, date format and working days/hours :![](https://lh4.googleusercontent.com/6beCi6irD2Sl-95UpAmWFP6E3oX0exc4-MVfMYi8w3LfRspcOaJ61E4cZG_C6pq-LjZFQi9_w42A3UG-xAyernChFj4nNQJbQpC-XE4vT3l8IH01rC31KV3g-0vWzD_2Bb5CLWTM=s0)
    
Caution

In order for the loans system to work well, don't leave this 'working days' calendar empty ! If no working hours or days at all are defined the creation of a loans records will fail as no return date can be calculated.
-   definition of the holidays (non-working days) in the calendar , where simply the holidays need to be indicated on each month's map :  
    

![](https://lh6.googleusercontent.com/Mnn3D39lRsOzRc4pYefnVMSjV8Xg7d6yAIuKN7cqWRUR2GAhG8NKlE875jD7DJCnHTvewPZbYKkXASR5Er_YrKs6acSpIb9X-SU-IXgkgLF_RTOrHSi3Nel7C-OUGEBcZaDWJfyc=s0)


-   generation of Loan reports : for each database in Loans (transactions, borrowers and suspensions) a set of PFT's (as these are in fact the reports in ABCD) can be generated using the same interface as used for other PFT's (e.g. in the Database Administration module). As the procedure is fully identical we won't repeat the steps here, please refer to the dedicated section in the Database Administration module chapter.
    

  
![](https://lh6.googleusercontent.com/ZbZ4sQHpFvItLVlZFSJLnen4LXmtqY_1UHnpgTPMH5HZZAAE1LjYeGqmWsDU_y3Rs-HoG-tP05AeYF_4TwqPuVoQtYwYnveZQDlddxA4tt4rDCrB8xz0SRR8ujv39ZdGJTPGb2ot=s0)



### Transactions : loan, returns, reservation, renewals, fines/suspensions
    
Most of the transactions themselves are rather easy to understand. Efficiency is the key here : mostly the system simply needs one or two bar-codes to be scanned in, and pressing a button 'go' to store the transaction. A list of possible transactions is shown in the transactions menu of ABCD :

![](https://lh6.googleusercontent.com/6YnR4t80Fo-q_PImJMADjjLBRhvSwuVztD-euVPu8xKn9CUluSkpgZbu4CUs_vsa76xRyU1bNocTynaY9QfLixkAE3dpYUdkEDYdDa0W2ka6gJlfe6Rh-EpNUNzlqSd3wQbdZopq=s0)


Let's discuss each of them now.

### Issuing a loan on an object

This page offers identification boxes (in which either the barcode or identifier can be input directly or selected from a list) for both the object and the user, the two crucial elements of any loans transaction.
**![](https://lh5.googleusercontent.com/2fSP_FSboOOmsz4xUSc1Lic4_q2oWHVsi96DlslGybteqcosWYQrBVd_X6eeifoRqgrHG7Inzhw0usASxEpM3YdgwZoay99bKe0yupLlcr964JpjnctEdNf4sifJkjbtTe74bkJl=s0)**

After having identified both elements, a simple click on the 'loan'-button will actually create the transaction (into the 'loans' database). The user information is shown and all loans transactions related to the users will be listed in a table, where one or more transactions can be selected for immediate editing (e.g. returning or renewing the loan).
**![](https://lh6.googleusercontent.com/DG-5Au7hLm3P8FkTDwtLddB-9O4lavdXbFC5VT-TmOZp5sjYuTa_ahs6NhC7GvJNmXEZyDviRFKc1PeHars5e2fdH9R0ZfteTTCwNoutFuK7wXLC0YLczI11kAsmpjJvDjtTPYEr=s0)**

### Returning an object

Here only the object returned needs to be identified and with a simple click the transaction record in the loans database will note the fact that the object has been returned. The loaned object can also be returned from the table in the borrowers' statement, then the transaction will be removed from the table. [!!]

### Renewing a loan

This is a simple continuation of a running loan, but dependent again on specified rules as on whether the object has not been reserved by someone else and the user requesting the renewal has no pending fines etc. When consulting the list, only the objects on loan will be listed. In case all conditions for renewal are fulfilled, the transaction will be granted and listed, if not a warning or error message will be shown, e.g.
**![](https://lh5.googleusercontent.com/dNWC1wNy2xvr5fLMeStDh38yRPprjj19dRzXCNbGO2aca_a0yvZOkGsmT0p0YbLsVyN9zWRaH5Eo8H5bF1XoIJpi6KC-Ofs0xrV4nvgv4YjeA1J-c_XaQbq4WvWA5HxGkLzXsGkb=s0)**

#### Fines and suspension of users
   
Fines and suspension of users are offered in the same ABCD-page :  

![](https://lh5.googleusercontent.com/1J4Vidce2YbB_6jVMmf6wAB-YeamvQH9AHbftJXf3Ofzmz-v8BC-p19SiJCcwnLXK9xbD5XOg_11WesLtwUf0lROIheLG4ZWWzRU31wF2wIqQT7wh1cBSQ91nm_ve8_yZQ1adc9r=s0)

For the selected user the following fields can be filled in : the type of sanction (fine or suspension), the date, the number of days or the amount of the fine, the reason (motivation) and any comments.

#### The borrower statement
From this screen all information on a borrower or user is displayed, giving also direct access to other functions where only an access from the object was given, e.g. to allow renewal from the borrower's identification instead of the object.

[!!] Interesting to note that borrowers not only can be selected from the list of borrowers but also from the inven- tory-number of the objects loaned by the borrower.![](https://lh3.googleusercontent.com/P3gCoCY1EOshWnu8CqoEttEP8TRkzcD8WJtMDOoltTeQolpp_nA0m9CR9yLB0_XGcwECixpxrHU4MWXS7F1S_u0Hn3Fz1N21xlVmxoNnUgsBHRPaxPvwbPwYkWR2UZEOooDouS1A=s0)

#### State of an item

As with the borrower's statement, an overview (history) of all loans of this given item or object can be retrieved here.  


### Databases in the loans module![](https://lh5.googleusercontent.com/VUKJlGTEWKWBRywofBDcrrQvb5DCBlM59Akf1-yNTdUhSNCjDt0y4UVO0SVj2V0js_wNSTU0C7snhq9kM7uGDAPOEVZkmXIay5aYhyot1_zl5u7Z5jHQDoFIZGdgF3J_8pT4sx12=s0)
    
The following databases are used in the Central Loans module :
  
![](https://lh6.googleusercontent.com/PvShCrOz6KIGdgpDbGO3nzwBxaGICizAb9MfG2o0cySUvNPQdmKVA64nVBzBbt2_goOGTchRTDk4iYJfLthjSuTNVwBSjQ_fwLBqpTYRoAUf2XK2own5jNW_MzEiJv8eJjVRYnsv=s0)  

For each of these databases, whose names explain their purpose, an interface is presented which lists the records with a search function and edit or delete buttons.

The transactions database records the actual events in the loans system. ABCD opts to keep this database as 'mean and lean' (i.e. compact) as possible, without duplicating data e.g. from the bibliographic databases. This database will be rather 'dynamic' with many movements, and since ISIS is not at its best in such environment (for which simple tables with fixed structures would be more suited), we need to keep its structure as compact as possible, using the REF-function of ISIS to 'loan' data from other databases, e.g. the bibliographic data.

So this will allow the librarian to directly interact with the records of the borrowers (e.g. to create new library users), the transacions (e.g. to check a loans record), reservations and suspensions or fines. In this last database the librarian could interfere with existing due fines and suspensions of users in case of a necessity to do so by- passing the rules - take care !


### Loans administration
   
This third and last section of the loans module not only offers the loans configuration option (discussed above here) but also gives access to the Statistics module (which is also discussed elsewhere in this manual) and the 'Reports' option, which will be added in a later version of the ABCD-software. This module will create all types of output documents, e.g. alerts, confirmations of loans etc.  


![](https://lh5.googleusercontent.com/vfnqTJnSEqf6trRYHyyP3Euk7Bc0hdkZvyiq5yhCngDGvYQ7Lp2ugtBmYPgxv_S2bZW9idEQlEr9AUqvD-GiW8BW1tRxmhCBd7GMhyPYmhpuWS1buSMsaBU4LpQjvH1Uy97so9oX=s0)

  

## The advanced loans module

The advanced loans module of ABCD is an add-on module which can be installed as a separate member of the 'ABCD Suite'. It requires additional software technology (e.g. JAVA, MySQL) to be installed and can also be run as an independent software. Since this module was originally programmed as a DOS-software named 'Emp' (Por- tugese for 'loans'= emprestímos', the module is called 'EmpWeb' as for ABCD it has been converted into a Web- software, using new web-technology like web-services. So we consider this 'E'mpweb as an 'E'xtra or 'E'nhanced module', maybe changing 'ABCD' into 'ABCDE' ?

Extra functionalities as compared to the integrated loans module are :
-   better capability to deal with complex organisational structures (multi-branch libraries with different loans poli- cies, different servers e.g.)
-   more robust handling of high-volume transactions situations
-   more interaction with users form the OPAC module, e.g. the 'MySite' function to allow logged-in users to keep track of their own status etc from the OPAC.
-   a 'MySite' function allows registered end-users (after logging in) to enter their own space in the loans system to check on their status as a library user and other interactive users. This function at this time is not yet available in the Central Loans module.

Some important concepts of EmpWeb are briefly presented here :
-   web-services : instead of needing full access to external resources (databases), which can in some case create problems with the data-providers, web-based 'requests' are sent to the server to just deliver - as a response to the request - some specific data.
-   pipe-lines : any transaction (like a loan, a reservation, a return...) goes through a pipe-line of conditions which can be defined. Only if all conditions are met throughout the pipe-line, the transaction will be 'granted', if not it just stops and returns the defined (by the software) error message or instruction (e.g. 'User has been suspended'). This allows any number of conditions and rules to be applied on any decision taken by the software.
    
EmpWeb therefore can run on any set of external data for which drivers are available or can be accessed by webservices and apply any set of rules onto these data and perform processes (like changing a record) in case of having succeeded to pass all rules and conditions. 

[!!] EmpWeb in this way is more of a generic transactional engine but used as a loans system in ABCD.  
  **![](https://lh5.googleusercontent.com/_K5Avz3PD4Pl_OG63mU5JEWnctpdBKIQ-qrvcmuIqRjwOU_Q58ViR1RgulNfC96nvoEW9iyMoHB2IRMYKlEpL6y0Q8AOWDEi0GVy8BwtJFmRMZkKHj3Rok6u2prokAIMPZejYjYX=s0)**
[!!] This advanced loans module is discussed in detail in a separate Manual.
