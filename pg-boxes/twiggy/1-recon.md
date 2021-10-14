# 1 recon

```
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 7.4 (protocol 2.0)
| ssh-hostkey:
|   2048 44:7d:1a:56:9b:68:ae:f5:3b:f6:38:17:73:16:5d:75 (RSA)
|   256 1c:78:9d:83:81:52:f4:b0:1d:8e:32:03:cb:a6:18:93 (ECDSA)
|_  256 08:c9:12:d9:7b:98:98:c8:b3:99:7a:19:82:2e:a3:ea (ED25519)
53/tcp   open  domain  NLnet Labs NSD
80/tcp   open  http    nginx 1.16.1
|_http-server-header: nginx/1.16.1
|_http-title: Home | Mezzanine
8000/tcp open  http    nginx 1.16.1
|_http-open-proxy: Proxy might be redirecting requests
|_http-server-header: nginx/1.16.1
4505/tcp open  zmtp    ZeroMQ ZMTP 2.0
4506/tcp open  zmtp    ZeroMQ ZMTP 2.0
|_http-title: Site doesn't have a title (application/json).

# nikto 
- Nikto v2.1.6
---------------------------------------------------------------------------
+ Target IP:          192.168.246.62
+ Target Hostname:    192.168.246.62
+ Target Port:        8000
+ Start Time:         2021-09-06 23:30:11 (GMT-7)
---------------------------------------------------------------------------
+ Server: nginx/1.16.1
+ Uncommon header 'x-upstream' found, with contents: salt-api/3000-1
```
