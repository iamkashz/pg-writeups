# 1 recon

```
PORT    STATE SERVICE  VERSION
22/tcp  open  ssh      OpenSSH 8.2p1 Ubuntu 4ubuntu0.1 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey:
|   3072 c1:99:4b:95:22:25:ed:0f:85:20:d3:63:b4:48:bb:cf (RSA)
|   256 0f:44:8b:ad:ad:95:b8:22:6a:f0:36:ac:19:d0:0e:f3 (ECDSA)
|_  256 32:e1:2a:6c:cc:7c:e6:3e:23:f4:80:8d:33:ce:9b:3a (ED25519)
25/tcp  open  smtp     Postfix smtpd
|_smtp-commands: postfish.off, PIPELINING, SIZE 10240000, VRFY, ETRN, STARTTLS, ENHANCEDSTATUSCODES, 8BITMIME, DSN, SMTPUTF8, CHUNKING,
| ssl-cert: Subject: commonName=ubuntu
| Subject Alternative Name: DNS:ubuntu
| Not valid before: 2021-01-26T10:26:37
|_Not valid after:  2031-01-24T10:26:37
|_ssl-date: TLS randomness does not represent time
80/tcp  open  http     Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: W3.CSS Template
110/tcp open  pop3     Dovecot pop3d
|_pop3-capabilities: SASL(PLAIN) USER UIDL TOP RESP-CODES STLS PIPELINING CAPA AUTH-RESP-CODE
| ssl-cert: Subject: commonName=ubuntu
| Subject Alternative Name: DNS:ubuntu
| Not valid before: 2021-01-26T10:26:37
|_Not valid after:  2031-01-24T10:26:37
143/tcp open  imap     Dovecot imapd (Ubuntu)
|_imap-capabilities: IMAP4rev1 more listed have AUTH=PLAINA0001 SASL-IR post-login capabilities Pre-login LITERAL+ OK IDLE ID STARTTLS ENABLE LOGIN-REFERRALS
| ssl-cert: Subject: commonName=ubuntu
| Subject Alternative Name: DNS:ubuntu
| Not valid before: 2021-01-26T10:26:37
|_Not valid after:  2031-01-24T10:26:37
993/tcp open  ssl/imap Dovecot imapd (Ubuntu)
|_imap-capabilities: IMAP4rev1 listed more AUTH=PLAINA0001 SASL-IR have post-login capabilities LITERAL+ Pre-login IDLE ID OK ENABLE LOGIN-REFERRALS
| ssl-cert: Subject: commonName=ubuntu
| Subject Alternative Name: DNS:ubuntu
| Not valid before: 2021-01-26T10:26:37
|_Not valid after:  2031-01-24T10:26:37
995/tcp open  ssl/pop3 Dovecot pop3d
|_pop3-capabilities: SASL(PLAIN) TOP RESP-CODES USER CAPA PIPELINING UIDL AUTH-RESP-CODE
| ssl-cert: Subject: commonName=ubuntu
| Subject Alternative Name: DNS:ubuntu
| Not valid before: 2021-01-26T10:26:37
|_Not valid after:  2031-01-24T10:26:37
Service Info: Host:  postfish.off; OS: Linux; CPE: cpe:/o:linux:linux_kernel
```
