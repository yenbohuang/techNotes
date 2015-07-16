# Enable remote desktop services

    netsh firewall set service remotedesktop enable
    netsh firewall set service remoteadmin enable

# Finding port in use

    netstat -a -b

See details on <http://stackoverflow.com/questions/48198/how-can-you-find-out-which-process-is-listening-on-a-port-on-windows> 
