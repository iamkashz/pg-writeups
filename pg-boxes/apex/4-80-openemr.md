# 4 :80 openemr

```
http://192.168.137.145/openemr/interface/login/login.php?site=default
OpenEMR Login

# default creds not working
admin:pass

$ gobuster dir -u http://192.168.137.145/openemr/ -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,html,txt -t 80
===============================================================
/modules              (Status: 301) [Size: 328] [--> http://192.168.137.145/openemr/modules/]
/common               (Status: 301) [Size: 327] [--> http://192.168.137.145/openemr/common/]
/services             (Status: 301) [Size: 329] [--> http://192.168.137.145/openemr/services/]
/library              (Status: 301) [Size: 328] [--> http://192.168.137.145/openemr/library/]
/public               (Status: 301) [Size: 327] [--> http://192.168.137.145/openemr/public/]
/templates            (Status: 301) [Size: 330] [--> http://192.168.137.145/openemr/templates/]
/version.php          (Status: 200) [Size: 0]
/admin.php            (Status: 200) [Size: 937]
/portal               (Status: 301) [Size: 327] [--> http://192.168.137.145/openemr/portal/]
/images               (Status: 301) [Size: 327] [--> http://192.168.137.145/openemr/images/]
/index.php            (Status: 302) [Size: 0] [--> interface/login/login.php?site=default]
/tests                (Status: 301) [Size: 326] [--> http://192.168.137.145/openemr/tests/]
/sites                (Status: 301) [Size: 326] [--> http://192.168.137.145/openemr/sites/]
/custom               (Status: 301) [Size: 327] [--> http://192.168.137.145/openemr/custom/]
/contrib              (Status: 301) [Size: 328] [--> http://192.168.137.145/openemr/contrib/]
/interface            (Status: 301) [Size: 330] [--> http://192.168.137.145/openemr/interface/]
/vendor               (Status: 301) [Size: 327] [--> http://192.168.137.145/openemr/vendor/]
/config               (Status: 301) [Size: 327] [--> http://192.168.137.145/openemr/config/]
/setup.php            (Status: 500) [Size: 0]
/Documentation        (Status: 301) [Size: 334] [--> http://192.168.137.145/openemr/Documentation/]
/sql                  (Status: 301) [Size: 324] [--> http://192.168.137.145/openemr/sql/]
/controller.php       (Status: 200) [Size: 37]
/LICENSE              (Status: 200) [Size: 35147]
/ci                   (Status: 301) [Size: 323] [--> http://192.168.137.145/openemr/ci/]
/cloud                (Status: 301) [Size: 326] [--> http://192.168.137.145/openemr/cloud/]
/ccr                  (Status: 301) [Size: 324] [--> http://192.168.137.145/openemr/ccr/]
/patients             (Status: 301) [Size: 329] [--> http://192.168.137.145/openemr/patients/]
/repositories         (Status: 301) [Size: 333] [--> http://192.168.137.145/openemr/repositories/]
/myportal             (Status: 301) [Size: 329] [--> http://192.168.137.145/openemr/myportal/]
/entities             (Status: 301) [Size: 329] [--> http://192.168.137.145/openemr/entities/]
/controllers          (Status: 301) [Size: 332] [--> http://192.168.137.145/openemr/controllers/]

http://192.168.137.145/openemr/admin.php
OpenEMR Site Administration
DBNAME: openemr
Version: 5.0.1 (1)

All exploits are Authenticated; nothing here.
```
