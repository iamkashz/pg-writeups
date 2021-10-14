# 3 :8080 nodebb

```
http://192.168.136.69:8080/
NodeBB landing page
| nodejs based forum software
# view source
<meta property="og:url" content="http://localhost:4567" />
# something on localhost:4567

# nmapAutomator
| http-enum:
|   /login/: Login page
|   /robots.txt: Robots file
|_  /top/: Potentially interesting folder

$ gobuster dir -u http://192.168.136.69:8080/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x js,php,html,txt -t 90
===============================================================
/login                (Status: 200) [Size: 11618]
/register             (Status: 200) [Size: 14357]
/top                  (Status: 200) [Size: 18180]
/uploads              (Status: 302) [Size: 52] [--> /assets/uploads/?v=7sgruj70sic]
/users                (Status: 302) [Size: 28] [--> /login]
/admin                (Status: 302) [Size: 36] [--> /login?local=1]
/categories           (Status: 200) [Size: 18970]
/assets               (Status: 301) [Size: 179] [--> /assets/]
/flags                (Status: 500) [Size: 10870]
/groups               (Status: 302) [Size: 28] [--> /login]
/tags                 (Status: 302) [Size: 28] [--> /login]
/Login                (Status: 200) [Size: 11618]
/popular              (Status: 200) [Size: 18355]
/api                  (Status: 200) [Size: 3255]
/recent               (Status: 200) [Size: 17544]
/robots.txt           (Status: 200) [Size: 111]
/ping                 (Status: 200) [Size: 3]
/reset                (Status: 200) [Size: 12470]
/chats                (Status: 302) [Size: 28] [--> /login]

http://192.168.136.69:8080/register
# registered as kashz:iamkashz

# http://192.168.136.69:8080/login gives empty page
http://192.168.136.69:8080/admin > http://192.168.136.69:8080/login?local=1
# login page
# default admin:admin does not work
Login Unsuccessful
Local login system has been disabled for non-privileged accounts.

http://192.168.136.69:8080/robots.txt
User-agent: *
Disallow: /admin/
Disallow: /reset/
Disallow: /compose
Sitemap: http://localhost:4567/sitemap.xml

http://192.168.136.69:8080/reset
Pass reset page

http://192.168.136.69:8080/ping
200

# found exploit for account-takeover
Using https://www.exploit-db.com/exploits/48875
# changed pass but 
Login Unsuccessful
Local login system has been disabled for non-privileged accounts.

http://192.168.136.69:8080/user/kashz/chats
Internal Error.
Oops! Looks like something went wrong!
/user/kashz/chats
You do not have enough privileges for this action.
```
