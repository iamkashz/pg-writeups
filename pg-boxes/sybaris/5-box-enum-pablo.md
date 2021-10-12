# 5 box enum pablo

```
[pablo@sybaris html]$ grep -rnw . -ie password --color=always 2>/dev/null
./config/users/pablo.ini
[pablo@sybaris users]$ cat pablo.ini
password = PostureAlienateArson345
role = admin

# pablo user:pass identified.
pablo:PostureAlienateArson345 
```

## LSE

```
[*] fst130 Does 'pablo' have mail?......................................... yes!

[!] ret060 Can we write to executable paths present in cron jobs........... yes!
---
/etc/crontab:LD_LIBRARY_PATH=/usr/lib:/usr/lib64:/usr/local/lib/dev:/usr/local/lib/utils
---
[*] net000 Services listening only on localhost............................ yes!
```

## PEAS

```
OS: Linux version 3.10.0-1127.19.1.el7.x86_64

╣ Cron jobs
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
LD_LIBRARY_PATH=/usr/lib:/usr/lib64:/usr/local/lib/dev:/usr/local/lib/utils
MAILTO=""

*  *  *  *  * root       /usr/bin/log-sweeper

tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      -

╣ Active Ports
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      -

╣ Mails (limit 50)
963780    0 -rw-rw----   1 pablo    mail            0 Sep  4  2020 /var/mail/pablo
963780    0 -rw-rw----   1 pablo    mail            0 Sep  4  2020 /var/spool/mail/pablo

╣ Searching specific hashes inside files - less false positives (limit 70)
/var/www/html/system/vendor/ircmaxell/password-compat/lib/password.php
```
