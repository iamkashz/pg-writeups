# 1 recon

```
PORT   STATE SERVICE VERSION
21/tcp open  ftp     vsftpd 3.0.2
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
|_drwxrwxrwx    2 0        0               6 Apr 01  2020 pub [NSE: writeable]
| ftp-syst:
22/tcp open  ssh     OpenSSH 7.4 (protocol 2.0)
80/tcp open  http    Apache httpd 2.4.6 ((CentOS) PHP/7.3.22)
| http-cookie-flags:
|   /:
|     PHPSESSID:
|_      httponly flag not set
|_http-generator: HTMLy v2.7.5
| http-robots.txt: 11 disallowed entries
| /config/ /system/ /themes/ /vendor/ /cache/
| /changelog.txt /composer.json /composer.lock /composer.phar /search/
|_/admin/
|_http-server-header: Apache/2.4.6 (CentOS) PHP/7.3.22
|_http-title: Sybaris - Just another HTMLy blog
| http-enum:
|   /robots.txt: Robots file
|   /icons/: Potentially interesting folder w/ directory listing
|_  /index/: Potentially interesting folder
6379/tcp open  redis   Redis key-value store 5.0.9
Service Info: OS: Unix
```
