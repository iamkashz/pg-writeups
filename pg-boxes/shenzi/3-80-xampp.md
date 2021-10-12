# 3 :80 xampp

```
http://192.168.99.55/dashboard/
XAMPP Splash Page (XAMPP for Windows 7.4.6)

$ gobuster dir -u http://192.168.99.55 -w /usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt -x php,html,txt -t 70
===============================================================
2021/08/12 16:04:21 Starting gobuster in directory enumeration mode
===============================================================
/img                  (Status: 301) [Size: 336] [--> http://192.168.99.55/img/]
/applications.html    (Status: 200) [Size: 3607]
/examples             (Status: 503) [Size: 1059]
/index.php            (Status: 302) [Size: 0] [--> http://192.168.99.55/dashboard/]
/licenses             (Status: 403) [Size: 1204]
/dashboard            (Status: 301) [Size: 342] [--> http://192.168.99.55/dashboard/]
/phpmyadmin           (Status: 403) [Size: 1204]
/webalizer            (Status: 403) [Size: 1045]

http://192.168.99.55/dashboard/phpinfo.php
PHP Version 7.4.6
System 	Windows NT SHENZI 10.0 build 18363 (Windows 10) AMD64 
Architecture 	x64
Loaded Configuration File 	C:\xampp\php\php.ini 

http://192.168.99.55/phpmyadmin/
Access forbidden!
postmaster@localhost
```
