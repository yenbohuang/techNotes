# Install and run on Windows

* Download hudson-x-x-x.war
* Run `java -jar hudson-x.x.x.war --httpPort=9090 --httpListenAddress=127.0.0.1`
  * `C:\Users\<your user folder>\.hudson` will be created.
* Browse `http://localhost:9090`

See details on <http://wiki.eclipse.org/Hudson-ci/Use_Hudson>

# Job configuration

* General section
  * Discard Old Builds
    * Max # of builds to keep -> 5
* Source Code Management
  * Subversion
    * Repository URL -> Branch URL path
      * Example for local SVN: `file:///D:/svn-repo/yenbo/testProject`
    * Check-out Strategy -> Clean check out folders and then checkout
* Build Environment
  * **DO NOT** check "Delete workspace before build starts", or Maven plugin will fail.
  *  Abort the build if it's stuck
* Build
  * Add build step -> Invoke Maven 3
    * Goal -> Example for test-only project: `clean test`
* Post-build Actions
  * Publish JUnit test result report
    * Test report XMLs -> `target/surefire-reports/*.xml`
  * Notify that Maven dependencies have been updated by Maven 3 integration 
    * Notify even when build is unstable