# Create shortcut on desktop

    gnome-desktop-item-edit Desktop --create-new

See details on <http://askubuntu.com/questions/67925/how-to-create-a-desktop-shortcut-in-unity> 

# Install desktop to console-only image

Install desktop package.

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

    sudo yum install kernel-devel-3.10.0-327.el7.x86_64
    sudo yum install gcc

Restart VM. 