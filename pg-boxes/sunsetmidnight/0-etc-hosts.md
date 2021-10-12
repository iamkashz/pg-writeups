# 0 /etc/hosts

```
$ curl http://192.168.122.88

$ curl http://192.168.122.88 -v
*   Trying 192.168.122.88:80...
* Connected to 192.168.122.88 (192.168.122.88) port 80 (#0)
> GET / HTTP/1.1
> Host: 192.168.122.88
> User-Agent: curl/7.74.0
> Accept: */*
>
* Mark bundle as not supporting multiuse
< HTTP/1.1 301 Moved Permanently
< Date: Wed, 25 Aug 2021 01:51:43 GMT
< Server: Apache/2.4.38 (Debian)
< X-Redirect-By: WordPress
< Location: http://sunset-midnight/
< Content-Length: 0
< Content-Type: text/html; charset=UTF-8
<
* Connection #0 to host 192.168.122.88 left intact

# adding to /etc/hosts
192.168.122.88 sunset-midnight
```
