# WireShark Wiki

<https://wiki.wireshark.org/>

# Filters

## Show only SMTP (port 25) and ICMP traffic

    tcp.port eq 25 or icmp

## IP source and destination

Show only traffic in the LAN (192.168.x.x), between workstations and servers -- no Internet:

    ip.src==192.168.0.0/16 and ip.dst==192.168.0.0/16

## IP address

    ip.addr == 10.43.54.65
    is equivalent to
    ip.src == 10.43.54.65 or ip.dst == 10.43.54.65

    ip.addr != 10.43.54.65
    which is equivalent to
    ip.src != 10.43.54.65 or ip.dst != 10.43.54.65

## Filter on Windows

Filter out noise, while watching Windows Client - DC exchanges

    smb || nbns || dcerpc || nbss || dns

## URI

Match HTTP requests where the last characters in the uri are the characters "gl=se":

    http.request.uri matches "gl=se$"