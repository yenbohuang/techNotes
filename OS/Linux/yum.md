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

```
    yum list installed
    yum search ***
    yum localinstall *.rpm
```