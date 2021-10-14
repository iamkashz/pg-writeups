# 1 recon

```
22/tcp   open  ssh        OpenSSH 7.4p1 Debian 10+deb9u7 (protocol 2.0)
| ssh-hostkey:
|   2048 09:80:39:ef:3f:61:a8:d9:e6:fb:04:94:23:c9:ef:a8 (RSA)
|   256 83:f8:6f:50:7a:62:05:aa:15:44:10:f5:4a:c2:f5:a6 (ECDSA)
|_  256 1e:2b:13:30:5c:f1:31:15:b4:e8:f3:d2:c4:e8:05:b5 (ED25519)
80/tcp   open  http       nginx 1.10.3
|_http-server-header: nginx/1.10.3
|_http-title: Welcome to nginx!
8080/tcp open  http-proxy
| fingerprint-strings:
|     <title>Not Found | NodeBB</title>
|     X-Powered-By: NodeBB
| http-robots.txt: 3 disallowed entries
|_/admin/ /reset/ /compose
|_http-title: Home | NodeBB
| http-enum:
|   /login/: Login page
|   /robots.txt: Robots file
|_  /top/: Potentially interesting folder
6379/tcp  open  redis   Redis key-value store 5.0.9
27017/tcp open  mongodb MongoDB 4.0.18
|   mongodb:
|     errmsg
|     command serverStatus requires authentication

Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```
