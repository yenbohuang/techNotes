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

* Extract "jdk-9.0.1_windows-x64_bin.exe".
* Extract "tools.zip".
* Run `for /r %i in (*.pack) do .\bin\unpack200.exe %i %~pi%~ni.jar` in CMD under "jdk-9.0.1_windows-x64_bin\tools" folder

See details on <https://techtavern.wordpress.com/2014/03/25/portable-java-8-sdk-on-windows/>
