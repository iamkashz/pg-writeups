# 4 :25 smtp

```
# automator
192.168.174.56: admin exists
192.168.174.56: ftp exists
192.168.174.56: mail exists
192.168.174.56: mysql exists
192.168.174.56: postfix exists
192.168.174.56: postgres exists
192.168.174.56: postmaster exists
192.168.174.56: root exists
192.168.174.56: sys exists
192.168.174.56: www-data exists
192.168.174.56: www exists
192.168.174.56: webmaster exists

$ smtp-user-enum -M VRFY -U /usr/share/seclists/Usernames/Names/names.txt -t 192.168.174.56
Starting smtp-user-enum v1.2 ( http://pentestmonkey.net/tools/smtp-user-enum )

 ----------------------------------------------------------
|                   Scan Information                       |
 ----------------------------------------------------------

Mode ..................... VRFY
Worker Processes ......... 5
Usernames file ........... /usr/share/seclists/Usernames/Names/names.txt
Target count ............. 1
Username count ........... 10177
Target TCP port .......... 25
Query timeout ............ 5 secs
Target domain ............

######## Scan started at Mon Aug 30 12:18:06 2021 #########
192.168.174.56: admin exists
192.168.174.56: bin exists
192.168.174.56: irc exists
192.168.174.56: mail exists
192.168.174.56: man exists
192.168.174.56: root exists
192.168.174.56: sys exists
######## Scan completed at Mon Aug 30 12:28:09 2021 #########
```
