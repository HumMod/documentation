<!DOCTYPE html> 
<html> 
<head> 
  <title>HumMod | Documentation</title> 
  <link href="/css/application.css" media="screen" rel="stylesheet" type="text/css" /> 
</head> 
<body id="help"> 
  <!-- Fork Me Badge -->
  <a href="http://github.com/hummod"><img style="position: absolute; top: 0; right: 0; border: 0;" src="https://d3nwyuy0nl342s.cloudfront.net/img/30f550e0d38ceb6ef5b81500c64d970b7fb0f028/687474703a2f2f73332e616d617a6f6e6177732e636f6d2f6769746875622f726962626f6e732f666f726b6d655f72696768745f6f72616e67655f6666373630302e706e67" alt="Fork me on GitHub"></a>
  <!-- End of Badge -->
  <header id="main"> 
    <h1><a href="http://hummod.org">HumMod</a></h1> 
      <h2>Help</h2> 
      <nav class="main"> 
        <a href="http://hummod.org/about">About</a> / 
        <a href="http://hummod.org/projects">Projects</a> / 
        Help / 
        <a href="http://hummod.org/contact">Contact</a> 
      </nav> 
  </header> 
    <hr /> 
  <div id="content">

  <section>
  <header>
  <h1>Overview</h1>
  </header>

	<p>
	This section defines elements that can be part of a script that 	controls the solution.
	</p>

	<p>
	Multiple solutions may be calculated and selected data can be saved to
	data files. User interaction is not necessarily required.
	</p>

	<p>
	The highest-level scripted control element is named scripted. It is a
	container element for the scripted control children.
	</p>

	<p>
	scripted
	     |---fixedparm
	     |---%tasks
	</p>

	<p>
	%tasks
	    |---accept
	    |---advancefor
	    |---advanceto
	    |---call
	    |---def
	    |---eval
	    |---exitscript
	    |---fileaccept
	    |---fileannotate
	    |---fileclose
	    |---filenewline
	    |---fileopenappend
	    |---fileopencreate
	    |---fileroster
	    |---filestarttracking
	    |---filestoptracking
	    |---filetimestamp
	    |---fileupdate
	    |---fileverify
	    |---filewriteheader
	    |---loadics
	    |---message
	    |---pause
	    |---repeatfor
	    |---repeatwhile
	    |---replacenote
	    |---reset
	    |---restart
	    |---saveics
	    |---selectpanel
	    |---setdisplayspeed
	    |---setfileattribute
	    |---setpagerstatus
	    |---setworkdir
	</p>

  </section>

  </div> 

  <footer class="main"> 
    &copy;2010 &ndash; University of Mississippi Medical Center
  </footer> 
</body> 
</html>
