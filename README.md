# Emscripten-codeblocks-profile.
A emscripten profile for the  code:blocks ide

## Prerequisites

This is an untested profile, so far I've succesfully build a few applications but havn't tried all options yet.  
This readme only covers instalation on windows but I think Linux woudn't be to disimilar.

## Instalation

Installation can be a bit confusing depending on how codeblocks is installed.  
If you included the codeblocks launcher during the instalation there are two places codeblocks will store settings.  
One for the the regular codeblocks and one for the codeblocks launcher. You can insall the profile for either or both but the directories will be different.  

For the regular the codeblocks the settings are sored in:  
C:\Users\<USER>\AppData\Roaming\CodeBlocks  
For the codeblocks launcher the stettings are stored in:  
C:\Program Files\CodeBlocks\AppData\codeblocks  

When I refer to a file in the rest of this readme it's in either of these directories.  

### Add the compiler to the list.
Find the default.conf file and open it in a text editor.  
Navigate to the "compiler" node and within that, locate the "User_sets" node. If User_sets doesn't excist create it.  
Within the user_sets node paste the following node:  

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
Drop the options_emscripten.xml into the share/codeblocks/compilers directory.  

### Set the compiler path  
When you start codeblocks goto Settings->compiler. Emscripten should now be listed in the list of compilers.  
Select it and click on Toolchain executables and under "Compiler's instalation directory", supply the location of the emscripten compiler (E.g C:\emsdk-main\upstream\emscripten).  

## Usage  

### Start a new project  
To start a new project you could either create an empty project or a console project to start with a basic main.cpp file. When it asks what compiler you want to use select emscripten.  

### Outputformat  
Emscripten has the ability to generate a html page which is great to quickly test your application inside a browser.  
To enable this using codeblocks click on settings->compiler->Custom variables. Select the "OUTPUTFORMAT" variable and click edit.
Change the value from "js" to "html".  

**WARNING:**  
Everytime the project is build the index.html is overwritten when this variable is set to "html". I would recomend changing this setting back to "js" once an index.html has been created to avoid potential data loss.


