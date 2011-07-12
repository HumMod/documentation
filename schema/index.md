---
layout: default
title: Schema Index
---

# 2010 HumMod Schema

These documents describe the rules used by HumMod, and possibly other
equation solvers, to define a mathematical model.


Our intent was that the simulation environment would not be associated
with proprietary hardware, software and formatting. Extensible Markup
Language (XML) was selected as the grammar.


Briefly, XML uses names in angle brackets (`< and >`) to identify data. The brackets and names are called tags. Data lies between two tags. The tag � data � tag sequence is called an element and the data is called the element content.


There are five volumes in this document. The main task of these volumes
is to describe all of the XML elements that we have defined for out
modeling environment.


# Contents


[Volume 1. Model](1_model) 

This volume develops three topics. The first introduces
XML. The second describes some additional grammatical rules to be
used in model definition. The third describes the highest-level elements of the HumMod schema.


[Volume 2. Structure] (2_structure)

This volume describes the elements used in
defining a model's mathematical structure. Sections include variables,
equations, functions and math.


[Volume 3. Control] (3_control)

This volume describes control of the calculation of
solutions using interactive control.


[Volume 4. Display] (4_display)

This volume describes the elements used in creating
the display of a model?s calculated solution. Tasks include selecting the variables to be displayed, selecting the display method (numerical, graph, other), and laying out the screen?s panels.


[Volume 5. Miscellaneous] (5_misc)

This volume might describe a variety of miscellaneous
issues � but right now it focuses on file formats (schema) used for some of HumMod?s XML I/O.