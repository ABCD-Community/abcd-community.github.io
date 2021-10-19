---
title: ABCD Unicode
description: As from ABCD v2.0 both the software-interface as the data can work with non-Latin alphabet characters, based on the 'UTF8' standard of the Unicode-technology.
lang: en
lang-ref: abcd-unicode
---

# ABCD Unicode

{: .no_toc }

## Content
{: .no_toc .text-delta }

1. TOC
{:toc}

---


# ABCD Unicode and localisation
    
As from ABCD v2.0 both the software-interface as the data can work with non-Latin alphabet characters, based on the 'UTF8' standard of the Unicode-technology.

Unicode means that instead of the historically very limited 'ASCII-table' with 256 character codes (e.g. 65 for 'A', 66 for 'B' etc.), i.e. the basic interpunction (.,;-...), the numbers 0-9 and alphabetical characters in lower and upper- case only another limited non-standard set of characters could be defined. E.g. frequently used Greek characters like alpha (##) or sigma (##) were typically included in the encoding table of ASCII. Even with such 'available' space to redefine 128 characters in the non-standard part of the table (which was e.g. also used to make WinISIS capable of dealing with Arab), not all alphabets could be accommodated for (e.g. Chinese has many more char- acters), let alone combinations of alphabets. With Unicode the capacity of this table is enlarged to about 65000 characters, enough to include all known alphabets. In modern computer hardware and software storing such a table is no longer a real challenge.

Basically introducing Unicode to ABCD required making the (C)ISIS technology Unicode-compatible and add some functions (e.g. conversion from ANSI to UTF8 of text-files) in the interface. Both aspects will be explained in this chapter in the following two sections.

## Unicode processing of the information

CISIS just stores 'characters' as bytes and in the original non-Unicode era (ASCII or its Windows-variant ANSI) each character was one single byte to represent it : single-byte. In order for ISIS to read the next character it simply needs reading the next byte. This changes drastically when multi-byte solutions as necessary for Unicode come into action : one byte can only represent 2^8 = 256 characters, so if more characters need to be encoded, more bytes will be necessary.

The UTF8 method was chosen for its backwards-compatibility with ASCII : UTF8 (but not UTF16 which always uses at least 2 bytes) allows single-byte encoding for the basic alphabets (Latin) and therefore ASCII-coded texts remain fully compatible with UTF8. This is of course very important for ABCD where such a wealth of ASCII- encoded information already exists and needs to remain available. However UTF8 or UTF16 can go up to 4 bytes for one character, so a sophisticated mechanism is needed to tell the software whether after reading the next byte still another (and another...) byte needs to be read in order to represent the next one character. These functions were implemented in the CIUTF8.c code of CISIS. Needless to state that these functions are very crucial since they are activated whenever bytes need to be read from a record.

Whenever a function of CISIS needs this multi-byte capability, such different mechanisms need to be used instead of the previous single-byte functions. In addition, the simple structure of the basic ASCII 'isisac.tab' just lists all up to 256 characters to be considered as 'alphanumerical' when ISIS is parsing data in order to identify 'words' which can be indexed for searching. For the upper-case translation table isisuc.tab two lists are needed : one with the lowercase values and another one with the corresponding uppercase values to which the lowercase ones will be translated. When - as it the case with UTF8 - characters no longer are defined with one single value (e.g. 65) they can only be defined with 'separators' in order to keep them grouped by character, so the UTF8 version of CISIS needs the ACTAB and UCTAB tables to use separate lines for each character, and each line can have, except for some optional 'comments' after a comment-separator '#', up to four columns.

So the original format of the ACTAB, which defines all characters considered to be part of a word for indexing, looks like this :

  
```
048 049 050 051 052 053 054 055 056 057 065 066 067 068 069 070 071 072 073 074 075 076

077 078 079 080 081 082 083 084 085 086 087 088 089 090 097 098 099 100 101 102 103 104

105 106 107 108 109 110 111 112 113 114 115 116 117 118 119 120 121 122 192 193 194 195

196 197 199 200 201 202 203 204 205 206 207 209 210 211 212 213 214 216 217 218 219 220

221 224 225 226 227 228 229 231 232 233 234 235 236 237 238 239 241 242 243 244 245 246

248 249 250 251 252 253 255  
```
  
whereas the UTF8 format now looks like (taking only some parts of the real table, the 'tab-signs' are represented to identify colums) :
```
065 # A
195 128 # A grave
216 128 # ARABIC NUMBER SIGN
224 164 132 # Devanagari #
224. 182 133 #SINHALA LETTER AYANNA #
225. 136 128 # ETHIOPIC SYLLABLE HA #
```

> Note
> 1.  decimal values are used while most Unicode-tables use hexadecimal coded values



> Note
> 2.  all values need to be listed in ascending order, otherwise the software will reject the table

In the case of upper-case translation a typical conversion for ABCD Unicode line will look as follows : 225 136 128=225 136 128 # ETHIOPIC SYLLABLE HA

> Note
> 1.  Most non-Latin alphabets don't have case-sensitiveness, so in this case (Amharic) the 'lowercase' is translated to the uppercase with
> exactly the same values. Such lines can as well be omitted and then no uppercase-translation will be performed.
> 
> 
> 
> Note
> 2.  Adjustments in the FST are needed : since in non-Latin scripts the use of upper-case translation is not known in advance, UTF8-databases
> need to be indexed with specif- ic instructions for the ’mode’-setting
> for uppercase, therefore : specifically add the in- struction mode
> ’mpu’ (instead of mpl), ’mhu’ (instead of mhl), e.g. 245 5
> ’/TI_/’,mpu, v245^a

Adding Unicode to ABCD mainly - or in fact 'only' - has relevance when indexing and searching a database : in these functions the 'bytes' stored in the MST need to make sense to indicate whether they are alphanumerical or not. But when indexing and searching is to be done, the differences in the basic tables of ASCII vs. UTF8 as illustrated above are very important, so a non-UTF8 version of ISIS cannot deal with a Unicode database properly and v.v. whenever indexing and searching are involved. In ABCD 2.0 both versions non-UTF8 and UTF8 are 'co- existing' for this reason, in the following way :

-   the cgi-bin directory where the ISIS-executables are located has been completely re-organized : it now contains two basic sub-directories, one for ANSI and one for UTF8 and all executables are located there according to whether they are 'classic' (ANSI) or UTF8.
-   all calls to the ISIS-executables (mainly wxis and mx) are now constructed in the PHP-scripts using a variable '$unicode' which defines whether the path /ansi/ or /utf8/ needs to be added to the cgi-bin folder when calling the executable.
    

> Note The same mechanism is used for the definition of special
> CISIS-versions, whether ANSI or UTF8, e.g. 'BigISIS' with the variable
> $cisis_ver

-   in the base directory for databases (e.g. /var/opt/ABCD/bases in Linux) both the classic isisac.tab and isisuc.tab as well as the new UTF8-versions isisactab_utf8.tab and isisuctab_utf8.tab are stored. All PHP-scripts needing them (e.g. for indexing) will search for these tables according to whether the database is Unicode or not, first of all in the proper 'data'-subdirectory of the database itself, if not found in the base directory.


> Note:
> This last mechanism allows for the use of adapted tables per
> database : if a catalog e.g. only uses in addition to Latin the
> Amharic alphabet, only the Amharic entries are needed in the table and
> no unnecessary large tables need to be loaded in memory and parsed.

  
## Unicode interface elements

After the explanation about the Unicode data-storage, the Unicode interface elements are discussed next.

### General interface setting : Unicode or ANSI

In the Central main menu a (new) option 'Encoding' is provided to select either ANSI or Unicode as the default charset for displaying ABCD interface pages. This only relates to the HTML-pages and text-files used in ABCD, not the databases and their contents. This is a system-wide setting, so it defines all pages of ABCD Central.![](https://lh4.googleusercontent.com/ng26tvkoBhcZTrCTyYLW3jPGQa__ZS_inMt0Ie9_lPh-QFNgmSL0e83PwqTmcgXZxyShiFOymfcO3kBKkP94AD3YQJGU83llp35AuRKbHmzxI87MWNCOqt8UBhiUwYTYbHIymvg=s0)


So when UTF8 encoding is used in e.g. configuration files like abcd.def, non-ASCII characters like diacritics, will be displayed wrongly unless the correct setting here is selected.

### Conversion of text-files in htdocs and database-definitions to UTF8
    
When an existing ABCD (1.x) installation needs to be converted to a UTF8 environment, many files in the file- system of ABCD are encoded as 'ANSI', which will have consequences in how non-ASCII like diacritics are displayed - mostly wrongly ! Their encoding therefore needs to be converted to UTF8-encoding in order for such special characters (or any non-Latin characters by definition) to display correctly.

  

Tools in the extra ’utilities’-menu are provided to convert selected types of existing files (php-scripts, text-files, ISIS-formats…) from ANSI to UTF8 and vice versa. See also the discussion of the utilities in the chapter about ABCD modules.![](https://lh6.googleusercontent.com/XUNMtRvPsmpStIVlWtqk8OD_0YHHR4fQ2649AUCqdL9-2bBMU_kJgvaW8H5ABHprKzW7NDIM_6QpbAmp626tmwwawUX--lk7zk4vMLCm6W-LhdMeV0UKKE-Dz1_yb2SFl3Phb8U=s0)

An important thing to consider here is that as far as the databases themselves are concerned, only the database-de- finition files (which are text-files) will be converted, e.g. the FDT (so it can then use non-Latin alphabet field names), the PFTs, the FST, the stopwords-list etc. The database-files themselves, in fact the 'master' MST is not affected by this conversion. For the MST file with the actual data in the database, the following reasoning applies :  

-   if only ASCII-encoding was used, no conversion is actually needed, except for the indexes which need to be rebuilt
-   if non-Latin characters were encoded e.g. with 'HTML-codes', a gizmo needs to be applied to convert these strings, which look like Unicode on the screen (because of the browser interpreting them correctly) but actu- ally are not stored as UTF8. E.g. a string 'àé' could also have been stored with html-codes as '&Agrave;&Ea- cute;' but the string '&Agrave;' will not have been translated to 'A' as per the ISIS-uppercase translation table (ISISUC.TAB) nor will be searchable as 'AE'. These two HTML-codes need to be converted to the UTF8 rep- resentation for 'àé' and indexed with the appropriate 'isisactab_utf8.tab' and if you want 'à' to be converted to 'A' for searching, the appropriate 'isisuctab_utf8.tab'.
-   ANSI-databases can be exported to ISO2709 text-files and imported with the UTF8-version of mx; re-encoding the text-file itself to UTF8 will lead to problems because ISO2709 is very sensitive to the stored lengths of strings, so if a character which was stored in one byte is now stored in two bytes the ISO2709 file no longer can be read and reconstructed correctly.
    

The situation of still existing mixed ASCII, ANSI and Unicode charactersets is a problematic one anyway. E.g. the PHP-language for this reason has given up on becoming Unicode and skipped its version 6 which was meant to solve this... Characters displayed wrongly will be seen still for long on many screens, mostly in websites but even in subtitles for movies.

### Dynamic adjustments of the selected 'charset'
    
The $unicode setting is taken from either the system-wide 'abcd.def' or the database-specific 'dr_path.def'.

#### ABCD Central

In HTML-pages an instruction can define which character-set (or charset) to use with the 'charset='-instruction. In ABCD Central some scripts therefore will check for the unicode-parameter and select a different charset accord- ingly. E.g. in the files htdocs/central/common/header.php and htdocs/central/common/display_header.php, which are creating the first part of the HTML-pages, the following code can be found :

```
if ($unicode==1) {
echo "<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\" />";
}else{
echo "<meta http-equiv=\"Content-Type\" content=\"text/html; charset=ISO-8859-1\" />";
}
```

#### ABCD iAH

Also in iAh (the ABCD OPAC) pages can be dynamically adjusted to whether or not they use Unicode databases. For this the following elements are needed :
  
DBN.def : a new parameter is added (at the end) : UNICODE=n, with AHINDXn.htm in iah/scripts/lang. When this parameter is set, i.e. is greater than 0, the value is put into the virtual field v5018^w, (with also an adjustment of the DBGIZMO in v5018^g) in the main script 'iah.xis', the actual script steering the whole OPAC. Different values, non-zero, can be used to activate different sets of alphabets, since the value set will define which file 'AHINDX.htm' will be used when displaying the buttons of the alphabets for end-user navigation into the related alphabet. E.g if UNICODE is set to 1, iAH will use the file AHINDEX1.htm of the related language folder in de scripts-directory, and this file can contain ’anchors’ to specific parts of the related alphabet. E.g. for Devanagari/Hindu :

```
<div class="rowCenter">
<input value="012..." name="indexRoot" type="submit">&nbsp;<input value=" A" name="indexRoot" type="subm
[...]
type="submit"><input value=" Z" name="indexRoot" type="submit" />
<HR>
<input value="#" name="indexRoot" type="submit">
<input value="#" name="indexRoot" type="submit">
<input value="#" name="indexRoot" type="submit">
<input value="#" name="indexRoot" type="submit">
<input value="#" name="indexRoot" type="submit">
```

The resulting screen of the ABCD OPAC will then show, in addition to the Latin alphabet, alsom some anchors for Devanagari/Hindu characters :
**![](https://lh5.googleusercontent.com/ar_7jS0oojOq9lvto0IqPH0dBShPr8KOz9iRRWvgdgrowXBnqfocNIA_l3R3yM-7G2LgeD4D99t_36NOgODazpFU3FXELY3PSYb_B5hYhz5Ugf0tA0c8OcNr7K5_FDJBYY8TpWU=s0)**

By creating other files AHINDEXn.htm with other values for n (e.g. 2, 3 …) one can adjust this screen for any combination of special alphabets to be used.

-   GIZMO databases : Since iAH uses optionally gizmo-databases, these need to be replicated in the proper version used for the main database searched, e.g. if the database is 1660utf8, then also the gXML-gizmo has to be transposed to 1660utf8 format, saved in a subdirectory of the gizmo-databasefolder or with a different name, and has to be referenced to accordingly (see next paragraph). If this is not done properly, 0 search results will be obtained.
    
First the original 1660 gizmo-database has to be exported into an ISO-file and this then has to be imported to create the special database, e.g. creating the gXML gizmo for ffiutf8 :

    mxffiutf8 iso=gXML.iso create=gXML_ffiutf8 now -all

In order for the above mentioned gizmo-files to be found by the iAH OPAC, they need to be correctly referenced to in the .def file for the related database in the PAR-database directory, e.g. for a UTF8 database in the 'FFI' variant (ffiutf8) :

mxffiutf8 iso=gXML.iso create=gXML_ffiutf8 now -all

In order for the above mentioned gizmo-files to be found by the iAH OPAC, they need to be correctly referenced
to in the .def file for the related database in the PAR-database directory, e.g. for a UTF8 database in the 'FFI'
variant (ffiutf8) :

```
FILE gXML_ffiutf8.*=/ABCD/www/bases/gizmo/gXML_ffiutf8.*
FILE gXML=/ABCD/www/bases/gizmo/gXML_ffiutf8.*
```

Dynamic adjustment of the correct charset in the iAH script `htdocs/iah/scripts/lang/ahhead.pft`, checking the above mentioned v5018^w to see if Unicode is to be used :

```
if val(v5018^w)>0 then
'<meta http-equiv="Content-Type" content="text/html; charset=utf-8" /> '
else
'<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" /> '
fi,
```

 Finally also the opening script 'index.php' for iAH needs now to check for the correct Unicode (and possibly also special CISIS-version) settings :

```
<?php
$base = ($_REQUEST['base'] != '' ?
 $_REQUEST['base'] : 'rda');
$lang = ($_REQUEST['lang'] != '' ?
 $_REQUEST['lang'] : 'en');
$form = $_REQUEST['form'];
//define database path according to OS
if (stripos($_SERVER["SERVER_SOFTWARE"],"Win") > 0)
$db_path="/ABCD/www/bases/" ;
else
$db_path="/var/opt/ABCD/bases/";
//unicode defined in abcd.def
$dbpath=$db_path."abcd.def";
$def2= parse_ini_file($dbpath);
if (isset($def2["UNICODE"])) {
$unicode=trim($def2["UNICODE"]);
if (intval($unicode)!=0) $unicode="utf8"; else $unicode="ansi";}
else
$unicode="ansi";
//cisis_ver and unicode defined in dr_path.def
$drpath= $db_path.$base."/dr_path.def";
$def= parse_ini_file($drpath);
if (isset($def["CISIS_VERSION"]))
$cisis_version=trim($def["CISIS_VERSION"]);
else
$cisis_version="";
if (isset($def["UNICODE"])) {
$unicode=trim($def["UNICODE"]);
if (intval($unicode)!=0) $unicode="utf8"; else $unicode="ansi";}
//echo "cisisver=".$cisis_version."<BR>";
//die;
if ($cisis_version!="")
$cisis_ver=$unicode."/".$cisis_version."/";
else $cisis_ver=$unicode."/";
//Path to the wwwisis executable (include the name of the program, in Windows add .exe)
$Wxis=$cisis_ver."wxis";
$hdr = "Location: /cgi-bin/". $Wxis . "/iah/scripts/?IsisScript=iah.xis&lang=" . $lang . "&base=" . strt
header($hdr);
?>
```

#### ABCD Site

The ABCD Site module is mostly based on HTML- and XML-files to store the 'configuration' of the Site, defining the layout and contents of the main web-page of the Site and some sub-pages referred to from this page, e.g.
warnings, explanations etc. If non-Latin is used in the website, make sure these files are encoded as UTF8, not as ANSI as is the case for the original ABCD-Site files.
While these text-files (.html and .xml in the 'site' database, for each language used in a sub-directory) can be edited directly, it is safer to use the Site Admin (e.g. http://127.0.0.1:9090/site/admin) CMS to now add the UTF8
path-parts (and similarly additional path-parts for special CISIS-versions) into the URL's of the metasearch-linked databases. E.g. the URL for a 'MARC'-catalog in UTF8 (MARCUNI) on a localhost ABCD-installation would
have to change from :

    /cgi-bin/wxis/iah/scripts/?IsisScript=iah.xis&lang=en&base=MARCUNI

to :

    /cgi-bin/utf8/wxis/iah/scripts/?IsisScript=iah.xis&lang=en&base=MARCUNI

and the same additional 'utf8/' path-string has to be added to the other links for resp. the search- and 'show result' link URLs. Failing to do so will result in either a 'file not found' error (e.g. the previous wxis-executable is no longer found) or the database being searched by the wrong version of wxis, resulting in 0-results.
For a small cosmetic correction, in the file `htdocs/site/xsl/public/metaiah/result.xslv` of UTF8 ABCD installations,
replace the string `'&#160;'` by :

    <xsl:text disable-output-escaping="yes">&amp;nbsp;</xsl:text>
