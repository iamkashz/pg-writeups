# 1 recon

```
22/tcp open  ssh     OpenSSH 8.4 (protocol 2.0)
| ssh-hostkey:
|   3072 78:2f:ea:84:4c:09:ae:0e:36:bf:b3:01:35:cf:47:22 (RSA)
|   256 d2:7d:eb:2d:a5:9a:2f:9e:93:9a:d5:2e:aa:dc:f4:a6 (ECDSA)
|_  256 b6:d4:96:f0:a4:04:e4:36:78:1e:9d:a5:10:93:d7:99 (ED25519)
17445/tcp open  unknown
fingerprint-strings:
|   GetRequest:
|     HTTP/1.1 200
|     <title>Issue Tracker</title>
|     href="/login" class="btn btn-primary" style="float:right">Sign In</a>
|     href="/register" class="btn btn-primary" style="float:right;margin-right:5px">Register</a>
30455/tcp open  http    nginx 1.18.0
|_http-server-header: nginx/1.18.0
|_http-title: W3.CSS
| http-enum:
|_  /phpinfo.php: Possible information file
50080/tcp open  http    Apache httpd 2.4.46 ((Unix) PHP/7.4.15)
| http-methods:
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/2.4.46 (Unix) PHP/7.4.15
|_http-title: W3.CSS Template
| http-enum:
|   /4/: Potentially interesting folder w/ directory listing
|   /icons/: Potentially interesting folder w/ directory listing
|_  /images/: Potentially interesting folder w/ directory listing
```
