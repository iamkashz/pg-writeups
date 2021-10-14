# 4 box enum www-data

```
www-data@tre:/var/www/html$ ls -la
total 748
drwxr-xr-x  5 www-data www-data   4096 May 12  2020 .
drwxr-xr-x  3 root     root       4096 May 12  2020 ..
-rw-r--r--  1 root     root     489307 May 12  2020 adminer.php
drwxr-xr-x  9 www-data www-data   4096 May 12  2020 cms
-rw-r--r--  1 www-data www-data 227984 Oct 24  2017 file.jpg
-rw-r--r--  1 www-data www-data    164 May 12  2020 index.html
-rw-r--r--  1 root     root         20 May 12  2020 info.php
drwxr-xr-x 16 www-data www-data  12288 Apr  1  2017 mantisbt
drwxr-xr-x 16 root     root      12288 May 12  2020 systeml

# /tmp
www-data@tre:/tmp$ ls -la
total 12
drwxrwxrwt  2 root	LP     root     4096 Aug 17 14:00 .
drwxr-xr-x 18 root     root     4096 Jul  7  2020 ..
-rw-rw----  1 www-data www-data  401 Aug 17 14:00 adminer.version
www-data@tre:/tmp$ cat adminer.version
a:2:{s:9:"signature";s:344:"GiPxUGEMmriNQOjeQZec/6XaQqiYCO7N5hML0GeG3WSri0ByL/ywzAnVKn28JvqZw78+N1eenJr4UpColdxbOvHaHcTz8OpNOQ9cU6HclcIWtHW/6wZdRosM5xZGbMM3fdwFcQQia5+Y2kz5QLdcGl2szCiIAhjGuUdJeu1Hgg5o5ZtSV0i9A/IlZpRb6GAqjSqHtR0mamVNvVj6FDGLiJ47bcS3Qr+9MsUDYuqMlEWZotMHIyDJ8AoN4ory2uPAfMEvzuBFzU+1/3JPiY9jdcJnRdlTi6Xj/95zmHnqt0CBxqoxIzsBuHz3yqwptObWc608MzUCOyQRhkKG1IX8jQ==";s:7:"version";s:5:"4.8.1";}www-data@tre:/tmp$

# /config
www-data@tre:/var/www/html/system/config$ ls -la
total 68
drwxr-xr-x  2 root root  4096 May 12  2020 .
drwxr-xr-x 16 root root 12288 May 12  2020 ..
-rw-r--r--  1 root root   190 May 12  2020 .htaccess
-rw-r--r--  1 root root   309 May 12  2020 Web.config
-rw-r--r--  1 root root  3411 May 12  2020 a.txt
-rw-r--r--  1 root root   338 May 12  2020 config_inc.php
-rw-r--r--  1 root root  3354 May 12  2020 config_inc.php.sample
-rw-r--r--  1 root root 31123 May 12  2020 data.sql

www-data@tre:/var/www/html/system/config$ cat config_inc.php
<?php
$g_hostname               = 'localhost';
$g_db_type                = 'mysqli';
$g_database_name          = 'mantis';
$g_db_username            = 'mantissuser';
$g_db_password            = 'password@123AS';
$g_default_timezone       = 'America/New_York';
$g_crypto_master_salt     = 'uuvODlMDm11FeEgAJ5Fqo9Nmswufd5ELmgJkEuQGvGA=';

# we know we have adminer.php and can use these creds to access localhost db
http://192.168.214.84/adminer.php
Login Page > creds work
# db: mantis |table: mantis_user_table
realname | email | password | cookie_string
administrator | root@localhost | 5a1bcf797d654174aa5f3dba8ec0170c | 8TjkrfD-9O_JNGrVnCMTEtdBdaVpRN4DY3WqJgCFI4wELvI6yzCiNw_epcGei4Ev
Tr3@123456A! | tre@localhost | 64c4685f8da5c2225de7890c1bad0d7f | bp9uP3SY4tyKMFHSytb2RyecV5fPrsvGjb4sLboLkoyodEPn0NbZID9GhRURGAvf
```

#### PEAS

```
╣ MySQL version
mysql  Ver 15.1 Distrib 10.3.22-MariaDB, for debian-linux-gnu (x86_64) using readline 5.2
lrwxrwxrwx 1 root root 22 May 12  2020 /etc/alternatives/my.cnf -> /etc/mysql/mariadb.cnf
lrwxrwxrwx 1 root root 24 May 12  2020 /etc/mysql/my.cnf -> /etc/alternatives/my.cnf

drwxr-xr-x 2 root root 4096 May 12  2020 /etc/apache2/sites-enabled
lrwxrwxrwx 1 root root 35 May 12  2020 /etc/apache2/sites-enabled/000-default.conf -> ../sites-available/000-default.conf

╣ Analyzing Htpasswd Files (limit 70)
-rw-r--r-- 1 root root 44 May 12  2020 /etc/apache2/.htpasswd
admin:$apr1$klmM2diE$hD.osekk3Zh3yho7NZlV50
# cracked => admin:admin

╣ Analyzing Backup Manager Files (limit 70)
-rwxr-xr-x 1 root root 12591 Mar  5  2020 /var/www/html/cms/core/inc/bigtree/apis/storage.php

╣ Analyzing Interesting logs Files (limit 70)
-rw-r----- 1 www-data adm 3062558 Aug 17 13:08 /var/log/nginx/access.log
-rw-r----- 1 www-data adm 0 Sep  3  2020 /var/log/nginx/error.log

Files with capabilities (limited to 50):
/usr/bin/ping = cap_net_raw+ep
```

#### LSE.sh

```
[*] ret020 Cron jobs....................................................... yes!
[*] pro020 Processes running with root permissions......................... yes!
[*] pro030 Processes running by non-root users with shell.................. yes!
```
