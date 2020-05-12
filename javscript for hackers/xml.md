### what is xml ?
- it stands for extensible markup language 
- it is used to store and transport data from server to client 
- it has tree like structure 

``` xml 
<root>
    <child>
        <subchild> ------ </subchild>
    </child>
</root>
```

- every xml file has prolog in starting
``` xml 
<?xml version="1.0" encoding ="UTF-8"?>
```

- all xml element must have closing tag , tags are not predefined like html , we can use our own tags
 ``` xml 
<?xml version="1.0" encoding ="UTF-8"?>
<bookstore>
    <book>
        <title>harry porter</title>
    </book>
</bookstore>
 ```

 - tag can have attribute in name/value parts and attribute must be in quoted 
 ``` xml 
<note date ="11/04/2020">
    <to>nitish</to>
    <from>nit</from>
</note>
 ```
 - we cannot use special characcters in xml instead we use entity reference
    - &lt
    - &gt 
    - &amp
    - &apos
    - &quot

- to avoid name space conflicts we use prefix
``` xml
<bookstore>
    <h:book> 
        <title>title</title>
    <h:book>
    <p:book>
        <title>title2</title>
    <p:book>
</bookstore>
```

### XML DOM 
- it is same as html DOM
- / -> root node 
-  // -> //book ,all book elements
- . -> current node
- .. -> parent of current node
- @ -> attributes

![img](https://github.com/nitishsaini706/references-images/blob/master/xmldom.gif)
``` xml
<bookstore>
    <book>
        <title lang="en">harry </title>
        <price> 29 </price>
    </book>
</bookstore>
```
- /bookstore - root element bookstore
- //book -> select all books
- //@lang -> select all attributes names lang

### xquerry 
- it is used for queryinh xml
- doc(xml file) - to open xml file
- FLWOR -; for , let , where , order by , return , it uses path expression

        doc(xml file)/bookstore/book

``` xml
for $x in doc("book.xml")/bookstore/book
    return if ($x/@category = "children")
    then <child>{data($x/title)}</child>
    else <adult>{data($x/title)}</child>
```

### document type definition (DTD)
- it is declared inside xml file wrapped inside 
    - <!DOCTYPE> definition

- these are building blocks of xml document 
- elements 
    - body
    - hr
    - table
    - br ,etc

- attributes 
    - extra info about elements 

- entities 
    - special meaning characters 
- pc data 
    - parsed character data , text that will be parsed by parser
- cdata
    - character data not be parsed by parsed

- elements are declared within element declaration 
    - <!ELEMENT     element-name category or (elemnt content) >

- attributes
    <!ATTlist elementname attribname attribtype attribvalue>

- entities - three types of entities 
    - internal
    - external
    - parameter xml
- internal -> defined within local DTD 
    - ``<!Entity foo"bar" >  = this is refered as foo; in xml in place of bar

- external ->outside of local dtd 
    - ``<!Entity foo system" file:///external link>
- parameter xml - used with dtd , % symbol 
    - <!Entity % name "entity-value">
- internal entity example
``` xml

<!ENTITY writer "Donald Duck.">
<!ENTITY copyright "Copyright W3Schools.">

<author>&writer;&copyright;</author>

```
- external entity example
``` xml 
<!ENTITY writer SYSTEM "https://www.w3schools.com/entities.dtd">
<!ENTITY copyright SYSTEM "https://www.w3schools.com/entities.dtd">


<author>&writer;&copyright;</author>
```


## attacks on xml
- The penetration tester running XML tests against application will have to determine which XML parser is in use, and then to what kinds of below listed attacks that parser will be vulnerable.

### [1] XML External Entities expansion / XXE

An XML External Entity attack is a type of attack against an application that parses XML input. This attack occurs when XML input containing a reference to an external entity is processed by a weakly configured XML parser. This attack may lead to the disclosure of confidential data, denial of service, server side request forgery, port scanning from the perspective of the machine where the parser is located, and other system impacts.


```
<?xml version="1.0" encoding="ISO-8859-1"?>
  <!DOCTYPE foo [  
  <!ELEMENT foo ANY >
  <!ENTITY xxe SYSTEM "file:///etc/passwd" >]><foo>&xxe;</foo>
```

### [2] DTD Retrieval

This case is similar to external entity expansion, too. Some XML libraries like Python's xml.dom.pulldom retrieve document type definitions from remote or local locations. Several attack scenarios from the external entity case apply to this issue as well.

```
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html>
    <head/>
    <body>text</body>
</html>
```
### [3] Decompression Bomb

Decompression bombs (aka [ZIP bomb](https://en.wikipedia.org/wiki/Zip_bomb)) apply to all XML libraries that can parse compressed XML streams such as gzipped HTTP streams or LZMA-compressed files. For an attacker it can reduce the amount of transmitted data by three magnitudes or more.

```
$ dd if=/dev/zero bs=1M count=1024 | gzip > zeros.gz
$ dd if=/dev/zero bs=1M count=1024 | lzma -z > zeros.xy
$ ls -sh zeros.*
1020K zeros.gz
148K zeros.xy
```


---

### [4] XPath Injection

XPath injeciton attacks pretty much work like SQL injection attacks. Arguments to XPath queries must be quoted and validated prohttp://www.ibm.com/developerworks/xml/library/x-xpathinjectionperly, especially when they are taken from the user. The page [Avoid the dangers of XPath injection](/index.html) list some ramifications of XPath injections.

---

### [5] XInclude

XML Inclusion is another way to load and include external files:

```
<root xmlns:xi="http://www.w3.org/2001/XInclude">
  <xi:include href="filename.txt" parse="text" />
</root>
```


This feature should be disabled when XML files from an untrusted source are processed. Some Python XML libraries and libxml2 support XInclude but don't have an option to sandbox inclusion and limit it to allowed directories.

---

### [6] XSL Transformation

You should keep in mind that XSLT is a Turing complete language. Never process XSLT code from unknown or untrusted source! XSLT processors may allow you to interact with external resources in ways you can't even imagine. Some processors even support extensions that allow read/write access to file system, access to JRE objects or scripting with Jython.

Example from [Attacking XML Security](https://www.isecpartners.com/media/12976/iSEC-HILL-Attacking-XML-Security-bh07.pdf) for Xalan-J:

```
<xsl:stylesheet version="1.0"
 xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
 xmlns:rt="http://xml.apache.org/xalan/java/java.lang.Runtime"
 xmlns:ob="http://xml.apache.org/xalan/java/java.lang.Object"
 exclude-result-prefixes= "rt ob">
 <xsl:template match="/">
   <xsl:variable name="runtimeObject" select="rt:getRuntime()"/>
   <xsl:variable name="command"
     select="rt:exec($runtimeObject, &apos;c:\Windows\system32\cmd.exe&apos;)"/>
   <xsl:variable name="commandAsString" select="ob:toString($command)"/>
   <xsl:value-of select="$commandAsString"/>
 </xsl:template>
</xsl:stylesheet>
```

## what is xml attack
- it is using an malicious xml file which is send to the server 
-  impact when exploited 
	- dos 
	- information disclosure
	-external requests
	- remote code execution

## xml basics 
- it is extensible markup language , it is based on SGML or standard generalized markup language 
-  see owasp for futher detail 


## two types
- xml external entity injection
	- info disclosure
	- perform external requests
	- remote code execution
- xml external entity expansion
	- dos
	- recurevise references
	- deplete server of its resources 

- in injection xml has external entities like website or internal resource
- in expansion the file has recursive expansion, which causes dos

## xml validation
it is done using xlint 

## how to test for vuln
- it is done using tools like source code or specialized tools ,testing user inputs ,use payloads that retireve info , trying to access external resources  