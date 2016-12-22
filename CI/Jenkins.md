# Install and run on Windows

* Download jenkins.war
* Set `JENKINS_HOME` environment variable.
* Run `java -jar hudson-x.x.x.war --httpPort=9090 --httpListenAddress=127.0.0.1`
  * If `JENKINS_HOME` is not set, `C:\Users\<your user folder>\.jenkins` will be created.
  * If `C:\Users\<your user folder>\.hudson` was created, Jenkins will reuse it and might not work properly.
* Browse `http://localhost:9090`



See details on:
* <https://wiki.jenkins-ci.org/display/JENKINS/Starting+and+Accessing+Jenkins>
* <https://wiki.jenkins-ci.org/display/JENKINS/Administering+Jenkins>