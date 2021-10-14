# 4 box enum www-data

```
www-data@zino:/var/www/html/booked/config$ ls -la
total 60
drwxrwxrwx  2 www-data www-data  4096 Apr 28  2020 .
drwxrwxrwx 17 www-data www-data  4096 Apr 28  2020 ..
-rw-rw-rw-  1 www-data www-data 13250 Feb  5  2019 config.dist.php
-rw-r--r--  1 www-data www-data 13255 Aug 23 14:54 config.php
-rw-rw-rw-  1 www-data www-data     0 Feb  5  2019 index.html
-rw-rw-rw-  1 www-data www-data   979 Feb  5  2019 log4php.config.dist.xml
-rw-rw-rw-  1 www-data www-data 14410 Feb  5  2019 timezones.php

$ cat config.php
$conf['settings']['database']['type'] = 'mysql';
$conf['settings']['database']['user'] = 'booked_user';        // database user with permission to the booked database
$conf['settings']['database']['password'] = 'RoachSmallDudgeon368';
$conf['settings']['database']['hostspec'] = '127.0.0.1';        // ip, dns or named pipe
$conf['settings']['database']['name'] = 'bookedscheduler';

# mysql enum
www-data@zino:/tmp$ mysql -u booked_user -p
Enter password: RoachSmallDudgeon368

MariaDB [(none)]> show databases;
+--------------------+
| Database           |
+--------------------+
| bookedscheduler    |
| information_schema |
| mysql              |
| performance_schema |
+--------------------+

MariaDB [bookedscheduler]> select username, password from users;
+----------+------------------------------------------+
| username | password                                 |
+----------+------------------------------------------+
| admin    | 979b3db10cd396e6886cda954958040910e6a670 |
+----------+------------------------------------------+
# its admin:adminadmin 
# thats how we logged in.
```

## PEAS

```
╣ Cron jobs
*/3 *   * * *   root    python /var/www/html/booked/cleanup.py

╣ Users with console
peter:x:1000:1000:peter,,,:/home/peter:/bin/bash
root:x:0:0:root:/root:/bin/bash
```
