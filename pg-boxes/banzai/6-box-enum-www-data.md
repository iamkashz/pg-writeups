# 6 box enum www-data

```
www-data@banzai:/var/www$ cat config.php
<?php
define('DBHOST', '127.0.0.1');
define('DBUSER', 'root');
define('DBPASS', 'EscalateRaftHubris123');
define('DBNAME', 'main');
?>

www-data@banzai:/home/banzai$ mysql -u root -p
Enter password:

mysql> SELECT @@version;
+-----------+
| @@version |
+-----------+
| 5.7.30    |
+-----------+
1 row in set (0.00 sec)
# nothing in mysql

www-data@banzai:/var/www$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
[truncated]
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
banzai:x:1000:1000:Banzai,,,:/home/banzai:/bin/bash
admin:x:1001:1001::/var/www/html/:
ftp:x:108:113:ftp daemon,,,:/srv/ftp:/bin/false
mysql:x:109:114:MySQL Server,,,:/var/lib/mysql:/bin/false
postfix:x:110:115::/var/spool/postfix:/bin/false
postgres:x:111:117:PostgreSQL administrator,,,:/var/lib/postgresql:/bin/bash

www-data@banzai:/home/banzai$ cat index.php
<!--
Silence is golden.-->
<h1>Welcome to Banzai WordPress Site...</h1>
# this is probably on 8080
```

## PEAS

```
Linux version 4.9.0-12-amd64 (debian-kernel@lists.debian.org) (gcc version 6.3.0 20170516 (Debian 6.3.0-18+deb9u1) ) #1 SMP Debian 4.9.210-1 (2020-01-20)
Description:    Debian GNU/Linux 9.12 (stretch)

╣ Sudo version
Sudo version 1.8.19p1

/etc/mysql/mysql.conf.d/mysqld.cnf
/etc/postgresql/9.6/main/pg_hba.conf
/etc/postgresql/9.6/main/postgresql.conf
```

## LSE

```
================================================================( network )=====
[*] net000 Services listening only on localhost............................ yes!
```
