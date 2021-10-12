# 5 box enum charles

```
charles@pelican:~/k$ cat /etc/passwd
root:x:0:0:root:/root:/bin/bash
[truncated]
charles:x:1000:1000::/home/charles:/bin/bash
```

## SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/bin/password-store
------------------------------
```

## PEAS

```
╣ Processes, Cron, Services, Timers & Sockets ╠
root       470  0.0  0.1   8504  2760 ?        Ss   13:44   0:00 /usr/sbin/cron -f
root       475  0.0  0.1   9468  2468 ?        S    13:44   0:00  _ /usr/sbin/CRON -f
root       489  0.0  0.0   2388  1596 ?        Ss   13:44   0:00      _ /bin/sh -c while true; do chown -R charles:charles /opt/zookeeper && chown -R charles:charles /opt/exhibitor && sleep 1; done
root      8793  0.0  0.0   5260   744 ?        S    14:09   0:00          _ sleep 1

╣ Cron jobs
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

@reboot         root    /usr/bin/password-store
@reboot         root    while true; do chown -R charles:charles /opt/zookeeper && chown -R charles:charles /opt/exhibitor && sleep 1; done

╣ Checking 'sudo -l', /etc/sudoers, and /etc/sudoers.d
Matching Defaults entries for charles on pelican:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User charles may run the following commands on pelican:
    (ALL) NOPASSWD: /usr/bin/gcore

╣ Analyzing Cacti Files (limit 70)
drwxr-xr-x 2 charles charles 4096 Feb 20  2014 /opt/zookeeper/src/contrib/monitoring/cacti
```

## pspy

```
2021/08/31 14:17:10 CMD: UID=0    PID=12536  | /bin/sh -c while true; do chown -R charles:charles /opt/zookeeper && chown -R charles:charles /opt/exhibitor && sleep 1; done
2021/08/31 14:17:10 CMD: UID=0    PID=12537  | /bin/sh -c while true; do chown -R charles:charles /opt/zookeeper && chown -R charles:charles /opt/exhibitor && sleep 1; done
2021/08/31 14:17:10 CMD: UID=0    PID=12538  | /bin/sh -c while true; do chown -R charles:charles /opt/zookeeper && chown -R charles:charles /opt/exhibitor && sleep 1; done
```
