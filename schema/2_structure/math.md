---
layout: default
title: Math
---

#Math


##Overview


The "definitions" element is a container element that holds blocks of
instructions. These blocks define the calculations and much of the
calculation sequence.


The "math" element is then used to specify how the calculations should be
started.


The equation solver does four types of math:


* Context Math: This math is calculated just once at the beginning of
a solution. The math is primarily used to scale the model.


* Parameter Math: This math is calculated after a parameter value
has been changed. This math defines values that a solely
derivatives of parameter values.


* Derivative Math: This math is used to calculate the derivatives
during each integration interval. This is the workhorse.


* Wrapup Math: This math is calculated after the successful
completion of an integration interval. Variables not used in
calculating the derivatives can be defined here, such as variables
used only in display. Variables that might cause a discontinuity in
the solution are also defined here.


The equation solver then wants to know the names of the four blocks that
initiate these four types of calculations. We use the math element to
specify the four appropriate block names.


Having a block of each calculation type is optional. Of course, if we have
no named blocks, no calculations will be undertaken.


The order of frequency of calculation types (most to least) is:


* Derivatives

* Parameters

* Wrapup

* Context


Calculation Sequence:

The sequence of calculation is significant. The technical rule is that each
variable must be defined before it can be referred to. This keeps
numerical errors small.


Referred to means being named in an equation on the right-hand side of
the equals sign.


Defined means being named in an equation on the left-hand side of the
equals sign.


In this XML schema, the def element is equivalent to an equation.


    <def>


        <name> Variable Name </name>


        <val> Mathematical Expression </val>


    </def>


The name variable name is on the left-hand side of the equals sign and is
defined in the def element. The val mathematical expression is on the
right-hand side of the equals sign. It can refer only to variables that are
defined.


As an example, consider the equations:


A = 20 * B 			(1)


B = 5 * C 			(2)


These two equations cannot be calculated in the order shown above,
because B is referred to in Equation (1) before it is defined in Equation (2).
So the order of calculation must be reversed, with (2) being calculated
before (1). In addition, C must be defined earlier yet to make it available
when (2) is calculated.


Use the order of def?s within a block and the math and call elements
across blocks to specify the correct order of calculation.


## < math >


Use this element to specify how the calculation sequence starts off in
several different calculation categories. A math block is specified for each
calculation category.


There are four types of calculations: context, parms, dervs and wrapup.


    <math>


        <context> Context math block. </context>


        <parms> Parameter math block. </parms>


        <dervs> Derivative math block. </dervs>


        <wrapup> Wrapup math block. </wrapup>


    </math>


The math element can be omitted when there are no relevant calculations
to call (which is never).


The various math elements are optional. There are no defaults.


I?ve snipped the math element from HUMMOD 2008, Model.DES.


    <math>


        <context> Context.Math </context>


        <parms> Structure.Parms </parms>


        <dervs> Structure.Dervs </dervs>


        <wrapup> Structure.Wrapup </wrapup>


    </math>