# 1 recon

```
PORT     STATE SERVICE VERSION
21/tcp   open  ftp     vsftpd 3.0.3
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_Can't get directory listing: TIMEOUT
| ftp-syst:
|   STAT:
| FTP server status:
|      Connected to 192.168.49.213
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      At session startup, client count was 2
|      vsFTPd 3.0.3 - secure, fast, stable
|_End of status
22/tcp   open  ssh     OpenSSH 8.3 (protocol 2.0)
| ssh-hostkey:
|   3072 9d:3f:eb:1b:aa:9c:1e:b1:30:9b:23:53:4b:cf:59:75 (RSA)
|   256 cd:dc:05:e6:e3:bb:12:33:f7:09:74:50:12:8a:85:64 (ECDSA)
|_  256 a0:90:1f:50:78:b3:9e:41:2a:7f:5c:6f:4d:0e:a1:fa (ED25519)
80/tcp   open  http    Apache httpd 2.4.46 ((Fedora))
|_http-generator: Drupal 9 (https://www.drupal.org)
| http-robots.txt: 22 disallowed entries (15 shown)
| /core/ /profiles/ /README.txt /web.config /admin/
| /comment/reply/ /filter/tips /node/add/ /search/ /user/register/
| /user/password/ /user/login/ /user/logout/ /index.php/admin/
|_/index.php/comment/reply/
|_http-server-header: Apache/2.4.46 (Fedora)
|_http-title: Home | Hacking Articles
3000/tcp open  http    Node.js (Express middleware)
|_http-title: Site doesn't have a title (text/html; charset=utf-8).
27017/tcp open  mongodb MongoDB 4.2.9
| mongodb-databases:
|   ok = 1.0
|   databases
|     3
|       sizeOnDisk = 73728.0
|       empty = false
|       name = local
|     0
|       sizeOnDisk = 131072.0
|       empty = false
|       name = account-app
|     1
|       sizeOnDisk = 40960.0
|       empty = false
|       name = admin
|     2
|       sizeOnDisk = 61440.0
|       empty = false
|       name = config
|_  totalSize = 307200.0
|_mongodb-info: ERROR: Script execution failed (use -d to debug)

Service Info: OS: Unix
```
