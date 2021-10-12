# 8 box enum www-data

```
www-data@APEX:/var/www/openemr/interface/main$ ls -la /home
total 12
drwxr-xr-x  3 root  root  4096 May 17 10:54 .
drwxr-xr-x 23 root  root  4096 May 17 10:50 ..
drwxr-xr-x  2 white white 4096 May 17 10:59 white
```

## PEAS

```
╣ Active Ports
╚ https://book.hacktricks.xyz/linux-unix/privilege-escalation#open-ports
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      -

╣ Users with console
root:x:0:0:root:/root:/bin/bash
white:x:1000:1000::/home/white:/bin/sh

╣ Analyzing CouchDB Files (limit 70)
drwxrwxr-x 3 root root 4096 May 17 10:55 /var/www/openemr/vendor/doctrine/couchdb

╣ Searching specific hashes inside files - less false positives (limit 70)
/var/www/openemr/vendor/ircmaxell/password-compat/lib/password.php:$2y$04$usesomesillystringfore7hnbRJHxXVLeakoG8K30oukPsA.ztMG

$ hashcat -m 3200 hash /usr/share/wordlists/rockyou.txt --show
$2y$04$usesomesillystringfore7hnbRJHxXVLeakoG8K30oukPsA.ztMG:password
```

Nothing via pspy
