# Edit hosts file

    sudo nano /etc/hosts

See details on <http://www.rackspace.com/knowledge_center/article/how-do-i-modify-my-hosts-file> 

# Edit hosts files

    sudo nano /etc/hosts

See details on <http://www.rackspace.com/knowledge_center/article/how-do-i-modify-my-hosts-file> 

# Enable SSH server

    sudo apt-get install openssh-server 
    sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.factory-defaults
    sudo chmod a-w /etc/ssh/sshd_config.factory-defaults
    sudo gedit /etc/ssh/sshd_config
    sudo restart ssh

See details on <https://help.ubuntu.com/community/SSH/OpenSSH/Configuring> 
