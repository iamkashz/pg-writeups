# 1 recon

```
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.4p1 Debian 10+deb9u7 (protocol 2.0)
| ssh-hostkey:
|   2048 cd:88:cb:33:78:9a:bf:f0:31:57:d9:2f:ae:13:ee:db (RSA)
|   256 fb:54:3b:ba:f6:68:57:81:e4:65:6e:24:9c:db:6d:8a (ECDSA)
|_  256 be:6e:25:d1:88:09:7e:33:40:b3:56:6a:b4:ce:16:0d (ED25519)
80/tcp   open  http    Apache httpd 2.4.25 ((Debian))
|_http-server-header: Apache/2.4.25 (Debian)
|_http-title: PHP Calculator
3306/tcp open  mysql   MariaDB (unauthorized)
5601/tcp  open  esmagent?
| fingerprint-strings:
|   DNSStatusRequestTCP, DNSVersionBindReqTCP, Help, Kerberos, LDAPBindReq, LDAPSearchReq, LPDString, RPCCheck, RTSPRequest, SIPOptions, SMBProgNeg, SSLSessionReq, TLSSessionReq, TerminalServerCookie, X11Probe:
|     HTTP/1.1 400 Bad Request
|   FourOhFourRequest:
|     HTTP/1.1 404 Not Found
|     kbn-name: kibana
|     kbn-xpack-sig: 79b8a7336823018e37a1e121a9f3bb67
|     content-type: application/json; charset=utf-8
|     cache-control: no-cache
|     content-length: 60
|     connection: close
|     Date: Tue, 31 Aug 2021 02:37:05 GMT
|     {"statusCode":404,"error":"Not Found","message":"Not Found"}
|   GetRequest:
|     HTTP/1.1 302 Found
|     location: /app/kibana
|     kbn-name: kibana
|     kbn-xpack-sig: 79b8a7336823018e37a1e121a9f3bb67
|     cache-control: no-cache
|     content-length: 0
|     connection: close
|     Date: Tue, 31 Aug 2021 02:37:03 GMT
|   HTTPOptions:
|     HTTP/1.1 404 Not Found
|     kbn-name: kibana
|     kbn-xpack-sig: 79b8a7336823018e37a1e121a9f3bb67
|     content-type: application/json; charset=utf-8
|     cache-control: no-cache
|     content-length: 38
|     connection: close
|     Date: Tue, 31 Aug 2021 02:37:03 GMT
|_    {"statusCode":404,"error":"Not Found"}
24007/tcp open  rpcbind
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
```
