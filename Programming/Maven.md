# Install on Windows

* Download "apache-maven-x.x.x-bin.zip" and unzip it.
* Check if `%JAVA_HOME%` is set.
* Set both `%M2_HOME%` and `%MAVEN_HOME%`.
* Append `%M2_HOME%\bin` to `%PATH%`.
* Use `mvn -v` on command console and see if it work.
  * There is a bug that it will not work under root folder. See details on  <https://issues.apache.org/jira/browse/MNG-5804>.

See details on <http://maven.apache.org/install.html>.

# User settings

    <settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">
      <localRepository>d:\mvn-repo</localRepository>
      <interactiveMode/>
      <usePluginRegistry/>
      <offline/>
      <pluginGroups/>
      <servers/>
      <mirrors/>
      <proxies>
        <proxy>
          <id>myproxy</id>
          <active>true</active>
          <protocol>http</protocol>
          <host>192.168.1.100</host>
          <port>6666</port>
          <username></username>
          <password></password>
          <nonProxyHosts>localhost,127.0.0.1</nonProxyHosts>
        </proxy>
      </proxies>
      <profiles/>
      <activeProfiles/>
    </settings>