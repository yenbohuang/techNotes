# Add user to group

    usermod -a -G ftp tony

See details on <http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/>

# Add sudoers

Edit `/etc/sudoers` and add this line under root account.

    your_name        ALL=(ALL)       ALL

See details on <https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux_OpenStack_Platform/2/html/Getting_Started_Guide/ch02s03.html> 

# Checking uid and gid

    id -u username
    id -g username

See details on <https://kb.iu.edu/d/adwf>