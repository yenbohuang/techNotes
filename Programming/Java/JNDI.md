# Using JNDI

See details on <http://tomcat.apache.org/tomcat-7.0-doc/jndi-resources-howto.html>

## JNDI supports the following resources

* Generic JavaBean resources
* Tomcat user database resources (`“tomcat-users.xml”`)
* JavaMail sessions
* JDBC data resources
* Custom resource factories

## JNDI configuration in `“$CATALINA_BASE/conf/server.xml”`

    <Context ...> ... 
       <Resource
          name="jdbc/EmployeeDB“
          auth="Container“
          type="javax.sql.DataSource“
          username="dbusername“
          password="dbpassword“
          driverClassName="org.hsql.jdbcDriver“
          url="jdbc:HypersonicSQL:database“
          maxActive="8“
          maxIdle="4"/>
    ... </Context>

## Getting connection by Java

    Context initCtx = new InitialContext();
    Context envCtx = (Context) initCtx.lookup("java:comp/env");
    DataSource ds = (DataSource) envCtx.lookup("jdbc/EmployeeDB");
    Connection conn = ds.getConnection();
    ... use this connection to access the database ...
    conn.close();
    
## MongoDB and Popular Libraries

Hibernate OGM + MongoDB + JNDI

* <http://docs.jboss.org/hibernate/ogm/4.1/reference/en-US/html/ogm-mongodb.html>

Spring + MongoDB + JNDI

* <http://docs.spring.io/spring/docs/current/spring-framework-reference/html/xsd-config.html>
* <http://docs.spring.io/spring-data/mongodb/docs/current/reference/html/>
* <http://stackoverflow.com/questions/4076254/mongodb-via-jndi>