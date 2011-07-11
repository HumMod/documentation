---
layout: default
title: Interactive
---

#Interactive


##Overview


This section defines elements that are used to control the solution through
the user?s interactive choices.


These elements help to populate a popdown menu (the Go menu) that
gives the user a choice of solution intervals.


The highest-level interactive control element is named interactive. It is a
container element for the interactive control children.


interactive

	  |

	  |-gobar

	  |-gofor

	  |-goto


The processing instructions include, prefixpath, and strict may also be
used in interactive where appropriate. See Volume 1. Model, Processing
Instructions.


## < gobar >


Use this element to add a separator bar to the
Go popdown menu, shown below.


   <gobar/>


![Go Bar](https://github.com/HumMod/documentation/raw/gh-pages/images/schema/go_bar_p100.jpg)


    Valid in < interactive >


See also:


    * < gofor >


    * < goto >


DTD


    <!ELEMENT gobar EMPTY>


## < goto >


See this volume?s Overview for a description of
intervals.


Use this element to create a Go menu item that can
be used to advance the solution. A Go menu is
shown below. Note the bottom four menu items.


Specify the solution, display and storage intervals and
define a menu item for the Go popdown menu.


This is a little tricky, but it works great in tidying up the
progress of a solution. A solution interval is specified,
but the solution doesn?t go the full interval. Instead, it
goes until the independent variable (System.X) has increased to the next
multiple of the specified solution interval.


Thus, this is a modified gofor element.


    <goto>


        <solutionint>


            Solution interval goes here.


        </solutionint>


        <displayint>


            Display interval goes here.


        </displayint>


        <storageint>


            Storaage interval goes here.


        </storageint>


        <menuitem>


            Go menu item goes here.


        </menuitem>


    </gofor>


As an example, suppose the independent variable has a current value of
2000. The Go menu has a goto menu item with a solution interval of 1440
(and maybe a label of To Next Day). When user clicks this choice, the
solution will be advanced to the next multiple of 1440, which is 2880, for a
net advance of 880.


    Valid in < interactive >


See also:


    * < gofor >


    * < gobar >

DTD


    <!ELEMENT gofor


    ( solutionint,


    displayint?,


    storageint?,


    menuitem?


    )


    >


    <!ELEMENT solutionint (#PCDATA)>


    <!ELEMENT displayint (#PCDATA)>


    <!ELEMENT storageint (#PCDATA)>


    <!ELEMENT menuitem (#PCDATA)>


The default displayint is solutionint / 10. The default storageint is
displayint. The default menuitem is an image of the solutionint.


## < gofor >


See this volume?s Overview for a description of
intervals.


Use this element to create a Go menu item that can be
used to advance the solution. A Go menu is shown at
right.


Specify the solution, display and storage intervals and
define a menu item for the Go popdown menu.


    <gofor>


        <solutionint>


             Solution interval goes here.


        </solutionint>


        <displayint>


             Display interval goes here.


        </displayint>


        <storageint>


            Storage interval goes here.


        </storageint>


        <menuitem>


            Go menu item goes here.


        </menuitem>


    </gofor>


    Valid in < interactive >


See also:


    * < goto >


    * < gobar >


DTD


    <!ELEMENT gofor


    ( solutionint,


    displayint?,


    storageint?,


    menuitem?


    )


    >


    <!ELEMENT solutionint (#PCDATA)>


    <!ELEMENT displayint (#PCDATA)>


    <!ELEMENT storageint (#PCDATA)>


    <!ELEMENT menuitem (#PCDATA)>


The default displayint is solutionint / 10. The default storageint is
displayint. The default menuitem is an image of the solutionint.


## < interactive >


Use this element as a container element for the interactive control
elements.


    <interactive>


        Interactive control elements go here.


    </interactive>


    Valid in < control >


See also: 


    * < scripted >


    * < remote >


    * < misc >


DTD

 The elements in interactive may be defined in any amount but order
is significant. Order determines the order of menu items in the Go
popdown menu.


    <!ELEMENT interactive


        ( gobar


        | gofor


        | goto


    )*


    >