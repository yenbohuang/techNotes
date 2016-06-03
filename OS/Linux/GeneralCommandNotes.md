# General Console Command Notes

## Check Ubuntu version

```
   lsb_release -a
```

## Decompress files

```
   tar -vxjf /mnt/mydownloads/archive.tar.bz2
   tar -vxzf /mnt/mydownloads/archive.tar.gz
   unzip archive.zip -d /home/yenbo.huang/folder
```

See details on:
* <http://logicassembly.com/linux/decompress_tar_dot_gz.htm?ext=bz2>
* <http://askubuntu.com/questions/86849/how-to-unzip-a-zip-file-from-the-terminal>

## Change timezone

```
   rm /etc/localtime
   ln -s /usr/share/zoneinfo/US/Pacific localtime
```

See details on <http://www.thegeekstuff.com/2010/09/change-timezone-in-linux/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+TheGeekStuff+%28The+Geek+Stuff%29>

# Logging

## Out message on both console and log file

```
   some-command | tee -a file
```

See details on <http://stackoverflow.com/questions/418896/how-to-redirect-output-to-a-file-and-stdout>

## Redirect stderr to stdout

```
   some-command 2>&1
```

See details on <http://superuser.com/questions/71428/what-does-21-do-in-command-line>
