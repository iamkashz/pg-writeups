# 2 :8089 DevOps dashboard

```
http://192.168.155.99:8089/
form action='http://169.254.109.39:33333/list-current-deployments' method='GET'>
<form action='http://169.254.109.39:33333/list-running-procs' method='GET'>
<form action='http://169.254.109.39:33333/list-active-nodes' method='GET'>

# possibly nothing; as its going out of the box; did nmap - no ports open
# but we have 33333 open on target
# time to burp

GET /list-current-deployments HTTP/1.1
Host: 169.254.109.39:33333
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Connection: close
Referer: http://192.168.155.99:8089/
Upgrade-Insecure-Requests: 1

# update target to http://192.168.155.99:33333 (top right side)

HTTP/1.1 200 OK
Content-Length: 45
Server: Microsoft-HTTPAPI/2.0
Date: Fri, 20 Aug 2021 20:19:41 GMT
Connection: close

<p>Cannot "GET" /list-current-deployments</p>

# trying POST; cleaning out request headers that are not needed (not required to do!)
POST /list-current-deployments HTTP/1.1
Host: 169.254.109.39:33333
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Content-Length: 0

HTTP/1.1 200 OK
Content-Length: 22
Server: Microsoft-HTTPAPI/2.0
Date: Fri, 20 Aug 2021 20:20:26 GMT

<p>Not Implemented</p>

# trying different endpoint
POST /list-running-procs HTTP/1.1
Host: 169.254.109.39:33333
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Content-Length: 0

HTTP/1.1 200 OK
Content-Length: 2712
Server: Microsoft-HTTPAPI/2.0
Date: Fri, 20 Aug 2021 20:21:08 GMT

<with output of running procs>

# using curl for better viewing.
```
