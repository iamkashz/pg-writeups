# 1 recon

```
22/tcp  open  ssh         OpenSSH 4.6p1 Debian 5build1 (protocol 2.0)
| ssh-hostkey:
|   1024 f3:6e:87:04:ea:2d:b3:60:ff:42:ad:26:67:17:94:d5 (DSA)
|_  2048 bb:03:ce:ed:13:f1:9a:9e:36:03:e2:af:ca:b2:35:04 (RSA)
80/tcp  open  http        Apache httpd 2.2.4 ((Ubuntu) PHP/5.2.3-1ubuntu6)
|_http-server-header: Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6
|_http-title: CS-Cart. Powerful PHP shopping cart software
110/tcp open  pop3        Dovecot pop3d
|_pop3-capabilities: RESP-CODES TOP UIDL CAPA STLS SASL PIPELINING
| ssl-cert: Subject: commonName=ubuntu01/organizationName=OCOSA/stateOrProvinceName=There is no such thing outside US/countryName=XX
| Not valid before: 2008-04-25T02:02:48
|_Not valid after:  2008-05-25T02:02:48
|_ssl-date: 2021-08-16T21:01:06+00:00; +6s from scanner time.
139/tcp open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: MSHOME)
143/tcp open  imap        Dovecot imapd
|_imap-capabilities: completed Capability MULTIAPPEND IDLE SASL-IR LOGIN-REFERRALS LITERAL+ IMAP4rev1 STARTTLS SORT LOGINDISABLEDA0001 OK THREAD=REFERENCES NAMESPACE CHILDREN UNSELECT
| ssl-cert: Subject: commonName=ubuntu01/organizationName=OCOSA/stateOrProvinceName=There is no such thing outside US/countryName=XX
| Not valid before: 2008-04-25T02:02:48
|_Not valid after:  2008-05-25T02:02:48
|_ssl-date: 2021-08-16T21:01:07+00:00; +6s from scanner time.
445/tcp open  netbios-ssn Samba smbd 3.0.26a (workgroup: MSHOME)
993/tcp open  ssl/imap    Dovecot imapd
|_imap-capabilities: completed MULTIAPPEND IDLE SASL-IR LOGIN-REFERRALS LITERAL+ IMAP4rev1 Capability SORT AUTH=PLAINA0001 OK THREAD=REFERENCES NAMESPACE CHILDREN UNSELECT
| ssl-cert: Subject: commonName=ubuntu01/organizationName=OCOSA/stateOrProvinceName=There is no such thing outside US/countryName=XX
| Not valid before: 2008-04-25T02:02:48
|_Not valid after:  2008-05-25T02:02:48
|_ssl-date: 2021-08-16T21:01:06+00:00; +6s from scanner time.
995/tcp open  ssl/pop3    Dovecot pop3d
|_pop3-capabilities: RESP-CODES TOP UIDL CAPA USER SASL(PLAIN) PIPELINING
| ssl-cert: Subject: commonName=ubuntu01/organizationName=OCOSA/stateOrProvinceName=There is no such thing outside US/countryName=XX
| Not valid before: 2008-04-25T02:02:48
|_Not valid after:  2008-05-25T02:02:48
|_ssl-date: 2021-08-16T21:01:06+00:00; +5s from scanner time.
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_clock-skew: mean: 40m05s, deviation: 1h37m59s, median: 5s
| smb-os-discovery:
|   OS: Unix (Samba 3.0.26a)
|   Computer name: payday
|   NetBIOS computer name:
|   Domain name:
|   FQDN: payday
|_  System time: 2021-08-16T17:00:59-04:00
| smb-security-mode:
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
|_smb2-time: Protocol negotiation failed (SMB2)
```
