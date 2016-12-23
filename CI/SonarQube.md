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
    * Goals and options: This is a sample for non-production usage. `package $SONAR_MAVEN_GOAL -Dsonar.host.url=$SONAR_HOST_URL -DskipTests`
* After build configuration is created, click "Build Now".
* After build is completed, click "SonarQube" and see code analysis report on SonarQube.