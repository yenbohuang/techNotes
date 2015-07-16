# Edit hosts file

    sudo nano /etc/hosts

See details on <http://www.rackspace.com/knowledge_center/article/how-do-i-modify-my-hosts-file> 

# List all listening port

    netstat -anp

See details on <https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/Security_Guide/s1-server-ports.html>

# Enable SSH server

    sudo apt-get install openssh-server 
    sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.factory-defaults
    sudo chmod a-w /etc/ssh/sshd_config.factory-defaults
    sudo gedit /etc/ssh/sshd_config
    sudo restart ssh

See details on <https://help.ubuntu.com/community/SSH/OpenSSH/Configuring> 
