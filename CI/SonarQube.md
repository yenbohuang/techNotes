# Building SonarQube + Jenkins on CentOS

## Install Pylint

Follow instructions on <https://pypi.python.org/pypi/pylint>

    $ sudo python -m pip install astroid
    $ sudo python -m pip install isort
    $ sudo python -m pip install pylint

## Install PostgreSQL Database

PostgreSQL database can be replaced by MSSQL, Oracle DB, or MySQL. Refer to details here: <http://docs.sonarqube.org/display/SONAR/Installing+the+Server#InstallingtheServer-installingDatabaseInstallingtheDatabase>

Install PostgreSQL server and initialize the database

    $ sudo yum install postgresql-server
    $ sudo postgresql-setup initdb
    $ sudo service postgresql start
    $ sudo chkconfig postgresql on

Change admin's password, create sonarqube DB and user

Open psql console

    $ sudo -u postgres psql
    $# alter user postgres password '???';
    $# create user sonarqube createdb password  '???';
    $# create database sonarqube owner sonarqube;
    $# \q

Change PostgreSQL listening address in "/var/lib/pgsql/data/postgresql.conf" as follows:

    listen_addresses = '*'

Change login method to "md5" in "/var/lib/pgsql/data/pg_hba.conf"

    host    all             all             127.0.0.1/32            md5

Restart PostgreSQL

    $ sudo service postgresql restart

Login sonarqube user and see if it works.

    $ psql -d sonarqube -h 127.0.0.1 -U sonarqube -W

## Install SonarQube

Install SonarQube

    $ sudo wget -O /etc/yum.repos.d/sonar.repo http://downloads.sourceforge.net/project/sonar-pkg/rpm/sonar.repo
    $ yum install sonar

Add PostgreSQL DB connection and enable server mode in "/opt/sonar/conf/sonar.properties".
 
    sonar.jdbc.username=sonarqube
    sonar.jdbc.password=???
    sonar.jdbc.url=jdbc:postgresql://127.0.0.1:5432/sonarqube
    sonar.web.javaOpts=-server

Assign JDK path in "/opt/sonar/conf/wrapper.conf"

    wrapper.java.command=/path/to/my/jdk/bin/java

Start SonarQube as a service

    $ sudo service sonar start
    $ sudo chkconfig sonar on

Set admin's password
* Open a browser with this URL: "http://<host IP>:9000/"
* Login by "admin/admin" and change the password.

Install Plugins from Update Center.

Refer to details on:
* <http://docs.sonarqube.org/display/SONAR/Installing+the+Server#InstallingtheServer-installingWebServerInstallingtheWebServer>
* <http://sonar-pkg.sourceforge.net/>
* <http://docs.sonarqube.org/display/PLUG/Plugin+Library>

## Install Jenkins

Install Jenkins and enable the service

    $ sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo
    $ sudo rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
    $ sudo yum install jenkins
    $ sudo service jenkins start
    $ sudo chkconfig jenkins on

Set admin's password
* Open browser with this URL: http://<host IP>:8080
* Copy initial password generated under "/var/lib/jenkins/secrets/initialAdminPassword" and use it on UI.
* Set new password

Install plugins by "Manage Jenkins > Manage Plugins":

Refer to details:
* <https://wiki.jenkins-ci.org/display/JENKINS/Installing+Jenkins+on+Red+Hat+distributions>

## Install SonarQube Plugin on Jenkins

Install plugins by "Manage Jenkins -> Manage Plugins".

Adding SonarQube Server
* Open "Manage Jenkins > Configure System".
  * In "SonarQube servers" section
    * Click at "Add SonarQube" button.
    * Check "Enable injection of SonarQube server configuration as build environment variables".
    * Fill in the following information
      * Name: Any given name.
      * Server URL: http://<host IP>:9000/
      * Server version: 5.3 or higher
      * Server authentication token: Generated from SonarQube
* Open SonarQube UI and open "Administration -> Security -> Users" page.
* Create a user with proper permission.
* In "Tokens" column, click at "Update Tokens".
  * Provide a token name and generate the token.

Adding SonarQube Scanner
* Open "Manage Jenkins > Global Tool Configuration".
* In "SonarQube Scanner" section
  * Click at "Add SonarQube Scanner" button.
  * Fill in the following information
    * Name: Any given name.
    * Check "Install automatically".

Refer to details:
* <http://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner+for+Jenkins>

## Create SonarQube Quality Profile

* Open "Quality Profiles" tab and click at "Create" button.
* On "New Profile" form, fill in the following information
  * Name: Any given name.
  * Language: Major programming language in this project.
* Click "Activate More" button.
* Check "Rules > Repository".
  * Click at the repository you would like to add.
  * Click "Bulk Change" button, choose "Activate in <your profile name>", and apply it.
  * Add more rules from other repositories.
* Go back to "Quality Profiles" tab, scroll down to your quality profile.
  * Under "Rules" column.
    * Click at "Deprecated Rules" (the red box.)
    * Click "Bulk Change" button, choose "Deactivate in <your profile name>", and apply it.
* Go back to "Quality Profiles" tab, scroll down to your quality profile.
  * Click at "Rules" (the one with number of activated rules.)
  * Deactivate the rules which are not appropriate to your applications.
* Done.

## Add SonarQube into Jenkins Build Configuration

### Maven Projects

* Click "New Item" and select "Maven Project".
  * In "Build Environment" section:
    * Check "Prepare SonarQube Scanner environment".
  * In "Build" section:
    * Goals and options: `package $SONAR_MAVEN_GOAL -Dsonar.host.url=$SONAR_HOST_URL -DskipTests`
      * This is a sample for non-production usage. 
* After build configuration is created, click "Build Now".
* After build is completed, click "SonarQube" and see code analysis report on SonarQube.

### Python Projects

Refer to this link for analysis properties and "sonar-project.properties":
* <http://docs.sonarqube.org/display/SONAR/Analysis+Parameters>
* <http://docs.sonarqube.org/display/PLUG/Pylint+Report>

#### By Build Configuration on Jenkins

* Click at "New Item" and select "Freestyle Project".
  * In "Build Environment" section:
    * Check "Prepare SonarQube Scanner environment".
  * In "Build" section:
    * Click at "Add build step", select "Execute SonarQube Scanner", and fill in the following information:
      * JDK: JDK 1.8
      * Analysis properties:
```
    sonar.sources=<comma separated source code folder path>
    sonar.projectKey=<unique string for this project>
    sonar.sourceEncoding=UTF-8
```

#### By "sonar-project.properties"

The procedure is the same as using "Analysis properties" in Jenkins build configuration except:
* Keep "Analysis properties" blank.
* Add the content in "Analysis properties" into "sonar-project.properties" and check in to project root folder.

# Using SonarQube in a Developer's Daily Life

## IDE Plugins

TBD
<http://www.sonarlint.org/>

## Command-Line Tool

TBD
<http://www.sonarlint.org/commandline/index.html>

# Troubleshooting

## SonarQube Related

### Adjust SonarQube Log Level

Add this property in "Analysis properties" or "sonar-project.properties". The supported log levels are DEBUG and TRACE.

    sonar.log.level=DEBUG

Refer to this link for other details:
* <http://docs.sonarqube.org/display/SONAR/Analysis+Parameters>

## Python Related

### Pylint rule '?' is unknown in Sonar

Pylint displays this log for deactivated rules and it is okay to ignore.
You can search the rule number by search input box under SonarQube "Rules" tab. 

    22:43:24 INFO: Sensor org.sonar.plugins.python.pylint.PylintSensor
    22:43:29 WARN: Pylint rule 'W1401' is unknown in Sonar

Refer to this link for other details:
* <http://stackoverflow.com/questions/24455176/pylint-rule-is-unkown-to-sonar>

## SBT Related

### Cannot Run FindBugs: This project contains Java source files that are not compiled

FindBugs requires more information when applying on SBT projects. For example, it has to know where the compiled classes are.

    01:34:50 ERROR: Error during SonarQube Scanner execution
    01:34:50 java.lang.IllegalStateException: Can not execute Findbugs
    01:34:50        at org.sonar.plugins.findbugs.FindbugsExecutor.execute(FindbugsExecutor.java:169)
    ...
    01:34:50 Caused by: java.lang.IllegalStateException: This project contains Java source files that are not compiled.
    01:34:50        at org.sonar.plugins.findbugs.FindbugsConfiguration.getFindbugsProject(FindbugsConfiguration.java:120)
    01:34:50        at org.sonar.plugins.findbugs.FindbugsExecutor.execute(FindbugsExecutor.java:119)
    01:34:50        ... 31 more

This can be fixed by adding `"sonar.java.binaries"` property:

    sonar.java.binaries=project1/target/classes,project2/target/classes

Remember excluding folders which don't include Java source files. Or, you will see this error message:

    01:03:57 ERROR: Error during SonarQube Scanner execution
    01:03:57 java.lang.IllegalStateException: No files nor directories matching 'project3/target/classes'

Refer to this link for other details:
* <http://stackoverflow.com/questions/39102924/can-not-execute-findbugs-caused-by-this-project-contains-java-source-files-that>

### Bytecode of dependencies was not provided

SonarQube requires more steps for knowing where the dependencies are for SBT projects.

    01:09:38 WARN: Bytecode of dependencies was not provided for analysis of source files, you might end up with less precise results. Bytecode can be provided using sonar.java.libraries property

Here are options to fix it:
* Use Maven since SonarQube provides Maven plugin.
* Populate `"sonar.java.libraries"` property.
