# 7 privesc\_2

linPEAS showed vulnerable to smbGhost

### Requirement

```
# OS Name:                   Microsoft Windows 10 Pro
# OS Version:                10.0.18362 N/A Build 18362
# PS C:\users\public> (Get-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion" -Name ReleaseId).ReleaseId
1903

# needs 445 open
TCP    0.0.0.0:445            0.0.0.0:0              LISTENING       4
```

## [smbGhost Privilege Escalation ](https://app.gitbook.com/s/fHlnRfvCUtetz8zIeUjA/windows-exploits/smbghost)
