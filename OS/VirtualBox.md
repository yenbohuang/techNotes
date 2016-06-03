# Port forward

Add another port forward to virtualbox with:

Host IP 127.0.0.1 Host Port 2222 Guest IP 10.0.2.15 Guest port 22
Then ssh to port 2222 on 127.0.0.1
Rinse and repeat for any other ports required, remembering that the port cannot be <1024 on the host side.

See detail on <http://superuser.com/questions/738462/accessing-virtualbox-with-nat-adapter-using-ssh> 

# Mounting share folders

    sudo mount -t vboxsf share ~/host

See details on <https://forums.virtualbox.org/viewtopic.php?t=15868> 

# Fix resolution issue

    sudo apt-get install virtualbox-guest-utils virtualbox-guest-x11 virtualbox-guest-dkms

See details on <http://askubuntu.com/questions/73589/higher-screen-resolution-for-virtualbox>

# Fix add on issue for CentOS 7

Install the following packages before installing add on:

    sudo yum install kernel-devel
    sudo yum install gcc

# Cannot use host-only adapter after VirtualBox update

Delete/re-add "VirtualBox Host-Only Ethernet Adapter":

* File -> Preferences -> Network -> Host-only Networks
* Edit details
* For "Adapter" tab

    IPv4 Address: 192.168.56.1
    IPv4 Network Mask: 255.255.255.0

* For "DHCP Server" tab

    Enable Server: checked
    Server Address: 192.168.56.100
    Server Mask: 255.255.255.0
    Lower Address Bound: 192.168.56.101
    Upper Address Bound: 192.168.56.254