# Useful plugins

* Subclipse <https://marketplace.eclipse.org/content/subclipse>
* Find bugs <https://marketplace.eclipse.org/content/findbugs-eclipse-plugin>
* Log Viewer <https://marketplace.eclipse.org/content/logviewer>
* Properties Editor <https://marketplace.eclipse.org/content/properties-editor>
* Markdown Text Editor <https://marketplace.eclipse.org/content/markdown-text-editor>


# Setting

## Intelli-sense

* Windows -> Preferences -> Java -> Editor -> Content Assist
* Auto Activation -> Auto Activation Trigger for Java
* Change "." to ".(abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ"


See details on <http://stackoverflow.com/questions/2943131/eclipse-intellisense>

## Export Preferences

File -> Export -> General -> Preferences

## Enable debug view

![Debug View](https://github.com/yenbohuang/techNotes/blob/master/IDE/images/debugView.png) 

See details on <https://github.com/yenbohuang/techNotes/tree/master/IDE>

## Using UTF-8

* Windows > Preferences > General > Content Types, set UTF-8 as the default encoding for all content types.
* Windows > Preferences > General > Workspace, set "Text file encoding" to "Other : UTF-8".

See details on <http://stackoverflow.com/questions/9180981/how-to-support-utf-8-in-eclipse> 

# eclipse.ini

## Change UI language

    -Duser.language=en

## -vm

    -vm /opt/sun-jdk-1.6.0.02/bin/java
    
See details on <https://wiki.eclipse.org/Eclipse.ini#-vm_value:_Linux_Example>


# Using local SVN repo

* Install SVN command-line tool
* Create folder 'd:\svn-repo'
* Create SVN repo by 'svnadmin create myproject' under 'svn-repo' folder.
* Use URL 'file:///d:/svn-repo/myproject'

See details on <http://www.jayway.com/2009/04/03/setting-up-a-local-subversion-repository-to-use-with-your-eclipse/>