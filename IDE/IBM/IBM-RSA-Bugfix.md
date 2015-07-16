# JVM terminated. Exit code=160

Comment out the following line in `eclipse.ini`:

    -Xshareclasses:name=IBMSDP_%u 

See details on <https://jazz.net/forum/questions/126400/show-view-pending-changes-kills-rtc-404-client>

* Error message on Eclipse console:

    JVM terminated. Exit code=160
    /opt/IBM/SDP//jdk/jre/bin/javaw
    -Xquickstart
    -Xms40m
    -Xmx1024m
    -Xmnx64m
    -Xgcpolicy:gencon
    -Xscmx96m
    -Xshareclasses:name=IBMSDP_%u
    -XX:MaxPermSize=512M
    -Xcompressedrefs
    -Dcom.ibm.ws.management.event.max_polling_interval=1000
    -Djava.util.Arrays.useLegacyMergeSort=true
    -Dorg.eclipse.swt.browser.XULRunnerPath=/opt/xulrunner/xulrunner-3.6.20
    -jar /opt/IBM/SDP//plugins/org.eclipse.equinox.launcher_1.3.0.v20120522-1813.jar
    -os linux
    -ws gtk
    -arch x86_64
    -showsplash
    -launcher /opt/IBM/SDP/eclipse
    -name Eclipse
    --launcher.library /opt/IBM/SDP//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.1.200.v20120913-144807/eclipse_1502.so
    -startup /opt/IBM/SDP//plugins/org.eclipse.equinox.launcher_1.3.0.v20120522-1813.jar
    --launcher.overrideVmargs
    -exitdata 11f8017
    -install /opt/IBM/SDP
    -vm /opt/IBM/SDP//jdk/jre/bin/javaw
    -vmargs
    -Xquickstart
    -Xms40m
    -Xmx1024m
    -Xmnx64m
    -Xgcpolicy:gencon
    -Xscmx96m
    -Xshareclasses:name=IBMSDP_%u
    -XX:MaxPermSize=512M
    -Xcompressedrefs
    -Dcom.ibm.ws.management.event.max_polling_interval=1000
    -Djava.util.Arrays.useLegacyMergeSort=true
    -Dorg.eclipse.swt.browser.XULRunnerPath=/opt/xulrunner/xulrunner-3.6.20
    
    -jar /opt/IBM/SDP//plugins/org.eclipse.equinox.launcher_1.3.0.v20120522-1813.jar

# XPCOM error 0x80004005 (no solution yet)

** This solution does not work. **

    -Dorg.eclipse.swt.browser.UseWebKitGTK=true
 
See details on <https://jazz.net/forum/questions/72508/xpcom-error-2147467262-with-64bit-client-ext-on-linux-mint> 

** This solution does not work. **

* Eclipse 3.4.x: Mozilla 1.4 GTK2 - 1.7.x GTK2, XULRunner 1.8.x - 1.9.0.x.
* Eclipse 3.6.x: Mozilla 1.4 GTK2 - 1.7.x GTK2, XULRunner 1.8.x - 1.9.x and 3.6.x (but not 2.x), WebKitGTK+ 1.2.x


See details on <http://www-01.ibm.com/support/docview.wss?uid=swg21598554> 