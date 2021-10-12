# 7 box enum

## PEAS

```
╣ Active Ports
╚ https://book.hacktricks.xyz/linux-unix/privilege-escalation#open-ports
tcp        0      0 127.0.0.53:53           0.0.0.0:*               LISTEN      -

╣ My user
uid=1000(brian.moore) gid=1000(brian.moore) groups=1000(brian.moore),8(mail),997(filter)

╣ Users with console
brian.moore:x:1000:1000::/home/brian.moore:/bin/bash
claire.madison:x:1002:1002::/home/claire.madison:/bin/bash
filter:x:997:997:Postfix Filters:/var/spool/filter:/bin/sh
hr:x:1005:1005::/home/hr:/bin/sh
it:x:1006:1006::/home/it:/bin/sh
legal:x:1007:1007::/home/legal:/bin/sh
mike.ross:x:1001:1001::/home/mike.ross:/bin/bash
root:x:0:0:root:/root:/bin/bash
sales:x:1008:1008::/home/sales:/bin/sh
sarah.lorem:x:1003:1003::/home/sarah.lorem:/bin/bash

╣ Readable files belonging to root and readable by me but not world readable
-rwxrwx--- 1 root filter 1184 Aug 25 00:24 /etc/postfix/disclaimer
```
