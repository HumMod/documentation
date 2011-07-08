---
layout: default
title: Volume 3 - Control
---

#Volume 3 - Control

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


##Contents


[Control](control.md)


[Interactive](interactive.md)


[Miscellaneous](misc.md)


[Remote](remote.md)


[Scripted](scripted.md)