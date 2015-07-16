# User settings

Maven plugin uses a settings file where the configuration can be set. Its path is available in Window|Preferences|Maven|User Settings. If the file doesn't exist, create it and put on something like this:

    <settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      http://maven.apache.org/xsd/settings-1.0.0.xsd">
      <localRepository/>
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
    
After editing the file, it's just a matter of clicking on update settings button and it's done. I've just done it and it worked :)

See details on <http://stackoverflow.com/questions/7737710/maven-plugin-not-using-eclipses-proxy-settings> 
