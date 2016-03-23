# General Console Command Notes

## Check Ubuntu version

```
   lsb_release -a
```
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

## Decompress files

```
   tar -vxjf /mnt/mydownloads/archive.tar.bz2
   tar -vxzf /mnt/mydownloads/archive.tar.gz
```

See details on <http://logicassembly.com/linux/decompress_tar_dot_gz.htm?ext=bz2>