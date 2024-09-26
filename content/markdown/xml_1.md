- Derived from Standard Generalized Markup Language
- Software and Hardware Independent
- Used for Storing and transporting data
- Self-descriptive
- W3C (World Wide Web Consortium) Recommendation

### Characteristics
- Extensibility: Create new self-descriptive tags or language.
- Functional: Used not to present but to store.
- Standard: It has an open standard recommended by W3C

### Applications

- Simplify creation of HTML documents
- Exchange Information
- Offloading and reloading databases
- Merged with Style Sheets to create any desired output

### Differences between XML and HTML

| XML           | HTML          |
| :-------------: | :-------------: |
| Carry Data    | Display Data  |
| Self-descriptive tags | Pre-defined tags |

### Syntax
```xml
<?xml version="1,0"?>
<contact_info>
    <name>Nancy</name>
    <company>Arkade</company>
    <phone> 8506025748 </phone>
</contact_info>
```
Two kinds of information: Markup(contact_info), Text(Nancy)

### XML Declaration

```xml
<?xml version="1.0" encoding="UTF-8"?>
```

Here, *version* is the XML version and *encoding* is the character encoding used.

__XML Declaration__ is case sensitive. ``` "<?xml>" ``` must  be written as is.

It should be the __first__ line of the document.

An HTTP protocol can override the value of encoding specified.

### Tags and Elements

- enclosed in triangular brackets < >
- Should be closed either by a closing tag or by adding / to the opening tag.

- Can contain multiple XML-Elements as its children. Children must not overlap.

### Root Element

A document can have only one root element. 
```xml
<root> 
    <x></x>
    <y></y>
</root>
```

### Case Sensitivity

Tags are case sensitive. The opening and closing tags must be in exactly the same case.

### Attributes

A property of an element, in the form of a name/value pair.

- case-sensitive
- an element cannot have two attributes with the same name
- attribute name is written without quotation marks, values are always written with quotation marks.

### XML References

Used to add additional text or markup in a document. 

- begin with an **&** and end with **;**. Two types of references:
    - **Entity References**: contains a name.
    - **Character References**: contains a hash and a number.

### XML Text

- Whitespaces are ignored.
- Some characters are reserved by xml and therefore cannot be used directly. Entities can be used instead.

| Character | Replacement-entity |
|:---------:|:------------------:|
| < | \&lt; |
| > | \&gt; |
| & | \&amp; |
| ' | \&apos; |
| " | \&quot; |

### XML Namespaces

Solves conflicts between different xml documents used together.

xmlns attribute can be used int the starting tag of an element.

```xml
<root> 
<h:element xmlns:h="http://www.w3.org/TR/html4/">
    <h:subelement />
</h:element>

<f:element xmlns:f="http://www.w3.org/TR/furniture">
</f:element>
</root>
```

### XML Validator

A "valid" XML docuement must be well-formed(follow syntax rules ) and it must conform to a document type definition.

There are 2 different document type definitions:
- **DTD** - The original Document Type Definition
- **XML Schema** - An xml0based alternative to DTD 

#### DTD

```xml
<!DOCTYPE book [
<!ELEMENT book (title, author, price)>
<!ELEMENT title (#PCDATA)>
<!ELEMENT author (#PCDATA)>
<!ELEMENT price (#PCDATA)> 
]>
```

The document type is ``` book ```.
The ``` book ``` element must contain ``` title ```, ```author``` and ```price```.
```title```, ```author``` and ```price``` require to be of type "#PCDATA"(Parse-able Character Data)

DTDs can be internal or external.

- Internal DTDs are defined just after the XML Definition.
- External DTD are sourced from another file.

```xml
<!DOCTYPE student SYSTEM "external.dtd">
```

Applications of DTD:
- Independent groups of people can agree to use a standard DTD.
- To verify own data.

#### XML Schema

Alternative to DTD, xml-based.

```xml
<xs:schema>
    <xs:element name="elementName">
        <xs:complexType>
            <xs:sequence>
                <xs:element name="title" type="xs:string"/>
                <xs:element name="author" type="xs:string"/>
            </xs:sequence>
        </xs:complexType>
    </xs:element>
</xs:schema>
```

the element ```book``` is a complexType i.e. root.

Can be saved as schema.xsd and imported

```xml 
<student xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.w3schools.com student.xsd"> 
```

### XSLT

XSL - Extensible Stylesheet Language
XSLT - XSL Transformations

- XSLT transforms XML into another XML document
- XSLT uses XPath to navigate in XML documents
- XSLT is a W3C recommendation

```xml
<?xml-stylesheet type="text/xsl" href="book.xsl"?>
```

```xml
<?xml version="1.0" encoding="UTF-8"?><xsl:stylesheet version="1.0" xmlns:xls="http://www.w3.org/1999/XSL/Transform"><xsl:template match="/">
<html>
    <body>
        <h2>Book Details</h2>
        <table border="1">
            <tr>
                <th>Title</th>
                <th>Author</th>
            </tr>
            <xsl:for-each select="book_store/book">
                <tr>
                    <td><xsl:value-of select="title" /></td>
                    <td><xsl:value-of select="author"/></td>
                </tr>
            </xsl:for-each>
        </table>
    </body>
</html>
</xsl:template>
</xsl:stylesheet>
```

