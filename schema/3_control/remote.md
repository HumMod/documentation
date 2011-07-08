---
layout: default
title: Remote
---

#Remote


##Overview


This section defines the elements that implement remote requests for
processing submitted scripts.


The highest-level remote control element is named remote. It is a
container element for the remote control children.


remote

    |

    |-openlistener

    |-closelistener

    |-changewindow

    |-logfile

    |-closesolver


A listener periodically looks for the existence of a specific file. When the listener finds the file, it processes the file.


A remote user may establish its own listener, with appropriate filename
and listening interval.


To start (bootstrap) the process, we must first open basic listener that listens for a standard filename.


I arbitrarily recommend a basic listener named BasicListener that listens for a file name BasicListener.DAT at an interval of 5 seconds.


A listener does not parse the entire model XML schema. Instead, it
parses three out the four child elements in control.


A new document element, named remoterequest, is used in this remote
request schema.


remoterequest

		|

		|-scripted

		|-remote

		|-misc


A remote request, then, is primarily a script.


## < remote >


Use this element as a container element for all of the remote control
elements.


    <remote>


        Remote control elements go here.


    </remote>


    Valid in < control >


See also


    * < interactive >


    * < scripted >


    * < misc >


DTD The elements in remote may be defined in any order and amount.


    <!ELEMENT remote


      ( openlistener


      | closelistener


      | changewindow


      | logfile


      | closesolver


      )*


    >


## < openlistener >


Use this element to open a listener.


A listener periodically (once each interval) checks for the existence of a specific (target) file. When the listener finds the file, it processes the file.


    <openlistener>


        <name>


            Listener?s name goes here.


        </name>


        <filename>


            Target filename goes here.


        </filename>


        <interval>


             Listening interval (seconds) goes here.


        </interval>


    </openlistener>


We refer to the listener?s name when closing the listener.
Valid in remote.


DTD


    <!ELEMENT openlistener (name, filename, interval)>


    <!ELEMENT name (#PCDATA)>


    <!ELEMENT filename (#PCDATA)>


    <!ELEMENT interval (#PCDATA)>


## < closelistener >


Use this element to close down a listener.


Listeners consume resources. If you are done using a listener, close it
down.


    <closelistener>


        Listener name goes here.


    </closelistener>


Valid in remote.


DTD


    <!ELEMENT closelistener (#PCDATA)>


## < logfile >


Use this element request a log file. A log file is used to log the progress
made when a script is processed.


The file is created when the processing is completed.


The presence of this file tells a remote user that the script has been
processed and the script output file is now ready for parsing.


The content of this file indicates success or failed and it shows the errors,
if any, that were logged.


See Volume 5. Misc, File Formats for the file format.


    <logfile>


        Log file name goes here.


    </logfile>


Valid in remote.


DTD


    <!ELEMENT logfile (#PCDATA)>


## < closesolver >


Use this element to close down the equation solver.
If a remote user launched the equation solver and is
now done using it, this is the proper way to shut it
down.


    <closesolver>


Valid in remote.


DTD


    <!ELEMENT closesolver EMPTY>


## < changewindow >


Use this element to change the state of the equation solver?s main
window.


    <changewindow>


       Window action goes here.


    </changewindow>


Possible actions are HIDE, SHOW, MINIMIZE and RESTORE.


Valid in remote.


DTD


    <!ELEMENT changewindow (#PCDATA)>