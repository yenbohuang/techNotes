# Using proxy

To enable proxy access for a specific user, add the lines in the example box below to the user's shell profile. For the default bash shell, the profile is the file `~/.bash_profile`. The settings below enable yum to use the proxy server mycache.mydomain.com, connecting to port 3128.
 
    # The Web proxy server used by this account
    http_proxy="http://mycache.mydomain.com:3128"
    export http_proxy
    
If the proxy server requires a username and password, add these to the URL. To include the username yum-user and the password qwerty, add these settings: 

    # The Web proxy server, with the username and password for this account
    http_proxy="http://yum-user:qwerty@mycache.mydomain.com:3128"
    export http_proxy

See details on <https://www.centos.org/docs/5/html/yum/sn-yum-proxy-server.html> 

# Useful commands

    yum list installed
    yum search ***
    yum localinstall *.rpm
    yum erase ***

# Install `locate` command

    sudo yum install mlocate
    sudo updatedb

See details on <http://askubuntu.com/questions/215503/how-to-install-the-locate-command>

# Update exclude package

    yum update --exclude=PACKAGENAME

See details on <https://access.redhat.com/solutions/10185>

# Enable EPEL Repository

This works on CentOS 7:

    yum install epel-release

If it doesn't work, do it manually:

    wget http://dl.fedoraproject.org/pub/epel/7/x86_64/e/epel-release-7-8.noarch.rpm
    rpm -ivh epel-release-7-8.noarch.rpm

See details on <http://www.tecmint.com/how-to-enable-epel-repository-for-rhel-centos-6-5/>

# Install Google Chrome

* Create `/etc/yum.repos.d/google-chrome.repo` with the following content:

    [google-chrome]
    name=google-chrome
    baseurl=http://dl.google.com/linux/chrome/rpm/stable/$basearch
    enabled=1
    gpgcheck=1
    gpgkey=https://dl-ssl.google.com/linux/linux_signing_key.pub

* Install by yum

    sudo yum install google-chrome-stable

See details on <http://www.tecmint.com/install-google-chrome-on-redhat-centos-fedora-linux/>

# Purge Old Kernels

* Install `yum-utils`.

    yum install yum-utils

* Clean old kernels and only keep two latest kernels.

    package-cleanup --oldkernels --count=2

* To keep fewer kernels automatically edit `/etc/yum.conf` and change `installonly_limit=2`.

See details on <https://www.centos.org/forums/viewtopic.php?t=2120>

# Install Fonts

    sudo yum groupinstall "Fonts"

See details on <https://ask.fedoraproject.org/en/question/7032/how-do-i-install-fonts-in-fedora/>
