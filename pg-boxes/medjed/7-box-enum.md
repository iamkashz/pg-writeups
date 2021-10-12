# 7 box enum

```
systeminfo

Host Name:                 MEDJED
OS Name:                   Microsoft Windows 10 Pro
OS Version:                10.0.18363 N/A Build 18363
System Type:               x64-based PC
Hotfix(s):                 8 Hotfix(s) Installed.
```

## PowerUp.ps1

```
[*] Checking %PATH% for potentially hijackable .dll locations...
HijackablePath : C:\Ruby26-x64\bin\
AbuseFunction  : Write-HijackDll -OutputFile 'C:\Ruby26-x64\bin\\wlbsctrl.dll' -Command '...'

HijackablePath : C:\Users\Jerren\AppData\Local\Microsoft\WindowsApps\
AbuseFunction  : Write-HijackDll -OutputFile 'C:\Users\Jerren\AppData\Local\Microsoft\WindowsApps\\wlbsctrl.dll' -Command '...'

HijackablePath : C:\Users\Jerren\AppData\Local\Yarn\bin\
AbuseFunction  : Write-HijackDll -OutputFile 'C:\Users\Jerren\AppData\Local\Yarn\bin\\wlbsctrl.dll' -Command '...'

HijackablePath : C:\Users\Jerren\AppData\Roaming\npm\
AbuseFunction  : Write-HijackDll -OutputFile 'C:\Users\Jerren\AppData\Roaming\npm\\wlbsctrl.dll' -Command '...'

[*] Checking for Autologon credentials in registry...
DefaultUserName      : Jerren
DefaultPassword      : CatastropheToes543
```

## PEAS

```
[?] Windows vulns search powered by Watson(https://github.com/rasta-mouse/Watson)
 [*] OS Version: 1909 (18363)
 [*] Enumerating installed KBs...
 [!] CVE-2019-1385 : VULNERABLE
  [>] https://www.youtube.com/watch?v=K6gHnr-VkAg

 [!] CVE-2019-1405 : VULNERABLE
  [>] https://www.nccgroup.trust/uk/about-us/newsroom-and-events/blogs/2019/november/cve-2019-1405-and-cve-2019-1322-elevation-to-system-via-the-upnp-device-host-service-and-the-update-orchestrator-service/
  [>] https://github.com/apt69/COMahawk

 [!] CVE-2020-0668 : VULNERABLE
m4n/SysTracingPochub.com/it

 [!] CVE-2020-0683 : VULNERABLE
  [>] https://github.com/padovah4ck/CVE-2020-0683
  [>] https://raw.githubusercontent.com/S3cur3Th1sSh1t/Creds/master/PowershellScripts/cve-2020-0683.ps1

 [!] CVE-2020-1013 : VULNERABLE
  [>] https://www.gosecure.net/blog/2020/09/08/wsus-attacks-part-2-cve-2020-1013-a-windows-10-local-privilege-escalation-1-day/

 [!] CVE-2020-0796 : VULNERABLE
ithub.com/danigargu/CVE-2020-0796 (smbghost)

 [*] Finished. Found 6 potential vulnerabilities.

͹ Current TCP Listening Ports
State             Process ID      Process NameRemote Address        Remote Port
TCP        127.0.0.1             14147         0.0.0.0               0               Listening         6296            c:\xampp\filezillaftp\filezillaserver.exe

Enumerating Security Packages Credentials
Version: NetNTLMv2
101000000000000c63372a4d796d7018ab30d157ff118430000000008003000300000000000000000000000002000000dfe4e3589b6595250d5a741bcb63fb976be7f41b8ad689b0e5a0f0b7d1b3e390a00100000000000000000000000000000000000090000000000000000000000
```
