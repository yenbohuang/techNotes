# tomcat-users.xml

```
<role rolename="manager-gui"/>
<role rolename="admin-gui"/>
<user password="yenbo" roles="manager-gui,admin-gui" username="yenbo"/>
```

# Tomcat IP/hostname filters

Add this line in `conf\context.xml`:

```
<Valve className="org.apache.catalina.valves.RemoteAddrValve" 
   allow="127\.\d+\.\d+\.\d+|::1|0:0:0:0:0:0:0:1"/>
```

* <http://tomcat.apache.org/tomcat-7.0-doc/config/valve.html#Remote_Address_Filter>
* <https://stackoverflow.com/questions/3381531/how-to-restrict-access-by-ip-address-with-tomcat>
