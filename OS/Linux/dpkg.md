# Install package
    sudo dpkg -i DEB_PACKAGE

See details on <http://askubuntu.com/questions/40779/how-do-i-install-a-deb-file-via-the-command-line> 

# List installed packages

    dpkg --get-selections | grep postgres
    dpkg -l

See details on <http://askubuntu.com/questions/17823/how-to-list-all-installed-packages>