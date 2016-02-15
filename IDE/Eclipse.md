# Useful plugins

Editors
* Properties Editor <https://marketplace.eclipse.org/content/properties-editor>
* Markdown Text Editor <https://marketplace.eclipse.org/content/markdown-text-editor>
* ShellEd <http://sourceforge.net/projects/shelled>
* Eclipse CDT

CI
* Hudson/Jenkins Mylyn Builds Connector <http://marketplace.eclipse.org/content/hudsonjenkins-mylyn-builds-connector>

# Optional plugins

Version controls
* Subclipse <https://marketplace.eclipse.org/content/subclipse>
* EGit <http://marketplace.eclipse.org/content/egit-git-team-provider>

Others
* Find bugs <https://marketplace.eclipse.org/content/findbugs-eclipse-plugin>

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

# Using Tomcat in Eclipse

Eclipse use the following in launch configuration:

    -Dcatalina.base="D:\ws-git\.metadata\.plugins\org.eclipse.wst.server.core\tmp0" 
    -Dcatalina.home="D:\PortablePrograms\apache-tomcat-8.0.28" 
    -Dwtp.deploy="D:\ws-git\.metadata\.plugins\org.eclipse.wst.server.core\tmp0\wtpwebapps" 
    -Djava.endorsed.dirs="D:\PortablePrograms\apache-tomcat-8.0.28\endorsed"

# Cygwin for CDT

* Install Cygwin dependencies properly. I am too lazy to check them, so, I installed everything.
* Add "%cygwin%\bin" to "PATH" environment variable.
* Go to "Windows -> Preference -> C/C++ -> Debug -> Source Lookup Path"
  * Add "Path Mapping"
  * "\cygdrive\c" -> "c:\"
  * "\cygdrive\d" -> "d:\"

See details on <http://wyding.blogspot.tw/2009/04/setup-cygwin-toolchain-in-eclipse-cdt.html>