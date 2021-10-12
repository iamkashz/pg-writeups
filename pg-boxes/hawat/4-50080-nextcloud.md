# 4 :50080 nextcloud

```
http://192.168.136.147:50080/
Pizza Site | landing Page

| http-enum:
|   /4/: Potentially interesting folder w/ directory listing
|   /icons/: Potentially interesting folder w/ directory listing
|_  /images/: Potentially interesting folder w/ directory listing

http://192.168.136.147:50080/4/
# file w3.css
# just css data

$ gobuster dir -u http://192.168.136.147:50080/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 90
===============================================================
/images               (Status: 301) [Size: 244] [--> http://192.168.136.147:50080/images/]
/4                    (Status: 301) [Size: 239] [--> http://192.168.136.147:50080/4/]
/index.html           (Status: 200) [Size: 9088]
/cloud                (Status: 301) [Size: 243] [--> http://192.168.136.147:50080/cloud/]

192.168.136.147:50080/cloud > http://192.168.136.147:50080/cloud/index.php/login
Nextcloud Login Page

# default creds admin:admin work
http://192.168.136.147:50080/cloud/index.php/apps/dashboard/

# language is not english
# fix: icon-click on top, Settings > Language > English > Save

# enumerating Nextcloud
http://192.168.136.147:50080/cloud/index.php/settings/user
# Under Settings > (left) Administration >

# version check
Overview 
http://192.168.136.147:50080/cloud/index.php/settings/admin/overview
Nextcloud 20.0.7

# System information
Support > Generate System Report
Operating system: Linux 5.10.14-arch1-1 #1 SMP PREEMPT Sun, 07 Feb 2021 22:42:17 +0000 x86_64
Webserver: Apache/2.4.46 (Unix) PHP/7.4.15 (apache2handler)
Database: mysql 10.5.8
PHP version: 7.4.1
Nextcloud version: 20.0.7 - 20.0.7.1
Configuration (config/config.php)

# looking at FileManager (top)
http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/
# shows all files
(bottom-left) > Settings > WebDAV link
```
