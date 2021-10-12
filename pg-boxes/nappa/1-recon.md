# 1 recon

```
PORT     STATE SERVICE    VERSION
21/tcp   open  ftp        vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_drwxr-xr-x   14 14       11           4096 Nov 06  2020 forum
| ftp-syst:
|   STAT:
| FTP server status:
|      Logged in as ftp
|      vsFTPd 3.0.3 - secure, fast, stable
3306/tcp open  mysql?
| fingerprint-strings:
|   Kerberos, NULL:
|_    Host '192.168.49.99' is not allowed to connect to this MariaDB server
8080/tcp open  http-proxy
|  GetRequest, HTTPOptions:
|     HTTP/1.0 403 Forbidden
|     Content-Type: text/html; charset=UTF-8
|     Content-Length: 3102
| http-enum:
|   /login.html: Possible admin folder
|   /login/: Login page
|_  /robots.txt: Robots file
28080/tcp open  http    Apache httpd 2.4.46 ((Unix))
| http-methods:
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/2.4.46 (Unix)
|_http-title: html5-goku-en-javascript
60022/tcp open  ssh     OpenSSH 8.4 (protocol 2.0)
| ssh-hostkey:
|   3072 76:61:5c:e1:8c:ca:14:e8:7a:63:ba:a3:46:9f:09:b3 (RSA)
|   256 e3:ed:fc:a8:10:d7:8e:b1:7c:de:a2:59:df:19:06:29 (ECDSA)
|_  256 e5:dd:dd:a7:e3:ac:5f:b9:2b:4b:d0:27:e3:3c:c2:43 (ED25519)
```
