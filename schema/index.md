------------------
layout: default
title: Schema Index
-------------------

#2010 HumMod Schema

##About
HumMod Schema


©1997 - 2011


Tom Coleman

mailto:support@biosim.com


Robert Hester

mailto:rhester@physiology.umc.edu


Richard Summers

mailto:rsummers@emergmed.umsmed.edu


Department of Emergency Medicine

Department of Physiology and Biophysics


University of Mississippi Medical Center

2500 N. State St.

Jackson, MS 39216 USA

[Modeling Workshop Workshop](http://physiology.umc.edu/themodelingworkshop/)

[Modeling Workshop Google Group](http://groups.google.com/group/modelingworkshop)

##Preface

These documents describe the rules used by HumMod, and possibly other
equation solvers, to define a mathematical model.


Our intent was that the simulation environment would not be associated
with proprietary hardware, software and formatting. Extensible Markup
Language (XML) was selected as the grammar.


Briefly, XML uses names in angle brackets (< and >) to identify data. The brackets and names are called tags. Data lies between two tags. The tag – data – tag sequence is called an element and the data is called the element content.


There are five volumes in this document. The main task of these volumes
is to describe all of the XML elements that we have defined for out
modeling environment.


[Volume 1. Model](1_model/index.md) 

This volume develops three topics. The first introduces
XML. The second describes some additional grammatical rules to be
used in model definition. The third describes the highest-level elements of the HumMod schema.


[Volume 2. Structure] 

This volume describes the elements used in
defining a model?s mathematical structure. Sections include variables,
equations, functions and math.


[Volume 3. Control] 

This volume describes control of the calculation of
solutions using interactive control.


[Volume 4. Display] 

This volume describes the elements used in creating
the display of a model?s calculated solution. Tasks include selecting the variables to be displayed, selecting the display method (numerical, graph, other), and laying out the screen?s panels.


[Volume 5. Misc]

This volume might describe a variety of miscellaneous
issues – but right now it focuses on file formats (schema) used for some of HumMod?s XML I/O.
