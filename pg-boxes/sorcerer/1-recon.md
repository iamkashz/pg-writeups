# 1 recon

```
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey:
|   2048 81:2a:42:24:b5:90:a1:ce:9b:ac:e7:4e:1d:6d:b4:c6 (RSA)
|   256 d0:73:2a:05:52:7f:89:09:37:76:e3:56:c8:ab:20:99 (ECDSA)
|_  256 3a:2d:de:33:b0:1e:f2:35:0f:8d:c8:d7:8f:f9:e0:0e (ED25519)
80/tcp   open  http    nginx
|_http-title: Site doesn't have a title (text/html).
111/tcp  open  rpcbind 2-4 (RPC #100000)
| rpcinfo:
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100003  3           2049/udp   nfs
|   100003  3,4         2049/tcp   nfs
|   100005  1,2,3      45519/tcp   mountd
|   100005  1,2,3      50443/udp   mountd
|   100021  1,3,4      43329/tcp   nlockmgr
|   100021  1,3,4      50121/udp   nlockmgr
|   100227  3           2049/tcp   nfs_acl
|_  100227  3           2049/udp   nfs_acl
2049/tcp open  nfs_acl 3 (RPC #100227)
8080/tcp open  http    Apache Tomcat 7.0.4
|_http-favicon: Apache Tomcat
|_http-title: Apache Tomcat/7.0.4
7742/tcp  open  http     nginx
|_http-title: SORCERER
| http-enum:
|   /default/: Potentially interesting folder
|_  /zipfiles/: Potentially interesting folder w/ directory listing
43329/tcp open  nlockmgr 1-4 (RPC #100021)
45519/tcp open  mountd   1-3 (RPC #100005)
54375/tcp open  mountd   1-3 (RPC #100005)
55683/tcp open  mountd   1-3 (RPC #100005)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```
