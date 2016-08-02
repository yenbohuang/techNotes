# General Console Command Notes

## Decompress files

    tar -vxjf /mnt/mydownloads/archive.tar.bz2
    tar -vxzf /mnt/mydownloads/archive.tar.gz
    unzip archive.zip -d /home/yenbo.huang/folder

See details on:
* <http://logicassembly.com/linux/decompress_tar_dot_gz.htm?ext=bz2>
* <http://askubuntu.com/questions/86849/how-to-unzip-a-zip-file-from-the-terminal>

## Change timezone

    rm /etc/localtime
    ln -s /usr/share/zoneinfo/US/Pacific localtime

See details on <http://www.thegeekstuff.com/2010/09/change-timezone-in-linux/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+TheGeekStuff+%28The+Geek+Stuff%29>

## Generate UUID

    uuidgen

## Calculate MD5

    md5sum <filename>
    echo <string> | md5sum

## Finding files

    locate <filename>
    find <path> -name <filename>
    which <filename>
    whereis <filename>

See details on <https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/4/html/Step_by_Step_Guide/s1-managing-locating.html>

## Running sudo with environment variables

    sudo <key1>=<value1> <key2>=<value2> .... <command>

See details on <http://askubuntu.com/questions/57915/environment-variables-when-run-with-sudo>

## Using systemd

This is an example for docker daemon in `/etc/systemd/system/docker.service.d/override.conf`:

    [Service]
    Environment="CONSUL_HTTP_TOKEN=<ACL token>"
    ExecStart=
    ExecStart=/usr/bin/docker daemon --insecure-registry <url:port> -H fd:// -s overlay

Run the following commands after changes:

    #!/bin/sh
    
    sudo systemctl daemon-reload
    sudo systemctl enable docker
    sudo systemctl start docker

See details on <https://www.freedesktop.org/software/systemd/man/systemd.service.html>

# Logging

## Out message on both console and log file

    some-command | tee -a file

See details on <http://stackoverflow.com/questions/418896/how-to-redirect-output-to-a-file-and-stdout>

## Redirect stderr to stdout

    some-command 2>&1

See details on <http://superuser.com/questions/71428/what-does-21-do-in-command-line>
