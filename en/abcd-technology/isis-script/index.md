---
title: IsisScript language
description: IsisScript is a scripting language, developed by BIREME, in order to make stronger the functions available to the WEB ISIS server "WWWISIS" for the creation of pages with elements of ISIS databases. ISIS Script in fact was one of the main elements in the evolution from WWWISIS to "WXIS" which is the underlying web server for ABCD.
lang: en
lang-ref: isis-script
---

# IsisScript language

IsisScripts are stored as files with the extension .xis. 
ABCD uses many scripts, most of them in the **central/dataentry/wxis folder**.
iAH (/iah/scripts) makes extensive use of such scripts.
The language uses XML like instructions, such as, for example, between the `<pft>` and `</pft>` tags a print format can be placed and that format can be displayed by placing it between the `<display>` and `</display>` tags. 

All WXIS parameters can be set within the `<parm>` and `</parm>` tags and fields can be set with values, for example `<field action="replace" tag="6000″>field_value_6000 </field>` will put the string "`Field_value_6000`" into the 6000 tag field (such high tag values, actually all tags above 999, are used in general in ISIS applications for internal temporary values that are not actually stored in ISIS records but as "virtual records".

IsisScript allows a more flexible manipulation of data elements, coming from ISIS databases, in web pages. In combination with PHP, which is a language for creating web pages, sophisticated results are possible and this certainly contributes to the overall advanced functionality of ABCD.


# How to use this language

All the liguage is on this page containing all the commands, parameters and options available in the IsisScript language.

The commands are organized at hierarchy level 2 and their elements follow the hierarchy up to level 4.

Each command, parameter or option will contain a brief description of its purpose. Additional information such as attributes, syntax, elements contained and where it applies are also provided, completing an example of code to illustrate the command, option or parameter.

The only prerequisites to the user are knowledge of format language and the model and structure of a standard CDS/ISIS base.



{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---



# IsisScript reference



## < IsisScript >

**May Contais** `<function>` `<section>` `<trace>`

**Attributes**  `name`

**Syntax** `<IsisScript> ... </IsisScript>`


The  `<IsisScript>`  element is used to indicate an IsisScript instruction group.  
  
The  _name_  attribute is used to name and document the group.


**Example**
```
<IsisScript name=HelloWorld>
  <section>
    <display>Hello World!</display>
  </section>
</IsisScript>
```

----------

### IsisScript.name

**May Be Used in** `<call> <function> <IsisScript> <section>`

**Syntax**  `name=...`



The  **name**  attribute is optional and it can be used for documentation purposes.



**Example**
```
<IsisScript name=HelloWorld>
  <section>
    <display>Hello World!</display>
  </section>
</IsisScript>
```


----------

## < call >


**May Contais** `<pft>`

**May Be Used in** `<do> <function> <hl> <loop> <section> <update>`

**Attributes** `name`

**Syntax** `<call> ... </call>`



The  `<call>`  element indicates a call to a function. The function to be called is specified by the  _name_  attribute.  
  
The argument of the  `<call>`  element is passed as parameter to the function.


**Example**


```script
<IsisScript>

  <function name=First>
    <display>FIRST </display>
  </function>

  <function name=Second>
    <display>SECOND </display>
  </function>

  <function name=ParamTest action=replace tag=1 split=occ>
    <display><pft>##'ParamTest'/</pft></display>
    <display><pft>ALL</pft></display>
    <return action=replace tag=9999 split=occ><pft>(v1/)</pft></return>
  </function>

  <section>
    <call name=First>now</call>
    <call name=Second>now</call>
    <call name=ParamTest><pft>'One'/'Two'/</pft></call>

    <display><pft>ALL</pft></display>
  </section>
</IsisScript>
```

----------

### call.name

**May Be Used in** `<call> <function> <IsisScript> <parm> <section>`

**Syntax** `name=...`



Name of the function to be called.


**Example**


```script
<IsisScript>


  <function name=First>
    <display>FIRST </display>
  </function>

  <function name=Second>
    <display>SECOND </display>
  </function>

  <function name=ParamTest action=replace tag=1 split=occ>
    <display><pft>##'ParamTest'/</pft></display>
    <display><pft>ALL</pft></display>
    <return action=replace tag=9999 split=occ><pft>(v1/)</pft></return>
  </function>

  <section>
    <call name=First>now</call>
    <call name=Second>now</call>
    <call name=ParamTest><pft>'One'/'Two'/</pft></call>

    <display><pft>ALL</pft></display>
  </section>
</IsisScript>
```

----------


## < cgitable >

**May Contais** `<pft>`

**May Be Used in** `<do> <function> <hl> <loop> <section> <update>`

**Syntax** `<cgitable> ... </cgitable>`



For each line of the specified argument, adds the CGI content ("value") of the "name" specifield for the given field. Each argument line is equivalent to the `<field action="cgi" tag="...">`name`</field>` definition.
 
**Example**

```language
...
   <cgitable>
     <pft>'2001 db'/
          '2002 from'/
          ref(['CONFIG']1,(v1^t,x1,v1^n/))/
     </pft>
   </cgitable>
...
```

----------


## < define > 

**May Contais** `<pft>`

**May Be Used in** `<do> <function> <hl> <loop> <section> <update>`

**Syntax** `<define> ... </define>`



It defines the fields to be used inside the `<loop>` element. Each argument line is equivalent to the `<field action="define" tag="...">Isis_...</field>` definition.



**Example:**


```language
...
   <define>
     <pft>'1001 Isis_Current'/
          '2002 Isis_Total'/
     </pft>
   </define>
...
```

----------


## < display >

**May Contais** `<htmlpft> <pft>`

**May Be Used in** `<do> <function> <hl> <loop> <section> <update>`

**Syntax** `<display> ... </display>`


It sends text to the current output. IsisScript's current output is initially set to the "standard output" of the operating system.
The current output can be redirected with the `<file>` element.



**Example:**


```language
<IsisScript>
 <section>
  <display><pft>'Content-type: text/html'/#</pft></display>
  <display>Hello World!<br></display>
  <field action=cgi tag=100>^n^v</field>
  <display><pft>(|100=|v100|<br>|/)</pft></display>
 </section>
</IsisScript>
```

----------


## < do >

**May Contais** `<call> <cgitable> <define> <display> <do> <export> <extract> <field> <file> <flow> <hl> <label> <list> <loop> <parm> <proc> <return> <trace> <update>`

**May Be Used in** `<do> <function> <hl> <loop> <section> <update>`

**Attributes** `task`

**Syntax** `<do> ... </do>`




The `<do>` element indicates the beginning of an IsisScript task. The possible tasks are: record range, key range, search, repetition, list, record importing, data base sorting, inverted file loading, and full inverted file generation. The list task can be a frequency list, a sorted list, or a simple list.

The task attribute is used to indicate the type of task to be executed.

The parameters for execution of a task are indicated with the `<parm>` element.

The `<loop>` element indicates the set of instructions to be executed for each task item.




**Example:**


```language
...
  <do task=search>
    <parm name=db>CDS</parm>
    <parm name=expression>plants * water</parm>
    <loop>
       <display><pft>mfn/</pft></display>
    </loop>
  </do>
...

```

----------

### do.task

**Options** fullinvertion import invertedload keyrange list mastersort mfnrange search update

**May Be Used in** `<do>`

**Syntax** `task=...`



It identifies the task to be performed.

The absence of the task attribute indicates a task independent repetition.



**Example**


```language
...
  <do>
     <parm name=to>500</field>
     <field action=define tag=1001>Isis_Current</field>
     <field action=define tag=1002>Isis_Total</field>
     <loop>
        <display>
          <pft>newline('<br>'),v1001,'/',v1002/</pft>
        </display>
     </loop>
   </do>
...
```
----------

### do.task=fullinvertion



Full generation of the database inverted file.

The database name is specified by the `<parm name=db>` element.

The FST (Field Select Table) is specified by the `<parm name=fst>` element.


 
**Example**

```language
...
  <do task=fullinvertion>
     <parm name=db><pft>v2001</pft></parm>
     <parm name=fst><pft>v2061</pft></parm>
     <field action=define tag=1102>Isis_Status</field>
     <display><pft>'Full invertion: ',v2001/</pft></display>
     <loop></loop>
     <display><pft>'Finished.'/</pft></display>
     <display><pft>'Lock status = 'v1102/</pft></display>
  </do>
...

```

----------

### do.task=import



It imports data from a text file, loading it as database records.  
  
The file name is specified by the `<parm name=file>` element.  
  
The `<parm name=type>` element may be used to specify the type of the text file; ***ISO-2709*** type text file is assumed if the type is not specified.



 **Example**


```language
...
  <do task=import>
     <parm name=file><pft>v2041</pft></parm>
     <parm name=type><pft>v2042</pft></parm>
     <loop>
        <display><pft>ALL</pft></display>
     </loop>
  </do>
...

```

----------

### do.task=invertedload



It loads the inverted file using a database containing the sorted keys.

The database name whose inverted file is being loaded is specified by the `<parm name=db>` element.

The sorted keys database name is specified by the `<parm name=keysdb>` element.



**Example**


```language
...
  <do task=invertedload>
     <parm name=db>TEST</parm>
     <parm name=keysdb>TESTKEYS</parm>
     <field action=define tag=1>Isis_Posting</field>
     <field action=define tag=2>Isis_Key</field>
     <field action=define tag=1102>Isis_Status</field>
     <display><pft>'Inverted load ...'/</pft></display>
     <loop></loop>
     <display><pft>'Lock status = 'v1102/</pft></display>
     <flow action=exit>
        <pft>if val(v1102) <> 0 then v1102 fi</pft>
     </flow>
     <display><pft>'Inverted load: TEST loaded.'/</pft></display>
  </do>
...

```

----------


### do.task=keyrange





It accesses the database inverted file.

The data base name is specified by the `<parm name=db>` element.

The initial inverted file key is specified by the `<parm name=from>` element.

The final inverted file key is specified by the `<parm name=to>` element.

The number of inverted file keys may be limited by the `<parm name=count>` element.

The `<parm name=reverse>` element may be used to access the inverted file keys in a reverse order.

The `<parm name=posting>` element may be used to go through the postings list of each inverted file key.

The `<parm name=posttag>` element may be used to go through the postings list of each inverted file key for a given tag.
 



**Example**


```language
...
  <do task=keyrange>

    <parm name=db><pft>v2001</pft></parm>
    <parm name=from>
       <pft>v2002,if a(v2002) then v2101 fi</pft>
    </parm>
    <parm name=count><pft>v2003,"20"n2003</pft></parm>
    <parm name=reverse><pft>v2004</pft></parm>
    <parm name=to><pft>v2006</pft></parm>

    <field action=define tag=1001>Isis_Current</field>
    <field action=define tag=1>Isis_Key</field>
    <field action=define tag=2>Isis_Postings</field>

    <display><pft>'##) POSTINGS',c15,'KEY'/#</pft></display>

    <loop>

       <display>
         <pft>f(val(v1001),2,0),') ',v2,c15,v1/</pft>
       </display>
       <field action=export tag=1031>
          <pft>if val(v1001) = 1 then '1' fi</pft>
       </field>
       <field action=export tag=1032>1</field>

    </loop>

    <display>
       <pft>'***************'/,
            f(val(v1001),2,0),') ',v1031,' / ',v1032/
       </pft>
    </display>

  </do>
...
```

----------


### do.task=list




It accesses the list of items previously loaded with the `<list action=load type=...>` element.

The list may be sorted using the `<parm name=sort>` element.

The starting item is set by the `<parm name=from>` element.

The last item is set by the `<parm name=to>` element.

The number of items can be limited by the `<parm name=count>` element.

The `<parm name=reverse>` element may be used to go access the list in reverse order.




**Example:**


```code
...
  <list action=load type=sort><pft>'1'/,'2'/,'3'/</pft></list>
  <list action=load type=sort><pft>'9'/,'8'/,</pft></list>
  <list action=load type=sort><pft>'F'/,'Z'/,'A'/</pft></list>

  <do task=list>
     <field action=define tag=1001>Isis_Current</field>
     <field action=define tag=1002>Isis_Items</field>
     <field action=define tag=1>Isis_Item</field>
     <loop>
         <display>
            <pft>v1001,'/',v1002,c10,v1/)</pft>
         </display>
     </loop>
  </do>
...
```

----------


### do. task=mastersort


It sorts the records of a data base.

The data base name is specified by the `<parm name=db>` element.

The sort key is specified by the `<parm name=key>` element.

The sort key length is specified by the `<parm name=keylength>` element.


**Example**



```language
...
  <do task=mastersort>

     <parm name=db>CDS</parm>
     <parm name=key><pft>v24</pft></parm>
     <parm name=keylength>100</parm>

     <field action=define tag=1102>Isis_Status</field>

     <display><pft>'Key sort ...'/</pft></display>
     <loop></loop>
     <display><pft>'Lock status = 'v1102/</pft></display>

     <flow action=exit>
        <pft>if val(v1102) <> 0 then v1102 fi</pft>
     </flow>

     <display><pft>'Key sort: CDS sorted.'/</pft></display>

  </do>
... 

```

----------


### do.task=mfnrange



It accesses a range of database records - MFN (Master File Number) range.

The database name is specified by the `<parm name=db>` element.

The initial record (MFN) is specified by the `<parm name=from>` element.

The final record (MFN) is specified by the `<parm name=to>` element.

The number of records (MFN range) may be limited by the `<parm name=count>` element.

The `<parm name=reverse>` element may be used to access the records (MFN range) in reverse order, regarding MFN.


**Example**


```language
...
  <do task=mfnrange>

    <parm name=db>CDS</parm>
    <parm name=from>25</parm>
    <parm name=count>10</parm>

    <loop>
       <display><pft>ALL</pft></display>
    </loop>

  </do>
...
```

----------



### do.task=search



It accesses the database records according to a search expression.

The data base name is specified by the `<parm name=db>` element.

The search expression is specified by the `<parm name=expression>` element.

The initial record is specified by the `<parm name=from>` element.

The final record is specified by the `<parm name=to>` element.

The number of records may be limited by the `<parm name=count>` element.

The `<parm name=reverse>` element may be used to access the retrieved records in reverse order.



**Example**


```language
...
  <do task=search>
    <parm name=db>CDS</parm>
    <parm name=expression>plants * water</parm>
    <loop>
       <display><pft>mfn/</pft></display>
    </loop>
  </do>
...
```


----------


### do.task=update




It updates the database records, or adds a new record to the database.

The data base name is specified by the `<parm name=db>` element.

The `<parm name=mfn>` element is used to indicate the MFN to be updated, or that a new record is to be added to the data base.

The `<parm name=lockid>` element is used to identify the "owner" of the record.

The `<parm name=expire>` element may be used to indicate how long the record "belongs" to the "owner".



**Example**


```language
...
  <do task=update>

     <parm name=db>CDS</parm>
     <parm name=mfn>New</parm>

     <field action=define tag=1102>Isis_Status</field>

     <update>
        <field action=replace tag=20>
           <pft>date</pft>
        </field>
        <write>Unlock</write>
        <display><pft>ALL</pft></display>
     </update>

  </do>
...
```

----------


## < export >

**May Contais** `<pft>`

**May Be Used in** `<do> <function> <hl> <loop> <section> <update>`

**Syntax** `<export> ... </export>`




It adds the current record to a text file.

The file name must be previously indicated by the `<parm file=...>` element.

The default file type is ISO2709; other export file type can be specified with the `<parm type=...>` element. The export file types are: ISO2709, HLine, and VLine.




**Example**


```language
...
  <do task=mfnrange>
    <parm name=db>CDS</parm>
    <parm name=file>CDS.ISO</parm>
    <loop>
      <export>this</export>
    </loop>
  </do>
...
```


----------



## < extract >

**May Contais** `<pft>`

**May Be Used in** `<do> <function> <hl> <loop> <section> <update>`

**Syntax** `<extract> ... </extract>`



It adds the keys extracted from the current record to the keys database.

The FST (Field Select Table) must be previously indicated by the `<parm name=fst>` element.

The keys data base must be previously indicated by the `<parm name=keysdb>` element.

The field that shall contain the keys must be previously indicated by the `<field action=define tag=...>Isis_Key</field>` element.

The field that shall contain the postings data must be previously indicated by the `<field action=define tag=...>Isis_Posting</field>` element.





**Example**


```language
...
  <do task=mfnrange>
    <parm name=fst>1 0 v1</parm>
    <parm name=keysdb>tmp1</parm>
    <field action=define tag=1>Isis_Posting</field>
    <field action=define tag=2>Isis_Key</field>
    <loop>
       <extract>this</extract>
    </loop>
  </do>
...
```


----------



## < field >

**May Contais** `<pft>`

**May Be Used in** `<do> <function> <hl> <loop> <section> <update>`

**Attributes** action from previous split tag type

**Syntax** `<field> ... </field>`





The `<field>` element is used to add, modify, delete, import, export or define fields.

The action attribute indicates the usage of the element.

The tag attribute indicates the field that is subject to the action.

The split attribute may be used to indicate that each line will be a new occurrence of the field.

The previous attribute indicates whether the previous content is to be eliminated or not.

The type attribute indicates the type of field to be accessed.

The from attribute indicates the number of the field to be accessed.
 




**Example**


```language
...
   <field action=replace tag=2><pft>v400^b</pft></field>
...
```


----------


### field.action


**Options** add cgi define delete export hl import occ replace statusdb statusfile

**May Be Used in** `<field> <file> <flow> <function> <htmlpft> <list> <return>`

**Syntax** `action=...`




It indicates the action that the `<field>` element is to execute.



**Example**


```language
...
   <field action=replace tag=2><pft>v400^b</pft></field>
...

```


----------


#### field.action=add



It adds a new occurrence to the field specified by the tag atribute.

The argument of the element contains the data to be added.





**Example**


```language
...
  <field action=add tag=2>A</field>
  <field action=add tag=2>B</field>
  <field action=add tag=2>C</field>
...
```

----------


#### field.action=cgi


It adds the CGI item value, of the corresponding CGI item name, to the field tag specified by the tag attribute.

The argument of the `<field>` element indicates the CGI item name.



**Example**


```language
...
  <field action=cgi tag=2>phone</field>
...
```

----------



#### field.action=define


It defines the field number specified by the tag attribute to be automatically generated inside the `<loop>` scope.

The argument of the `<field>` element indicates the type of information stored in the field.

Possible argument values:

**Isis_Current** - Current execution index of the `<loop>`

**Isis_Total** - Total possible count for the `<loop>`

**Isis_From** - from parameter of the `<loop>`

**Isis_To** - to parameter of the `<loop>`

**Isis_Lock** - Record lock control

**Isis_Status** - Task execution status

**Isis_Item** - IsisScript list item

**Isis_Value** - Number of items as calculated by frequency count

**Isis_Key** - Current key

**Isis_Posting** - Current posting data

**Isis_Postings** - Current key total postings

**Isis_Items** - Number of items on IsisScript list

**Isis_ErrorInfo** - Search error pointer

**Isis_Keys** - Highlight keys

**Isis_MFN** - Field number to store the record number (MFN) for import or export task

**Isis_RecordStatus** - Field number to store the record status



**Example**


```language
...  <field action=define tag=1001>Isis_Current</field>...
```

----------


#### field.action=delete


Deletes one or all occurrences of the field specified by the tag attribute.

The argument of the `<field>` element indicates the occurrence to be deleted; ALL in the argument indicates the deletion of all ocurrences.



**Example**


```language
...
  <field action=delete tag=5>ALL</field>
  <field action=delete tag=6>1</field>
...
```

----------


#### field.action=export


It modifies the content of one or more fields within the previous scope of IsisScript.

The field is specified by the tag attribute.

Use tag=list to indicate that the argument contains a list of fields to be exported.




**Example**


```language
...
  <field action=export tag=2205>5</field>
  <field action=export tag=list>6,7,21/29</field>
...
```

----------


#### field.action=hl


It replaces the contents of the field specified by the tag attribute with a new value accorfing to text highlighting specifications.



**Example**


```language
...
  <parm name=prefix><b></parm>
  <parm name=suffix></b></parm>
  <parm name=keys><pft>(v1022/)</pft></parm>
  <field action=hl tag=70><pft>(v70/)</pft></field>
...
```

----------


#### field.action=import


It modifies the content of one or more fields within the current scope of IsisScript by copying the fields from the previous scope.

The field is specified by the tag attribute.

Use tag=list to indicate that the argument contains the list of fields to be imported.



**Example**

```language
...
  <field action=import tag=2070>70</field>
  <field action=import tag=list>201,206,301/314,321</field>
...
```

----------


#### field.action=occ


It replaces the content of the field specified by the tag attribute with the content of the field specified by the from attribute, but only with the content of the occurrence specified by the element argument.



**Example**


```language
...
  <do>
    <parm name=to><pft>f(nocc(v70),1,0)</pft></parm>
    <field action=define tag=1001>Isis_Current</field>
    <loop>
      <field action=import tag=70>70</field>
      <field action=occ tag=1 from=70><pft>v1001</pft></field>
      ...
    </loop>
  </do>
...
```

----------


#### field.action=replace



It replaces the content of the field specified by the tag attribute with the the new content specified by the argument.



**Example**


```language
...
   <field action=replace tag=2><pft>v400^b</pft></field>
...
```

----------


#### field.action=statusdb



It replaces the content of the field specified by the tag attribute with the status of the data base indicated by the argument of the `<field>` element.

If either the master file or the inverted file exists or both of them exist, a field will be created containing the s subfield (^s). The s subfield will contain the character m if the master file exists, and the character i if the inverted file exists.

If the master file exists, then the field will also contain the n subfield (^n) storing the total number of data base records plus one, the d subfield (^d) storing Data Entry Lock number, and the e subfield (^e) storing the Exclusive Write Lock number.



**Example**


```language
...
  <field action=statusdb tag=1091><pft>v2001</pft></field>
  <flow action=jump>
     <pft>if v1091^s : 'm' then 'LABEL_OK' fi</pft>
  </flow>
...

```

----------


### field.action=statusfile


It replaces the content of the field specified by the tag attribute with the status of the file indicated by the argument of the <field> element.

If the file exists, the field contains the s subfield (^s) with the character "e", otherwise the field is absent.
 


**Example**


```language
...
  <field action=statusfile tag=1091>C:\AUTOEXEC.BAT</field>
  <flow action=jump>
     <pft>if v1091^s : 'e' then 'LABEL_OK' fi</pft>
  </flow>
...
```

----------


### field.from


**May Be Used in** `<field>`

**Syntax** `from=...`



It specifies the field number accessed by the action=occ attribute.



**Example**


```language
...
  <do>
    <parm name=to><pft>f(nocc(v70),1,0)</pft></parm>
    <field action=define tag=1001>Isis_Current</field>
    <loop>
      <field action=import tag=70>70</field>
      <field action=occ tag=1 from=70><pft>v1001</pft></field>
      ...
    </loop>
  </do>
...
```


----------


### field.previous

**Options** `add` `delete`

**May Be Used in** `<field>`

**Syntax** `previous=...`




It specifies whether the previous content of the imported or exported field has to be deleted, or if new occurrences of the field have to be added to the existing data.

The absence of this attribute means that the previous content will be deleted.



**Example**


```language
...
  <field action=import tag=1 previous=add>200</field>
...

```


----------


#### field.previous=add



Add new field occurrences to the data.



**Example**

```language
...
   <field action=export tag=200 previous=add>1</field>
...
```

----------


#### field.previous=delete



It deletes previous field occurrences.



**Example**

```language
...
   <field action=export tag=4001 previous=delete>1</field>
...
```

----------


### field.split

**Options** `flddir` `occ`

**May Be Used in** `<field>`

**Syntax** `split=...`



It indicates how to store the field data.




**Example**


```language
...
  <field action=replace tag=1 split=occ><pft>(v200/)</pft></field>
...
```

----------


#### field.split=flddir




O texto a ser armazenado no campo especificado pelo atributo tag é o diretório de campos do registro com os respectivos conteúdos.

Cada linha contém o número do campo (5 dígitos), um espaço em branco e o conteúdo do campo.



**Example**


```language
...
  <do task="mfnrange">
    <parm name="db">CDS</parm>
    <parm name="count">5</parm>
    <loop>
      <field action="replace" tag="1" split="flddir">ALL</field>
      <display><pft>ALL</pft></display>
    </loop>
  </do>
...
```

----------


#### field.split=occ



Indicates that each line of the argument of the `<field>` element shall be stored as a new occurrence of the field specified by the tag attribute.



**Example**

```language
...
  <field action=replace tag=1 split=occ><pft>(v200/)</pft></field>
...
```

----------


### field.tag

**Options** `list`

**May Be Used in** `<field> <parm>`

**Syntax** `tag=...`




The tag attribute specifies the field number.

Use tag=list to indicate that the field list will be passed as an argument of the `<field>` element.



**Example**


```language
...
   <field action=replace tag=2><pft>v400^b</pft></field>
...
```

----------


#### field.tag=list



It indicates that the field list is passed as an argument of the `<field>` element.

Use a comma "," to separate field number within the field list. Use a slash "/" to indicate a field range. Use openning bracket "[" to indicate that the field will be stored with the field number specified after the colon character ":" and before the closing bracket "]".



**Example**


```language
...
  <field action=import tag=list>1,2,3,11/19,[30:20]</field>
...
```


----------


### field.type

**Options** `flag`

**May Be Used in** `<field> <file> <htmlpft> <list> <pft>`

**Syntax** `type=...`


It indicates the data type accessed.


**Example**


```language
...
  <field action=cgi tag=2011 type=flag>trace</field>
...
```

----------


#### field.type=flag



It indicates if the CGI data is either present or absent.

If the field is present but empty, then the field shall store a value of On, otherwise the field will store the value being passed.

This attribute only is used with the action=cgi attribute.



**Example**


```language
...
  <field action=cgi tag=2011 type=flag>trace</field>
...
```

----------


## < file >


**May Contais** `<pft>`

**May Be Used in** `<do> <function> <hl> <loop> <section> <update>`

**Attributes** `action type`

**Syntax** `<file> ... </file>`



The `<file>` element may be used to create, unlock or close data bases, to create temporary files, to delete files, and to change the standard output of IsisScript.

The action attribute indicates the action.

The type attribute indicates the type of file that will be subject to the action.



**Example**

```language
...
  <file action=create type=database>TESTX</file>
...
```


----------


### file.action


**Options** `append close create delete unlock`

**May Be Used in** `<field> <file> <flow> <function> <htmlpft> <list> <return>`

**Syntax** `action=...`



It indicates the action executed by the `<file>` element.



**Example**


```language
...
  <file action=create type=database>TESTX</file>
...
```

----------


#### file.action=append



It opens an output where data will be appended.



**Example**


```language
...
  <file action=append type=output>TEST.LOG</file>
...
```

----------


#### file.action=close



It closes either an output file when type=output or a database type=database.



**Example**


```language
...
  <file action=close type=output>TEST.LOG</file>
...
```

----------


#### file.action=create


It creates either a new output file if type=output or it initialize a database if type=database.


**Example**


```language
...
  <file action=create type=database>TESTX</file>
...
```

----------


#### file.action=delete


Deletes a file.

**Example**


```language
...
  <file action=delete type=file>TESTX</file>
...
```

----------


#### file.action=unlock



Unlocks a data base.

The Data Entry Lock and the Exclusive Write Lock numbers are reset to zeroes.

> ATTENTION: The records remain unchanged.

 

**Example**

```language
...
  <file action=unlock type=database>CDS</file>
...

```

----------


### file.type


**Options** `database file inverted master output tempfile`

**May Be Used in** `<field> <file> <htmlpft> <list> <pft>`

**Syntax** `type=...`



Indicates the type of the file subject to the action.



**Example**


```language
...
  <file action=create type=database>TESTX</file>
...

```

----------


#### file.type=database



It indicates that the action is on a database.

 


**Example**

```language
...
  <file action=create type=database>TESTX</file>
...
```

----------


#### file.type=file



It indicates that the action is on a file.

This option is valid only with the action=delete option.



**Example**

```language
...
  <file action=delete type=file>TEST.LOG</file>
...
```

----------


#### file.type=inverted



It indicates that the action is on the database inverted file.

This option is valid only with the action=create option.



**Example**


```language
...
  <file action=create type=inverted>TESTX</file>
...
```

----------


#### file.type=master



It indicates that the action is on the database master file.

This option is valid only with the action=create option.




**Example**

```language
...
  <file action=create type=master>TESTX</file>
...

```

----------


#### file.type=output



It indicates that the action is on an output file.



**Example**


```language
...
  <file action=create type=output>TEST.LOG</file>
...
```

----------


#### file.type=tempfile



It indicates that the action is on a temporary file.

This option is valid only with the action=create option.

The argument indicates the field number of the field that stores the name of the uniquely identified temporary file created by the operating system.



**Example**


```language
...
  <file action=create type=tempfile>4001</file>
...
```

----------


## < flow >

**May Contais** `<pft>`

**May Be Used in** `<do> <function> <hl> <loop> <section> <update>`

**Attributes** `action`

**Syntax** `<flow> ... </flow>`


The `<flow>` element is used to alter the execution flow of IsisScript instructions.

The action attribute indicates the action.


**Example**


```language
...

  <flow action=jump><pft>if p(v1) then 'GO' fi</pft></flow>
  <display>Field 1 absent</display>
  <flow action=exit>1</flow>

  <label>GO</label>
  <display>Field 1 present, continue</display>
  ...

...
```

----------


### flow.action


**Options** `exit jump skip`

**May Be Used in** `<field> <field> <flow> <function> <htmlpft> <list> <return>`

**Syntax** `action=...`


It indicates the action that the `<flow>` element will follow.


**Example**


```language
...

  <flow action=jump><pft>if p(v1) then 'GO' fi</pft></flow>
  <display>Field 1 absent</display>
  <flow action=exit>1</flow>

  <label>GO</label>
  <display>Field 1 present, continue</display>
  ...

...
```

----------


#### flow.action=exit



It ends the execution of the current IsisScript script.

The argument of the `<flow>` element indicates the return code that is passed to the operating system.



**Example**

```language
...

  <flow action=jump><pft>if p(v1) then 'GO' fi</pft></flow>
  <display>Field 1 absent</display>
  <flow action=exit>1</flow>

  <label>GO</label>
  <display>Field 1 present, continue</display>
  ...

...

```

----------


#### flow.action=jump




It branchs the execution of IsisScript to the corresponding `<label>` element.

The argument of the `<flow>` instruction indicates the branching point.



**Example**


```language
...

  <flow action=jump><pft>if p(v1) then 'GO' fi</pft></flow>
  <display>Field 1 absent</display>
  <flow action=exit>1</flow>

  <label>GO</label>
  <display>Field 1 present, continue</display>
  ...

...
```

----------


#### flow.action=skip



Either it branches the execution of IsisScript to the beginning of the `<loop>` of the current scope if the `<flow>` argument is Next, or it leaves the current scope and returns to the previous scope, if the `<flow>` argument is Quit.



**Example**


```language
...
  <do>

     <parm name=db>CDS</db>

     <loop>
       <flow action=skip>
         <pft>if a(v24) then 'Next'
              else if val(v26^c) > 1989 then 'Quit' fi
              fi
         </pft>
       </flow>
       <display><pft>@CDS.PFT</pft></display>
     </loop>

  </do>
...

```

----------


## < function >

**May Contais** `<call> <cgitable> <define> <display> <do> <export> <extract> <field> <file> <flow> <hl> <label> <list> <parm> <proc> <return> <trace>`

**May Be Used in** `<IsisScript>`

**Attributes** `action from name split tag`

**Syntax** `<function> ... </function>`



The `<function>` element starts a declare block for a function.

Use the action, tag and split attributes to receive parameters, as described for the `<field>` element.




**Example**


```language
...
  <function name=Test action=replace tag=1>
    <diplay>Inside Test function<br></display>
    <diplay><pft>'Field 1 = ',v1</pft></display>
  </function>
...

```

----------


### function.action


**See** `<field action=...>`



It passes the parameters for the function.

This is functionally equivalent to the action attribute of the `<field>` element.



**Example**


```language
...
  <function name=Test action=replace tag=1>
    <diplay>Inside Test function<br></display>
    <diplay><pft>'Field 1 = ',v1</pft></display>
  </function>
...
```

----------


### function.from


**See** `<field from=...>`



It passes the parameters for the function.

This is functionally equivalent to the from attribute of the `<field>` element.



**Example**


```language
...
  <function name=Test action=replace tag=1>
    <diplay>Inside Test function<br></display>
    <diplay><pft>'Field 1 = ',v1</pft></display>
  </function>
...
```

----------


### function.name


**May Be Used in** `<call> <function> <IsisScript> <section>`

**Syntax** `name=...`



The name attribute identifies the function declared.

This name will be used by the `<call>` element to call the function.



**Example**


```language
...
  <function name=Test action=replace tag=1>
    <diplay>Inside Test function<br></display>
    <diplay><pft>'Field 1 = ',v1</pft></display>
  </function>
...
```

----------


### function.split


**See** `<field split=...>`



It passes the parameters for the function.

This is functionally equivalent to the split attribute of the `<field>` element.



**Example**


```language
...
  <function name=Test action=replace tag=1>
    <diplay>Inside Test function<br></display>
    <diplay><pft>'Field 1 = ',v1</pft></display>
  </function>
...
```

----------


### function.tag


**See** `<field tag=...>`



It passes the parameters for the function.

This is functionally equivalent to the tag attribute of the `<field>` element.



**Example**

```language
...
  <function name=Test action=replace tag=1>
    <diplay>Inside Test function<br></display>
    <diplay><pft>'Field 1 = ',v1</pft></display>
  </function>
...
```

----------


## < hl >

**May Contais** `<call> <cgitable> <define> <display> <do> <export> <extract> <field> <file> <flow> <label> <list> <parm> <proc> <trace>`

**May Be Used in** `<do> <function> <loop> <section> <update>`

**Syntax** `<loop> ... </loop>`



The `<hl>` element starts a block of instructions that highlight text.



**Example**


```language
...
  <hl>
    <parm prefix><b></parm>
    <parm suffix></b></parm>
    <parm keys><pft>(v1022/)</pft></parm>
    <field action=hl tag=18><pft>v18</pft></field>
    <display><pft>ALL</pft></display>
  </hl>
...
```

----------


## < htmlpft >

**May Contais** `<pft>`

**May Be Used in** `<display>`

**Attributes** `action type`

**Syntax** `<htmlpft> ... </htmlpft>`



It interprets and formats an HTML file that contains formatting language instructions.



**Example**


```language
...
  <display>
     <htmlpft><pft>cat('Test.htm')</pft></htmlpft>
  </display>
...
```

----------


### htmlpft.action

**Options** `convert`

**May Be Used in** `<field> <file> <flow> <function> <htmlpft> <list> <return>`

**Syntax** `action=...`

It specifies an action that is different from the standard action of the `<htmlpft>` element.


**Example**


```language
...
   <file action=create type=output>TEST.PFT</file>
   <display>
     <htmlpft action=convert>
       <pft>cat('TEST.HTML')</pft>
     </htmlpft>
   </display>
   <file action=close type=output>now</file>
...
```

----------


### htmlpft.type


**See** `<pft type=...>`



It specifies the yype of action to be taken for the execution of the format.



**Example**

```language
...
  <display>
     <htmlpft type=reload>
        <pft>cat('Test.htm')</pft>
     </htmlpft>
  </display>
...
```

----------


## < label >

**May Be Used in** `<do> <function> <hl> <loop> <section> <update>`

**Syntax** `<label> ... </label>`


The `<label>` element indicates a point within the instructions where IsisScript may direct the flow of execution as specified by the `<flow action=jump>` element.


**Example**


```language
...
  <field action=cgi tag=2001>db</field>
  <flow action=jump><pft>if p(v2001) then 'OK' fi</flow>
  <display>db parameter absent, must exit</display>
  <flow action=exit>0</exit>

  <label>OK</label>
  <display>db parameter present, continue</display>
...
```

----------


## < list >

**May Contais** `<pft>`

**May Be Used in** `<do> <function> <hl> <loop> <section> <update>`

**Attributes** `action type`

**Syntax** `<list> ... </list>`



The `<list>` element modifies IsisScript's internal list. The options are: add items to the list or delete all the items on the list.

The action attribute indicates the option.

The type attribute indicates the list type.



**Example**

```language
...
  <list action=load type=freq><pft>(v66/)</pft></list>
...
```

----------


### list.action

**Options** `delete load`

**May Be Used in** `<field> <file> <flow> <function> <htmlpft> <list> <return>`

**Syntax** `action=...`



Indicates the action to be executed on IsisScript's list.



**Example**


```language
...
  <list action=load type=freq><pft>(v66/)</pft></list>
...
```

----------


### list.type

**Options** `freq list sort`

**May Be Used in** `<field> <file> <htmlpft> <list> <pft>`



It indicates the type of storage on the list.



**Example**

```language
...
  <list action=load type=freq><pft>(v66/)</pft></list>
...
```

----------


#### list.type=freq



Item frequency counting list. It indicates that the list contains frequency counting for the item.

Istead of adding repeated item, the counting is incremented.



**Example**


```language
...
  <list action=load type=freq><pft>(v66/)</pft></list>
...
```

----------


#### list.type=list



**Example**


```language
...
  <list action=load type=list><pft>(v66/)</pft></list>
...
```

----------


#### list.type=sort


It indicates that the list is sorted by item value.

**Example**


```language
...
  <list action=load type=sort><pft>(v66/)</pft></list>
...
```




----------


## < loop >


**May Contais** `<call> <cgitable> <define> <display> <do> <export> <extract> <field> <file> <flow> <hl> <label> <list> <parm> <proc> <return> <trace>`

**May Be Used in** `<do>`

**Syntax** `<loop> ... </loop>`


The `<loop>` element indicates the group of instructions that will be repeated upon all itens found, according to the type of task in the corresponding <do> element and the specified parameters.


**Example**


```language
...
 <do task=search>

   <parm name=db>        <pft>v2001</pft></parm>
   <parm name=expression><pft>v2005</pft></parm>

   <loop>
      <display><pft>mfn/</pft></display>
   </loop>

 </do>
...
```

----------


## < parm >


**May Contais** `<pft>`

**May Be Used in** `<do> <function> <hl> <loop> <section> <update>`

**Attributes** `name tag type`

**Syntax** `<parm> ... </parm>`



The `<parm>` element indicates a parameter for the corresponding set of instructions.



**Example**


```language
...
 <do task=search>

   <parm name=db>        <pft>v2001</pft></parm>
   <parm name=expression><pft>v2005</pft></parm>

   <loop>
       <display><pft>mfn/</pft></display>
   </loop>

 </do>
...
```

----------


### parm.name

**Options** `actab buffersize cipar count db decod delimiter expire expression file freqsum from fst gizmo indexlist key keyfield keylength keys keysdb lockid maxlk mfn posting posttag prefix reset reverse sort stw suffix task to type uctab`


**May Be Used in** `<call> <function> <IsisScript> <parm> <section>`

**Syntax** `name=...`


It is the name of the parameter.


**Example**


```language
<IsisScript>
  <section>

    <parm name=actab><pft>cat('ISISAC.TAB')</pft></parm>
    <parm name=uctab><pft>cat('ISISUC.TAB')</pft></parm>
    <parm cipar><pft>'CDS.*=/bases/cds/cds.*'/,
                     'ACTAB=/isis/menu/isisac.tab'/</pft>
                     'UCTAB=/isis/menu/isisuc.tab'/</pft>
    </parm>

    <do task=search>

      <parm name=db>CDS</parm>
      <parm name=expression>plants*water</parm>
      <parm name=to>10</parm>

      <loop>
         ...
      </loop>

    </do>

    ...

  </section>
</IsisScript>
```


----------


#### parm.name=actab



It changes the alphabetic characters table of IsisScript for the current `<section>`.

The alphabetic characters table specifies, for inverted file updating and for record keys extraction, which characters are to be considered as alphabetic.

Characters not included on this table is considered as delimiter characters.

If the `<parm name=actab>` is not specified, IsisScript assumes its default ANSI alphabetic characters table.



**Example**


```language
<IsisScript>
  <section>

    <parm cipar><pft>'CDS.*=/bases/cds/cds.*'/,
                     'ACTAB=/isis/menu/isisac.tab'/</pft>
                     'UCTAB=/isis/menu/isisuc.tab'/</pft>
    </parm>
    <parm name=actab><pft>cat('ACTAB')</pft></parm>
    <parm name=uctab><pft>cat('UCTAB')</pft></parm>

    <do task=search>

      <parm name=db>CDS</parm>
      <parm name=expression>plants*water</parm>
      <parm name=to>10</parm>

      <loop>
         <display><pft>mpu,v24,mpl</pft></display>
      </loop>

    </do>

    ...

  </section>
</IsisScript>
```

----------

#### parm.name=buffersize



It allows to change the WXIS internal buffer size (in bytes). The buffer is used to store the format result.



**Example**

```language
...
   <parm name="buffersize">90000</parm>
...
```


----------


#### parm.name=cipar


It activates a table associating of logical names with physical names of files for the `<section>`.

Each line establishes an association: to the left of the = character (equal sign) the logical name is specified, and to its right the physical name of the file.

The `*` character (asterisk) specifies that the correspondence is valid for any data base physical file.

**Example**


```language
...
  <parm name=cipar>
    <pft>
       'CDS.ISO=/bases/cds/cds.iso'/
       'CDS.*=/bases/cds/cds.*'/
       'TEST.PFT=/bases/cds/test.pft'/
    </pft>
  </parm>
...

```


----------


#### parm.name=count

It indicates the number of times the set of instruction within the `<loop>` element will be executed.

**Example**


```language
...
     <do task=search>

       <parm name=db>        <pft>v2001</pft></parm>
       <parm name=expression><pft>v2005</pft></parm>
       <parm name=from>      <pft>v2002</pft></parm>
       <parm name=count>10</parm>

       <loop>
           <display><pft>mfn/</pft></display>
       </loop>

     </do>
    ...
```

----------


#### parm.name=db

It specifies the database to be used by any of the following tasks:

- task=mfnrange
- task=keyrange
- task=search
- task=update
- task=fullinvertion
- task=mastersort
- task=invertedload


**Example**

```language
...
 <do task=search>

   <parm name=db>        <pft>v2001</pft></parm>
   <parm name=expression><pft>v2005</pft></parm>

   <loop>
       <display><pft>mfn/</pft></display>
   </loop>

 </do>
...
```



----------

#### parm.name=decod


It specifies the expansion database for decoded fields.


**Example**


```language
...
 <do task=search>
   <parm name=db>        <pft>v2001</pft></parm>
   <parm name=decod>     <pft>v2101</pft></parm>
   <parm name=expression><pft>v2005</pft></parm>
   <loop>
       <display><pft>mfn/</pft></display>
   </loop>
 </do>
...
```

----------

#### parm.name=delimiter

It indicates the field separator when importing records with the option RLine. The default parameter is the character | (pipe).

**Example**

```language
...
  <do task="import">
    <parm name="file"><pft>v2041</pft></parm>
    <parm name="type"><pft>v2042</pft></parm>
    <parm name="delimiter"><pft>v2043</pft></parm>
    <loop>
      <display><pft>ALL</pft></display>
    </loop>
  </do>
...
```


----------

#### parm.name=expire


It specifies the maximum time limit for the record to remain locked.

Another user (with a different identification) can lock the same record after that time limit has expired.

**Example**


```language
...
 <do task=update>

   <field action=cgi tag=2001>db</field>
   <field action=cgi tag=2002>mfn</field>

   <parm name=db><pft>v2001</pft></parm>
   <parm name=mfn><pft>v2002</pft></parm>
   <parm name=expire>14400</parm>

   <field action=define tag=1101>Isis_Lock</field>
   <field action=define tag=1102>Isis_Status</field>

   <update>

     <write>Unlock</write>

     <display><pft>ALL</pft></display>
     <display><pft>'*** LOCK STATUS: 'v1102/</pft></display>

   </update>

 </do>
...
```


----------

#### parm.name=expression

It specifies the search expression.

**Example**


```language
...
 <do task=search>

   <parm name=db>        <pft>v2001</pft></parm>
   <parm name=expression><pft>v2005</pft></parm>

   <loop>
       <display><pft>mfn/</pft></display>
   </loop>

 </do>
...
```

----------

#### parm.name=file

It specifies the name of the file that will be imported or exported.


**Example**

```language
...
  <do task=import>

    <parm name=file><pft>v2041</pft></parm>
    <parm name=type><pft>v2042</pft></parm>

    <loop>
       <display><pft>ALL</pft></display>
    </loop>
  </do>
...
```

----------

#### parm.name=freqsum

It specifies the value to be added to the sum when items are included in the frequency list.

**Example**

```language
...
  <loop>

     <!-- field 1 = Product
          field 2 = Quantity -->

     <parm name=freqsum><pft>v2</pft></parm>
     <list action=load type=freq><pft>v1</pft></list>
  </loop>
...

```


----------

#### parm.name=from

It indicates is the first item to be accessed by the set of intructions within the `<loop>` element.

**Example**

```language
...
 <do task=search>
   <parm name=db>        <pft>v2001</pft></parm>
   <parm name=expression><pft>v2005</pft></parm>
   <parm name=from>      <pft>v2002</pft></parm>
   <parm name=count>     <pft>v2003</pft></parm>
   <loop>
       <display><pft>mfn/</pft></display>
   </loop>
 </do>
...
```


----------

#### parm.name=fst


It specifies the FST (Field Select Table) that is used for inverted file updating or for record keys extraction.


**Example**

```language
...
  <do task=update>

     <parm name=db><pft>v2001</pft></parm>
     <parm name=mfn>New</parm>
     <parm name=fst>1 0 v1</parm>

     <field action=define tag=1102>Isis_Status</field>

     <update>

        <field action=cgi tag=1>Name</field>
        <field action=cgi tag=2>Phone</field>
        <write>Unlock</write>
        <display><pft>ALL</pft></display>

     </update>

  </do>
...

```

----------

#### parm.name=gizmo

It specifies the conversion database.

**Example**


```language
...
  <file action=create type=database>GIZMO_DIAC</file>
  <do task=update>
    <parm name=db>GIZMO_DIAC</parm>
    <parm name=mfn>New</parm>
    <field action=define tag=1101>Isis_Status</field>
    <update>
      <field action=replace tag=1>á</field>
      <field action=replace tag=2>á</field>
      <write>Unlock</write>
    </update>
  </do>

  <do task=mfnrange>
    <parm name=db>CDS</parm>
    <parm name=gizmo>GIZMO_DIAC</parm>
    <loop>
       <display><pft>ALL</pft></display>
    </loop>
  </do>
...
```


----------

#### parm.name=indexlist

It specifies the list of indices for searching on the database.

**Example**


```language
...
  <do task=search>

    <parm name=db>cds</parm>
    <parm name=indexlist><pft>
       '^p*^ycds^m** '/,
       '^pAU ^ycdsaut^mAU '/,
       '^pTI ^ycdstit^mTI '/
    </pft></parm>
    <parm name=expression>
      Au Mag$ or ([Ti] plants AND water)
    </parm>

    <loop>
       <display><pft>ALL</pft></display>
    </loop>

  </do>
...
```

----------

#### parm.name=key

It specifies the record sorting key of the database.

Example

```language
...
  <do task=mastersort>

    <parm name=db>CDS</parm>
    <parm name=key><pft>v24</pft></parm>
    <parm name=keylength>100</parm>

    <field action=define tag=1102>Isis_Status</field>

    <display><pft>'Sort ...'/</pft></display>
    <loop></loop>
    <display><pft>'Lock status = 'v1102/</pft></display>

    <flow action=exit>
       <pft>if val(v1102) <> 0 then v1102 fi</pft>
    </flow>
    <display><pft>'Sort: CDS sorted.'/</pft></display>

  </do>
...
```



----------

#### parm.name=keyfield

It specifies the field number used as database sorting key.

**Example**

```language
...
   <do task="mastersort">
      <parm name="db">CDS</parm>
      <parm name="keyfield">24</parm>
      <parm name="keylength">200</parm>
      <field action="define" tag="1102">Isis_Status</field>
      <display><pft>'Key sort ...'/</pft></display>
      <loop></loop>
      <display>
         <pft>'Lock status = 'v1102/</pft>
      </display>
      <flow action="exit">
         <pft>if val(v1102) <> 0 then v1102 fi</pft>
      </flow>
      <display>
         <pft>'Key sort: ',v2001,' sorted.'/</pft>
      </display>
   </do>
...
```

----------

#### parm.name=keylength

It specifie the length of the record sorting key.

**Example**

```language
...
  <do task=mastersort>

    <parm name=db>CDS</parm>
    <parm name=key><pft>v24</pft></parm>
    <parm name=keylength>100</parm>

    <field action=define tag=1102>Isis_Status</field>

    <display><pft>'Sort ...'/</pft></display>
    <loop></loop>
    <display><pft>'Lock status = 'v1102/</pft></display>

    <flow action=exit>
       <pft>if val(v1102) <> 0 then v1102 fi</pft>
    </flow>
    <display><pft>'Sort: CDS sorted.'/</pft></display>

  </do>
...
```


----------

#### parm.name=keys

It specifies the list of record keys for the text highlighting preferences.

**Example**


```language
...
  <do task=search>

    <parm name=db>cds</parm>
    <parm name=expression><pft>v2005</pft></parm>
    <parm name=from><pft>v2002,"1"n2002</pft></parm>
    <parm name=count>10</parm>

    <field action=define tag=1001>Isis_Current</field>
    <field action=define tag=1002>Isis_Total</field>
    <field action=define tag=1022>Isis_Keys</field>

    <loop>

      <hl>

	<parm name=prefix><b></parm>
	<parm name=suffix></b></parm>
	<parm name=keys><pft>(v1022/)</pft></parm>

       	<field action=hl tag=24><pft>v24</pft></field>
       	<field action=hl tag=70 split=occ><pft>(v70/)</pft></field>
        <display><pft>ALL</pft></display>

      </hl>

    </loop>

    <display><pft>
      if val(v1002) = 0 then 'No record found!' fi
    </pft></display>

   </do>
...
```


----------

#### parm.name=keysdb

It specifies the database that contains the record keys extracted, if used as parameter of the `<extract>` element.

It specifies the database with the record keys sorted for inverted file loading, if used as parameter of the `<do task=invertedload>` element.


**Example**

```language
...
  <do task=invertedload>

    <parm name=db><pft>v2001</pft></parm>
    <parm name=keysdb><pft>v2064</pft></parm>

    <field action=define tag=1>Isis_Posting</field>
    <field action=define tag=2>Isis_Key</field>
    <field action=define tag=1102>Isis_Status</field>

    <display><pft>'Inverted load ...'/</pft></display>
    <loop></loop>
    <display><pft>'Lock status = 'v1102/</pft></display>

    <flow action=exit><pft>
      if val(v1102) <> 0 then v1102 fi
    </pft></flow>
    <display><pft>
       'Inverted load: ',v2001,' loaded.'/
    </pft></display>

   </do>
...
```


----------

#### parm.name=lockid

It specifies the record lock identifier.

**Example**

```language
...
  <do task=update>

    <parm name=db><pft>v2023</pft></parm>
    <parm name=mfn><pft>mfn</pft></parm>

    <field action=define tag=1101>Isis_Lock</field>
    <parm name=lockid>
      <pft>getenv('REMOTE_ADDR'),x1,s(date).8</pft>
    </parm>
    <field action=define tag=1102>Isis_Status</field>

    <update>

      <field action=cgi tag=1>phone</field>
      <field action=replace tag=1><pft>v1</pft></field>

      <write>Unlock</write>
      <display><pft>ALL</pft></display>
      <display>
        <pft>'*** LOCK STATUS: 'v1102/</pft>
      </display>

    </update>

  </do>
...
```

----------

#### parm.name=maxlk

It specifies the maximum number of record keys (per record) during record keys extraction via FST (Field Select Table).

The default value is 1024.

**Example**


```language
...
  <do task=fullinvertion>

    <parm name=db><pft>v2001</pft></parm>
    <parm name=fst><pft>v2061</pft></parm>
    <parm name=maxlk>5000</parm>

    <field action=define tag=1102>Isis_Status</field>
    <display><pft>'Full invertion: ',v2001/</pft></display>

    <loop></loop>

    <display><pft>'Finished.'/</pft></display>
    <display><pft>'Lock status = 'v1102/</pft></display>

  </do>
...
```

----------

#### parm.name=mfn


It specifies:
- the record number of the record to be updated;
- new record to be added to the database, if the value is New;
- new record to be added to the database importing fields from the previous scope record, if the value is ***GetNew***;

**Example**


```language
...
  <do task=update>

    <parm name=db><pft>v2023</pft></parm>
    <parm name=mfn><pft>mfn</pft></parm>

    <field action=define tag=1101>Isis_Lock</field>
    <parm name=lockid>
      <pft>getenv('REMOTE_ADDR'),x1,s(date).8</pft>
    </parm>
    <field action=define tag=1102>Isis_Status</field>

    <update>

      <field action=cgi tag=1>phone</field>
      <field action=replace tag=1><pft>v1</pft></field>

      <write>Unlock</write>
      <display><pft>ALL</pft></display>
      <display>
        <pft>'*** LOCK STATUS: 'v1102/</pft>
      </display>

    </update>

  </do>
...
```


----------

#### parm.name=posting

If specifies the number of postings for each record key.

Use All to specify "all postings".

**Example**


```language
...
  <do task=keyrange>

    <parm name=db>CDS</parm>
    <parm name=from>PLANTS</parm>
    <parm name=count>20</parm>
    <parm name=posting>All</parm>

    <field action=define tag=1001>Isis_Current</field>
    <field action=define tag=1>Isis_Key</field>
    <field action=define tag=2>Isis_Postings</field>
    <field action=define tag=3>Isis_Posting</field>

    <display><pft>
      '    POSTINGS',c15,'KEY',c46,'POSTING DETAIL'/#
    </pft></display>
    <loop>
      <display><pft>
        f(val(v1001),2,0),') ',v2,c15,v1,c46,v3/
      </pft></display>
    </loop>

  </do>
...
```

----------

#### parm.name=posttag

It specifies the field number of the posting that shall be accessed within the record key range.

**Example**


```language
...
  <do task=keyrange>

    <parm name=db>CDS</parm>
    <parm name=from>B</parm>
    <parm name=count>20</parm>
    <parm name=posttag>70</parm>

    <field action=define tag=1001>Isis_Current</field>
    <field action=define tag=1>Isis_Key</field>
    <field action=define tag=2>Isis_Postings</field>
    <field action=define tag=3>Isis_Posting</field>

    <display><pft>
      '    POSTINGS',c15,'KEY',c46,'POSTING DETAIL'/#
    </pft></display>
    <loop>
      <display><pft>
        f(val(v1001),2,0),') ',v2,c15,v1,c46,v3/
      </pft></display>
    </loop>

  </do>
...
```

----------

#### parm.name=prefix

It specifies the prefix to be inserted within the text highlighting specifications, or the prefix to be used by the `<htmlpft>` element.

**Example**

```language
...
   <parm name=prefix>[pft]</prefix>
   <parm name=suffix>[/pft]</suffix>
   <htmlpft><pft>cat('TEST.HTM')</pft></htmlpft>
...
```

----------

#### parm.name=reset

It specifies that the inverted file updating needs to keep set the "inverted file update is pending flag" into the master file record. It applies to databases with multi-inverted files.

**Example**

```language
...
   <do task="fullinvertion">
     <parm name="db">CDS</parm>
     <parm name="fst">CDS.FST</parm>
     <parm name="reset">Off</parm>
     <field action="define" tag="1102">Isis_Status</field>
     <display><pft>'Full invertion: CDS'/</pft></display>
     <loop></loop>
     <display><pft>'Finished.'/</pft></display>
     <display><pft>'Lock status = 'v1102/</pft></display>
   </do>
...
```


----------

#### parm.name=reverse

It indicates that the records produced by the task specified in the `<do>` element shall be accessed in reverse order.

**Example**


```language
...
  <do task=search>

    <parm name=db><pft>v2001</pft></parm>
    <parm name=expression><pft>v2005</pft></parm>
    <parm name=reverse>On</parm>

    <loop>
      <display><pft>mfn/</pft></display>
    </loop>

  </do>
...
```


----------

#### parm.name=sort

It specifies the sort format for the `<do task="list">` task.

**Example**

```language
...
  <list action=load type=list>
    <pft>'5.00'/,'1.50'/,'10.00'/,'8'/,'3.75'/,'14.20'/,'0.40'/
  </pft></list>

  <do task=list>

    <field action=define tag=1001>Isis_Current</field>
    <field action=define tag=1002>Isis_Itens</field>
    <field action=define tag=1>Isis_Item</field>

    <parm name=sort><pft>f(val(v1),10,2)</pft></parm>

    <loop>
      <display><pft>v1001,'/',v1002,c10,v1/</pft></display>
    </loop>

  </do>
...
```

----------

#### parm.name=stw

It specifies the stop word table file used in the inverted file updating or in the record keys extraction.

**Example**


```language
...
  <do task=fullinvertion>

    <parm name=db><pft>v2001</pft></parm>
    <parm name=fst><pft>v2061</pft></parm>
    <parm name=stw><pft>v2001,'.stw'</pft></parm>

    <field action=define tag=1102>Isis_Status</field>

    <display><pft>'Full invertion: ',v2001/</pft></display>
    <loop></loop>
    <display><pft>'Finished.'/</pft></display>

    <display><pft>'Lock status = 'v1102/</pft></display>

   </do>
...
```


----------

#### parm.name=suffix

It specifies the suffix to be inserted within the text highlighting specifications, or the suffix to be used by the `<htmlpft>` element.

**Example**


```language
...
   <parm name=prefix>[pft]</prefix>
   <parm name=suffix>[/pft]</suffix>
   <htmlpft><pft>cat('TEST.HTM')</pft></htmlpft>
...
```

----------

#### parm.name=task

It indicates the task type for the `<loop>` element. It has no effect if the attribute task of the element `<do>` is specified.

**Example**


```language
...
  <do>
    <field action="cgi" tag="2081">dotask</field>
    <parm name="task"><pft>v2081</pft>
    <loop>
       ...
    </loop>
  </do>
...
```


----------

#### parm.name=to

It indicates the last item to be accessed by the set of instructions within the `<loop>` element.

**Example**


```language
...
 <do task=keyrange>

   <parm name=db>  <pft>v2001</pft></parm>
   <parm name=from><pft>v2002</pft></parm>
   <parm name=to>  <pft>v2002,'ZZZZZZZZZ'</pft></parm>

   <loop>
       <display><pft>v1/</pft></display>
   </loop>

 </do>
...
```

----------

#### parm.name=type

It specifies the type of file for export or import.

Possible values are: ISO2709, HLine, RLine and VLine.

ISO2709 is an ISO (International Standards Organization) standard but it limits the field identification number to 3 digits.

HLine is more efficient, uses the H command of the `<proc>` element.

RLine is used only for importing purposes, where each line of a sequential file is stored as a record.

VLine is recommended where data modifications has to be done via a text editor.


**Example**



```language
...
  <do task=import>

    <parm name=file><pft>v2041</pft></parm>
    <parm name=type><pft>v2042</pft></parm>

    <loop>
      <display><pft>ALL</pft></display>
    </loop>

  </do>
...

```

----------

#### parm.name=uctab

It changes the uppercase conversion table of IsisScript for the `<section>`.

This uppercase conversion table specifies, for inverted file updating, for record keys extraction, and for the "mode" option of the formatting language, the correspondence from lowercase, uppercase and diacritical characters to uppercase non diacritical characters.

If the `<parm name=uctab>` option is not specified, IsisScript assumes its default ANSI table.

**Example**


```language
<IsisScript>
  <section>

    <parm cipar><pft>'CDS.*=/bases/cds/cds.*'/,
                     'ACTAB=/isis/menu/isisac.tab'/</pft>
                     'UCTAB=/isis/menu/isisuc.tab'/</pft>
    </parm>
    <parm name=actab><pft>cat('ACTAB')</pft></parm>
    <parm name=uctab><pft>cat('UCTAB')</pft></parm>

    <do task=search>

      <parm name=db>CDS</parm>
      <parm name=expression>plants*water</parm>
      <parm name=to>10</parm>

      <loop>
         <display><pft>mpu,v24,mpl</pft></display>
      </loop>

    </do>

    ...

  </section>
</IsisScript>
```

----------

### parm.tag


**May Be Used in** `<field> <parm>`

**Syntax** `tag=...`

The tag attribute is used to specify the field number.

**Example**


```language
...
   <parm name="fst" type="check" tag="1">
     <pft>cat(v2065)</pft>
   </parm>
...
```


----------

### parm.type

*Options* `check`

**May Be Used in** `<do>`

**Syntax** `type=check`


It specifies the parameter type.

**Example**


```language
...
   <parm name="fst" type="check" tag="1">
     <pft>cat(v2065)</pft>
   </parm>
...
```

----------

#### parm.type=check

It specifies a FST (Field Select Table) syntax verification. It replaces the field specified by the tag attibute with the error code (5 digits), a space and the syntax error pointer; or 00000 if there is no error.

**Example**


```language
...
   <field action="cgi" tag="2065">fst</field>
   <parm name="fst" type="check" tag="1"><pft>cat(v2065)</pft></parm>
   <display><pft>ALL</pft></display>
...
```

----------

## < pft >

May Contais `<pft>`

*May Be Used in* `<call> <cgitable> <define> <display> <export> <extract> <field> <file> <flow> <htmlpft> <label> <list> <parm> <pft> <proc> <return> <trace> <write>`

*Attributes* `type`

**Syntax** `<pft> ... </pft>`

It formats the current record.

**Example**


```language
...
  <display><pft>("Autor: "v70+|; |)</pft></display>
  <display><pft>@CDS.PFT</pft></display>
  <display><pft>cat('C:\AUTOEXEC.BAT')</pft></display>
  <display><pft>ref(['CONFIG']1,v500/)</pft></display>
...
```


----------

### pft.type

*Options* `check reload`

*May Be Used in* `<field> <file> <htmlpft> <list> <pft>`

**Syntax** `type=...`

It specifies the action type for format execution.

*Example*

```language
...
  <do>

    <parm name=to>10</parm>

    <loop>
      <display>
        <pft type=reload>
          <pft>ref(['CONFIG']val(v1),v500/)</pft>
        </pft>
      </display>
    </loop>

  </do>
...
```

----------

#### pft.type=check

It allows the format syntax validation. It returns the error code (5 digits), a space character and the detected syntax error pointer, or 00000 if there is no error.

**Example**


```language
...
   <field action="cgi" tag="2065">pft</field>
   <display>
     <pft type="check">
       <pft>v2065</pft>
     </pft>
   </display>
...
```

----------

#### pft.type=reload

It specifies that the format must be recompiled each time this instruction is executed.

**Example**


```language
...
  <display>
    <pft type=reload>
       <pft>ref(['CONFIG']1,v500/)</pft>
    </pft>
  </display>
...
```

----------

## < proc >

**May Contais** `<pft>`

**May Be Used in** `<do> <function> <hl> <loop> <section> <update>`

**Syntax** `<proc> ... </proc>`

It modifies the contents of the current record.

**Example**


```language
...
  <proc><pft>'a',v2024,'~',v2027,'~'</pft></proc>
...
```

----------

## < return >

**May Contais** `<pft>`

**May Be Used in** `<function>`

**Attributes** `action split tag`

**Syntax** `<return> ... </return>`



It exits the current function.


**Example**


```language
...
 <function name=ParamTest action=replace tag=1 split=occ>
   <display><pft>##'ParamTest'/</pft></display>
   <display><pft>ALL</pft></display>
   <return action=replace tag=9999 split=occ>
      <pft>(v1/)</pft>
   </return>
   <display>Parameter field 1 absent!</display>
 </function>
...

```

----------

### return.action

**See** `<field action=...>`

It returns parameters to the caller function. It is functionally equivalent to the action attribute of the `<field>` element.

**Example**


```language
...
 <function name=ParamTest action=replace tag=1 split=occ>
   <display><pft>##'ParamTest'/</pft></display>
   <display><pft>ALL</pft></display>
   <return action=replace tag=9999 split=occ>
      <pft>(v1/)</pft>
   </return>
   <display>Parameter field 1 absent!</display>
 </function>
...
```

----------

### return.split

**See** `<field split=...>`

It returns parameters to the caller function. It is functionally equivalent to the split attribute of the `<field>` element.
 

**Example**

```language
...
 <function name=ParamTest action=replace tag=1 split=occ>
   <display><pft>##'ParamTest'/</pft></display>
   <display><pft>ALL</pft></display>
   <return action=replace tag=9999 split=occ>
      <pft>(v1/)</pft>
   </return>
   <display>Parameter field 1 absent!</display>
 </function>
...
```


----------


### return.tag

**See** `<field tag=...>`

**Example**


```language
...
 <function name=ParamTest action=replace tag=1 split=occ>
   <display><pft>##'ParamTest'/</pft></display>
   <display><pft>ALL</pft></display>
   <return action=replace tag=9999 split=occ>
      <pft>(v1/)</pft>
   </return>
   <display>Parameter field 1 absent!</display>
 </function>
...
```

----------


## < section >
**May Contais** `<call> <cgitable> <define> <display> <do> <export> <extract> <field> <file> <flow> <hl> <label> <list> <parm> <proc> <trace>`

**May Be Used in** `<IsisScript>`

**Attributes** `name`

**Syntax** `<section> ... </section>`


The `<section>` element is used to begin a sequence of instructions.

The name attribute may be used for identification purposes.


**Example**

```language
<IsisScript name=Test>
  <section name=TestFirst>
    <display><pft>mpu,'Test'</pft></display>
  </section>
</IsisScript>
```


----------

### section.name


**May Be Used in** `<call> <function> <IsisScript> <section>`

**Syntax** `name=...`

The name attribute is optional and may be used it for identification purposes.

**Example**

```language
<IsisScript name=Test>
  <section name=TestFirst>
    <display><pft>mpu,'Test'</pft></display>
  </section>
</IsisScript>
```


----------

## < trace >

**May Contais** `<pft>`

**May Be Used in** `<do> <function> <hl> <IsisScript> <loop> <section> <update>`

**Syntax** `<trace> ... </trace>`


It activates or deactivates the display of the instruction that is being executed. The possible options are normal, line by line, or table, respectively: On, BR, or Table.

**Example**

```language
...
   <trace>On</trace>
...

```

----------

## < update >
**May Contais** `<call> <cgitable> <define> <display> <do> <export> <extract> <field> <file> <flow> <hl> <label> <list> <parm> <proc> <return> <trace> <write>`

**May Be Used in** `<do>`

**Syntax** `<update> ... </update>`

It starts the set of instructions to modify or add a record.

**Example**

```language
...
  <do task=update>
    <parm name=db>CDS</parm>
    <parm name=mfn>New</parm>
    <field action=define tag=1102>Isis_Status</field>
    <update>
      <field action=append tag=1>One more</field>
      <write>Unlock</write>
      <display><pft>ALL</pft></display>
    </update>
  </do>
...

```

----------

## < write >

**May Contais** `<pft>`

**May Be Used in** `<update>`

**Syntax** `<write> ... </write>`

This element stores the modified record.

If the `<parm name=mfn>` element value is New, then a new record is added, otherwise the mfn passed as argument is updated.

Possible values for the argument of the `<write>` element:
Unlock - it unlocks the record after it is stored
Lock - record remains locked after it is stored
NoUnlock - the record remains locked after it is stored and the lock information is not changed
Delete - the record is deleted


**Example**


```language
...
  <do task=update>

    <parm name=db>CDS</parm>
    <parm name=mfn>New</parm>

    <field action=define tag=1102>Isis_Status</field>

    <update>

      <field action=add tag=1>Mais um</field>
      <write>Unlock</write>
      <display><pft>ALL</pft></display>

    </update>

  </do>
...
```

