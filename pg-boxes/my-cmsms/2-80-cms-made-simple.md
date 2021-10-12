# 2 :80 cms made simple

```
http://192.168.131.74/
Landing Page - CMS Made Simple
version 2.2.13

$ gobuster dir -u http://192.168.131.74 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 80
===============================================================
/modules              (Status: 301) [Size: 318] [--> http://192.168.131.74/modules/]
/uploads              (Status: 301) [Size: 318] [--> http://192.168.131.74/uploads/]
/doc                  (Status: 301) [Size: 314] [--> http://192.168.131.74/doc/]
/admin                (Status: 301) [Size: 316] [--> http://192.168.131.74/admin/]
/assets               (Status: 301) [Size: 317] [--> http://192.168.131.74/assets/]
/index.php            (Status: 200) [Size: 19502]
/lib                  (Status: 301) [Size: 314] [--> http://192.168.131.74/lib/]
/config.php           (Status: 200) [Size: 0]
/tmp                  (Status: 301) [Size: 314] [--> http://192.168.131.74/tmp/]
/phpmyadmin           (Status: 401) [Size: 461]
/phpinfo.php          (Status: 200) [Size: 90135]

http://192.168.131.74/modules/
Modules dir-listing

http://192.168.131.74/phpmyadmin/
phpMyAdmin

http://192.168.131.74/phpinfo.php
PHP Version 7.3.14-1~deb10u1
System 	Linux mycmsms 4.19.0-8-amd64 #1 SMP Debian 4.19.98-1 (2020-01-26) x86_64

http://192.168.131.74/admin/login.php
Admin Login Page

# default creds didnt work
root:root
bitnami:bitnami
root:bitnami

```
