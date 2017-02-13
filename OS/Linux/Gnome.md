# Create shortcut on desktop

    gnome-desktop-item-edit Desktop --create-new

See details on <http://askubuntu.com/questions/67925/how-to-create-a-desktop-shortcut-in-unity> 

# Enable screen sharing on CentOS

* Enable by "Setting -> System -> Sharing -> Screen Sharing"
* Run `gsettings set org.gnome.Vino require-encryption false`. "sudo" is not needed.

See details on <http://unix.stackexchange.com/questions/77885/how-can-i-connect-to-gnome-3-with-a-windows-vnc-client>

# How to Get rid of the login keyring password when starting Chrome?

Rename the folder `/home/username/.local/share/keyrings` to `/home/username/.local/share/keyrings.old` then reboot.

See comments in <https://community.linuxmint.com/tutorial/view/916> because `seahorse` is not pre-installed in Cent OS.
