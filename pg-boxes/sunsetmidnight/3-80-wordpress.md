# 3 :80 wordpress

```
$ wpscan --url http://sunset-midnight/
[+] robots.txt found: http://sunset-midnight/robots.txt
 | Interesting Entries:
 |  - /wp-admin/
 |  - /wp-admin/admin-ajax.php

[+] WordPress version 5.4.2 identified (Insecure, released on 2020-06-10).

[+] Upload directory has listing enabled: http://sunset-midnight/wp-content/uploads/

[+] WordPress version 5.4.2 identified (Insecure, released on 2020-06-10).

[i] Plugin(s) Identified:
[+] simply-poll-master
 | Location: http://sunset-midnight/wp-content/plugins/simply-poll-master/
 |
 | Found By: Urls In Homepage (Passive Detection)
 | Confirmed By: Urls In 404 Page (Passive Detection)
 |
 | Version: 1.5 (100% confidence)
 
[i] User(s) Identified:
[+] admin
 | Found By: Author Posts - Author Pattern (Passive Detection)
```
