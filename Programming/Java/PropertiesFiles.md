# Reading *.properties

* Remember setting proper file permission on properties files.


    Properties prop = new Properties();
    InputStream input = null;
    
    try {

	    input = new FileInputStream(System.getProperty("config"));
	    prop.load(input);
	    System.out.println(prop.getProperty("key"));

    } catch (Exception ex) {
	    ex.printStackTrace();
    }

# Load by command-line

* Use “-D” option for Java console programs

    java -Dconfig=/home/yenbohuang/mytemp/config.properties -classpath target/configdemo.jar org.yenbo.democodes.config.PropertiesDemo

# Load in Tomcat

* Use “JAVA_OPTS” option for Tomcat startup script
* Or use “setenv.sh” under Tomcat’s bin directory

    export JAVA_OPTS="$JAVA_OPTS -Dconfig=/home/yenbohuang/mytemp/config.properties"
    ~/softwares/apache-tomcat-7.0.57/bin/startup.sh
