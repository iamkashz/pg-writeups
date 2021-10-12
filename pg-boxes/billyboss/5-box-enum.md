# 5 box enum

## PowerUp.ps1

```
[*] Checking %PATH% for potentially hijackable .dll locations...
HijackablePath : C:\Users\nathan\Nexus\nexus-3.21.0-05\bin\..\lib\
AbuseFunction  : Write-HijackDll -OutputFile 'C:\Users\nathan\Nexus\nexus-3.21.0-05\bin\..\lib\\wlbsctrl.dll' -Command '...'

HijackablePath : C:\Users\nathan\AppData\Local\Microsoft\WindowsApps\
AbuseFunction  : Write-HijackDll -OutputFile 'C:\Users\nathan\AppData\Local\Microsoft\WindowsApps\\wlbsctrl.dll' -Command '...'

HijackablePath : c:\users\nathan\nexus\nexus-3.21.0-05\jre\bin\
AbuseFunction  : Write-HijackDll -OutputFile 'c:\users\nathan\nexus\nexus-3.21.0-05\jre\bin\\wlbsctrl.dll' -Command '...'
```

## PEAS

```
[?] Windows vulns search powered by Watson(https://github.com/rasta-mouse/Watson)
[*] OS Version: 1903 (18362)
[!] CVE-2020-1013 : VULNERABLE
[>] https://www.gosecure.net/blog/2020/09/08/wsus-attacks-part-2-cve-2020-1013-a-windows-10-local-privilege-escalation-1-day/

[!] CVE-2020-0796 : VULNERABLE
[>] https://github.com/danigargu/CVE-2020-0796 (smbghost)

# windows defender is running
AV Information
    Some AV was detected, search for bypasses
    Name: Windows Defender
    ProductEXE: windowsdefender://

PS history file: C:\Users\nathan\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt

nexus(2100)[C:\Users\nathan\Nexus\nexus-3.21.0-05\bin\nexus.exe] -- POwn: nathan
Possible DLL Hijacking folder: C:\Users\nathan\Nexus\nexus-3.21.0-05\bin (nathan [AllAccess])
Command Line: C:\Users\nathan\Nexus\nexus-3.21.0-05\bin\nexus.exe "Sonatype Nexus" __i4j_restart

Sonatype Nexus(Sonatype Nexus)["C:\Users\nathan\Nexus\nexus-3.21.0-05\bin\nexus.exe"] - Auto - Running
Possible DLL Hijacking in binary folder: C:\Users\nathan\Nexus\nexus-3.21.0-05\bin (nathan [AllAccess])

Enumerating Security Packages Credentials
Version: NetNTLMv2
Hash:    nathan::BILLYBOSS:1122334455667788:37c0d7e575add1f9784b9cba50fca53f:010100000000000090921b1a0d99d701f68d15dcc2a8dc12000000000800300030000000000000000000000000300000d4849b579c2c4771f737b9806bc787f24b892f7f78a81b086694e411a24f49de0a00100000000000000000000000000000000000090000000000000000000000

C:\Users\All Users\Microsoft\UEV\InboxTemplates\RoamingCredentialSettings.xml
```
