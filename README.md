# Emscripten-Codeblocks profile.
A Emscripten profile for the  Codeblocks ide.

## Prerequisites

This is an untested profile, so far I've succesfully build a few applications but haven't tried all options yet.  
This readme only covers installation on windows but I think Linux woudn't be too dissimilar.

## Instalation

Installation can be a bit confusing depending on how Codeblocks is installed.  
If you included the Codeblocks launcher during the installation there are two places Codeblocks will store settings.  
One for the the regular Codeblocks and one for the Codeblocks launcher. You can install the profile for either or both but the directories will be different.  

For the regular the Codeblocks the settings are sored in:  
*C:\Users\<USER>\AppData\Roaming\CodeBlocks*  
For the Codeblocks launcher the stettings are stored in:  
*C:\Program Files\CodeBlocks\AppData\codeblocks*  

When I refer to a file in the rest of this readme it's in either of these directories.  

### Add the compiler to the list.
Find the *default.conf* file and open it in a text editor.  
Navigate to the "compiler" node and within that, locate the "user_sets" node. If it doesn't excist create it.  
Within the "user_sets" node paste the following node:  

```xml
<emscripten>
  <NAME>
    <str>
      <![CDATA[Emscripten]]>
    </str>
  </NAME>
  <PARENT>
    <str>
      <![CDATA[null]]>
    </str>
  </PARENT>
  <MASTER_PATH>

  </MASTER_PATH>
  <regex>
    <re001>
      <DESCRIPTION>
        <str>
          <![CDATA[Fatal error]]>
        </str>
      </DESCRIPTION>
      <TYPE int="2" />
      <REGEX>
        <str>
          <![CDATA[FATAL:[ 	]*(.*)]]>
        </str>
      </REGEX>
      <MSG1 int="1" />
    </re001>
  </regex>
  <custom_variables>
    <OUTPUTFORMAT>
      <str>
        <![CDATA[js]]>
      </str>
    </OUTPUTFORMAT>
  </custom_variables>
</emscripten>
```

### Add the compiler options  
Drop the *options_emscripten.xml* into the *share/codeblocks/compilers* directory.  

### Set the compiler path  
When you start Codeblocks click on settings->compiler. Emscripten should now be listed in the list of compilers.  
Select it and click on "Toolchain executables" and under "Compiler's instalation directory", supply the location of the Emscripten compiler (E.g C:\emsdk-main\upstream\emscripten).  

## Usage  

### Start a new project  
To start a new project you could either create an empty project or a console project to start with a basic main file. When it asks what compiler you want to use select Emscripten.  

### Output format  
Emscripten has the ability to generate an html page which is great to quickly test your application inside a browser.  
To enable this using codeblocks click on settings->compiler->Custom variables. Select the "OUTPUTFORMAT" variable and click edit.
Change the value from "js" to "html".  

**WARNING:**  
Everytime the project is built while this variable is set to "html" the index.html is overwritten. 


