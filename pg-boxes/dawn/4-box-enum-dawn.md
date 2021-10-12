# 4 box enum dawn

```
dawn@dawn:~$ cd /home
dawn@dawn:/home$ ls -la
total 16
drwxr-xr-x  4 root      root      4096 Aug  2  2019 .
drwxr-xr-x 18 root      root      4096 Mar 16  2020 ..
drwxr-xr-x  5 dawn      dawn      4096 Jul 22  2020 dawn
drwxr-xr-x  4 ganimedes ganimedes 4096 Aug  2  2019 ganimedes
```

## SuidEnum

```
[#] SUID Binaries in GTFO bins list (Hell Yeah!)
------------------------------
/usr/bin/zsh -~> https://gtfobins.github.io/gtfobins/zsh/#suid
------------------------------
[$] Please try the command(s) below to exploit harmless SUID bin(s) found !!!
------------------------------
[~] /usr/bin/zsh
------------------------------
```

```
dawn@dawn:~$ sudo -l
Matching Defaults entries for dawn on dawn:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User dawn may run the following commands on dawn:
    (root) NOPASSWD: /usr/bin/mysql
```
