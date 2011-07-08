---
layout: default
title: Definitions
---

#Definitions


##Overview


The definitions element specifies the math used to calculate the model?s
derivatives and intermediate variables.


The math specifications are grouped into named blocks. The information
in the blocks describes the calculations and much of the calculation
sequence.


The math element will be presented in another section. It is used to
describe how the calculations are started.


A couple of the workhorse elements here are def which defines a variable
and call which invokes a block of definitions.


## < definitions >


Use this element as a container for the blocks of math used to calculate
the model?s derivatives and intermediate variables.


    <definitions> Blocks of math. </definitions>


## < block >


Use this element to define a named block of math.


    <block>


        <name> Unique block name. </name>


        Many different math elements can go here.


    </block>


A block of math is invoked (or called) using the call element.


## < call >


Use the call element to call or invoke a block of math in definitions.


    <call> Block name goes here. </call>


## < implicitmath >


Use this element to define the math that is used to solve an implicit
algebraic equation.


Here is a brief review, taken from the Equations section of this volume.
An implicit algebraic equation has the form of:


Y = f(Y) 				(1)


This equation is solved using two estimates of Y: the beginning Y (referred
to as YStart here) and the ending Y (referred to as YEnd). Equation (1)
becomes:


YEnd = f(YStart) 			(2)


A solution has been obtained when:


| YEnd - YStart | <= Error Limit 	(3)


where the vertical bars denote absolute value and the error limit is the
largest difference that is acceptable.


When an impliciteq equation element is created, variables representing
YStart and YEnd above are named (declared). The next step,
implementing Equation (2), takes place here.


Use the implicitmath element to create the math that fleshes out Equation
(2). The starting variable, named in the impliciteq declaration, is defined
at the start of the element. The ending variable, also named in the
impliciteq declaration, must be defined by this math by the end of the
element.


Equation (3) above is automatically evaluated at the end of the element.
The element is iterated until an acceptably small error is obtained.


    <implicitmath>


        <name> Implicit equation name. </name>


        The YStart variable is defined here. Now do the math needed to
        define YEnd.


    </implicitmath>


## < beep >


When this element is encountered during the calculation of a solution, it
signals the equation solver that an audio beep is needed.


A beep element is generally only useful in conditional math or when trying
to straighten out tangled logic.


    <beep/>


## < calclag >


A lag equation is like a delay equation. The output variable follows the
input variable by a 1st-order delay that is determined by the rate constant.


But there are differences. A delay equation creates a delay in a model. A
lag equation creates a delay in an algebraic relationship. This means that
a delay equation acts like a modified differential equation while a lag
equation acts like a modified algebraic variable.


The lag equation?s lead variable is the output or delayed variable. It must
be defined in a definitions element just like any other variable. Think of
this as:


Lag Output = k * Lag Input


where k is a magic coefficient that produces a delay.


In definitions, at any point after the lag?s input variable has been defined,
define the lag?s output variable by referring to the lag using the calclag
element and the lag?s name.


    <calclag> Lag name goes here. </calclag>


You?ll get a run time error if the calclag element is invoked before its input
variable is defined.


## < conditional >


Use the conditional element to implement conditional math.


The mathematical expression in test is evaluated. If it evaluates to TRUE,
the expression in true is evaluated and the result is assigned to the named
variable. If it evaluates to FALSE, the expression in false is evaluated and
the result is assigned to the named variable.


    <conditional>


        <name> Variable name. </name>


        <test> Evaluate this expression. </test>


        <true> Exression for TRUE outcome. </true>


        <false> Exression for FALSE outcome. </false>


    </conditional>


The true or false elements are not needed if there is no assignment to
make.


## < copy >


We can use a math block as a multiple input – multiple output funtion. Use
the copy element to copy values into the block, call the block, and use the
copy element a second time to copy values back out of the block.


    <copy>


        <from> Source variable name. </from>


        <to> Destination variable name. </to>


    </copy>


## < def >


Use the def element to define a declared variable that has not yet been
defined. Define means to assign a value or instructions for calculating a
value (a mathematical expression).


    <def>


        <name> Variable name. </name>


        <val> Mathematical expression. </val>


    </def>


Evaluate the mathematical expression and assign the result to the named
variable.


If this was a traditional assignment statement, it would look like this:


Variable name = Mathematical expression


## < exitblock >


When this element is encountered during the calculation of a solution, it
triggers an immediate exit from the block that is being calculated.


An exitblock element can be useful in conditional math that has a rather
complex organization.


    <exitblock/>


## < if >


Use this element to implement conditional math.


The mathematical expression in test is evaluated. If it evaluates to TRUE,
the math in the true element is executed. If it evaluates to FALSE, the
math in the false element is executed.


    <if>


        <test> Evaluate this expression. </test>


        <true> Math for TRUE outcome. </true>


        <false> Math for FALSE outcome. </false>


    </if>


The true or false element is not needed if there is no conditional math for it
to do.


Note that our parser does not support recursion, so nested if elements are
not allowed in this schema. If you need an if element within an if element,
use a andif element for the 2nd if.


## < logevent >


This element asks the equation solver to update storage and refresh the
display between regularly scheduled display updates.


Some values are of interest, but are not displayed because they exist
within a display interval rather than at the end of the interval. This element
can be used to conditionally capture a value that would otherwise be
missed, such as a maximum or minimum when a variable suddenly
changes direction.


The independent variable will be advanced to exactly the value specified
by the named variable and storage and display will be updated at that
time.


If the named variable is the independent variable (System.X) then the
logging takes place immediately.


The logevent element is generally only useful in conditional math.


    <logevent>


        Name of variable specifying logging time (or technically specifying

        logging value of independent variable) goes here.


    </logevent>

Valid in %math.

DTD


    <!ELEMENT logevent (#PCDATA)>


## < message >


Use this element to define a message to be displayed by the equation
solver. A message is meant to be displayed immediately while a page is
meant to be displayed after the completion of a successful integration
interval.


A message is generally only useful in conditional math.


    <message> Message text here. </message>


The message element is sometimes useful to the model builder when the
model?s logic is not clear (i.e. use it for debugging).


## < onjustchanged >


Sometimes a parameter feeds some dependent variables that should be
recalculated when the parameter is assigned a new value. But the
dependent variables should not be recalculated otherwise. Use this
element to implement such a scenario.


    <onjustchanged>


        <name> Parameter name goes here. </name>


        Math goes here. Math will be executed if the named parameter has
        just been assigned a new value.


    </onjustchanged>


## < ontimedout >


Sometimes we set a timer variable and then want to take some action
when the timer variable times out (i.e. counts up or down to zero). The
action is typically turning on or off some regimen.


Use the ontimedout element to implement such a scheme.


    <ontimedout>


        <name> Timer variable name. </name>


        Math goes here. Math will be executed if the named timer variable
        has just timed out (counted up or down to zero).


    </ontimedout>


Note that timer variables can only time out in wrapup code – where time is
known with certainly.


## < page >


Use this element to define a message to be displayed by the equation
solver. A page is meant to be displayed after the completion of a
successful integration interval while a message is meant to be displayed
immediately.


A page is generally only useful in conditional math.


    <page> Pager message. </page>


Pages are queued, so multiple pages can appear at the end of a
successful integration interval.


HUMMOD uses pages extensively to report unexpected events.


## < stop >


When this element is encountered during the calculation of a solution, it
signals the equation solver that the solution should be stopped.


A stop element is usually only useful in conditional math.


    <stop/>


## < testcase >


Use the testcase element as a container for an arbitrary number of case
elements.


The test expression in each case is evaluated until a TRUE value is
obtained. Then the math elements following the test element are
executed and testcase is exited.


Note that this logic means that only one or none cases will be executed
per iteration.


    <testcase>


        <case>


            <test> Evaluate this expression. </test>


            If the expression evaluates to TRUE, do this math.


        </case>


        More cases go here.


    </testcase>


Sometimes we want the final case to be executed if none of the other
cases are executed (i.e. execute the default case). To implement this,
simply make the test expression TRUE.


    <test> TRUE </test>


## < timer >


Use this element to change the value and state of a timervar. This
element is designed for use in conditional math, supplying the appropriate
response when a pump, treadmill or something similar is turned on or off.


    <timer>


        <name> Timer variable name. </name>


        <val> New value via expression. </val>


        <state> New state. </state>


    </timer>


Valid states are UP, DOWN and OFF.


If the value or state is not being changed, the appropriate element can be
omitted.