# Plugins
## Useful plugins

CI
* Hudson/Jenkins Mylyn Builds Connector <http://marketplace.eclipse.org/content/hudsonjenkins-mylyn-builds-connector>

Editors
* Properties Editor <https://marketplace.eclipse.org/content/properties-editor>
* Markdown Text Editor <https://marketplace.eclipse.org/content/markdown-text-editor>
* ShellEd <http://sourceforge.net/projects/shelled>. Note that you don't have to download it from sourceforge. Use "help-> Install New Software" and find "Dynamic Languages Toolkit - ShellEd".

Version controls
* EGit <http://marketplace.eclipse.org/content/egit-git-team-provider>

## Optional plugins

Editors
* Eclipse CDT
* PyDev <http://marketplace.eclipse.org/content/pydev-python-ide-eclipse>

Version controls
* Subclipse <https://marketplace.eclipse.org/content/subclipse>

Testing
* TestNG <http://testng.org/doc/eclipse.html>
* EclEmma <http://www.eclemma.org/>

Others
* Find bugs <https://marketplace.eclipse.org/content/findbugs-eclipse-plugin>

# Short-Cuts

Preferences -> General -> Keys:

* Finding Java classes: "Ctrl + Shift + T"
* Go to line number: "Ctrl + L"

See details on:
* <http://www.mkyong.com/eclipse/how-to-find-java-class-in-eclipse/>.

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

OpenJDK is usually pre-installed in Linux distributions (e.g. Ubuntu, CentOS.) If we'd like to use Oracle JDK for running Eclipse, we have to provide the JDK path in `eclipse.ini`:

    -vm
    /opt/sun-jdk-1.6.0.02/bin/java
    
See details on <https://wiki.eclipse.org/Eclipse.ini#-vm_value:_Linux_Example>

## Workaround KDE GTK3 incompatible issues

Add these 2 lines before the line "--launcher.appendVmargs":

    --launcher.GTK_version
    2

See details on <https://bbs.archlinux.org/viewtopic.php?id=200053>

# Subversion

## Using local SVN repo

* Install SVN command-line tool
* Create folder 'd:\svn-repo'
* Create SVN repo by 'svnadmin create myproject' under 'svn-repo' folder.
* Use URL 'file:///d:/svn-repo/myproject'

See details on <http://www.jayway.com/2009/04/03/setting-up-a-local-subversion-repository-to-use-with-your-eclipse/>

## Java HL on Ubuntu

The followings are the extra steps except install Java HL by Eclipse:

* Run `sudo apt-get install libsvn-java`
* Run `locate libsvnjava` and find the path.
* Add the following line into eclipse.ini

```
    -Djava.library.path=/usr/lib/x86_64-linux-gnu/jni
```

See details on <http://stackoverflow.com/questions/3274890/javahl-not-loading-noclassdeferror>

# Git

## Add toolbar

* Click at "Menu Bar -> Window -> Perspective -> Customize Perstive"
* Check "Git" under "Action Set Availability"

See details on <http://www.vogella.com/tutorials/EclipseGit/article.html#egitconfiguration_toolbar>

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

# Creating linked resources

Create folder shortcut without creating projects:

* Create a non-Java project.
* Right click and choose "New -> Folder".
* Enter folder name and expend "Advanced" button.
* Choose "Link to alternate location (Linked Folder)" and click "Browse" button.

Version control function cannot be done on linked resources; do it by command-line utilities instead.

See details on <http://help.eclipse.org/juno/index.jsp?topic=%2Forg.eclipse.platform.doc.user%2Ftasks%2Ftasks-45.htm>

# Scala

## Compile Error for Scala + Java Projects

Some projects contains both Scala and Java source codes. You will see this error if you didn't install m2e-scala and Scala IDE.

    Plugin execution not covered by lifecycle configuration: net.alchim31.maven:scala-maven-plugin:3.2.1:add-source 
    (execution: scala-compile-first, phase: process-resources)
    Plugin execution not covered by lifecycle configuration: net.alchim31.maven:scala-maven-plugin:3.2.1:compile 
    (execution: scala-compile-first, phase: process-resources)
    Plugin execution not covered by lifecycle configuration: net.alchim31.maven:scala-maven-plugin:3.2.1:testCompile 
    (execution: scala-test-compile, phase: process-test-resources)

Remember changing compiler target to "jvm-1.8": Window -> Preferences -> Scala -> Compiler -> Standard -> target drop down list.

See details on:
* Scala IDE getting started guide <http://scala-ide.org/docs/current-user-doc/gettingstarted/index.html>
* Scala IDE on Eclipse marketplace <http://marketplace.eclipse.org/content/scala-ide>
* m2e-scala plugin update link <http://alchim31.free.fr/m2e-scala/update-site/>

## Install sbteclipse

* Follow instructions and install sbt <http://www.scala-sbt.org/release/docs/Manual-Installation.html>
* Run `sbt`. It takes a long while for downloading sbt environment.
* Exit sbt session by `exit` sbt command.
* Follow instructions and add sbteclipse plugin <https://github.com/typesafehub/sbteclipse/wiki/Installing-sbteclipse>.
  * Add sbteclipse to global plugin definition.
* Run `sbt` and it starts downloading sbteclipse environment.
* Run `eclipse` sbt command. It takes a long while downloading dependencies and create Eclipse project files.
* Import existing project into Eclipse.
