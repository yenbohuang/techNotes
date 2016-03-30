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
* Run `sudo yum localinstall jre-8u60-linux-x64.rpm`

See details on <https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora>