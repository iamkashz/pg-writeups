# 5 box enum www-data

```
# config file paths
- config.php
- /zp-data/zp-config.php
- /zp-core/zp-config.php

zenphoto-shell# cat /var/www/test/zp-data/zp-config.php

$conf['db_software'] = 'MySQL';
$conf['mysql_user'] = 'root';           // Supply your Database user id.
$conf['mysql_pass'] = 'hola';           // Supply your Database password.
$conf['mysql_host'] = 'localhost';  // Supply the name of your Database server.
$conf['mysql_database'] = 'zenphoto';       // Supply the name of Zenphoto's database

www-data@offsecsrv:/var/www$ mysql -u root -p
Enter password: hola
Server version: 5.1.41-3ubuntu12.10 (Ubuntu)

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| zenphoto           |
+--------------------+
3 rows in set (0.00 sec)

mysql> select user, pass from zp_administrators;
+----------------+------------------------------------------+
| user           | pass                                     |
+----------------+------------------------------------------+
| administrators | NULL                                     |
| viewers        | NULL                                     |
| bozos          | NULL                                     |
| album managers | NULL                                     |
| default        | NULL                                     |
| newuser        | NULL                                     |
| admin          | 63e5c2e178e611b692b526f8b6332317f2ff5513 |
+----------------+------------------------------------------+
# not crackable

www-data@offsecsrv:/opt$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
[truncated]
www-data:x:33:33:www-data:/var/www:/bin/sh
saned:x:112:118::/home/saned:/bin/false
```

### SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/bin/lppasswd
/usr/bin/mtr
/usr/bin/X
/usr/bin/sudoedit
/usr/lib/pt_chown
/usr/sbin/uuidd
------------------------------
```

### PEAS

```
╣ Operative system
Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010
Description:    Ubuntu 10.04.3 LTS

╣ Sudo version
Sudo version 1.7.2p1
```
