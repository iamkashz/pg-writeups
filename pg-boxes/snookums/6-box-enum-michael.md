# 6 box enum michael

```
$ ssh michael@192.168.144.58
michael@192.168.144.58's password: HockSydneyCertify123

[michael@snookums ~]$ whoami;id;hostname
michael
uid=1000(michael) gid=1000(michael) groups=1000(michael) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
snookums
```

## SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/bin/chage
/usr/bin/crontab
/usr/sbin/unix_chkpwd
/usr/sbin/pam_timestamp_check
/usr/sbin/usernetctl
------------------------------
```

## PEAS

```
═╣ Writable passwd file? ................ /etc/passwd is writable
```
