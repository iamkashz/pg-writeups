# 2 :113 ident

```
# enumerating owner of a tcp connection
$ ident-user-enum 192.168.197.60 22 113 5432 8080 10000
ident-user-enum v1.0 ( http://pentestmonkey.net/tools/ident-user-enum )

192.168.197.60:22       root
192.168.197.60:113      nobody
192.168.197.60:5432     <unknown>
192.168.197.60:8080     <unknown>
192.168.197.60:10000    eleanor

# possible username: eleanor
```
