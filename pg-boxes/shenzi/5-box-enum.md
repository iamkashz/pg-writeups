# 5 box enum

```
PS C:\xampp\htdocs\shenzi> more wp-config.php
	define( 'DB_NAME', 'shenzi' );
	define( 'DB_USER', 'root' );
	define( 'DB_PASSWORD', '' );
	define( 'DB_HOST', 'localhost' );
```

## PowerUp.ps1

```
[*] Checking %PATH% for potentially hijackable .dll locations...
HijackablePath : C:\Users\shenzi\AppData\Local\Microsoft\WindowsApps\
AbuseFunction  : Write-HijackDll -OutputFile 'C:\Users\shenzi\AppData\Local\Microsoft\WindowsApps\\wlbsctrl.dll'
                 -Command '...'

[*] Checking for AlwaysInstallElevated registry key...
OutputFile    :
AbuseFunction : Write-UserAddMSI
```

## Checks

```
PS C:\Users\shenzi\Desktop> cmd.exe /c reg query HKCU\SOFTWARE\Policies\Microsoft\Windows\Installer /v AlwaysInstallElevated
HKEY_CURRENT_USER\SOFTWARE\Policies\Microsoft\Windows\Installer
    AlwaysInstallElevated    REG_DWORD    0x1

PS C:\Users\shenzi\Desktop> cmd.exe /c reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\Installer /v AlwaysInstallElevated
HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Installer
    AlwaysInstallElevated    REG_DWORD    0x1
```
