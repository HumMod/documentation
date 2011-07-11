---
layout: default
title: Model Editor Manual
---

#Using the HumMod Model Editor

#Introduction to the Model Editor

The HumMod Model Editor is a program allowing the user to view, edit, and run specific XML files using the DESolver, a controller and solver program designed to run the XML schema used by HumMod XML files.


When the Editor is first run, it looks like this:

![Editor Startup](https://github.com/HumMod/documentation/raw/gh-pages/images/editor/editor_beginning.jpg)


The editor will show a tiered list of your machine's drives and directories in the left side of the box. The right side of the box is reserved for viewing the information contained in XML files. If you navigate down to find the DES files in whatever, directory you have placed them, you can highlight one to display its contents. Here we show the Bouncing Ball.DES file contained in the HumMod minis folder.

![Bouncing Ball](https://github.com/HumMod/documentation/raw/gh-pages/images/editor/editor_xml.jpg)


You can review and edit the text of this DES file using the Editor. However, we will focus on the steps necessary to run a DES file. The Editor requires that a Model Root File and a Controller/Solver program to be set. The Model Root file should be set as the DES file you wish to run--simply right click on the desired file and select "Make This File The Model Root."

![Setting a Root](https://github.com/HumMod/documentation/raw/gh-pages/images/editor/editor_root.jpg)

You can also set the model root manually by going to the "Options" window in the Model Editor and going to the "Model Root File" tab.


The second priority in running a DES file is to have a controller/solver selected to run the file. This is accomplished by going to the "Options" window and going to the "Controller-Solver" tab. The easisest and most effective solution is to select the "Combined Controller And Solver" bubble and to set the executable of choice as the DESolver by finding the DESolver.EXE file and selecting it as the combined controller and solver, as the DESolver is designed to operate hand-in-hand with the MOdel Editor. Make sure to hit "Apply" to ensure your controller/solver is properly selected.

![Setting a Controller/Solver](https://github.com/HumMod/documentation/raw/gh-pages/images/editor/editor_controller-solver.jpg)


Once your root file, controller, and solver are all properly selected, simply press the "Run" command at the top of the Model Editor window. A DESolver window should open and run the selected DES file.

![Running a DES file](https://github.com/HumMod/documentation/raw/gh-pages/images/editor/editor_execution.jpg)

As you can see, the DESolver has opened up and is running the root .DES file. Time is advanced much in the same manner as it is in HumMod, by a dropdown menu labeled "Go." Here is a sample execution run for 10 seconds.

![Advancing Time](https://github.com/HumMod/documentation/raw/gh-pages/images/editor/editor_bouncing.jpg)


#Introduction To the DESolver

The DESolver is a combined controller and solver designed to work with HumMod-styled XML files. It is more simplistic than HumMod, and the commands available to it are very similar. The usage of the DESolver will depend heavily on the XML file being run by it, as displays and options for advancing time will be unique to the DES file being run as the model root. For any specific questions regarding the operation of the DESolver, please refer to the HumMod documentation. 

The primary purpose of the DESolver is to run it with the model editor, which would allow you to run "mini's". which are models pre-coded to perform certain actions such as modeling a ball bouncing. There are other mini's as well to do things like measure glucose or model circulation. All of these mini's are availiable on the HumMod Github page.

#Using the DESolver with the Model Editor

Once you get the Editor, DESolver, and the mini's from Github you will need to do some rearranging for the DESolver to work with the Editor. Open your Mini's folder and then drag the DESolver executable and .DES files into the Models folder (Both should be inside the Mini's folder). Then open your editor folder and drag the Model Editor to the same folder as your DESolver (so in the Models folder through the Mini's folder).If you have correctly set your controller and solver as described above you should now be able to run a mini on the DESolver.

#Navigating the DESolver

Any questions abput navigating through the DESolver can be answered in the HumMod User's Manual. The main differance between what you'll see in HumMod and what you'll see running Mini's in the DESolver is that the DESolver doesn't give you the all the options to change physiology that HumMod does. It only gives you the option to change preset variables for that particular model. On top of that the "go" option is also set to only be able to run certain time I.E. in the Bouncing Ball model you can only advance time by 1 second or to the next 10 second mark.
