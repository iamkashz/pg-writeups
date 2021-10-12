# 1 recon

```
PORT     STATE SERVICE VERSION
21/tcp   open  ftp     Microsoft ftpd
| ftp-syst:
|_  SYST: Windows_NT
80/tcp   open  http    Microsoft IIS httpd 10.0
|_http-cors: HEAD GET POST PUT DELETE TRACE OPTIONS CONNECT PATCH
|_http-server-header: Microsoft-IIS/10.0
|_http-title: BaGet
8081/tcp open  http    Jetty 9.4.18.v20190429
| http-robots.txt: 2 disallowed entries
|_/repository/ /service/
|_http-server-header: Nexus/3.21.0-05 (OSS)
|_http-title: Nexus Repository Manager
| http-enum:
|_  /robots.txt: Robots file
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows
```
