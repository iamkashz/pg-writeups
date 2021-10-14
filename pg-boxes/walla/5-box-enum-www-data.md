# 5 box enum www-data

```
user@192.168.125.97 ~$ pwd
/var/www/html/includes

www-data@walla:/var/www/html/includes$ cat config.php
<?php
define('RASPI_BRAND_TEXT', 'RaspAP');
define('RASPI_VERSION', '2.5');
define('RASPI_CONFIG', '/etc/raspap');
define('RASPI_LIGHTTPD_CONFIG', '/etc/lighttpd/lighttpd.conf')


user@walla /home$ ls -la
total 24
drwxr-xr-x  6 root     root     4096 Sep 17  2020 .
drwxr-xr-x 18 root     root     4096 Sep 17  2020 ..
drwxr-xr-x  2 janis    janis    4096 Mar  4 11:41 janis
drwxr-xr-x  2 paige    paige    4096 Sep 17  2020 paige
drwxr-xr-x  2 terry    terry    4096 Sep 17  2020 terry
drwxr-xr-x  2 www-data www-data 4096 Sep 17  2020 walter
```

### PEAS

```
╣ Active Ports
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      -

╣ Users with console
janis:x:1004:1004::/home/janis:/bin/bash
paige:x:1001:1001::/home/paige:/bin/zsh
root:x:0:0:root:/root:/bin/bash
terry:x:1002:1002::/home/terry:/bin/bash
walter:x:1003:1003::/home/walter:/bin/bash

╣ Checking 'sudo -l', /etc/sudoers, and /etc/sudoers.d
╚ https://book.hacktricks.xyz/linux-unix/privilege-escalation#sudo-and-suid
Matching Defaults entries for www-data on walla:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User www-data may run the following commands on walla:
    (ALL) NOPASSWD: /sbin/ifup
    (ALL) NOPASSWD: /usr/bin/python /home/walter/wifi_reset.py
    (ALL) NOPASSWD: /bin/systemctl start hostapd.service
    (ALL) NOPASSWD: /bin/systemctl stop hostapd.service
    (ALL) NOPASSWD: /bin/systemctl start dnsmasq.service
    (ALL) NOPASSWD: /bin/systemctl stop dnsmasq.service
    (ALL) NOPASSWD: /bin/systemctl restart dnsmasq.service
	
╣ Permissions in init, init.d, systemd, and rc.d
╚ https://book.hacktricks.xyz/linux-unix/privilege-escalation#init-init-d-systemd-and-rc-d
You have write privileges over /lib/systemd/system/raspapd.service

╣ Readable files belonging to root and readable by me but not world readable
-rwxr-x--- 1 root www-data 124 Sep 17  2020 /etc/raspap/hostapd/enablelog.sh
-rwxr-x--- 1 root www-data 3113 Sep 17  2020 /etc/raspap/hostapd/servicestart.sh
-rwxr-x--- 1 root www-data 102 Sep 17  2020 /etc/raspap/hostapd/disablelog.sh

╣ Searching specific hashes inside files - less false positives (limit 70)
/etc/raspap/raspap.php:$2y$10$YKIyWAmnQLtiJAy6QgHQ.eCpY4m.HCEbiHaTgN6.acNC6bDElzt.i
/var/www/html/raspap.php:$2y$10$YKIyWAmnQLtiJAy6QgHQ.eCpY4m.HCEbiHaTgN6.acNC6bDElzt.i
```
