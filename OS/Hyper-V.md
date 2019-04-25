* Download Ubuntu LTS version which is more stable.
* Follow this blog and create VM
  * <https://www.windowscentral.com/how-run-linux-distros-windows-10-using-hyper-v>
  * Enable "Virtualization Technology" and "Hardware Enforced Data Execution Prevention" on BIOS.
  * Check pre-requirement by `systeminfo.exe`
  * Enable Hyper-V by "Programs and Features" on Windows setting.
  * Create virtual switch.
  * Create Generation 1 VM (I don't know how to work on Gen 2 yet.)
  * Disable secure boot.
  * Add both Internal Virtual Switch and External Virtual Switch
* After install
  * Ubuntu
    * Disable Wayland <https://askubuntu.com/questions/1085296/ubuntu-18-10-cosmic-not-starting-gnome-session-on-bootup>
      * Press "Ctrl + Alt + F2" and login
      * `sudo vi /etc/gdm3/custom.conf`
      * Uncomment "#WaylandEnable=false"
    * Change resolution <https://metinsaylan.com/8991/how-to-change-screen-resolution-on-ubuntu-18-04-in-hyper-v/>
      * `sudo nano /etc/default/grub`
      * Append "video=hyperv_fb:1920x1080"
        * `GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video=hyperv_fb:1920x1080"`
      * `sudo update-grub`
      * Reboot
    * Set IP in eth1
      * Use `ipconfig` under Windows and check "Ethernet adaptor vEthernet".
      * Manual assign IPv4 address in Ubuntu. For example, if IP is "169.254.141.53" for Windows, assign "169.254.141.53" for Ubuntu.
      * Assign the same subnet mask. For example, "255.255.0.0".
    * Enable sshd.
  * (Optional) Run Hyper-V Linux Guest VM Enhancements
    * <https://github.com/Microsoft/linux-vm-tools>