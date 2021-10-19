---
title: ABCD Thesaurus
description: In ABCD a thesaurus can be used as a 'guided authority' list of terms at two different stages - while assigning descriptors during data-entry and while defining keywords for searching in a database.
lang: en
lang-ref: abcd-thesaurus
---

# ABCD Thesaurus

{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---

    
## Thesaurus
    

In ABCD a thesaurus can be used as a 'guided authority' list of terms at two different stages : while assigning descriptors during data-entry and while defining keywords for searching in a database.

The thesaurus itself is a database (remember in ABCD 'everything is a database') with a specific structure of fields which cover the main standard-thesaurus elements of identifier, descriptor, scope note, use, used-for, broader/nar- rower term and related terms as well as 'non-descriptor' (a term to be avoided and replaced by a 'preferred' one). For more background information on this standard 'ISO 25964' check e.g. the Wikipedia-page at the URL https://en.wikipedia.org/wiki/ISO_25964.

### Configuration of a thesaurus database for ABCD Central

In the file 'dr_path.def' of the associated database (e.g. your MARC-catalog) the following parameters have to be added :

-   Thesaurus = , followed by the name of a thesaurus database, e.g. 'agrovoc' (without path information as that will be obtained, as for any database in ABCD, from its par-file in the bases/par directory;
    
-   prefix_search_tesaurus = , followed by a prefix which is used to index the 'descriptors' field in your database,
    

e.g. 'MA_' in the demo MARC-database for field 650. This prefix will be added by the software in front of the selected term in order to search it in the (catalog-)database.

In addition a file 'dbn.dat' (where 'dbn' is the name of the thesaurus database, e.g. 'agrovoc') needs to be created in the active language of the 'def'-directory of the thesaurus-database, e.g. in the case of English agrovoc : bases/ agrovoc/def/en/agrovoc.dat. In that file 4 parameters need to be defined :

1.  Alpha_prefix = : Prefix to use to retrieve the alphabetical list of thesaurus terms, as indexed in the FST
    
2.  Perm_prefix = : Prefix to use to form permuted listing of terms. The prefix PER_ must be used and the line of the fst in which it is used must be indexed by technique 8 (each word of the term with addition of a prefix
    
3.  Alpha_pft = : Format to use to display the term in the alphabetical or permuted list
    
4.  Display = : Name of the format (without the .pft extension) to format the thesaurus record and display it in the thesaurus terms tab in full detail with links.
    

An example such configuration file looks like the following :  

* Alpha_prefix = TE 
* Perm_prefix = PER_
* Alpha_pft = v8 
* Display = tab

The 'Display = ' PFT, in this example therefore named 'tab.pft', will require some additional elaboration in order to format the record in a useful and attractive way. Here is an example of such PFT, using the fields :

* v8 = Base term
* v12 = Use or 'see' (US) 
* v13 = Used for (UF) 
* v14 = Scope note (SN)
* v16 = Broader term (BT) 
* v17 = Narrower term (NT) 
* v18 = Related term (RT)
* v30 = Notes

```
'<a href='javascript:Search("`v8`")'>'
'<img src=../dataentry/img/search.gif border=0>' 
'</a>'
"<Strong>" V8 "</ Strong>" v45/ "<br>" v32,/

'<Table>',

if p (v12) then 
'<tr>'
	'<td valign = top> Use </td>'	 
	'<td>'
		(if p (v12) then `<a href='javascript:Show("`v12`")'>` V12 '' '/ fi), 
	'</td>' fi,
if p (v13) then 
'<tr>'
	'<td valign=top>UF</td>'	
	'<td>'
		(if p (v13) then `<a href='javascript:Show("`v16`")'>` V13 '' '/ fi), 
	'</td>' / 
fi,
'<td> </td>'
'<td> </td>'

if p (v16) then '<tr>' 
'<td valign=top>BT</td>' 
'<td>' (if p (v16) then `<a href='javascript:Show("`v16`")'>` v16 '/'), '</td>' / fi,
if p (v17) then '<Tr> <td valign = top> NT </td> <td>' (if p (v17) then `<a href='javascript:Show("`v17`")'>` V17 '' '/ fi), '</td>' / fi,
if p (v18) then '<Tr> <td valign = top> RT </td> <td>' (if p (v18) then `<a href='javascript:Show("`v18`")'>` V18 '' '/ fi), '</td>' / fi,
if p (v30) then '<Tr> <td valign = top> See also </td> <td>' (if p (v30) then `<a href='javascript:Show("`v30`")'`` V30 '/'), '</td>' / fi,
'</table>'
/
```

The initial statement `<a href='javascript:Search('v8')'><img src=.. /dataentry/img /search.gif border=0></a>` will allow to launch a search when clicking on the term.

> Note:
> the use of the special quotes ` in this statement to still allow
> the 'normal' quotes ' and " without disturbing the format

The statements calling a javascript 'Show', generalized as follows :

    (if p (vxx) then '<a href='javascript:Show("`vxx`")'`` Vxx '' '/ fi),  

allows to use the terms of the relationships to navigate through the thesaurus by clicking on them ('Vxx' being the related field).

> Note:
> The javascript codes for Search and Show are already inserted in
> the script tesaurus / show.php in charge of showing the full records
> of the thesaurus

Finally, the descriptors field in the catalog FDT and FST has to be defined as a thesaurus-supported field as follows :

-   FDT : in the 'descriptors' field (e.g. 650 in MARC) define 'thesaurus' as the picklist database-type and add the prefix used (e.g. MA_); put the field-tag in both 'list as' and 'extract as' columns, e.g. v650 | v650
-   FST : if V8 contains the main term, at least two entries need to be present in the FST of the thesaurus database : 

    8 0 "TE_" v8
    8 8 '| PER_ |' v8 

for resp. the base-term listing and the permuted listing.
    

### The use of a thesaurus in data-entry

When the previous configuration with its 2 parameters is found to be present, the Central toolbar will show the Thesaurus icon ![](https://lh4.googleusercontent.com/lz_gPAo_tTdjEetjx7NR4l8D8dQnikSPnAFvazvdUqxeHI1Tf-YzC9zZhmpaPsyVzaU98MjUTQrRGG1z_0jp2T3Gn5KlexsAoUnVvWOelqXHGXDZIUV0ttAAQXNoM8LEyPvilzJM=s0)

Clicking on that icon will open a new sub-window with the initial listing of your thesaurus terms, e.g. in the case of agrovoc :![](https://lh6.googleusercontent.com/qQ_Phi6CQfOE6Lv-OExL36GFqc3ll501_GZeHubwrzGC5Z7FG4vydl0D73bwiGN8kQS7serih_JiOIoji7Tw6G6-gNGCiIolAB2lLvPjLJMbT5H1P1cxLqmRidDHopaAK2eH-MjQ=s0)

 
The listing shown is the 'alphabetical' one ('ABC...') with all Latin alphabet characters available for quick reposi- tioning in the thesaurus. Also the 'go to' box at the bottom can be used to enter a few characters and then immedi- ately jump to the closest term by clicking on 'continue'.

An alternative way of showing this listing is using the 'permuted' listing - see the two options 'ABC...' and 'Per- muted' at the bottom of the screen - which will show all terms starting with the selected character but with its context (other included words) before or after the word itself. In the illustration below we have opted for the 'D' character as the starting point and the list shows all terms with words starting with 'D' also if it is not the first words in the multi-word term :  

![](https://lh3.googleusercontent.com/4K6aei9b3_GoezBpnd4qi4vh3VC60ytRrvmKUzIepY0Wg0CGpXfuFFES-eexwOK8cxzCM0PXL6kH6ZYbFBQGawxAvkw-Ywn5BBTw8U8RP2Oox11c4MCV5UpnYuq-xE20AFHt7XwE=s0)

Finally, when the tick-box at the upper-right corner is indeed ticked (active), selecting a term will first show the selected term with its relations, i.e. the full record formatted according to a pre-defined PFT (which is explained above in the configuration).![](https://lh5.googleusercontent.com/tOGns4MX5eI0RIg-etV937Bf3SA9xKLblr-g-PbcfCAP_yfITESxrTAQTVEw3Z4EHOkdG4uB0o76Mg0EXznUxWXoaXQwS7oVMsDY1LvBaChnYy6qZ5JTe2IDCSulTxZ8T0QB6qbS=s0)

Whenever the 'thesaurus consultation' is finished (by navigating into it or simply selecting a term), the finally selected term will be inserted into the data-entry form (field), however only at the field level [the sub-field level still needs to be implemented].

### The use of a thesaurus in searching
    
In fact exactly the same mechanisms of opening and consulting the thesaurus as above for data-entry apply for searching. After finally a term has been selected, it will be used as the current search-term and the resulting records will be shown.

Note that such search will only result in real records when they were entered using thesaurus-terms at data-entry stage. When a database is searched which was created without a thesaurus, only by co-incidence the same terms from the thesaurus might have been used as non-authoritatively assigned descriptors.