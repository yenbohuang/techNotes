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

# Forgot password and cannot login

* Edit `/var/lib/jenkins/config.xml`
  * Change `<useSecurity>true</useSecurity>` to `false`
* Restart Jenkins: `sudo service jenkins restart`
* Make changes in "Configure Global Security".

See details on:
* <http://stackoverflow.com/questions/15227305/what-is-the-default-jenkins-password>

# jenkins-inheritance-plugin

## No such property: codeMirrorConfig for class: hudson.markup.EscapedMarkupFormatter

Change "Mange Jenkins -> Configure Global Security -> Markup Formatter" to "Safe HTML"

See details on:
* <https://github.com/i-m-c/jenkins-inheritance-plugin/issues/19>

# Make Jenkins build failed when Maven unit test failed

There are ways to do it, and I prefer the first option:

* Keep the Maven Jenkins job and explicitly add `-Dmaven.test.failure.ignore=false` option.
* Using a FreeStyle Jenkins job template.
* Split the Maven Jenkins job in several build steps and only execute the next one if the previous was strictly successful (and not successful/unstable).
  * A first step would be the classic "mvn clean install".
  * Keep others in the rest of the steps.

See details on:
* <http://stackoverflow.com/questions/28683518/how-do-i-make-jenkins-build-fail-when-maven-unit-tests-fail>
* <http://stackoverflow.com/questions/38486416/keeping-the-maven-deploy-plugin-from-deploying-on-test-failures>
