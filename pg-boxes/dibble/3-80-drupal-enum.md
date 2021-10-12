# 3 :80 drupal enum

```
http://192.168.213.110/
Landing Page
| contains posts - some form of CMS
# view source
<meta name="Generator" content="Drupal 9 (https://www.drupal.org)" />

# possible username admin

192.168.213.110/node/1 > post on sql injection
192.168.213.110/node/2 > post on xml tutorial
http://192.168.213.110/node/3 > post on LFI
http://192.168.213.110/node/4 > post on web exploitation

# from automator
| http-enum:
|   /rss.xml: RSS or Atom feed
|   /robots.txt: Robots file
|   /INSTALL.txt: Drupal file
|   /: Drupal version 9
|   /README.txt: Interesting, a readme.
|   /contact/: Potentially interesting folder
|   /core/: Potentially interesting folder w/ directory listing
|   /icons/: Potentially interesting folder w/ directory listing
|   /modules/: Potentially interesting folder w/ directory listing
|   /sites/: Potentially interesting folder w/ directory listing
|_  /themes/: Potentially interesting folder w/ directory listing

$ gobuster dir -u http://192.168.213.110 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 90
===============================================================
/contact              (Status: 200) [Size: 8187]
/search               (Status: 302) [Size: 382] [--> http://192.168.213.110/search/node]
/index.php            (Status: 200) [Size: 13708]
/themes               (Status: 301) [Size: 238] [--> http://192.168.213.110/themes/]
/user                 (Status: 302) [Size: 378] [--> http://192.168.213.110/user/login]
/modules              (Status: 301) [Size: 239] [--> http://192.168.213.110/modules/]
/admin                (Status: 403) [Size: 4306]
/node                 (Status: 200) [Size: 13655]
/sites                (Status: 301) [Size: 237] [--> http://192.168.213.110/sites/]
/Search               (Status: 302) [Size: 382] [--> http://192.168.213.110/search/node]
/Contact              (Status: 200) [Size: 8187]
/core                 (Status: 301) [Size: 236] [--> http://192.168.213.110/core/]
/profiles             (Status: 301) [Size: 240] [--> http://192.168.213.110/profiles/]
/README.txt           (Status: 200) [Size: 5971]
/vendor               (Status: 403) [Size: 199]
/robots.txt           (Status: 200) [Size: 1594]
/INSTALL.txt          (Status: 200) [Size: 95

http://192.168.213.110/robots.txt
User-agent: *
# CSS, JS, Images
Allow: /core/*.css$
Allow: /core/*.css?
Allow: /core/*.js$
Allow: /core/*.js?
Allow: /core/*.gif
Allow: /core/*.jpg
Allow: /core/*.jpeg
Allow: /core/*.png
Allow: /core/*.svg
Allow: /profiles/*.css$
Allow: /profiles/*.css?
Allow: /profiles/*.js$
Allow: /profiles/*.js?
Allow: /profiles/*.gif
Allow: /profiles/*.jpg
Allow: /profiles/*.jpeg
Allow: /profiles/*.png
Allow: /profiles/*.svg
# Directories
Disallow: /core/
Disallow: /profiles/
# Files
Disallow: /README.txt
Disallow: /web.config
# Paths (clean URLs)
Disallow: /admin/
Disallow: /comment/reply/
Disallow: /filter/tips
Disallow: /node/add/
Disallow: /search/
Disallow: /user/register/
Disallow: /user/password/
Disallow: /user/login/
Disallow: /user/logout/
# Paths (no clean URLs)
Disallow: /index.php/admin/
Disallow: /index.php/comment/reply/
Disallow: /index.php/filter/tips
Disallow: /index.php/node/add/
Disallow: /index.php/search/
Disallow: /index.php/user/password/
Disallow: /index.php/user/register/
Disallow: /index.php/user/login/
Disallow: /index.php/user/logout/

http://192.168.213.110/README.txt
Drupal README

http://192.168.213.110/web.config
# possible contains creds
# not loading properly; xml is loaded with comments

http://192.168.213.110/admin/
Access Denied

http://192.168.213.110/user/ > http://192.168.213.110/user/login
Login Page

# possible creds
http://192.168.213.110/sites/default/settings.php
```
