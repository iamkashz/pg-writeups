# 4 box enum

```
www-data@bottleneck:~/html/web_utils$ ls -la
total 8
drwxrwxr-x 2 www-data www-data 4096 Mar  2  2020 .
drwxr-xr-x 7 root     root     4096 Sep 26  2019 ..
lrwxrwxrwx 1 root     root       18 Mar  2  2020 clear_logs -> /opt/clear_logs.sh

www-data@bottleneck:/var$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
[truncated]
bytevsbyte:x:1000:1000:bytevsbyte:/home/bytevsbyte:/bin/bash

www-data@bottleneck:/opt$ ls -la
total 16
drwxr-xr-x  2 root       root       4096 Sep 27  2019 .
drwxr-xr-x 20 root       root       4096 Feb 20  2020 ..
-rwxr--r--  1 bytevsbyte bytevsbyte   43 Sep 27  2019 clear_logs.sh
-rw-r--r--  1 root       root        359 Sep 27  2019 ids_strong_bvb.py

www-data@bottleneck:/opt$ cat clear_logs.sh
#!/bin/bash
rm -f /var/log/soc/intrusion_*

www-data@bottleneck:/opt$ cat ids_strong_bvb.py
#!/usr/bin/python3
#-*- coding: utf-8 -*-
import smtplib

address = 'soc.protections@beerpwn.it'
data = str(input('report: '))
print('[+] sending the message: ' + str(data))
try:
    server = smtplib.SMTP("beerpwn.it", None, None)
    server.sendmail("local@bottleneck", address, str(data))
    server.close()
except Exception as e:
    pass
```
