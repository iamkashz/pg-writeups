# 5 box enum max

```
max@sorcerer:/home$ ls -la
total 28
drwxr-xr-x  7 root    root    4096 Sep 24  2020 .
drwxr-xr-x 18 root    root    4096 Sep 24  2020 ..
drwxr-xr-x  2 dennis  dennis  4096 Sep 24  2020 dennis
drwxr-xr-x  2 francis francis 4096 Sep 24  2020 francis
drwxr-xr-x  3 max     max     4096 Sep 24  2020 max
drwxr-xr-x  2 miriam  miriam  4096 Sep 24  2020 miriam
drwxr-xr-x  2 sofia   sofia   4096 Sep 24  2020 sofia

max@sorcerer:~$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
[truncated]
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
francis:x:1000:1000::/home/francis:/bin/bash
sofia:x:1001:1001::/home/sofia:/bin/bash
miriam:x:1002:1002::/home/miriam:/bin/bash
max:x:1003:1003::/home/max:/bin/bash
dennis:x:1004:1004::/home/dennis:/bin/bash
tomcat:x:1005:1005::/opt/tomcat:/bin/false

# tried user:VTUD2XxJjf5LPmu6 => none worked.
```
