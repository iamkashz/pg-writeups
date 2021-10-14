# 5 box enum PEAS

```
╣ Active Ports
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      -

╣ Checking 'sudo -l', /etc/sudoers, and /etc/sudoers.d
Matching Defaults entries for www-data on bottleneck:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User www-data may run the following commands on bottleneck:
    (bytevsbyte) NOPASSWD: /var/www/html/web_utils/clear_logs
	
╣ Users with console
bytevsbyte:x:1000:1000:bytevsbyte:/home/bytevsbyte:/bin/bash
root:x:0:0:root:/root:/bin/bash

╣ PHP exec extensions
drwxr-xr-x 2 root root 4096 Sep 25  2019 /etc/nginx/sites-enabled
drwxr-xr-x 2 root root 4096 Sep 25  2019 /etc/nginx/sites-enabled
lrwxrwxrwx 1 root root 29 Sep 25  2019 /etc/nginx/sites-enabled/bottleneck -> ../sites-available/bottleneck
```
