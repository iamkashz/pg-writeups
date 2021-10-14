# 7 privesc > root

## SuidEnum

```
[~] Custom SUID Binaries (Interesting Stuff)
------------------------------
/usr/test/testlib
------------------------------
```

## PEAS

```
╣ Cron jobs
*/5 * * * * /opt/clear_logs.sh
```

## Trying /usr/test/testlib

```
$ file testlib
testlib: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=cfa09044d8f9f24e041d3ae81107ff6a91d775d5, for GNU/Linux 3.2.0, not stripped

bytevsbyte@bottleneck:/usr/test$ ls -la
total 32
drwxr-x---  2 root tester  4096 Sep 27  2019 .
drwxr-xr-x 14 root root    4096 Sep 26  2019 ..
-rwsr-x---  1 root tester 16528 Sep 26  2019 testlib
-rw-r-----  1 root tester   281 Sep 27  2019 testlib.c

bytevsbyte@bottleneck:/usr/test$ cat testlib.c
#include <dlfcn.h>
#include <unistd.h>

int main(int argc, char *argv[]){
    void *handle;
    int (*function)();
    if(argc < 2)
        return 1;
    handle = dlopen(argv[1], RTLD_LAZY);
    function = dlsym(handle, "test_this");
    function();
    return 0;
}

# accepts an argument
# opens the file
# function "test_this" is found
# and executed
# always got segmentation fault
```

## Trying cronjob

```
bytevsbyte@bottleneck:/tmp$ ls -la /opt/clear_logs.sh
-rwxr--r-- 1 bytevsbyte bytevsbyte 43 Sep 27  2019 /opt/clear_logs.sh
```
