---
layout:default
title: Additional Grammar
---

#Additional Grammar

##Mathematical Expressions

A mathematical expression is a set of instructions that
is used to calculate a single numerical value. This value is then used in def, if and other elements.


The goal is to have documents that can be directly parsed into an
equation solver, HTML, a database or document translation tools.
Whitespace characters are space, tab and the character created by
pressing the Enter key.


Tokens are sequences of visible characters that represent single entities within a mathematical expression. These entities can be variable names, curve names, numbers (literal numbers), mathematical operators, and punctuation.


All tokens in a mathematical expression must be separated by
whitespace. N.B. This is an important rule. It allows us to implement a fast and efficient expression parser.


Variable And Curve Names:

Rules for variable and curve names are described in the Names chapter.


The Order Of Calculation:

Calculations inside of parentheses are completed before calculations
outside of parentheses. Parentheses may be nested; calculations inside
inner parentheses are completed before calculations inside outer
parentheses.


Otherwise, calculations proceed from left to right.


There is no operator precedence. That is, the order of calculation is not
affected by the presence or absence of a particular mathematical
operator.


The expression 2 * 5 + 4 * 5 will evaluate to 70 while the expression ( 2 * 5
) + ( 4 * 5 ) will evaluate to 30.


When in doubt, use parentheses.


Operators:

Unary operators operate on a single following value. Binary operators
operate on 2 values, one preceding and one following.


Mathematical operators return a decimal number. Logical operators return
TRUE (1) or FALSE (0).


The names of operators are case sensitive. All operators are named
using all uppercase letters.


Unary Operators:

Unary mathematical operators are:


- 			-1.0 Multiplied By


INVERT 		1.0 Divided By


EXP 			Exponential Function


LOG 			Natural Logarithm


LOG10 		Logarithm Base 10


SQRT 			Square Root


SIN 			Sine


COS 			Cosine


TAN 			Tangent


ABS 			Absolute Value


ARCSIN 		Arc Sine


ARCCOS 		Arc Cosine


ARCTAN 		Arc Tangent


SINDEG 		Sine Degrees


COSDEG 		Cosine Degrees


TANDEG 		Tangent Degrees


RADTODEG 		Radians To Degrees


DEGTORAD 		Degrees To Radians


ROUND 		Round Off


ROUNDUP 		Round Up


ROUNDDOWN 		Round Down


FRACTPART 		Fractional Part


The argument for traditional trig operators is radians.


Unary logical operators are:


NOT	 		Logical Not


Binary Operators:

Binary mathematical operators are:


+ 			Addition


- 			Subtraction


* 			Multiplication


/ 			Division


^ 			Raise To The Power


MIN 			Return Minimum Of


MAX 			Return Maximum Of


ATAN2 		Arc Tangent (X, Y) With Horz


REM 			Remainder


ROUNDAT 		Round At < Or > Than 1


Binary logical operators are:


AND 			Logical And


OR 			Logical Or


EQ 			Equal To


NE 			Not Equal To


GT 			Greater Than


GE 			Greater Than Or Equal To


LT 			Less Than


LE 			Less Than Or Equal To


Pi:

And we have one literal : PI (3.14159 …).


Functions:

Functions are defined in the functions element. The only function just now is "curve".


Functions are invoked by name followed by an argument name, with the
name enclosed in square brackets. For example:


Frank-Starling [ RAP ]:

describes a function named Frank-Starling operating on a variable named
RAP. Note the requisite spaces separating all four tokens.


##Internal Variables


The equation solver will recognize and provide the correct values for the following variables. The names are treated as if they were created in the structure "System".


System.X:

The model?s independent variable, usually thought of as time.


System.Dx: 

Numerical integration?s integration interval. Actually used in
the calculations.


System.DefaultDx: 

Numerical integration?s integration interval. Used in
calculation if there is no truncation.


System.Random:

A random number between -1 and 1. The equation solver should generate a new random value at the beginning of each integration interval.


System.Normal: 

A random number from a normal distribution having a mean of 0 and a standard deviation of 1. The equation solver should generate a new random, normally distributed value at the beginning of each integration interval.


System.Pi: 

This variable holds the value of pi – 3.14 …
For more on system random numbers, see Volume 4. Control < scramble
>.


System.Starting: 

This variable is TRUE only once – when the equation
solver is starting. Otherwise, it is FALSE. 


The following intervals are for display only. Do not mess with them:


System.SolutionInterval


System.DisplayInterval


System.StorageInterval: Currently not implemented.


##Special Numbers

The equation solver can recognize the following special numbers, in
addition to recognizing integer and decimal numbers and scientific
notation:


TRUE: 

This is a synonym for 1. It is the value that is returned when an
expression evaluates to true. This number should be displayed as TRUE.


FALSE: 

This is a synonym for 0. It is the value that is returned when an
expression evaluates to false. This number should be displayed as
FALSE.


INFINITE: 

OK for use in logical expressions, but avoid using in
mathematical expressions. This number is the result of a divide by 0. This number should be displayed as INFINITE.


UNDEFINED: 

OK for use in logical expressions, but avoid using in
mathematical expressions. This number should be displayed as
UNDEFINED.


UNKNOWN: 

OK for use in logical expressions, but avoid using in
mathematical expressions. This number should be displayed as
UNKNOWN.


BLANK: 

OK for use in logical expressions, but avoid using in mathematical
expressions. This number should be displayed as _____ (5 underline
characters).


The advice to not use some of these numbers in mathematical
expressions follows from the fact that they are very big numbers that may just trigger math processor exceptions.


##Names


In this model description schema, many of the model?s parts are named.
This makes the specification and manipulation of names an important
undertaking.


Model parts with names include variables, equations, curves, blocks of
math, symbols, lists and panels.


The names involved in model structure (variables, equations, curves and
blocks of math) are created within the structure element, and each
structure element has a name. This fact is used to advantage.


Each name has two forms: local and global.


The local name is used to refer to a model part from within the structure where the name was created. As an example, in the structure "Exercise", we have a variable named "ElapsedTime".


The global name is used to refer to a model part from outside the structure where the name was created. A global name is formed by prefixing a structure name to a local name. A dot or period (.) is used as a separator between the structure and local names.


Thus exercise elapsed time is referred to as "ElapsedTime" within the
structure named Exercise and is referred to as "Exercise.ElapsedTime"
everywhere else in the XML document.


Leading and trailing spaces in names are not significant and should be
stripped by the XML parser.


Interior whitespace is not allowed in names that can appear in
mathematical expressions. Currently, these are the names of structures
(as part of global names), variables and curves. Notice that the example developed above does not contain interior whitespace.


Some characters are not allowed in names:


* XML special characters (see Special Characters, Introducing XML).


* Any dots or periods in addition to the global name separator dot.


* Additional characters may be restricted in the future.