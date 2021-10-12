# 3 :80 wpscan

```
$ wpscan --url http://muddy.ugc -e u,vp

[+] Headers
 | Interesting Entry: Server: Apache/2.4.38 (Debian)
 
[+] XML-RPC seems to be enabled: http://muddy.ugc/xmlrpc.php

[+] WordPress version 5.7 identified (Insecure, released on 2021-03-09).
 | Found By: Rss Generator (Passive Detection)
 |  - http://muddy.ugc/index.php/feed/, <generator>https://wordpress.org/?v=5.7</generator>
 |  - http://muddy.ugc/index.php/comments/feed/, <generator>https://wordpress.org/?v=5.7</generator
 
[+] WordPress theme in use: shapely
 | Location: http://muddy.ugc/wp-content/themes/shapely/
  | Readme: http://muddy.ugc/wp-content/themes/shapely/readme.txt
 | [!] The version is out of date, the latest version is 1.2.14
 
[i] Plugin(s) Identified:
[+] kali-forms
 | Location: http://muddy.ugc/wp-content/plugins/kali-forms/
 | [!] The version is out of date, the latest version is 2.3.9
 | Version: 2.3.0 (80% confidence)

[i] No Users Found.
```
