---
layout: default
title: Miscellaneous
---

#Miscellaneous


##Overview


This section describes elements that are not part of interactive control or scripted control. Thus, they are miscellaneous.


misc
   
    |

    |-initialx

    |-scramble


Elements include, prefixpath, datecreated and datelastaltered may also be
used in structure when appropriate. See Volume 1. Model, Top-Level
Elements.


## < misc >


Use this element as a container element for miscellaneous control
elements.


    <misc>


        Miscellaneous control elements go here.


    </misc>


    Valid in < control >


See also: 


    * < interactive>


    * < scripted >


DTD 


Some elements in misc may be defined only once.


    <!ELEMENT misc


    (( #PCDATA,


    initialx?,


    #PCDATA,


    scramble?,


    #PCDATA


    )


    |


    ( #PCDATA,


    scramble?,


    #PCDATA,


    initialx?,


    #PCDATA


    ))


    >


## < intialx >


Use this element to define the initial value of the equation solver?s
independent variable, called System.X, usually representing time. The
default, and most common, value is 0.


    <initialx>


        Initial value of X goes here.


    </initialx>


    Valid in < misc >


DTD


    <!ELEMENT initialx (#PCDATA)>


## < scramble >


The random number generator is always seeded the same way. Thus, it
generates a random, but predictable, sequence during repeat solutions.


Use this element to switch to a random seed. The random number
generator will generate a truly random sequence during each solution.


    <scramble/>


    Valid in < misc >


See also:


    * < whitenoise >


    * < normaldist >


in Volume 2. Structure...Variables


DTD


    <!ELEMENT scramble EMPTY>