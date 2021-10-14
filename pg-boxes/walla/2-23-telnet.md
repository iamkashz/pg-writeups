# 2 :23 telnet

```
$ nmap -n -sV -Pn --script "*telnet* and safe" -p 23 192.168.125.97
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times will be slower.
Starting Nmap 7.91 ( https://nmap.org ) at 2021-09-01 12:45 PDT
Nmap scan report for 192.168.125.97
Host is up (0.072s latency).

PORT   STATE SERVICE VERSION
23/tcp open  telnet  Linux telnetd
| telnet-encryption:
|_  Telnet server does not support encryption
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

# config files for telnet
- /etc/inetd.conf
- /etc/xinetd.d/telnet
- /etc/xinetd.d/stelnet

$ telnet 192.168.125.97 23
Trying 192.168.125.97...
Connected to 192.168.125.97.
Escape character is '^]'.
Linux Telnetd 0.17
Debian GNU/Linux 10
walla login: admin
Password:

Login incorrect
walla login:


# known exploit for Linux Telnetd <=0.17
https://www.exploit-db.com/exploits/48170

Not working
```
