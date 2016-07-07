# Edit hosts file

    sudo nano /etc/hosts

See details on <http://www.rackspace.com/knowledge_center/article/how-do-i-modify-my-hosts-file> 

# List all listening port

    netstat -anp

See details on <https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/Security_Guide/s1-server-ports.html>

# Enable SSH server

## Ubuntu
    sudo apt-get install openssh-server 
    sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.factory-defaults
    sudo chmod a-w /etc/ssh/sshd_config.factory-defaults
    sudo gedit /etc/ssh/sshd_config
    sudo restart ssh

See details on <https://help.ubuntu.com/community/SSH/OpenSSH/Configuring>

## CentOS

    sudo service sshd start

See details on <https://lecturesnippets.com/lesson/setting-up-ssh-server-in-centos-7-minimal-install/>

# /etc/resolv.conf

* Add nameserver in this file

    sudo nano /etc/resolvconf/resolv.conf.d/head

* Add search in this file

    sudo nano /etc/resolvconf/resolv.conf.d/tail

* Update

    sudo resolvconf -u

See details on <http://www.lampnode.com/linux/howto-setup-nameserver-on-ubuntu-1404-by-resolvconf/>

# Mounting network drive by samba

    sudo mount -t cifs \
      -o username=${name},password=${pwd},uid=${uid},gid=${gid} \
      ${network path} ${local path}

See details on <http://unix.stackexchange.com/questions/68079/mount-cifs-network-drive-write-permissions-and-chown>

# SCP

```
   scp SourceFile user@host:directory/TargetFile
   scp user@host:directory/SourceFile TargetFile
```

See details on <http://webdev.gmu.edu/uploading-files-with-secure-copy-scp/>.

# Firewall settings

## CentOS

Configure the Firewall Using the Command Line:

```
    sudo lokkit --port=123:udp --update
```

Checking Network Access for Incoming NTP Using the Command Line

```
    sudo less /etc/sysconfig/system-config-firewall
```

See details on <https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/s2-Configure_the_Firewall_Using_the_CLI.html>.