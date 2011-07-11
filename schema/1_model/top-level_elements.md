---
layout:default
title: Top-Level Elements
---


# Overview

An XML document has a single element (the document element or root
element) that holds (or encloses) all of the document's other elements (the child elements). In this schema, the document element is named model.


Elements in an XML document may be nested to any level. It is
customary to call elements that are the immediate children of the
document element the top-level elements. The model element's top-level
elements are:


* schema

* modeltitle

* structure

* math

* control

* display


Structure, math, control and display are described elsewhere.


# < schema >


Use this element to give the schema an identifier that can be used by a
parser to find out which model documentation schema is being parsed:


    <schema> Schema ID goes here. </schema>


This element is required. It must be the first element. Use only once per
model.


An example:


    <schema> 2008.0 </schema>


# < modeltitle >


Use this element to define a title for a model. I expect the equation solver will display the title on its title bar. We might also get some use out of it in Web pages and document translators.


    <modeltitle> Model title goes here. </modeltitle>


This element is required. Use only once per XML document.


# < model >


This is the model's document element or root element. It holds all of the model's other elements (the child elements).


    <model> Top-level elements go here. </model>


The model element holds several types of child elements:


* A schema identifier.


* A model title.


* One or more structure elements (Volume 2).


* A math element (Volume 2).


* A solution control element (Volume 3).


* Solution display elements (Volume 4).