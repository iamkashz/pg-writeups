# 5 box enum

## PEAS

```
╣ Users
Current user: ariah
Current groups: Domain Users, Everyone, Users, Network, Authenticated Users, This Organization, Local account, NTLM Authentication

╣ Current TCP Listening Ports
Protocol   Local Address         Local Port    Remote Address        Remote Port     State             Process ID      Process Name
TCP        127.0.0.1             14147         0.0.0.0               0               Listening         2000            FileZilla Server
  
╣ Enumerating Security Packages Credentials
Version: NetNTLMv2
Hash:    ariah::NICKEL:1122334455667788:cc82f6ee1002ccca239f42bba5dd5041:01010000000000001a0d24010596d7016b93430d8ef821470000000008003000300000000000000000000000002000008da3dcf95e2925ce59dd648e73bb4a25b17d5c66
1e53aac37bd3fbccc64ab49e0a00100000000000000000000000000000000000090000000000000000000000

╣ Looking for possible password files in users homes
C:\Users\All Users\Microsoft\UEV\InboxTemplates\RoamingCredentialSettings.xml
```

## PowerUp.ps1

```
[*] Checking %PATH% for potentially hijackable .dll locations...
HijackablePath : C:\Users\ariah\AppData\Local\Microsoft\WindowsApps\
AbuseFunction  : Write-HijackDll -OutputFile 'C:\Users\ariah\AppData\Local\Microsoft\WindowsApps\\wlbsctrl.dll' -Command '...'
```

## Seatbelt.exe

```
===== InstalledProducts ======
  DisplayName                    : FileZilla Server
  DisplayVersion                 : beta 0.9.60
  Publisher                      : FileZilla Project
  InstallDate                    : 1/1/0001 12:00:00 AM
  Architecture                   : x86
  
====== InterestingFiles ======
Accessed      Modified      Path
----------    ----------    -----
2021-08-20    2020-09-01    C:\Users\All Users\ssh\ssh_host_rsa_key
2021-08-20    2020-09-01    C:\Users\All Users\ssh\ssh_host_rsa_key.pub
```
