# Enable remote desktop services

    netsh firewall set service remotedesktop enable
    netsh firewall set service remoteadmin enable

# Network

## Finding port in use

    netstat -a -b

See details on <http://stackoverflow.com/questions/48198/how-can-you-find-out-which-process-is-listening-on-a-port-on-windows> 

## Find hostname by IP address

    nbtstat -a <IP address>

## Useful ipconfig commands

* Displays the full TCP/IP configuration for all adapters.

    ipconfig /all

* Flushes and resets the contents of the DNS client resolver cache. During DNS troubleshooting, you can use this procedure to discard negative cache entries from the cache, as well as any other entries that have been added dynamically. 

    ipconfig /flushdns

* Sends a DHCPRELEASE message to the DHCP server to release the current DHCP configuration and discard the IP address configuration for either all adapters (if an adapter is not specified) or for a specific adapter if the Adapter parameter is included.

    ipconfig /release

* Renews DHCP configuration for all adapters (if an adapter is not specified) or for a specific adapter if the Adapter parameter is included.

    ipconfig /renew

See details on <https://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/ipconfig.mspx?mfr=true>

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
* Window key + G: Start game bar and record the screen
  * https://www.windowscentral.com/windows-10-game-bar-everything-you-need-know
