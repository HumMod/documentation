---
layout: default
title: Introducing XML
---

# XML History

XML is an acronym for Extensible Markup Language.
This document defines the rules for using XML to document structure and
details of a mathematical model in human readable and computer
readable format.

Traditionally, a strange set of marks (like a wavy underline and a capital P facing backwards) were used by editors to communicate with typesetters, to ensure that a printed document was correctly laid out and attractive. This is called markup.

With the advent of the digital computer and electronic documents, a
markup schema was needed that could be read by computers and
transported across networks. In about 1969, Charles Goldfarb, Ed
Mosher and Ray Lorie at IBM provided a solution in the form of GML –
named after their last name initials (maybe). GML was intended to
markup legal documents to send to the electronic typesetters that were
rapidly replacing human typesetters. This scheme was renamed
Generalized Markup Language (or so the story goes).

In the mid 1970's, Goldfarb and others added features to GML and
Generalized Markup Language became Standard Generalized Markup
Language (or SGML). SGML became an ISO (International Organization
for Standardization) standard in 1986 and is the current standard for
document markup work. But, looking ahead, it is not a markup language.
It is a specification for creating markup languages and it is very
complicated.

In about 1990, Tim Berners-Lee and Anders Bergland at CERN in
Switzerland used SGML to define Hypertext Markup Language (or HTML)
and the World Wide Web was born. HTML describes how documents
should look when displayed on a computer screen. HTML was not
extensible, but it was corruptible. It was a weapon used in the great
browser wars (and was a casualty at that).

There remained a need to organize data as it passed not only from
database to computer screen but also from database to database. And it
would be nice if the scheme was much simpler than SGML. A number of
people including John Bosak, Tim Bray, James Clark and C.M. Sperberg-
McQueen worked in 1996 and 1997 to define a new and better markup
language using SGML as the overriding standard. Extensible Markup Language (or XML) was born. It received W3C (World Wide Web
Consortium) endorsement in February 1998.

The extensible in XML's name identifies one of its major strengths. XML
can be customized to meet specific needs. In the case of mathematical
model documentation, we've developed an XML schema that is used to
represent the details of mathematical models, including the structure, the control of solutions and the display of results.


# XML Basics

XML organizes data using information stored in angle brackets (also
known as the less than and greater than signs). A pair of angle brackets and the enclosed information is known as a tag.


A pair of tags and their enclosed data is known as an element. The
leading tag is called the open tag. The enclosed data is called the
content. The trailing tag is called the close tag. An example


    <name> Text representing a name. </name>


The first text in an open tag is the name of the element. Note that no
spaces are allowed between the opening angle bracket and the start of
the element name.


The element name is repeated in the close tag with a forward slash (/)
prefixed.


Some elements do not enclose content. All of their information is
represented by a single tag. These are called empty elements. An
example


    <beep/>


An empty element is identified by a forward slash (/) as the last character before the closing angle bracket.


In addition to the element name, additional information may be stored in a tag. This information is organized as attributes.


Attributes are allowed in open tags and empty tags but not in close tags. An attribute has a name, an equals sign and a value. Spaces are allowed before and after the equals sign.


Values are always enclosed in paired double (“) or single (') quotation
marks.


Attribute values are text that can represent anything. Values typically
represent names of things and numbers.


# Processing Instructions

Processing instructions do not describe the content of an XML document.
Rather, processing instructions describe how a document's content should be processed.


Processing instructions are a private contract between the document and
the parser.


The form of a processing instruction is:


    <?name content ?>


The name should follow XML's name rules. The content is all text after
the name up to the final '?>'.


HUMMOD has its own parsing algorithms. This allows us to make
maximum use of processing instructions.


Several processing instructions used by HUMMOD are described next.


    ## <?include … ?>


A document is typically assembled from more than one file. The
processor must be told the file names and the sequence.

Use this instruction at the appropriate places in the document to tell the processor to include a file.


    <?include Filename goes here. ?>


The DES XML parser insists that included files end at a logical break in the document. Specifically, an included file cannot end inside of a tag or in text that is being parsed for content (#PCDATA). An included file can end between elements.


    ## <?path … ?>


When a document is assembled from files located in more than one folder, it is convenient to define a path that is prefixed to all subsequent file names.

Use this instruction to define a path to be prefixed to subsequent file
names.


    <?path Path specification goes here. ?>


    ## <?create … ?>


This instruction and the next two implement conditional includes. A
conditional include is an include instruction that is executed if a specific token has been created. Otherwise, the include instruction is ignored.

This multi-step process allows a single token to control multiple file
includes.


Use this instruction at the appropriate place in the document (usually early on) to create a token that will control the execution of a conditional include.


    <?create Token_name goes here. ?>


The token name cannot contain internal spaces. White space is used as
the name delimiter.


    ## <?if … ?>


If the named token has been created, the named file is included.
Otherwise, no action is taken.


    <?if Token_name File name. ?>


    ## <?ifnot … ?>


If the named token has not been created, the named file is included.
Otherwise, no action is taken.


    <?ifnot Token_name File name. ?>

# Special Characters

The less than ('<') and greater than ('>') characters are used to identify tags in XML. As you might imagine, if you use these characters in ordinary text, the XML parser will declare an error. Or, worse yet, it will commit an error without declaring it.


To work around this, XML defines several special characters and provides a way to represent them unambiguously and without error. Technically, the representations for special characters are called character entities.


Character entities begin with an ampersand (&) and end with a semicolon
(;).


* Ampersand       	&    `&amp;`

* Apostrophe      	'    `&apos;`

* Greater Than    	>    `&gt;`

* Less Than       	<    `&lt;`

* Quotation Mark  	“    `&quot;`



The table above shows the character entities for five special characters. For example, the greater than character can be represented in text by the character sequence `&gt;`.


As the text is being parsed, the character entity is removed and replaced by the special character that has been specified.


The single quote (apostrophe above) and double quote (quotation mark
above) are allowed in XML documents, but some restrictions can occur.
An alternative representation of these two characters can come in handy.


HTML supports these character entities also and many, many more
(except that the apostrophe `&apos;` is not supported).

# Comments

Comments can be placed in XML documents as communication to human
readers. But comments might also be processed by the document parser,
although this was not the original intention.


Comments may appear anywhere in a document, even before and after
the document element.


The form of a comment is:


    <!-- comment -->


To document a file's history, put the following two comments near the
beginning of the file:


    <!-- datecreated dd-mmm-yy -->
    <!-- datelastchanged dd-mmm-yy -->


Forbidden characters, such as angle brackets, may appear in comments.
The only character sequence that is not allowed in a comment is two
dashes in a row (--) that do not immediately precede the closing angle
bracket. XML parsers scan for the character sequence dash-dash to
locate the end of a comment, ignoring all other characters.