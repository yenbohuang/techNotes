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

# Static code analysis related

## Cannot Run FindBugs: This project contains Java source files that are not compiled

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

## Bytecode of dependencies was not provided

SonarQube requires more steps for knowing where the dependencies are for SBT projects.

    01:09:38 WARN: Bytecode of dependencies was not provided for analysis of source files, you might end up with less precise results. Bytecode can be provided using sonar.java.libraries property

Here are options to fix it:
* Use Maven since SonarQube provides Maven plugin.
* Populate `"sonar.java.libraries"` property.

## sbt-scapegoat not found with SBT 1.0.0-M4

If you build sbt projects such as tsds with SBT 1.0.0-M4, you will see some dependencies cannot be resolved.

    03:10:22 [warn]         Note: Some unresolved dependencies have extra attributes.  Check that these dependencies exist with the requested attributes.
    03:10:22 [warn]                 com.typesafe.sbt:sbt-site:1.0.0 (scalaVersion=2.11, sbtVersion=1.0.0-M4)
    03:10:22 [warn]                 com.etsy:sbt-checkstyle-plugin:3.0.0 (scalaVersion=2.11, sbtVersion=1.0.0-M4)
    03:10:22 [warn]                 de.johoop:sbt-testng-plugin:3.0.2 (scalaVersion=2.11, sbtVersion=1.0.0-M4)
    03:10:22 [warn]                 net.virtual-void:sbt-dependency-graph:0.8.2 (scalaVersion=2.11, sbtVersion=1.0.0-M4)
    03:10:22 [warn]                 com.sksamuel.scapegoat:sbt-scapegoat:1.0.4 (scalaVersion=2.11, sbtVersion=1.0.0-M4)
    03:10:22 [warn]                 org.scalastyle:scalastyle-sbt-plugin:0.8.0 (scalaVersion=2.11, sbtVersion=1.0.0-M4)
    03:10:22 [warn]                 com.typesafe.sbteclipse:sbteclipse-plugin:4.0.0-RC2 (scalaVersion=2.11, sbtVersion=1.0.0-M4)

Use SBT 0.13.12 for now.
