# Add self-signed Bugzilla host to Mylyn

If your sever uses a certificate and fails to connect, e.g. you see exceptions `sun.security.validator.ValidatorException: PKIX path building failed` then you need to point Eclipse at your certificate

Follow the steps:

* Download Portecle and run it
  * `java -jar portecle.jar`
  * Click at "Exam -> Exam SSL/TLS Connection" menu item
    * Enter hostname without `http:://` or `https://`
    * Export certificate by "PEM Encoding" button
  * Click at "File -> Open Keystore File" menu iitem.
    * Open `%JAVA_HOME%\lib\security\cacerts`
      * `C:\Program Files\Java\jre1.8.0_65\lib\security\cacerts`
      * The default password is `changeit`
    * Click "Import Trusted Certificate" button and trust this certificate.
    * Save the change.
* Restart Eclipse
  * Open "Task Repositories" view
    * "Add Task Repository"

See details on:

* <http://portecle.sourceforge.net/>
* <https://confluence.atlassian.com/jira/connecting-to-ssl-services-117455.html>
* <http://wiki.eclipse.org/Mylyn/FAQ#Authentication_Troubleshooting>