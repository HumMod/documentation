---
layout: default
title: Control
---

#Control


##Overview


Volume 3. Control describes elements that are used to control a solution.


Several forms of control will eventually be implemented, including scripted
control and remote control. But in this part of the schema, we are referring
only to interactive control – which is the normal way that users control
HUMMOD 2008 solutions.


The top-level control element is named control. It is a container element
for child elements that, for the most part, populate the Go pop-down
menu.


Intervals:

A solution is all of the calculated values that accumulate as the model?s
independent variable is advanced.


A solution is defined by five interrelated intervals.


The cumulative interval is the advance in the independent variable
(usually time) from start to finish. More specifically, the cumulative interval
is the sum of all solution intervals. Cumulative intervals are generally
determined by the user?s interactive choices.


The solution interval is the advance in the independent variable from a
pause in the calculation to the next pause in the calculation. Solution
intervals are selected by the user from choices presented on the Go
menu. As noted above, solution intervals are strung together end to end
to create the cumulative interval. It follows that the solution interval is less
than or equal to the cumulative interval.


The display interval is the advance in the independent variable between
display updates. The display interval determines the frequency of screen
refreshes. The display interval is less than or equal to the solution
interval.


The storage interval is the advance in the independent variable between
storage updates. The storage interval determines the granularity of the
displayed solution. The storage interval is less than or equal to the display
interval. It the current implementation we don?t use a storage interval;
instead, we store all solution values.


The integration interval is the advance in the independent variable used in
numerical integration. The integration interval is determined by the
equation solver and is less than or equal to the storage interval. The size
of the integration interval is determined by the equation solver?s estimate
of the numerical integration error.


The integration interval is the advance in the independent variable used in
numerical integration. The integration interval is determined by the
equation solver and is less than or equal to the storage interval. The size
of the integration interval is determined by the equation solver?s estimate
of the numerical integration error.


## < control >


Use this element as a container element for solution control elements.
The control element is valid only as a child of the model element.


    <control>


        Child control elements go here.


        The main control elements are gofor, goto and gobar.


        Miscellaneous control elements are initialx, scramble and
        settlingtime.


    </control>


## < gobar >


Use this element to add a
separator bar to the Go popdown
menu, as illustrated below.


    <gobar/>


The separator bars in Vista are
very faint – acting almost as a
space. The visual at right is from
an older version of Windows.


A separator bar (using a different
element name) can also be added
to panel pop-down menus.

![Go Bar](https://github.com/HumMod/documentation/raw/gh-pages/images/schema/go_bar_p100.jpg)


## < gofor >


Use this element to create a Go menu item that
can be used to advance the solution. A Go
menu is shown below.


![Go For](https://github.com/HumMod/documentation/raw/gh-pages/images/schema/go_bar_p100.jpg)


Specify the solution and display intervals and
define a menu item for the Go popdown menu.
Intervals are specified in floating point.


Some typical menu items are shown above.


There are default values. The default displayint is solutionint / 10. The default menuitem is an image of the solutionint.


    <gofor>


        <solutionint> Solution interval. </solutionint>


        <displayint> Display interval. </displayint>


        <menuitem> Go menu item. </menuitem>


    </gofor>


We have also had a storage interval. But right now all of the numerical
values in a solution are stored, so the storage interval specification is not
implemented.


## < goto >


The goto element is very similar to the gofor
element, with one exception as explained below.


Use this element to create a Go menu item that
can be used to advance the solution. A Go
menu is shown below. The bottom four menu
items were generated using the goto element.


![Go To](https://github.com/HumMod/documentation/raw/gh-pages/images/schema/go_bar_p100.jpg)


Specify the solution and display intervals and
define a menu item for the Go popdown menu.


Intervals are specified in floating point.


There are default values. The default displayint is solutionint / 10. The
default menuitem is an image of the solutionint.


This is a little tricky, but it works great in tidying up the progress of a
solution. A solution interval is specified, but the solution doesn?t
necessarily go the full interval. Instead, it goes until the independent
variable (System.X) has increased to the next multiple of the specified
solution interval.


Thus, this is a modified gofor element.


    <goto>


        <solutionint> Solution interval. </solutionint>


        <displayint> Display interval. </displayint>


        <menuitem> Go menu item. </menuitem>


    </goto>


As an example, suppose the independent variable has a current value of
2000. The Go menu has a go to menu item with a solution interval of
1440 (and maybe a label of To Next Day). When user clicks this choice,
the solution will be advanced to the next multiple of 1440, which is 2880,
for a net advance of 880.


## < initialx >


Use this element to define the initial value of the equation solver's
independent variable, called System.X, usually representing time. The
default, and most common, value is 0.


    <initialx> Initial value of X goes here. </initialx>


The value is floating point.


## < scramble >


The random number generator is always seeded the same way. Thus, it
generates a random, but predictable, sequence during repeat solutions.


Use this (empty) element to switch to a truly random seed. The random
number generator will generate a new random sequence for each solution.


    <scramble/>


## < settlingtime >


There are two ways to start HUMMOD.


* Start with the specified initial conditions. This occurs when settling
time is not specified.


* Start with the specified initial conditions and advance the solution a
little bit to get a better estimate of steady-state. The values at the
end of this settling time are subsequently (and automatically) used
as the initial conditions. The settling time in minutes (floating point)
is specified using the following element.


    <settlingtime> Settling time here. </settlingtime>


I?ve been using 200 minutes as a settling time, but this is completely
arbitrary.