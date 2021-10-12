# 1 recon

```
PORT      STATE SERVICE           VERSION
22/tcp    open  ssh               OpenSSH 7.4p1 Debian 10+deb9u7 (protocol 2.0)
|_auth-owners: root
| ssh-hostkey:
|   2048 75:4c:02:01:fa:1e:9f:cc:e4:7b:52:fe:ba:36:85:a9 (RSA)
|   256 b7:6f:9c:2b:bf:fb:04:62:f4:18:c9:38:f4:3d:6b:2b (ECDSA)
|_  256 98:7f:b6:40:ce:bb:b5:57:d5:d1:3c:65:72:74:87:c3 (ED25519)
113/tcp   open  ident             FreeBSD identd
|_auth-owners: nobody
5432/tcp  open  postgresql        PostgreSQL DB 9.6.0 or later
| fingerprint-strings:
|   SMBProgNeg:
|     Munsupported frontend protocol 65363.19778: server supports 2.0 to 3.0
|     Fpostmaster.c
|     L2071
|_    RProcessStartupPacket
8080/tcp  open  http              WEBrick httpd 1.4.2 (Ruby 2.6.6 (2020-03-31))
| http-robots.txt: 4 disallowed entries
|_/issues/gantt /issues/calendar /activity /search
|_http-server-header: WEBrick/1.4.2 (Ruby/2.6.6/2020-03-31)
|_http-title: Redmine
| http-enum:
|   /login.stm: Belkin G Wireless Router
|   /admin.php: Possible admin folder (401 Unauthorized )
|   /login.php: Possible admin folder
|   /login.html: Possible admin folder
|   /admin.cfm: Possible admin folder (401 Unauthorized )
|   /login.cfm: Possible admin folder
|   /admin.asp: Possible admin folder (401 Unauthorized )
|   /login.asp: Possible admin folder
|   /admin.aspx: Possible admin folder (401 Unauthorized )
|   /login.aspx: Possible admin folder
|   /admin.jsp: Possible admin folder (401 Unauthorized )
|   /login.jsp: Possible admin folder
|   /users.sql: Possible database backup (401 Unauthorized )
|   /login/: Login page
|   /login.htm: Login page
|   /login.jsp: Login page
|   /robots.txt: Robots file
|   /admin.nsf: Lotus Domino (401 Unauthorized )
|   /news/: Potentially interesting folder
|_  /search/: Potentially interesting folder
10000/tcp open  snet-sensor-mgmt?
|_auth-owners: eleanor
| http-vuln-cve2006-3392:
|   VULNERABLE:
|   Webmin File Disclosure
|     State: VULNERABLE (Exploitable)
|     IDs:  CVE:CVE-2006-3392
|       Webmin before 1.290 and Usermin before 1.220 calls the simplify_path function before decoding HTML.
|       This allows arbitrary files to be read, without requiring authentication, using "..%01" sequences
|       to bypass the removal of "../" directory traversal sequences.
|
|     Disclosure date: 2006-06-29
|     References:
|       http://www.exploit-db.com/exploits/1997/
|       https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2006-3392
|_      http://www.rapid7.com/db/modules/auxiliary/admin/webmin/file_disclosure
2 services unrecognized despite returning data. If you know the service/version, please submit the following fingerprints at https://nmap.org/cgi-bin/submit.cgi?new-service :
Service Info: OSs: Linux, FreeBSD; CPE: cpe:/o:linux:linux_kernel, cpe:/o:freebsd:freebsd
```
