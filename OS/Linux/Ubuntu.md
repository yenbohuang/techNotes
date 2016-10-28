# Check Ubuntu version

    lsb_release -a

# Environment variables

Preferred

* `/etc/profile.d`
 
System

* `/etc/profile`
* `/etc/default/locale`
* `/etc/bash.bashrc`
* `/etc/sudoers`
* `/etc/environment`

See details on <https://help.ubuntu.com/community/EnvironmentVariables> 


# /etc/profile.d/*.sh

Files with the `.sh` extension in the `/etc/profile.d` directory get executed whenever a bash login shell is entered (e.g. when logging in from the console or over ssh), as well as by the DisplayManager when the desktop session loads. 

You can for instance create the file `/etc/profile.d/myenvvars.sh` and set variables like this: 

    export JAVA_HOME=/usr/lib/jvm/jdk1.7.0
    export PATH=$PATH:$JAVA_HOME/bin

See details on <https://help.ubuntu.com/community/EnvironmentVariables#A.2Fetc.2Fenvironment> 

# Upgrading from Ubuntu 14.04 LTS

To upgrade on a desktop system: 

* Open the "Software & Updates" Setting in Systemsettings. 
* Select the 3rd Tab called "Updates". 
* Set the "Notify me of a new Ubuntu version" dropdown menu to "For any new version". 
* Press Alt+F2 and type in "update-manager" (without the quotes) into the command box. 
* Update Manager should open up and tell you: New distribution release '14.10' is available. 
* Click Upgrade and follow the on-screen instructions.
 
To upgrade on a server system:
 
* Install the update-manager-core package if it is not already installed. 
* Make sure the `/etc/update-manager/release-upgrades` is set to normal. 
* Launch the upgrade tool with the command sudo do-release-upgrade. 
* Follow the on-screen instructions.
 
Note that the server upgrade will use GNU screen and automatically re-attach in case of dropped connection problems. 
There are no offline upgrade options for Ubuntu Desktop and Ubuntu Server. Please ensure you have network connectivity to one of the official mirrors or to a locally accessible mirror and follow the instructions above. 

See details on <https://wiki.ubuntu.com/UtopicUnicorn/ReleaseNotes> 
