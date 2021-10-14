# 1 recon

```
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey:
|   2048 74:ba:20:23:89:92:62:02:9f:e7:3d:3b:83:d4:d9:6c (RSA)
|   256 54:8f:79:55:5a:b0:3a:69:5a:d5:72:39:64:fd:07:4e (ECDSA)
|_  256 7f:5d:10:27:62:ba:75:e9:bc:c8:4f:e2:72:87:d4:e2 (ED25519)
80/tcp   open  http    Apache httpd 2.4.38 ((Debian))
| http-git:
|   192.168.136.109:80/.git/
|     Git repository found!
|     Repository description: Unnamed repository; edit this file 'description' to name the...
|     Remotes:
|       https://github.com/ColorlibHQ/AdminLTE.git
|_    Project type: Ruby on Rails web application (guessed from .gitignore)
|_http-server-header: Apache/2.4.38 (Debian)
|_http-title: AdminLTE 3 | Dashboard
| http-enum:
|   /.gitignore: Revision control ignore file
|   /.git/HEAD: Git folder
|   /db/: BlogWorx Database
|   /db/: Potentially interesting folder
|   /demo/: Potentially interesting directory w/ listing on 'apache/2.4.38 (debian)'
|   /docs/: Potentially interesting directory w/ listing on 'apache/2.4.38 (debian)'
|_  /pages/: Potentially interesting directory w/ listing on 'apache/2.4.38 (debian)'
| http-git:
|   192.168.136.109:80/.git/
|     Git repository found!
|     Repository description: Unnamed repository; edit this file 'description' to name the...
|     Remotes:
|       https://github.com/ColorlibHQ/AdminLTE.git
|_    Project type: Ruby on Rails web application (guessed from .gitignore)
111/tcp  open  rpcbind 2-4 (RPC #100000)
| rpcinfo:
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|   100000  3,4          111/udp6  rpcbind
|   100003  3           2049/udp   nfs
|   100003  3           2049/udp6  nfs
|   100003  3,4         2049/tcp   nfs
|   100003  3,4         2049/tcp6  nfs
|   100005  1,2,3      33711/tcp6  mountd
|   100005  1,2,3      36397/udp6  mountd
|   100005  1,2,3      36931/tcp   mountd
|   100005  1,2,3      50807/udp   mountd
|   100021  1,3,4      36090/udp   nlockmgr
|   100021  1,3,4      43185/tcp6  nlockmgr
|   100021  1,3,4      44931/tcp   nlockmgr
|   100021  1,3,4      53490/udp6  nlockmgr
|   100227  3           2049/tcp   nfs_acl
|   100227  3           2049/tcp6  nfs_acl
|   100227  3           2049/udp   nfs_acl
|_  100227  3           2049/udp6  nfs_acl
2049/tcp open  nfs_acl 3 (RPC #100227)
36931/tcp open  mountd   1-3 (RPC #100005)
44931/tcp open  nlockmgr 1-4 (RPC #100021)
45359/tcp open  mountd   1-3 (RPC #100005)
55419/tcp open  mountd   1-3 (RPC #100005)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```
