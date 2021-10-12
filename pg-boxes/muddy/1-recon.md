# 1 recon

```
# adding to /etc/hosts
192.168.197.161 muddy.ugc

PORT     STATE SERVICE       VERSION
22/tcp   open  ssh           OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey:
|   2048 74:ba:20:23:89:92:62:02:9f:e7:3d:3b:83:d4:d9:6c (RSA)
|   256 54:8f:79:55:5a:b0:3a:69:5a:d5:72:39:64:fd:07:4e (ECDSA)
|_  256 7f:5d:10:27:62:ba:75:e9:bc:c8:4f:e2:72:87:d4:e2 (ED25519)
25/tcp   open  smtp          Exim smtpd
| smtp-commands: muddy Hello nmap.scanme.org [192.168.49.197], SIZE 52428800, 8BITMIME, PIPELINING, CHUNKING, PRDR, HELP,
|_ Commands supported: AUTH HELO EHLO MAIL RCPT DATA BDAT NOOP QUIT RSET HELP
 smtp-vuln-cve2010-4344:
|   Exim version: 4.92
|   Exim heap overflow vulnerability (CVE-2010-4344):
|     Exim (CVE-2010-4344): NOT VULNERABLE
|   Exim privileges escalation vulnerability (CVE-2010-4345):
|     Exim (CVE-2010-4345): NOT VULNERABLE
|_  To confirm and exploit the vulnerabilities, run with --script-args='smtp-vuln-cve2010-4344.exploit'
80/tcp   open  http          Apache httpd 2.4.38 ((Debian))
|_http-server-header: Apache/2.4.38 (Debian)
|_http-title: Did not follow redirect to http://muddy.ugc/
| http-enum:
|   /readme.html: Wordpress version: 2
|   /: WordPress version: 5.7
|   /wp-includes/images/rss.png: Wordpress version 2.2 found.
|   /wp-includes/js/jquery/suggest.js: Wordpress version 2.5 found.
|   /wp-includes/images/blank.gif: Wordpress version 2.6 found.
|   /wp-includes/js/comment-reply.js: Wordpress version 2.7 found.
|   /wp-admin/upgrade.php: Wordpress login page.
|   /readme.html: Interesting, a readme.
|_  /webdav/: Potentially interesting folder (401 Unauthorized)
111/tcp  open  rpcbind       2-4 (RPC #100000)
| rpcinfo:
|   program version    port/proto  service
|   100000  2,3,4        111/tcp   rpcbind
|   100000  2,3,4        111/udp   rpcbind
|   100000  3,4          111/tcp6  rpcbind
|_  100000  3,4          111/udp6  rpcbind
808/tcp  open  ccproxy-http?
908/tcp open  unknown
8888/tcp open  http          WSGIServer 0.1 (Python 2.7.16)
|_http-title: Ladon Service Catalog
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```
