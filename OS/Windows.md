# Enable remote desktop services

    netsh firewall set service remotedesktop enable
    netsh firewall set service remoteadmin enable

# Network

## Finding port in use

    netstat -a -b

See details on <http://stackoverflow.com/questions/48198/how-can-you-find-out-which-process-is-listening-on-a-port-on-windows> 

## Find hostname by IP address

    nbtstat -a <IP address>

# Lock screen by command line

    C:\Windows\System32\rundll32.exe user32.dll,LockWorkStation

See details on <http://superuser.com/questions/838810/how-to-lock-screen-from-command-line-in-windows-8-1>

# Disabling startup programs

    msconfig

See details on <https://kb.wisc.edu/helpdesk/page.php?id=1868>

# Shortcuts

* Window key + P: Switch screen
* Window key + L: Lock computer
* Window key + D: Show desktop
