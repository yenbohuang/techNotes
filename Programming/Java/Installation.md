# Install JDK on Ubuntu

Do this in shell script:

    #!/bin/sh
    tar -xvf jdk-7*
    sudo mkdir /usr/lib/jvm
    sudo mv ./jdk1.7* /usr/lib/jvm/jdk1.7.0
    sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.7.0/bin/java" 1
    sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.7.0/bin/javac" 1
    sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jdk1.7.0/bin/javaws" 1
    sudo chmod a+x /usr/bin/java
    sudo chmod a+x /usr/bin/javac
    sudo chmod a+x /usr/bin/javaws

See details on <http://askubuntu.com/questions/56104/how-can-i-install-sun-oracles-proprietary-java-jdk-6-7-8-or-jre> 

If OpenJDK was installed already, replace it by the following commands: 

    sudo update-alternatives --set "java" "/usr/lib/jvm/jdk1.7.0/bin/java"
    sudo update-alternatives --set "javac" "/usr/lib/jvm/jdk1.7.0/bin/javac"

TODO: need reference link!

# Install JDK on CentOS

* Download RPM file from Oracle website.
* Remove OpenJDK by `sudo yum erase ****`
* Run `sudo rpm -ivh jdk-8u91-linux-x64.rpm`
* Run `rpm -q --whatprovides java` and see if "alternatives" is set correctly.

See details on <http://docs.oracle.com/javase/8/docs/technotes/guides/install/linux_jdk.html>

# Make JDK Portable on Windows

Running Java without libraries:
* Open "jdk-*_windows-x64_bin.exe" by 7-zip and enter "\.rsrc\1033\JAVA_CAB10\111\".
* Extract "tools.zip".
* Run this line in CMD under "jdk-*_windows-x64_bin\tools" folder.

`for /r %i in (*.pack) do .\bin\unpack200.exe %i %~pi%~ni.jar`

If you need to use it in Eclipse, proceed with the following steps:
* Extract "jdk-*_linux-x64_bin.tar.gz" by 7-zip.
* Copy "jdk-*_linux-x64_bin.tar\lib" folder and overwrite "jdk-*_windows-x64_bin\tools\lib" folder.
* Point Installed JRE to "jdk-*_windows-x64_bin\tools\" folder and see if all JAR files are configured correctly.

See details on <https://techtavern.wordpress.com/2014/03/25/portable-java-8-sdk-on-windows/>
