---
layout: default
title: Variables
---

# __Overview__


The variables element is used to declare and sometimes define the
model's variables.


There are currently eight variable types: var, parm, constant, fixedparm, fixedvar, timervar, normaldist, whitenoise.


A variable is declared when it is given a name. It is defined when it is given a value or instructions for calculating a value. Instructions usually come in the form of a mathematical expression.


All but two of the variable types are declared and defined in a single
element. The exceptions are the var and fixedvar variable types. These
variables can be declared and defined in a single element, but the var
variable type is usually declared but not initially defined. Defining takes place in a math block as part of the calculation of a derivative value or an intermediate value.


Variable Attributes:

The table below shows the attributes of each variable type.


![Variable Types](https://github.com/HumMod/documentation/raw/gh-pages/images/schema/variable_table.jpg)


System variables are defined, read-only, and restarted.


# __< variables >__


Use this element to declare and sometimes define the model's variables.


There are a variety of variable types, but the two most common are an
ordinary variable var and a parameter parm:


    <variables> Variable declarations. </variables>


These variable types are detailed next:


* var

* parm

* constant

* fixedparm

* fixedvar

* timervar

* normaldist

* whitenoise


# __< var >__


Use this element to declare an ordinary variable. The variable can also be defined here (by assigning it an initial value), but defining is typically deferred to a math block.


    <var>


        <name> Unique variable name here. </name>


        <val> Initial value (optional) here. </val>


    </var>


Initial value is floating point.


# __< parm >__


Use this element to declare and define a parameter, giving it a unique
variable name and an initial value.


    <parm>


        <name> Unique variable name here. </name>


        <val> Initial value goes here. </val>


    </parm>


Initial value is floating point.


A parameter is a defined variable having the additional privilege of being able to receive a new value in an interactive panel via a slide bar, radio button, check box, edit box, and maybe some other visual device.


# __< constant >__


Use this element to declare and define a constant, giving it a unique
variable name and a value.


    <constant>


        <name> Unique variable name here. </name>


        <val> Value goes here. </val>


    </constant>


Value is floating point.


A constant is a defined variable having the restriction that if can?t be assigned a new value. This restriction applies to `<def>` and `<conditional>` elements.


Internally, a constant has the ReadOnly variable attribute.


# __< fixedparm >__


Use this element to declare and define a fixed parameter, giving it a
unique variable name and an initial value.


    <fixedparm>


        <name> Unique variable name here. </name>


        <val> Initial value goes here. </val>


    </fixedparm>



Initial value is floating point.


A fixed parameter is a parameter having the additional attribute of not
being reset to its initial conditions at solution restart. Thus, a particular value will remain in place over multiple solutions.


# __< fixedvar >__


Use this element to declare and define a fixed variable, giving it a unique variable name and an (optional) initial value.


    <fixedvar>


        <name> Unique variable name here. </name>


        <val> Initial value (optional) goes here. </val>


    </fixedvar>


Initial value is floating point.


A fixed variable is a variable having the additional attribute of not being
reset to its initial conditions at solution restart. Thus, a particular value will
remain in place over multiple solutions.


The primary use of this variable type is to implement scaling in context
math.


# __< timervar >__


A timer variable is synchronized with the independent variable. It can
count up from an initial value, count down from an initial value, or be in an OFF state. One use is to track elapsed time.


Use this element to declare and define a timer variable, giving it a unique variable name, an (optional) initial value and an (optional) initial state.


    <timervar>


        <name> Unique variable name here. </name>


        <val> Initial value (optional) goes here. </val>


        <state> State (optional) goes here. </state>


    </timervar>


Initial value is floating point. The default value is 0.


Valid states are UP, DOWN and OFF. The default state is OFF.


There is a timer element in defininitions that can be used to change
(usually conditionally) the value and state of a timer variable.


# __< normaldist >__


Use this element to declare and define a variable that gets its value from a normal distribution. The mean and standard deviation of the distribution are specified here.


    <normaldist>


        <name> Unique variable name here. </name>


        <mean> Distribution mean here. </mean>


        <stddev> Standard deviation here. </stddev>


    </normaldist>


Default values for mean and standard deviation are floating point 0 and 1. There is a scramble element in control that controls randomness for this variable and the whitenoise variable.



# __< whitenoise >__


Use this element to declare and define a variable that gets its value from a
white noise distribution. The lower and upper limits of the distribution are
specified here.


    <whitenoise>


        <name> Unique variable name here. </name>


        <lowerlim> Lower limit. </lowerlim>


        <upperlim> Upper limit. </upperlim>


    </whitenoise>


Default values for the lower and upper limits of the distribution are floating point 0 and 1.


There is a scramble element in control that controls randomness for this variable and the normaldist variable.