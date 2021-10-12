# 1 recon

```
PORT     STATE SERVICE     VERSION
80/tcp   open  http        Apache httpd 2.4.29 ((Ubuntu))
|_http-server-header: Apache/2.4.29 (Ubuntu)
|_http-title: APEX Hospital
 http-enum:
|   /filemanager/: Potentially interesting folder
|_  /source/: Potentially interesting directory w/ listing on 'apache/2.4.29 (ubuntu)'
445/tcp  open  netbios-ssn Samba smbd 4.7.6-Ubuntu (workgroup: WORKGROUP)
3306/tcp open  mysql       MySQL 5.5.5-10.1.48-MariaDB-0ubuntu0.18.04.1
| mysql-info:
|   Protocol: 10
|   Version: 5.5.5-10.1.48-MariaDB-0ubuntu0.18.04.1
|   Thread ID: 33
|   Capabilities flags: 63487
|   Some Capabilities: IgnoreSpaceBeforeParenthesis, Support41Auth, FoundRows, ConnectWithDatabase, Speaks41ProtocolOld, SupportsCompression, LongPassword, DontAllowDatabaseTableColumn, IgnoreSigpipes, InteractiveClient, SupportsLoadDataLocal, LongColumnFlag, ODBCClient, Speaks41ProtocolNew, SupportsTransactions, SupportsMultipleResults, SupportsMultipleStatments, SupportsAuthPlugins
|   Status: Autocommit
|   Salt: z+e=@hlg=<Vz$AXyyqLh
|_  Auth Plugin Name: mysql_native_password
Service Info: Host: APEX

Host script results:
|_clock-skew: mean: 1h20m00s, deviation: 2h18m34s, median: 0s
| smb-os-discovery:
|   OS: Windows 6.1 (Samba 4.7.6-Ubuntu)
|   Computer name: apex
|   NetBIOS computer name: APEX\x00
|   Domain name: \x00
|   FQDN: apex
|_  System time: 2021-08-28T13:15:02-04:00
| smb-security-mode:
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode:
|   2.02:
|_    Message signing enabled but not required
| smb2-time:
|   date: 2021-08-28T17:15:01
|_  start_date: N/
```
