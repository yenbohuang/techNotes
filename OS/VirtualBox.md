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