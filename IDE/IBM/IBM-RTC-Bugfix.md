# Fix internal browser issue on Ubuntu x64

* Download "xulrunner-24.0.en-US.linux-x86_64.tar.bz2" and copy it to "/opt"
* `cd /opt`
* `sudo cat xulrunner-24.0.en-US.linux-x86_64.tar.bz2 | sudo tar -xj`
* Add `"-Dorg.eclipse.swt.browser.XULRunnerPath=/opt/xulrunner"` to `eclipse.ini`

See details on <https://jazz.net/forum/questions/93625/rtc-40-on-ubuntu-1204-blows-up-when-trying-to-open-history-of-a-work-item>

Eclipse 4.4 and newer: Mozilla 1.4 GTK2 - 1.7.x GTK2, XULRunner 1.8.x - 1.9.x, 3.6.x, 10.x and 24.x (but not 2.x nor other unlisted versions), WebKitGTK+ 1.2.x and newer (Eclipse 4.4 and newer uses GTK 3 by default and XULRunner cannot be used in this case as it is not ported to GTK 3 yet)


See details on <http://www.eclipse.org/swt/faq.php#specifyxulrunner>

* Error messages on Eclipse console:

    Error logged from Process Client UI: 
    No more handles [MOZILLA_FIVE_HOME='/usr/lib/firefox'] (java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons: 
	/home/yenbohuang/softwares/eclipse-luna/configuration/org.eclipse.osgi/1048/0/.cp/libswt-mozilla-gtk-4430.so: libxpcom.so: cannot open shared object file: No such file or directory
	no swt-mozilla-gtk in java.library.path
	Can't load library: /home/yenbohuang/.swt/lib/linux/x86_64/libswt-mozilla-gtk-4430.so
	Can't load library: /home/yenbohuang/.swt/lib/linux/x86_64/libswt-mozilla-gtk.so

    /home/yenbohuang/.swt/lib/linux/x86_64/libswt-mozilla-gtk-4430.so: libxpcom.so: cannot open shared object file: No such file or directory)

* Error messages on Eclipse console:
 
    Failed to create web browser. The MOZILLA_FIVE_HOME environment variable must be configured to point to your web browser install location. For example:
    
      export MOZILLA_FIVE_HOME = /usr/lib/firefox
      
    Also, MOZILLA_FIVE_HOME must be added to the LD_LIBRARY_PATH variable. For example:
    
      export LD_LIBRARY_PATH = "$MOZILLA_FIVE_HOME":"$LD_LIBRARY_PATH"
      
    More instructions for configuring the embedded browser can be found here:
    
      http://www.eclipse.org/swt/faq.php