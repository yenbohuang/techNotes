# Cent OS

## Install Desktop Environments

Install your favorite desktop environment.

    yum groups install "GNOME Desktop"
    yum groups install "KDE Plasma Workspaces"
    yum --enablerepo=epel groups install "MATE Desktop"
    yum --enablerepo=epel groups install "Xfce"

Logout and choose the desktop environment by "options icon" before you login CentOS 7.

See details on <http://unix.stackexchange.com/questions/181503/how-to-install-desktop-environments-on-centos-7>

## Install GNOME desktop to CentOS console-only image

Install minimal required packages:

    sudo yum groupinstall "X Window System"
    sudo yum install gnome-classic-session gnome-terminal nautilus-open-terminal control-center liberation-mono-fonts

Or, install full desktop packages:

    sudo yum groups install "GNOME Desktop"

Set default target to desktop environment. 

    sudo systemctl set-default graphical.target

If this command is not supported, edit `/etc/inittab`:

    id:5:initdefault:

Shutdown VM.

Setting VM by VirtualBox Manager:
* Add optical drive in "Storage".
* Set "Shared Clipboard" to "Bidirectional" in "General -> Advanced". 

Start VM.

Insert guest additions CD image.

Install VirtualBox addon. If this process failed due to missing packages, install pre-required packages for VirtualBox addons. Kernel version may very depending on OS versions. 
```
sudo yum install kernel-devel-3.10.0-327.el7.x86_64
sudo yum install gcc
```
Restart VM. 

See <https://www.centos.org/forums/viewtopic.php?t=47088> for details.

## Install xRDP
```
sudo yum install xrdp tigervnc-server
sudo systemctl start xrdp.service
sudo netstat -antup | grep xrdp
sudo systemctl enable xrdp.service
```
See <http://www.itzgeek.com/how-tos/linux/centos-how-tos/install-xrdp-on-centos-7-rhel-7.html> for details.

### Enable xfce for xRDP

* Create `~/.Xclients` with the following content:
```
#!/bin/bash
XFCE="$(which xfce4-session 2>/dev/null)"
exec "$XFCE"
```
* Make it executable and restart xRDP.
```
chmod 755 ~/.Xclients
sudo service xrdp restart
```
See <https://www.centos.org/forums/viewtopic.php?t=51046> for details.

### Reuse the same session
```
echo xfce4-session > .xsession
sudo service xrdp restart
```
See <http://c-nergy.be/blog/?p=6046> for details.

# Ubuntu

## Install GNOME desktop on Ununtu
```
sudo apt-get install ubuntu-gnome-desktop
```
See details on <https://wiki.ubuntu.com/UbuntuGNOME/Installation> 

## Switch to GNOME from Unity
	
* Install GNOME
* Choose session when login

See details on <http://askubuntu.com/questions/450294/how-to-switch-from-unity-to-gnome>

## Install Xfce desktop
```
sudo apt-get install -y xfce4 xfce4-goodies
```
See details on <https://www.liquidweb.com/kb/install-xfce-desktop-environment-on-ubuntu-16-04/>

## Install xrdp

You will see a blank screen if you only install xrdp. After some searches on google, modifying "startwm.sh" does not work but this works for me.

```
sudo apt install xrdp xserver-xorg-core xorgxrdp
echo xfce4-session > .xsession
sudo service xrdp restart
```
See the followings for details:
* <https://ubuntuforums.org/showthread.php?t=2413157>
* <http://c-nergy.be/blog/?p=6046>
