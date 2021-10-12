# 3 :80 sybaris

```
http://192.168.224.93/
Sybaris HTMLy blog 

$ gobuster dir -u http://192.168.224.93 -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 80
===============================================================
/themes               (Status: 301) [Size: 237] [--> http://192.168.224.93/themes/]
/index                (Status: 200) [Size: 7870]
/admin                (Status: 302) [Size: 0] [--> /login]
/upload.php           (Status: 302) [Size: 0] [--> /login]
/content              (Status: 301) [Size: 238] [--> http://192.168.224.93/content/]
/login                (Status: 200) [Size: 3046]
/Index                (Status: 200) [Size: 7870]
/system               (Status: 301) [Size: 237] [--> http://192.168.224.93/system/]
/front                (Status: 301) [Size: 0] [--> /]
/cache                (Status: 301) [Size: 236] [--> http://192.168.224.93/cache/]
/logout               (Status: 302) [Size: 0] [--> /login]
/lang                 (Status: 301) [Size: 235] [--> http://192.168.224.93/lang/]
/config               (Status: 403) [Size: 208]
/robots.txt           (Status: 200) [Size: 1154]
/LICENSE.txt          (Status: 200) [Size: 18092]
/INDEX                (Status: 200) [Size: 7870]

# most pages are unnaccessible

http://192.168.224.93/login
Sybaris Login Page

http://192.168.224.93/robots.txt
User-agent: *

# Disallow directories
Disallow: /config/
Disallow: /system/
Disallow: /themes/
Disallow: /vendor/
Disallow: /cache/

# Disallow files
Disallow: /changelog.txt
Disallow: /composer.json
Disallow: /composer.lock
Disallow: /composer.phar

# Disallow paths
Disallow: /search/
Disallow: /admin/

# Allow themes
Allow: /themes/*/css/
Allow: /themes/*/images/
Allow: /themes/*/img/
Allow: /themes/*/js/
Allow: /themes/*/fonts/

# Allow content images
Allow: /content/images/*.jpg
Allow: /content/images/*.png
Allow: /content/images/*.gif


http://192.168.224.93/composer.json
"config": {
		"vendor-dir": "system/vendor/",
		"optimize-autoloader": true,
		"platform": {
			"php": "5.3"
}
```
