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

# Enable VirtualBox host-only adapter in CentOS

* Add a new host-only adapter in VirtualBox
* Enter `/etc/sysconfig/network-scripts`
* Copy `ifcfg-eth0` to `ifcfg-eth1`
* Edit `ifcfg-eth1`
* Reboot

See details on <http://serverfault.com/questions/715369/centos-virtualbox-no-icfg-eth1-when-adding-secondary-network-interface>

# Enable screen sharing on CentOS

* Enable by "Setting -> System -> Sharing -> Screen Sharing"
* Run `gsettings set org.gnome.Vino require-encryption false`. "sudo" is not needed.

See details on <http://unix.stackexchange.com/questions/77885/how-can-i-connect-to-gnome-3-with-a-windows-vnc-client>