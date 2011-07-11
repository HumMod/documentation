---
layout: default
title: Volume 2 - Structure
---

# Overview


Volume 2. Structure describes elements that are used to describe a
model's structure.


The top-level element is named structure. It is a container element for
elements that declare the variables (variables), declare the differential and algebraic equations (equations), define the functions (functions), and specify the math used to calculate derivatives and intermediate values(definitions). Each of these elements has a section in this volume.


The element math is also defined in this volume but it is used as a top-level element in model. This is not meant to be trickery. Instead, math specifications are a top-level function but block names (introduced in this volume) are an inherent part of the specifications.


# < structure >


    <structure>


        <name> Unique structure name here. </name>

        Structure detail elements go here.


    </structure>


Variables, equations, functions, math blocks and other model components
created in a structure have a local name (valid within the structure) and a global name (valid everywhere). You can review naming in Volume 1. Model, Additional Grammar, Names.


# Contents


* [Variables](variables.html)


* [Equations](equations.html)


* [Functions](functions.html)


* [Definitions](definitions.html)


* [Math](math.html)