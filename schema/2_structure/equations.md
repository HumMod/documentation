---
layout: default
title: Equations
---

#Equations


##Overview


The equations element is used to declare the model?s differential and
implicit algebraic equations.


Equations are used to develop a relationship around several variables.
For instance, in differential equations (diffeq, backwardeuler and
stablediffeq) the declaration names the integral and its derivative. The
integral knows how to determine its own value by tracking values of its
derivative.


In implicit algebraic equations (impliciteq) the declaration names the
starting variable and ending variable. The implicit equation knows to
declare a solution when the starting and ending values are nearly the
same.


Automatic Declaration:

When a variable is named in an equation?s declaration, it is automatically
declared as a var variable. The variable does not require additional
declaration in a variables element.


In addition, some variables are automatically both declared and defined.
I?ll try to provide details in the individual equation descriptions that follow.


Calculation Sequence:

Defined variables have an important role in defining other variables, since
a variable cannot participate in a definition until it is itself defined.
See Math, Overview later in this volume for additional discussion of
calculation sequence


## < equations >

Use this element to declare the model?s differential and implicit algebraic
equations.


    <equations> Equation declarations. </equations>


Declaration and partial definition takes place here. Definition is completed
in definitions elements where derivatives and implicit equation values are
calculated.


Several different equation types are currently supported.


Differential Equations:

    <diffeq>

    <stablediffeq>

    <backwardeuler>


Time Delays:

    <delay>

    <stabledelay>

    <lag>


Implicit Algebraic Equations:

    <impliciteq>


## < diffeq >


The general form of a differential equation needing solution is:


dY/dX = f(Y) 			(1)


where Y is the dependent variable, X is the independent variable, and f()
is a functional relationship that is known. The initial value of Y is also
known.


Differential equation (1) implies integral equation (2), which is the equation
that is actually solved.


Y = int((dY/dX)) dX 		(2)


Use the diffeq element to declare and define Y and the integral in
Equation (2).


    <diffeq>


        <name> Equation name. </name>


        <integralname> Integral name. </integralname>


        <initialval> Integral?s initial value. </initialval>


        <dervname> Derivative name. </dervname>


        <errorlim> Integration error limit. </errorlim>


    </diffeq>


The equation name must be a unique name. Currently this name is used
for absolutely nothing, but it may be put to use in the future.


The integral and its derivative are model variables. Thus, they must have
a unique name in the variable space.


The integral?s initial value and integration error limit are floating point.
The integration error limit specification determines the accuracy of the
numerical integration. I typically use an integration error limit of 1% of the
integral?s initial value. This is arbitrary.


If the integration error limit is not specified, integration error is not controlled for this differential equation.


Two additional steps are needed to solve a differential equation:


* The derivative must be defined in a math block. This is essentially
an implementation of Equation (1).


* The derivative?s math block must be called at the correct point in
the calculation sequence.


These steps create a complete solution to Equations (1) and (2).


## < backwardeuler >


A backward Euler integral is more stable than the standard 1st-order Euler integral.


Normally, the diffeq element is used to declare a differential equation. A useful alternative is available, however, that is fast and stable (but generally doesn?t conserve mass). It can be used when the derivative has the form:


dY/dt = f1 - f2 * Y 		(1)


and


Y = int((dY/dX)) dX 		(2)


Use the backwardeuler element to declare a differential equation. The
underlying numerical method is a partially implicit 1st order Euler algorithm,
commonly known as a backward Euler algorithm.


Basically, what we are doing here is replacing the derivative variable with variables representing f1 and f2 in Equation (1) above.


    <backwardeuler>


        <name> Equation name. </name>


        <integralname> Integral name. </integralname>


        <initialval> Integral?s initial value. </initialval>


        <f1name> f1 name. </f1name>


        <f2name> f2 name. </f2name>


        <dervname> Derivative name. </dervname>


        <errorlim> Integration error limit. </errorlim>


    </backwardeuler>


Again, the equation name must be a unique name.


The integral, f1, f2 and the derivative are model variables. Thus, they all
must have unique names in the variable space.


The dervname element is optional. It is used for display only. The f1 and
f2 elements do the work.


If the integration error limit is not specified, integration error is not
controlled for this differential equation.


## < stabledelay >


A stable delay is a combination of a stable differential equation and a
delay.


I won?t repeat the details here. See stablediffeq and delay.


The stabledelay element is a delay element with maximum step size also
specified.


    <stabledelay>


        <name> Equation name. </name>


        <outputname> Output name. </outputname>


        <initialval> Output?s initial value. </initialval>


        <inputname> Input name. </inputname>


        <rateconstname> K. </rateconstname>


        <dervname> Derivative name. </dervname>


        <errorlim> Integration error limit. </errorlim>


        <dxmaxname> Max step size. </dxmaxname>


    </stabledelay>


Again, the equation name must be a unique name.


The output, input, rate constant, derivative and maximum step size are
model variables. Thus, they all must have unique names in the variable
space.


Rate constants of 0 (Tau = ) and INFINITY (Tau = 0) are supported.
The dervname element is optional. It is used for display only.



## < stablediffeq >


A stable differential equation is basically a differential equation with one
added feature.


The stable differential equation is used with stiff systems.


If we have physical or observational evidence that an equation will
become unstable at larger step sizes, we pass this information to the
stable differential equation; it will then attempt to take care of stability.


    <stablediffeq>


        <name> Equation name. </name>


        <integralname> Integral name. </integralname>


        <initialval> Integral?s initial value. </initialval>


        <dervname> Derivative name. </dervname>


        <errorlim> Integration error limit. </errorlim>


        <dxmaxname> Max step size. </dxmaxname>


    </stablediffeq>


The equation name must be a unique name. Currently this name is used
for absolutely nothing, but it may be put to use in the future.


The integral, its derivative and maximum step size are model variables.
Thus, they must have a unique name in the variable space.


The integral?s initial value and integration error limit are floating point.
The integration error limit specification determines the accuracy of the
numerical integration. I typically use an integration error limit of 1% of the
integral?s initial value. This is arbitrary.


If the integration error limit is not specified, integration error is not
controlled for this differential equation.


## < delay >


The output of a delay slowly follows its input as illustrated in the figure
below.


![I/O Curve](https://github.com/HumMod/documentation/raw/gh-pages/images/schema/input_output_p55.jpg)


The most common delay is called 1st-order. It is implemented with a
differential equation as shown in Equations (1) and (2) and the block
diagram below.


Output = (dOutput/dX) * dX 			(1)


dOutput/dX = K * (Input – Output) 		(2)


![I/O Diagram](https://github.com/HumMod/documentation/raw/gh-pages/images/schema/io_block_p55.jpg)


The rapidity of the output?s response is determined by the rate constant,
which is denoted above by K.


If time is the independent variable, a delay is called a time delay.
Use the delay element to create a delay.


    <delay>


        <name> Equation name. </name>


        <outputname> Output name. </outputname>


        <initialval> Output?s initial value. </initialval>


        <inputname> Input name. </inputname>


        <rateconstname> K. </rateconstname>


        <dervname> Derivative name. </dervname>


        <errorlim> Integration error limit. </errorlim>


    </delay>


Again, the equation name must be a unique name.


The output, input, rate constant and derivative are model variables. Thus,
they all must have unique names in the variable space.


Rate constants of 0 (Tau = ) and INFINITY (Tau = 0) are supported.
The dervname element is optional. It is used for display only.


If the integration error limit is not specified, integration error is not
controlled for this differential equation.


## < lag >


Use this element to create a lag. Like a delay, the output variable follows
the input variable by a 1st-order delay that is determined by the rate
constant.


But there is a difference here. A lag output variable must be referred to in
a math block to define it. The reference must be at a place where the
input variable is defined and the output variable is needed. The calclag
element in definitions is used to create the proper reference.


    <lag>


        <name> Equation name. </name>


        <outputname> Output name. </outputname>


        <initialval> Output?s initial value. </initialval>


        <inputname> Input name. </inputname>


       <rateconstname> K. </rateconstname>


       <dervname> Derivative name. </dervname>


    </lag>


Again, the equation name must be a unique name.


The output, input, rate constant and derivative are model variables. Thus,
they all must have unique names in the variable space.


Rate constants of 0 (Tau = inf) and INFINITY (Tau = 0) are supported.


The dervname element is optional. It is used for display only.


There is no integration error limit.


This is a rather weird numerical method, but it can be very useful in
introducing a little delay into a response. I think that it can be shown that a
lag becomes more stable as step size increases – but this is a topic for
elsewhere.


## < impliciteq >


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


Use this element to declare an implicit algebraic relationship. The lead
variable is YStart in Equation (2).


    <impliciteq>


        <name> Equation name. </name>


        <startname> Start name. </startname>


        <initialval> Start?s initial value. </initialval>


        <endname> End name. </endname>


        <errorlim> Solution error limit. </errorlim>


        <searchminname> Min name. </searchminname>


        <searchmin> Min value. </searchmin>


        <searchmaxname> Max name. </searchmaxname>


        <searchmax> Max value. </searchmax>


    </impliciteq>


We can improve search efficiency by constraining the search. Constraint
also allows us to get the correct root when more that one root exists. If the
minimum and/or maximum limits are not specified, the search is not
constrained in the respective direction.


We can limit the minimum value of the search space in any of three ways:


* Name a variable whose value limits the search space.

* Specify a floating point value that limits the search space.

* Specify nothing and get no constraint.


The maximum value of the search space can be limited in the same way.


Two additional steps are needed to fully solve an implicit algebraic
equation:


* The relationship between the start variable (YStart) and end
variable (YEnd) must be fleshed out in an implicit math block. The
start variable is assumed to be defined at the start of the block and
the end variable must be defined by the end of the block. This is an
implementation of Equation (2) above.


* The implicit math block must be called at the correct point in the
calculation sequence.


