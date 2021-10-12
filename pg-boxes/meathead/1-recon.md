# 1 recon

```
PORT     STATE SERVICE       VERSION
80/tcp   open  http          Microsoft IIS httpd 10.0
| http-methods:
|_  Potentially risky methods: TRACE
|_http-server-header: Microsoft-IIS/10.0
|_http-title: Plantronics
135/tcp  open  msrpc         Microsoft Windows RPC
139/tcp  open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp  open  microsoft-ds  Microsoft Windows Server 2008 R2 - 2012 microsoft-ds
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| rdp-ntlm-info:
|   Target_Name: MEATHEAD
|   NetBIOS_Domain_Name: MEATHEAD
|   NetBIOS_Computer_Name: MEATHEAD
|   DNS_Domain_Name: Meathead
|   DNS_Computer_Name: Meathead
|   Product_Version: 10.0.17763
|_  System_Time: 2021-08-23T20:18:47+00:00
| ssl-cert: Subject: commonName=Meathead
| Not valid before: 2021-08-22T20:05:12
|_Not valid after:  2022-02-21T20:05:12
|_ssl-date: 2021-08-23T20:19:27+00:00; -1s from scanner time.
1221/tcp open  ftp      Microsoft ftpd
| ftp-anon: Anonymous FTP login allowed (FTP code 230)
| 04-27-20  07:02PM                18866 Elementum Supremum.docx
| 04-27-20  07:02PM               764176 file_example_MP3_700KB.mp3
| 04-27-20  07:02PM                15690 img.jpg
| 04-27-20  07:02PM                  302 MSSQL_BAK.rar
| 04-27-20  07:02PM                  548 palindromes.txt
|_04-27-20  07:02PM                45369 server.jpg
| ftp-syst:
|_  SYST: Windows_NT
1435/tcp open  ms-sql-s Microsoft SQL Server 2017 14.00.1000
| ms-sql-ntlm-info:
|   Target_Name: MEATHEAD
|   NetBIOS_Domain_Name: MEATHEAD
|   NetBIOS_Computer_Name: MEATHEAD
|   DNS_Domain_Name: Meathead
|   DNS_Computer_Name: Meathead
|_  Product_Version: 10.0.17763
| ssl-cert: Subject: commonName=SSL_Self_Signed_Fallback
| Not valid before: 2021-03-10T18:55:34
|_Not valid after:  2051-03-10T18:55:34
|_ssl-date: 2021-08-23T20:24:38+00:00; 0s from scanner time.
5985/tcp open  http     Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
|_http-server-header: Microsoft-HTTPAPI/2.0
|_http-title: Not Found
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

Host script results:
| smb-security-mode:
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
| smb2-security-mode:
|   2.02:
|_    Message signing enabled but not required
| smb2-time:
|   date: 2021-08-23T20:18:52
|_  start_date: N/A
```
