---
title: Módulo central - estatísticas no ABCD
description: O módulo de Estatística pode ser invocado a partir da Administração principal
lang: pt
lang-ref: abcd-modules/abcd-statistics
---

# Central module : statistics in ABCD
    

{: .no_toc }

## Conteúdo
{: .no_toc .text-delta }

1. TOC
{:toc}

---


The Statistics module can be invoked from either the main Administration menu or from the cataloging toolbar's option :  
![](https://lh5.googleusercontent.com/gzZ2q9bFONPZ2N5UeHYQIR0T-pF8jcpP0G0LuS8b_OUYNPiTcOnSxoXqw3nBakDrNqBoXSCABu9fYaEza7oic4tRlutLO3h6wCHSG-irEL5GUoQJdPwSMNJXTPBl60NBkfHXPuBq=s0)


The main Statistics screen offers three functions :

1.  Use an existing table
2.  Create a new table
3.  Generate output
  
**a.  Use an existing table**
   
Existing tables will be listed in the options list by their row/column criteria. In the ABCD demo version one table has been pre-defined : a 'classification code by publication date' table.

> Note:
> The list of available tables is taken from a text-file 'tabs.cfg'
> in the /bases/{dbname]/def/[language]/ folder. This file contains, for
> each pre-defined table, three values separated by the '|' character :

-   the name as displayed in the menu of tables (which for clarity could be a mentioning of both criteria)
-   the field for the rows
-   the field for the columns

e.g.
  
    Classification number / Date of publication|Classification LC|Publication Date
       
![](https://lh6.googleusercontent.com/KSGmBH6TP029dpZR91ls8wBU9_g9r-_p5bpnPfkQmMwGmV7bd3QsLmYoXrdx0bagQ7rT4SLMtjhJR7SWFJXiBoDZ1wf7A6TZyOsq5IBLCHZ-A7i2GXqicVo8D-wzYl__WbM4Ilbq=s0)

After selection of the table one simply has to continue by using the 'Generate output' option, see below.

**b.  Create a new table**
    
A table has to be defined by identifying which values (as contained in an ISIS database field) will be used in the horizontal (rows) direction and which ones in the vertical (columns) direction. ABCD will display a list of available criteria (or fields) to select from for both rows and columns.  
![](https://lh5.googleusercontent.com/6HRJwhc7FHzsgYn1yxE6LmfWRRLnLB36mPWzCZBm9BdKMgJOWpavn0X0SkymDGizl1FY7l1HMqDLGNpMq1nH1iVEkRvAmGiOuLUszofWUZxcCNc-6IjBZCA5XOO3M0qaCUn9e9Wk=s0)

  

> Note:
> The list with available fields or criteria is taken from the
> text-file 'stat.cfg' in the folder /bases/ [dbname]/def/[language,
> which contains on each line one criterion, specified as a field name
> and a PFT to exactly define how the values should be extracted from
> the field. The MARC database demo example is :
  
```
Classification LC|v50^a
Date of publication|if val(v260^c)<2000 then '1900-2000' else F(val(v260^c),1,0) fi
```

in which the second line illustrates how it can be more than just a simple field value statement by using conditions etc.

Once both the 'Rows' and 'Column' criteria have been defined, the table can be used to generate output as explained below.

  

**c.  Generate output**
    
Generation of output in ABCD involves 2 stages : creating the table with the values and - if so desired - creating graphical output charts or exporting the table to other external document formats (e.g. worksheet for spreadsheet software which offers mostly more advanced/detailed graphical output possibilities).

Before creating the output one has to define the range of MFN's (ISIS records) to be used or a 'query' statement to apply the statistics only on a certain sub-set of the database. In the 'search' (or query) box one can use the ISIS Query Language with any accepted statement.![](https://lh3.googleusercontent.com/0UTY_HsC5tEBG8Zuz6ZfoPt4Di48TORKL8bSXtdTeyBwyPZi_mu_1UE_NmQiMDIs7qA_0LIC4Dms0LzzXcB79w8SqXD9_TKlkOvZefIGKmfOJ6hUhuECmHZuHsuln2CKTYctL048=s0)

  

In the first stage it is a matter to actually create the table with all the values in the cells combining both row- and column criteria (e.g. the documents published at a certain publication date belonging to a given  

LC classification code). Be careful to not calculate tables with individual extended range values (e.g. all years or all LC-codes), but rather use the Formatting Language to combine values into classes, as these make probably much more sense in your statistical report. The example above gives some hints on how to obtain such classes by using a condition on the value of a date, so the user can derive more classes from this basic example.

In this sense the following excerpt of a table gives a BAD example, as cell values are mostly if not always '1' due to too-detailed row- and column- criteria :
![](https://lh4.googleusercontent.com/vTGdwtE8RvBohzz3Yw-mIKgvK_szBkwFKHyl1f2WVhQM-LnPW_Rve-z5Z9oUOeUocPuaZe9rP9X_j544KzpUg1uZJtYMhZQ7tv0bSe8eg16gJ4QtAIO9QKEQLt0T0-BvEkJZhg3D=s0)

 The output options given by ABCD are the following :![](https://lh6.googleusercontent.com/5qhfX-KIM9I15TZsAJvy8jmLTtEoxQAo6VLQ-l6dxS8G9qn0fuT6G7KGO0xnQKZ8zxj2DUTnfYYh_CUcxg1QtaATNLHsNgCDCvj_zgt4zpQoE94WQf944dg_OeHsbhQY4UjKcjNi=s0)


-   Output to a worksheet will transfer the table to a Spreadsheet for further processing
-   Output to a document will transfer the table to a Word Processor document for further processing - this could be practical to include results into your annual report document etc..
-   Output to printer allows direct printing of the table using the printer(s) available to your Operating System
-   There are 2 graphic outputs provided by ABCD itself :
    * Animated graphic : this is a fancy way of displaying the graphs, mostly suited for attention-tracking presentations (but requiring Flash software to be installed on the computer)
    * Non-animated graphic : displaying the graphs but without the fancy animation.
    

In both cases several typical graphical output styles (horizontal or vertical bars, lines, three-dimensional bars etc...) are available and should be selected.  

![](https://lh3.googleusercontent.com/_XN6GSF_plEf4t8H1r8GNik03E6yOsUkTX1jgwq0nx8q_dos_cdODA898XMyAcniXTsybak9XNonVjEOalsOw2DVfEvLztC72RDKENqlCbTuFHYQIQW45_adAQSuEbB3mHt-mac3=s0)

If you are not acquainted with such styles, why not just try them and decide for yourself which one presents the message of the statistics in the most clear way ? Remember that conveying a message is the crucial thing here with statistics, not impressing an audience or reader with a jungle of too-much data - as is often the case with statistical tools. Often the simpler the more convincing !

  An example output of the graphical output looks like this :![](https://lh6.googleusercontent.com/wMHIN8P61F5tJh-0ucps73HvKaCGy6sKCX0MIir8Y92EJ3-z80RZRR0mv1SNJjGCoKYjBMO8oNE_QDtB6DlRod5cbaKABK1pS2pwNFG4GXm-bAkfGABZ0i3H1foX57wnZZN6kphE=s0)