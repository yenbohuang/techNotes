# "sbt publish-m2" Does Not Refresh Snapshots in Local Maven Repo

After running `sbt publish-m2` command, the snapshot JARs/POMs aren't updated to the latest local builds in local Maven repo (under `~/.m2/repository/`).

This is a bug in sbt 0.13.8. You can use the following command and see which sbt version you are using:

    sbt about

If you can't upgrade sbt, delete local Maven repo before running `sbt publish-m2` command. See the following link for details:
* <http://stackoverflow.com/questions/30760628/sbt-publishm2-do-not-refresh-snapshot-jar-in-local-maven-repo>

# Dependency issue after running "sbt eclipse"

sbt version can be hard-coded in `<project>/project/build.properties`:
* <http://www.scala-sbt.org/1.0/docs/Hello.html#Setting+the+sbt+version>

If you see dependency issues like this after running `sbt eclipse`, here are steps to fix it:
* Update sbt version in `build.properties`.
* Or, delete `build.properties` and use default version by locally installed sbt.

Errors on console

    Getting org.scala-sbt sbt 0.13.9 ...
    :: problems summary ::
    :::: WARNINGS
    module not found: jline#jline;2.11
    ==== local: tried
    /home/yenbo.huang/.ivy2/local/jline/jline/2.11/ivys/ivy.xml
    -- artifact jline#jline;2.11!jline.jar:
    /home/yenbo.huang/.ivy2/local/jline/jline/2.11/jars/jline.jar
    ==== Maven Central: tried
    https://repo1.maven.org/maven2/jline/jline/2.11/jline-2.11.pom
    -- artifact jline#jline;2.11!jline.jar:
    https://repo1.maven.org/maven2/jline/jline/2.11/jline-2.11.jar
    ...
    ::::::::::::::::::::::::::::::::::::::::::::::
    ::          UNRESOLVED DEPENDENCIES         ::
    ::::::::::::::::::::::::::::::::::::::::::::::
    :: jline#jline;2.11: not found
    ::::::::::::::::::::::::::::::::::::::::::::::
    ::::::::::::::::::::::::::::::::::::::::::::::
    ::              FAILED DOWNLOADS            ::
    :: ^ see resolution messages for details  ^ ::
    ::::::::::::::::::::::::::::::::::::::::::::::
    :: org.scala-sbt#control;0.13.9!control.jar
    ...
    :::: ERRORS
    Server access Error: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target url=https://repo1.maven.org/maven2/jline/jline/2.11/jline-2.11.pom
    ...
    :: USE VERBOSE OR DEBUG MESSAGE LEVEL FOR MORE DETAILS
    unresolved dependency: jline#jline;2.11: not found
    download failed: org.scala-sbt#control;0.13.9!control.jar
    ...
    Error during sbt execution: Error retrieving required libraries
    (see /home/yenbo.huang/.sbt/boot/update.log for complete log)
    Error: Could not retrieve sbt 0.13.9

In `~/.sbt/boot/update.log`

    :: problems summary ::
    :::: WARNINGS
    module not found: jline#jline;2.11
    ==== local: tried
    /home/yenbo.huang/.ivy2/local/jline/jline/2.11/ivys/ivy.xml
    -- artifact jline#jline;2.11!jline.jar:
    /home/yenbo.huang/.ivy2/local/jline/jline/2.11/jars/jline.jar
    ==== Maven Central: tried
    https://repo1.maven.org/maven2/jline/jline/2.11/jline-2.11.pom
    -- artifact jline#jline;2.11!jline.jar:
    https://repo1.maven.org/maven2/jline/jline/2.11/jline-2.11.jar
    ...
    ::::::::::::::::::::::::::::::::::::::::::::::
    ::          UNRESOLVED DEPENDENCIES         ::
    ::::::::::::::::::::::::::::::::::::::::::::::
    :: jline#jline;2.11: not found
    ::::::::::::::::::::::::::::::::::::::::::::::
    ::::::::::::::::::::::::::::::::::::::::::::::
    ::              FAILED DOWNLOADS            ::
    :: ^ see resolution messages for details  ^ ::
    ::::::::::::::::::::::::::::::::::::::::::::::
    :: org.scala-sbt#control;0.13.9!control.jar
    ...
    :::: ERRORS
    Server access Error: sun.security.validator.ValidatorException: PKIX path building failed: sun.security.provider.certpath.SunCertPathBuilderException: unable to find valid certification path to requested target url=https://repo1.maven.org/maven2/jline/jline/2.11/jline-2.11.pom
    ...
    :: USE VERBOSE OR DEBUG MESSAGE LEVEL FOR MORE DETAILS
    java.lang.RuntimeException: not found
        at org.apache.ivy.core.resolve.IvyNode.loadData(IvyNode.java:238)
        at org.apache.ivy.core.resolve.VisitNode.loadData(VisitNode.java:292)
    ...
    Error during sbt execution: Error retrieving required libraries

# Transitive jmx dependency issues

If you add `zkclient` directly under `libraryDependencies` in `build.sbt`, you will see jmx dependency errors.

    libraryDependencies ++= Seq(
    ...
      "com.101tec" % "zkclient" % "0.9",
    ...
    )

Error messages on console:

    [warn]  ::::::::::::::::::::::::::::::::::::::::::::::
    [warn]  ::              FAILED DOWNLOADS            ::
    [warn]  :: ^ see resolution messages for details  ^ ::
    [warn]  ::::::::::::::::::::::::::::::::::::::::::::::
    [warn]  :: com.sun.jdmk#jmxtools;1.2.1!jmxtools.jar
    [warn]  :: com.sun.jmx#jmxri;1.2.1!jmxri.jar
    [warn]  ::::::::::::::::::::::::::::::::::::::::::::::
    sbt.ResolveException: download failed: com.sun.jdmk#jmxtools;1.2.1!jmxtools.jar
    download failed: com.sun.jmx#jmxri;1.2.1!jmxri.jar
         at sbt.IvyActions$.sbt$IvyActions$$resolve(IvyActions.scala:313)
    ...
    [error] (commons-container/*:update) sbt.ResolveException: download failed: com.sun.jdmk#jmxtools;1.2.1!jmxtools.jar
    [error] download failed: com.sun.jmx#jmxri;1.2.1!jmxri.jar
    ...
    [error] Could not create Eclipse project files:
    [error] Error evaluating task 'scalacOptions': error
    [error] Error evaluating task 'externalDependencyClasspath': error

For resolving this issue, we have to exclude problematic dependencies manually (slf4j-log4j12 in this case.)

    libraryDependencies ++= Seq(
    ...
      "com.101tec" % "zkclient" % "0.9" exclude("org.slf4j", "slf4j-log4j12")
    ...
    )

See details on the following links:
* <https://github.com/twitter/cassie/issues/13>
* <https://groups.google.com/forum/#!topic/akka-dev/1gltGQHEwoE>
* <https://github.com/CSUG/sbt-one-log/issues/9>
