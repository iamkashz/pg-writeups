# 1 recon

```
adding to /etc/hosts
192.168.144.37 ucal.local
PORT   STATE SERVICE VERSION
21/tcp open  ftp     Pure-FTPd
22/tcp open  ssh     OpenSSH 5.8p1 Debian 7ubuntu1 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   1024 5b:b4:3f:ad:ac:70:b3:6f:70:db:de:72:11:03:d7:1d (DSA)
|   2048 13:dc:ff:d4:03:51:a5:9f:0c:05:33:82:f0:4a:dd:21 (RSA)
|_  256 fe:be:7f:91:5c:5e:64:78:0b:35:e4:73:1f:01:f5:a1 (ECDSA)
25/tcp open  smtp    Postfix smtpd
|_smtp-commands: ucal.local, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, ENHANCEDSTATUSCODES, 8BITMIME, DSN,
| ssl-cert: Subject: commonName=ucal.local
| Not valid before: 2013-01-14T10:28:18
|_Not valid after:  2023-01-12T10:28:18
|_ssl-date: 2021-09-04T20:43:01+00:00; +3h59m59s from scanner time.
53/tcp open  domain  ISC BIND 9.7.3
| dns-nsid:
|_  bind.version: 9.7.3
80/tcp open  http    Apache httpd 2.2.20 ((Ubuntu))
|_http-server-header: Apache/2.2.20 (Ubuntu)
|_http-title: Construction Page
Service Info: Host:  ucal.local; OS: Linux; CPE: cpe:/o:linux:linux_kernel

PORT   STATE SERVICE
53/udp open  domain

Host script results:
|_clock-skew: 3h59m58s
```
