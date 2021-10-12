# 1 recon

```
PORT     STATE SERVICE    VERSION
8080/tcp open  http-proxy
|     <title>My Haikus</title>
|_http-title: My Haikus
12445/tcp open  netbios-ssn Samba smbd 4.6.2
18030/tcp open  http        Apache httpd 2.4.46 ((Unix))
| http-methods:
|_  Potentially risky methods: TRACE
|_http-server-header: Apache/2.4.46 (Unix)
|_http-title: Whack A Mole!
| http-enum:
|_  /icons/: Potentially interesting folder w/ directory listing
43022/tcp open  ssh         OpenSSH 8.4 (protocol 2.0)
| ssh-hostkey:
|   3072 7b:fc:37:b4:da:6e:c5:8e:a9:8b:b7:80:f5:cd:09:cb (RSA)
|   256 89:cd:ea:47:25:d9:8f:f8:94:c3:d6:5c:d4:05:ba:d0 (ECDSA)
|_  256 c0:7c:6f:47:7e:94:cc:8b:f8:3d:a0:a6:1f:a9:27:11 (ED25519)
```
