# 1 recon

```
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey:
|   2048 27:21:9e:b5:39:63:e9:1f:2c:b2:6b:d3:3a:5f:31:7b (RSA)
|   256 bf:90:8a:a5:d7:e5:de:89:e6:1a:36:a1:93:40:18:57 (ECDSA)
|_  256 95:1f:32:95:78:08:50:45:cd:8c:7c:71:4a:d4:6c:1c (ED25519)
80/tcp   open  http    Apache httpd 2.4.38 ((Debian))
|_http-generator: CMS Made Simple - Copyright (C) 2004-2020. All rights reserved.
|_http-server-header: Apache/2.4.38 (Debian)
|_http-title: Home - My CMS
| http-enum:
|   /admin/login.php: Possible admin folder
|   /phpinfo.php: Possible information file
|   /phpmyadmin/: phpMyAdmin (401 Unauthorized)
|   /doc/: Potentially interesting folder
|   /lib/: Potentially interesting folder
|   /modules/: Potentially interesting directory w/ listing on 'apache/2.4.38 (debian)'
|   /tmp/: Potentially interesting directory w/ listing on 'apache/2.4.38 (debian)'
|_  /uploads/: Potentially interesting folder
3306/tcp open  mysql   MySQL 8.0.19
| mysql-info:
|   Protocol: 10
|   Version: 8.0.19
|   Thread ID: 11
|   Capabilities flags: 65535
|   Some Capabilities: LongPassword, Speaks41ProtocolOld, DontAllowDatabaseTableColumn, InteractiveClient, ConnectWithDatabase, Support41Auth, LongColumnFlag, FoundRows, ODBCClient, SupportsTransactions, IgnoreSigpipes, SwitchToSSLAfterHandshake, Speaks41ProtocolNew, IgnoreSpaceBeforeParenthesis, SupportsLoadDataLocal, SupportsCompression, SupportsMultipleStatments, SupportsMultipleResults, SupportsAuthPlugins
|   Status: Autocommit
|   Salt: \x16GK6o_\x1B%q\x1A
| ,\x0E\x15F\x0B\x03u]
|_  Auth Plugin Name: mysql_native_password
| ssl-cert: Subject: commonName=MySQL_Server_8.0.19_Auto_Generated_Server_Certificate
| Not valid before: 2020-03-25T09:30:14
|_Not valid after:  2030-03-23T09:30:14
|_ssl-date: TLS randomness does not represent time
33060/tcp open  mysqlx?
| fingerprint-strings:
|   DNSStatusRequestTCP, LDAPSearchReq, NotesRPC, SSLSessionReq, TLSSessionReq, X11Probe, afp:
|     Invalid message"
|_    HY000
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```
