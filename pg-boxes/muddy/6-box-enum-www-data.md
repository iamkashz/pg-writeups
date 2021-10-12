# 6 box enum www-data

```
www-data@muddy:/var/www/html$ cat wp-config.php
<?php
define( 'DB_NAME', 'wp' );
define( 'DB_USER', 'wpadmin' );
define( 'DB_PASSWORD', 'ec99e2a005aa8cf0550ddfbdcde11141' );
define( 'DB_HOST', 'localhost' );

# mysql creds not working

www-data@muddy:/home$ ls -la
total 12
drwxr-xr-x  3 root root 4096 Mar 29 09:13 .
drwxr-xr-x 18 root root 4096 Mar 29 09:07 ..
drwxr-xr-x  2 ian  ian  4096 Mar 29 09:16 ian
```

## PEAS

```
╣ Cron jobs
SHELL=/bin/sh
PATH=/dev/shm:/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

* * * * *   root    netstat -tlpn > /root/status && service apache2 status >> /root/status && service mysql status >> /root/status
@reboot /usr/local/bin/ladon-2.7-ctl testserve /var/tmp/ladon/muddy.py -p 8000

╣ Analyzing Wordpress Files (limit 70)
-rw-r--r-- 1 root root 3296 Mar 20 16:17 /var/www/html/wp-config.php
define( 'DB_NAME', 'wp' );
define( 'DB_USER', 'wpadmin' );
define( 'DB_PASSWORD', 'ec99e2a005aa8cf0550ddfbdcde11141' );
define( 'DB_HOST', 'localhost' );

╣ Searching specific hashes inside files - less false positives (limit 70)
/etc/apache2/passwd.dav:$apr1$GUG1OnCu$uiSLaAQojCm14lPMwISDi0
/var/www/html/webdav/passwd.dav:$apr1$GUG1OnCu$uiSLaAQojCm14lPMwISDi0
```
