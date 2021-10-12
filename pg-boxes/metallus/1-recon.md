# 1 recon

```
PORT      STATE SERVICE       VERSION
135/tcp   open  msrpc         Microsoft Windows RPC
139/tcp   open  netbios-ssn   Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds?
12000/tcp open  cce4x?
| fingerprint-strings:
|   Kerberos, SMBProgNeg:
|_    RECONNECT
5040/tcp  open  unknown
22222/tcp open  ssh        OpenSSH for_Windows_8.1 (protocol 2.0)
| ssh-hostkey:
|   3072 e5:92:a8:a8:57:16:73:42:1a:9b:c2:f2:e3:bd:8a:76 (RSA)
|   256 71:16:46:72:7a:05:c9:77:4e:c5:96:43:96:31:a6:12 (ECDSA)
|_  256 e3:42:cf:ff:ba:71:ff:27:09:fa:4d:d5:52:99:59:9c (ED25519)
40443/tcp open  unknown
| fingerprint-strings:
|   GetRequest:
|     HTTP/1.1 200
|     Set-Cookie: JSESSIONID_APM_40443=2B67DEEDB2547D05266E5A6A77E9D379; Path=/; HttpOnly
|     Accept-Ranges: bytes
|     ETag: W/"261-1591076589000"
|     Last-Modified: Tue, 02 Jun 2020 05:43:09 GMT
|     Content-Type: text/html
|     Content-Length: 261
|     Date: Thu, 12 Aug 2021 19:45:00 GMT
|     Connection: close
|     Server: AppManager
|     <!-- $Id$ -->
|     <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
|     <html>
|     <head>
|     <!-- This comment is for Instant Gratification to work applications.do -->
|     <script>
|     window.open("/webclient/common/jsp/home.jsp", "_top");
|     </script>
|     </head>
|     </html>
|   HTTPOptions:
|     HTTP/1.1 403
|     Set-Cookie: JSESSIONID_APM_40443=18C996A1E588BD992D6024242840F72A; Path=/; HttpOnly
|     Cache-Control: private
|     Expires: Thu, 01 Jan 1970 00:00:00 GMT
|     Content-Type: text/html;charset=UTF-8
|     Content-Length: 1810
|     Date: Thu, 12 Aug 2021 19:45:00 GMT
|     Connection: close
|     Server: AppManager
|     <meta http-equiv="X-UA-Compatible" content="IE=edge">
|     <meta http-equiv="Content-Type" content="UTF-8">
|     <!--$Id$-->
|     <html>
|     <head>
|     <title>Applications Manager</title>
|     <link REL="SHORTCUT ICON" HREF="/favicon.ico">
|     </head>
|     <body style="background-color:#fff;">
|     <style type="text/css">
|     #container-error
|     border:1px solid #c1c1c1;
|     background: #fff; font:11px Arial, Helvetica, sans-serif; width:90%; margin:80px;
|     #header-error
|     background: #ededed; line-height:18px;
|     padding: 15px; color:#000; font-size:8px;
|     #header-error h1
|     margin: 0; color:#000;
|     font-
|   RTSPRequest:
|     HTTP/1.1 505
|     vary: accept-encoding
|     Content-Type: text/html;charset=utf-8
|     Content-Language: en
|     Content-Length: 2142
|     Date: Thu, 12 Aug 2021 19:45:01 GMT
|     Server: AppManager
|     <!doctype html><html lang="en"><head><title>HTTP Status 505
|_    HTTP Version Not Supported</title><style type="text/css">h1 {font-family:Tahoma,Arial,sans-serif;color:white;background-color:#525D76;font-size:22px;} h2 {font-family:Tahoma,Arial,sans-serif;color:white;background-color:#525D76;font-size:16px;} h3 {font-family:Tahoma,Arial,sans-serif;color:white;background-color:#525D76;font-size:14px;} body {font-family:Tahoma,Arial,sans-serif;color:black;background-color:white;} b {font-family:Tahoma,Arial,sans-serif;color:white;background-color:#525D76;} p {font-family:Tahoma,Arial,sans-serif;background:white;color:black;font-size:12px;} a {color:black;} a.name {color:black;} .line {height:1px;background-color:#
49664/tcp open  msrpc      Microsoft Windows RPC
49665/tcp open  msrpc      Microsoft Windows RPC
49666/tcp open  msrpc      Microsoft Windows RPC
49667/tcp open  msrpc      Microsoft Windows RPC
49668/tcp open  msrpc      Microsoft Windows RPC
49669/tcp open  msrpc      Microsoft Windows RPC
49670/tcp open  tcpwrapped
49693/tcp open  java-rmi   Java RMI
49718/tcp open  unknown
49796/tcp open  unknown
| fingerprint-strings:
|   Kerberos, SMBProgNeg, X11Probe, ms-sql-s:
|_    CLOSE_SESSION
49797/tcp open  unknown
| fingerprint-strings:
|   Kerberos, SMBProgNeg, X11Probe, ms-sql-s:
|_    CLOSE_SESSION

Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb2-security-mode:
|   2.02:
|_    Message signing enabled but not required
| smb2-time:
|   date: 2021-08-12T19:39:43
|_  start_date: N/A
```
