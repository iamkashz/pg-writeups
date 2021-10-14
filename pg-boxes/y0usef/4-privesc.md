# 4 privesc

```
yousef@yousef-VirtualBox:~$ sudo -l
[sudo] password for yousef:
Matching Defaults entries for yousef on yousef-VirtualBox:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User yousef may run the following commands on yousef-VirtualBox:
    (ALL : ALL) ALL
	
yousef@yousef-VirtualBox:~$ sudo su
root@yousef-VirtualBox:/home/yousef# whoami;id;hostname
root
uid=0(root) gid=0(root) groups=0(root)
yousef-VirtualBox
```
