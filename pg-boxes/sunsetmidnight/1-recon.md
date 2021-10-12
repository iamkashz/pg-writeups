# 1 recon

```
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
| ssh-hostkey:
|   2048 9c:fe:0b:8b:8d:15:e7:72:7e:3c:23:e5:86:55:51:2d (RSA)
|   256 fe:eb:ef:5d:40:e7:06:67:9b:63:67:f8:d9:7e:d3:e2 (ECDSA)
|_  256 35:83:68:2c:33:8b:b4:6c:24:21:20:0d:52:ed:cd:16 (ED25519)
80/tcp   open  http    Apache httpd 2.4.38 ((Debian))
|_http-generator: WordPress 5.4.2
|_http-server-header: Apache/2.4.38 (Debian)
|_http-title: Midnight Blog &#8211; Just another WordPress site
|_http-trane-info: Problem with XML parsing of /evox/about
3306/tcp open  mysql   MySQL 5.5.5-10.3.22-MariaDB-0+deb10u1
| mysql-info:
|   Protocol: 10
|   Version: 5.5.5-10.3.22-MariaDB-0+deb10u1
|   Thread ID: 61
|   Capabilities flags: 63486
|   Some Capabilities: Speaks41ProtocolNew, ODBCClient, Speaks41ProtocolOld, ConnectWithDatabase, Support41Auth, LongColumnFlag, SupportsTransactions, SupportsCompression, IgnoreSigpipes, InteractiveClient, SupportsLoadDataLocal, FoundRows, IgnoreSpaceBeforeParenthesis, DontAllowDatabaseTableColumn, SupportsMultipleResults, SupportsMultipleStatments, SupportsAuthPlugins
|   Status: Autocommit
|   Salt: e_-_vX22DAUi2XG;0{Br
|_  Auth Plugin Name: mysql_native_password
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```
