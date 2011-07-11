---
layout: default
title: Hummod Quickstart Guide
---

#HumMod User's Manual, Version 1.2.1

#Contents:


[Installation]

[Introduction]

[Commands]

[Panel Display Overview]

[Basic Operation]

[Sample Execution]


#Installation

HumMod is available for download from our website, which can be found at
http://www.hummod.org. The model and related files are available as a zip folder. To install HumMod, simply download the folder and unzip it to the directory of your choice. HumMod can then be opened by running the executable file HumMod.exe.


#Introduction


HumMod is an integrated computer model of human physiology which allows the accurate simulation of the effects a person’s changing environment can have on their physiology. It is developed and maintained by the University of Mississippi Medical Center, and is the successor to the QCP (Quantitative Circulatory Physiology) program.

HumMod allows you to create disturbances in the environment and physiology of a virtual person and to track the effects these changes have over time, and to track the effects of these disturbances. Disturbances can be environmental (i.e. the atmospheric pressure surrounding them), related to normal physiology (i.e. the amount and intensity of physical exercise the patient is undergoing),
or related to pathophysiology (i.e. the patient has diabetes mellitus).

HumMod also allows you to control the person’s daily schedule, such as when they eat, when they exercise, when they work, and when they sleep.


This quickstart guide will address the basic premise of the program,describe the various commands the program has available, and contains several sample executions. This guide is most useful to users that are unfamiliar with concepts of computer simulation or have not operated HumMod or its predecessor, QCP, before (though QCP users may benefit from reading the information regarding the user interface, as it has changed significantly).


#Commands

When HumMod is first open, it will be set to display the “Chart” results under the “Clinic” dropdown menu by default. The patient will also have the default characteristics of a 5’10”, 159 lb, 37-year-old man, existing in an uninteresting room temperature environment and following a fairly normal daily schedule.


The most basic command in HumMod is the “Go” dropdown menu. Since
solutions in HumMod are calculated as a function of time, time must be advanced in order to achieve results.

![Advancing Time](https://github.com/HumMod/documentation/raw/gh-pages/images/hummod_quickstart/advancing_time.jpg)


Advancing a patient under the default conditions for any period of time will yield
predictable benchmark results.


The “Stop” command can be used to pause the advancement of the simulation at any time if the user desires to examine a specific point or to change something before the simulation reaches its originally scheduled duration.


The third command is “Restart”—this command immediately erases all data and
sends the program back to its default parameters. The Restart command should be viewed with absolutely no less awe and respect than the act of physically shaking an Etch-a-Sketch. If you hit it, and you did not mean to, tough cookies, your work is gone. So be careful.


##Saving and Loading

There are two types of files that can be saved and loaded. The first is initial
conditions, and the second is results. The initial condition refers to the physiological and environmental constraints that have been placed on a person before any time is actually advanced. Initial conditions files can be loaded or saved using the .ics file extension. Likewise, you can save the data that contains the solutions to the situations you create, as a .sol file. 


##Options Window

![Reset/Restart](https://github.com/HumMod/documentation/raw/gh-pages/images/hummod_quickstart/options_reset_restart.jpg)

The options window contains a couple of different subsets. The first tab is
“Reset/Restart.” There are two buttons under this category. Picking the first option will duplicate the action of the “Restart” button and clear all data while returning values to their default settings. Clicking the second button will reset the solution to time zero and initial conditions but keep environmental and physiological factors at the values they have been changed to.


![Notes](https://github.com/HumMod/documentation/raw/gh-pages/images/hummod_quickstart/options_notes.jpg)

The second tab under options allows for the notes section that occupies part of the “Chart” display (the default display) to be edited. Additional notes can be added or erased as desired.


![Saving IC's](https://github.com/HumMod/documentation/raw/gh-pages/images/hummod_quickstart/options_ics.jpg)

The third set of options allows you to decide whether saving initial conditions will record the IC file's starting time as the current time or whether the initial conditions file will be started from time zero.


![Arrows](https://github.com/HumMod/documentation/raw/gh-pages/images/hummod_quickstart/options_arrows.jpg)

The fourth set of options allows you to set how many display panels the forward and back arrows will remember, up to a possible maximum of 10 choices.


![Log](https://github.com/HumMod/documentation/raw/gh-pages/images/hummod_quickstart/options_log.jpg)

The final operation in the options window allows you to create a real-time log of the information recorded by the program. You can either append an old log file or make a new one at the destination which you specify. The bottom box allows you to toggle the log on or off, and also allows you to set the log to end after a certain number of steps.


##Help

The help tab is used to access the program’s version information and developer
contact information.


##Forward/Back Arrows

The forward and back arrows act much in the same manner as they would in a web browser. They control movement through HumMod's myriad display panels. For example, if you switch from the "Chart" display to the "Daily Planner" display, and then once more to the "Air Supply" panel, pressing the back arrow twice would return the display to "Chart." Pressing the forward arrow twice would then return you to the "Air Supply" display.


#Panel Display Overview

The dropdown lists on the second row control what screen is currently being displayed by HumMod. The default is “Chart,” a basic physiological overlay accessed through the “Clinic” menu.


The first tab is “Physiology.” Physiology focuses on physiological values and conditions like the concentration of electrolytes in the body, hormone levels, and the overall activity level of several organ systems such as the circulatory system.


The second tab is “Organs.” Organs contains in-depth information regarding the
structural values of specific organs, including size, tissue damage, and fuel consumption, among other things.


The third tab is “Lifestyle.” Lifestyle controls the environment of the model, from clothing to exercise to the actual environment surrounding the person.


The fourth tab is “Clinic.” Clinic contains displays that are medical in nature, allowing for the patient to be treated with different drugs and anesthesia, as well as allowing for the activation of certain afflictions such as hemorrhage.


The fifth tab is “Context.” Context shows basic information about the patient such as their gender, body size, and age.


The sixth tab is “Startup.” Startup displays the original values of physiological variables used by HumMod, and also displays the current values held by those variables.

#Basic Operation

Creating a basic solution in HumMod is quite simple. Any advancement of time will yield results in five-thousand-odd variables that run the program.

For example, just opening the program and immediately advancing it some period of time will give you basic results: A blood pressure of about
120/79, an internal temperature of around 98.5°F, a respiratory rate of roughly 12.0 breaths/minute, and a heart rate of approximately 72 BPM. This is the default "Chart" display which is opened up every time HumMod launches. 

!["Chart" display](https://github.com/HumMod/documentation/raw/gh-pages/images/hummod_quickstart/initial.jpg)


However, using the dropdown menu, you can navigate to any number of displays, such as our ersatz human’s blood volume statistics.

![Blood Volume Statistics](https://github.com/HumMod/documentation/raw/gh-pages/images/hummod_quickstart/blood_volume.jpg)


Any number of conditions or parameters can also be changed in order to create certain scenarios and results in the simulation. Conditions
are changed either through the use of radiobuttons (used for options that are toggled on/off) or sliders (used to set variables which have many possible quantitative settings). Oftentimes, both types of controls are used to influence a variable, using a radiobutton to turn the functionality of the slidebar below it, as is the case in the example below:

![Radiobutton, Slider, and Information Box](https://github.com/HumMod/documentation/raw/gh-pages/images/hummod_quickstart/sample_box.jpg)


Another important feature of HumMod’s user interface are the information boxes contained in many of the displays. Clicking on these boxes will yield a dialog box
holding information about the box, usually being either the normal values in a human being for the variables in the box, the units they are measured in, conversion factors for several units, or combinations of these three possibilities. The gray box with an exclamation point in the above image is an information box.


#Sample Execution


The following is a walkthrough of a demonstration in which several of the virtual
person’s environmental variables are changed and the effects of these changes are modified over time. 

First, open HumMod. It should be set, as always to the “Chart” of a
patient with default statistics. Use “Go” to advance the patient 10 minutes. His
uninteresting vitals should be just as uninteresting as they were when you started. Now we’re going to create a severe environmental change. 

So, our subject is now a mountain climber that has become stranded, so
we’ll need to change his environmental factors to match the circumstances that match this crisis.

The bottom row of dropdown menus controls the navigation to all of the variables that the program can monitor and all of the factors that can be changed. The “Environment” options and display can be found under the “Lifestyle” dropdown menu. Select this “Environment” option so that it can be changed in order to simulate our marooned mountaineer. 

![Lifestyle Dropdown Menu](https://github.com/HumMod/documentation/raw/gh-pages/images/hummod_quickstart/lifestyle_highlight.jpg)


The Environment page allows you to control temperature, altitude (which changes atmospheric pressure), wind speed, relative humidity, and the level of clothing worn by the patient (a choice between “no clothing”, “summer”, “normal”, “winter” and “arctic”).

![Environment](https://github.com/HumMod/documentation/raw/gh-pages/images/hummod_quickstart/environment.jpg)


Let’s have our subject stranded at 7000 feet (2134 meters for the
metrically inclined), suffering through 20 mph winds at 9°F, thankfully protected by warm winter clothing. If you advance the solution using "Go" for 30 minutes, you will see changes in the subject's physiology. If you go to "Chart", his vitals will appear to be fairly normal, except for his respiratory rate, which spikes due to the thinness of the air at 7000 feet. This lack of oxygen is having profound effects elsewhere, even though the subject's chart appers normal. Use to the "Physiology" dropdown menu, and go to "Acid/Base."

![Acid-Base](https://github.com/HumMod/documentation/raw/gh-pages/images/hummod_quickstart/acid_base.jpg)


The subject's blood pH is currently rising due to the effects of the thin mountain air, as can be easily seen by the graph tracking it over time.


The subject is surviving these conditions, but a more severe set of conditions could be creating by lowering the temperature even further, of moving him to a higher altitude. Such disturbances could easily cause major physiological aberrations, such as the body temperature dropping to 80°F or something fairly unconcerning like that. 

If these major changes affect the patient's physiology in a visible manner, often  a dialog box will interrupt the simultation, automatically pausing it and giving a description of the subject's condition, such as "I'm like.....confused."

At this point, the dialog box gives the option either to interrupt the simulation and attempt to change conditions or observe the patient's physiology at current, or to continue the simulation for the planned time interval under the same conditions.
