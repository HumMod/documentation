---
layout: default
title: Functions
---

#Functions


##Overview


The functions element is used to define the model?s functions. Currently
the only function that is supported is the curve.


A curve is a function that takes a single input and returns a single output.
The curve is used in mathematical expressions. The curve?s functional
relationship is represented by modified cubic splines.


There is an alternative way to implement the functionality of a function.
The alternative is to use a sequence of copy, call and copy elements. This
approach is useful, powerful and verbose. I?ll try to provide details in
definitions.


## < functions >


Use this element to define a model?s functions. The one available function
type is curve.


    <functions> Function definitions here. </functions>


The functions element is not needed in structures with no function
definitions.


## < curve >


A curve is a function that takes a single input and returns a single output in
a mathematical expression.


The curve element contains child elements that name the curve and list
the data points that define the curve.


Each data point contains an x value, y value and slope.


    <curve>


        <name> Curve name. </name>


        <point>

            <x> X </x> <y> Y </y> <slope> S </slope>

        </point>


        More points go here.


    </curve>


X, Y and S are floating point.


* A valid curve definition has two or more data points. There is no upper
limit to the number of data points.


* Curve X values must be defined in ascending order.


As an example, here is a curve named VolOnPressure taken from
HUMMOD 2008, BVSeqArtys.DES.


The curve is shown below as it appeared in the Tech tabbed dialog box.


![Curve](https://github.com/HumMod/documentation/raw/gh-pages/images/schema/curve_cap_p65.jpg)


The curve definition is:


    <curve>


        <name> VolOnPressure </name>


        <point>


            <x> 0 </x><y> 0 </y><slope> 0 </slope>


        </point>


        <point>


            <x> 50 </x><y> 97 </y><slope> 1.0 </slope>


        </point>


        <point>


            <x> 200 </x><y> 150 </y><slope> 0.5 </slope>


       </point>


    </curve>


The curve was used in the following def element.


    <def>


        <name> TMP </name>


        <val> VolOnPressure [ Vol ] </val>


    </def>


In the val element, the name of the curve is followed by square brackets
enclosing the name of the input variable. The output value is TMP (for
transmural pressure). The input value is Vol (for blood volume).