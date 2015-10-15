# Log4j.properties

    log4j.rootLogger=ERROR,stdout
    
    log4j.logger.org.yenbo=DEBUG
    
    log4j.appender.stdout=org.apache.log4j.ConsoleAppender
    log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
    log4j.appender.stdout.layout.ConversionPattern=%p\t%d\t%C.%M() line %L\t%m%n

See details on:
* <https://logging.apache.org/log4j/1.2/apidocs/org/apache/log4j/PatternLayout.html>