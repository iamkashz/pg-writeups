# 5 :50080 davtest

```
$ davtest -url http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/ -cleanup -auth admin:admin
********************************************************
 Testing DAV connection
OPEN            SUCCEED:                http://192.168.136.147:50080/cloud/remote.php/dav/files/admin
********************************************************
NOTE    Random string for this session: msgaP4b
********************************************************
 Creating directory
MKCOL           SUCCEED:                Created http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b
********************************************************
 Sending test files
PUT     jhtml   SUCCEED:        http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b/davtest_msgaP4b.jhtml
PUT     pl      SUCCEED:        http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b/davtest_msgaP4b.pl
PUT     cgi     SUCCEED:        http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b/davtest_msgaP4b.cgi
PUT     shtml   SUCCEED:        http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b/davtest_msgaP4b.shtml
PUT     html    SUCCEED:        http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b/davtest_msgaP4b.html
PUT     jsp     SUCCEED:        http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b/davtest_msgaP4b.jsp
PUT     aspx    SUCCEED:        http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b/davtest_msgaP4b.aspx
PUT     txt     SUCCEED:        http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b/davtest_msgaP4b.txt
PUT     php     SUCCEED:        http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b/davtest_msgaP4b.php
PUT     cfm     SUCCEED:        http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b/davtest_msgaP4b.cfm
PUT     asp     SUCCEED:        http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b/davtest_msgaP4b.asp
********************************************************
 Checking for test file execution
EXEC    jhtml   FAIL
EXEC    pl      FAIL
EXEC    cgi     FAIL
EXEC    shtml   FAIL
EXEC    html    SUCCEED:        http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b/davtest_msgaP4b.html
EXEC    jsp     FAIL
EXEC    aspx    FAIL
EXEC    txt     SUCCEED:        http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b/davtest_msgaP4b.txt
EXEC    php     FAIL
EXEC    cfm     FAIL
EXEC    asp     FAIL
********************************************************
 Cleaning up
DELETE          SUCCEED:        http://192.168.136.147:50080/cloud/remote.php/dav/files/admin/DavTestDir_msgaP4b
```
