# Install Gnome

    sudo apt-get install ubuntu-gnome-desktop

See details on <https://wiki.ubuntu.com/UbuntuGNOME/Installation> 

# Search new package

    apt-cache search <search_term>

See details on <https://help.ubuntu.com/community/AptGet/Howto>

# Not enough free disk space for "\boot"

1. Check disk space by `df -h`
2. Check kernel images by `dpkg -l | grep linux-image`
3. Check current kernel by `uname -r`
4. Clean other kernel by `sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic`

  * Do not include current kernel
  * Do not include target kernel
  * Keep at least one old kernel

See details on <http://askubuntu.com/questions/298487/not-enough-free-disk-space-when-upgrading> 

# Upgrade Ubuntu

    sudo apt-get update
    sudo apt-get full-upgrade

See details on <http://askubuntu.com/questions/81585/what-is-dist-upgrade-and-why-does-it-upgrade-more-than-upgrade>