# 7 fail privesc\_2 InspIRCd

```
ServiceName   : InspIRCd
Path          : C:\Program Files (x86)\InspIRCd\inspircd.exe
StartName     : NT AUTHORITY\NetworkService
AbuseFunction : Write-ServiceBinary -ServiceName 'InspIRCd' -Path <HijackPath>


# check if dir is writable
$ accesschk.exe /accepteula -uqvwd "C:\Program Files (x86)"
c:\Users\daisy>accesschk.exe /accepteula -uqvwd "C:\Program Files (x86)"
C:\Program Files (x86)
  Medium Mandatory Level (Default) [No-Write-Up]
  RW NT SERVICE\TrustedInstaller
        FILE_ALL_ACCESS
  RW NT AUTHORITY\SYSTEM
        FILE_ADD_FILE
        FILE_ADD_SUBDIRECTORY
        FILE_LIST_DIRECTORY
        FILE_READ_ATTRIBUTES
        FILE_READ_EA
        FILE_TRAVERSE
        FILE_WRITE_ATTRIBUTES
        FILE_WRITE_EA
        DELETE
        SYNCHRONIZE
        READ_CONTROL
  RW BUILTIN\Administrators
        FILE_ADD_FILE
        FILE_ADD_SUBDIRECTORY
        FILE_LIST_DIRECTORY
        FILE_READ_ATTRIBUTES
        FILE_READ_EA
        FILE_TRAVERSE
        FILE_WRITE_ATTRIBUTES
        FILE_WRITE_EA
        DELETE
        SYNCHRONIZE
        READ_CONTROL
		
# we cannot do anything; ignore this.
```
