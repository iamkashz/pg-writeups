# 3 ldap\_1

```
Using https://book.hacktricks.xyz/pentesting/pentesting-ldap

# basic enumerating using py3:ldap
# tried port 636 didnt work, 389 worked
# automated scan
$ nmap -n -sV --script "ldap* and not brute" 192.168.136.122

# manual
$ python3
Python 3.9.2 (default, Feb 28 2021, 17:03:44)
[GCC 10.2.1 20210110] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import ldap3
>>> server = ldap3.Server('192.168.136.122', get_info = ldap3.ALL, port=389, use_ssl = False)
>>> connection = ldap3.Connection(server)
>>> connection.bind()
True
>>> server.info
DSA info (from DSE):
  Supported LDAP versions: 3, 2
  Naming contexts:
    DC=hutch,DC=offsec
    CN=Configuration,DC=hutch,DC=offsec
    CN=Schema,CN=Configuration,DC=hutch,DC=offsec
    DC=DomainDnsZones,DC=hutch,DC=offsec
    DC=ForestDnsZones,DC=hutch,DC=offsec
	Supported controls:
    1.2.840.113556.1.4.1338 - Verify name - Control - MICROSOFT
    1.2.840.113556.1.4.1339 - Domain scope - Control - MICROSOFT
    1.2.840.113556.1.4.1340 - Search options - Control - MICROSOFT
    1.2.840.113556.1.4.1341 - RODC DCPROMO - Control - MICROSOFT
    1.2.840.113556.1.4.1413 - Permissive modify - Control - MICROSOFT
    1.2.840.113556.1.4.1504 - Attribute scoped query - Control - MICROSOFT
    1.2.840.113556.1.4.1852 - User quota - Control - MICROSOFT
    1.2.840.113556.1.4.1907 - Server shutdown notify - Control - MICROSOFT
    1.2.840.113556.1.4.1948 - Range retrieval no error - Control - MICROSOFT
    1.2.840.113556.1.4.1974 - Server force update - Control - MICROSOFT
    1.2.840.113556.1.4.2026 - Input DN - Control - MICROSOFT
    1.2.840.113556.1.4.2064 - Show recycled - Control - MICROSOFT
    1.2.840.113556.1.4.2065 - Show deactivated link - Control - MICROSOFT
    1.2.840.113556.1.4.2066 - Policy hints [DEPRECATED] - Control - MICROSOFT
    1.2.840.113556.1.4.2090 - DirSync EX - Control - MICROSOFT
    1.2.840.113556.1.4.2204 - Tree deleted EX - Control - MICROSOFT
    1.2.840.113556.1.4.2205 - Updates stats - Control - MICROSOFT
    1.2.840.113556.1.4.2206 - Search hints - Control - MICROSOFT
    1.2.840.113556.1.4.2211 - Expected entry count - Control - MICROSOFT
    1.2.840.113556.1.4.2239 - Policy hints - Control - MICROSOFT
    1.2.840.113556.1.4.2255 - Set owner - Control - MICROSOFT
    1.2.840.113556.1.4.2256 - Bypass quota - Control - MICROSOFT
    1.2.840.113556.1.4.2309
    1.2.840.113556.1.4.2330
    1.2.840.113556.1.4.2354
    1.2.840.113556.1.4.319 - LDAP Simple Paged Results - Control - RFC2696
    1.2.840.113556.1.4.417 - LDAP server show deleted objects - Control - MICROSOFT
    1.2.840.113556.1.4.473 - Sort Request - Control - RFC2891
    1.2.840.113556.1.4.474 - Sort Response - Control - RFC2891
    1.2.840.113556.1.4.521 - Cross-domain move - Control - MICROSOFT
    1.2.840.113556.1.4.528 - Server search notification - Control - MICROSOFT
    1.2.840.113556.1.4.529 - Extended DN - Control - MICROSOFT
    1.2.840.113556.1.4.619 - Lazy commit - Control - MICROSOFT
    1.2.840.113556.1.4.801 - Security descriptor flags - Control - MICROSOFT
    1.2.840.113556.1.4.802 - Range option - Control - MICROSOFT
    1.2.840.113556.1.4.805 - Tree delete - Control - MICROSOFT
    1.2.840.113556.1.4.841 - Directory synchronization - Control - MICROSOFT
    1.2.840.113556.1.4.970 - Get stats - Control - MICROSOFT
    2.16.840.1.113730.3.4.10 - Virtual List View Response - Control - IETF
    2.16.840.1.113730.3.4.9 - Virtual List View Request - Control - IETF
	Supported extensions:
    1.2.840.113556.1.4.1781 - Fast concurrent bind - Extension - MICROSOFT
    1.2.840.113556.1.4.2212 - Batch request - Extension - MICROSOFT
    1.3.6.1.4.1.1466.101.119.1 - Dynamic Refresh - Extension - RFC2589
    1.3.6.1.4.1.1466.20037 - StartTLS - Extension - RFC4511-RFC4513
    1.3.6.1.4.1.4203.1.11.3 - Who am I - Extension - RFC4532
  Supported features:
    1.2.840.113556.1.4.1670 - Active directory V51 - Feature - MICROSOFT
    1.2.840.113556.1.4.1791 - Active directory LDAP Integration - Feature - MICROSOFT
    1.2.840.113556.1.4.1935 - Active directory V60 - Feature - MICROSOFT
    1.2.840.113556.1.4.2080 - Active directory V61 R2 - Feature - MICROSOFT
    1.2.840.113556.1.4.2237 - Active directory W8 - Feature - MICROSOFT
    1.2.840.113556.1.4.800 - Active directory - Feature - MICROSOFT
  Supported SASL mechanisms:
    GSSAPI, GSS-SPNEGO, EXTERNAL, DIGEST-MD5
  Schema entry:
    CN=Aggregate,CN=Schema,CN=Configuration,DC=hutch,DC=offsec
Other:
  domainFunctionality:
    7
  forestFunctionality:
    7
  domainControllerFunctionality:
    7
  rootDomainNamingContext:
    DC=hutch,DC=offsec
  ldapServiceName:
    hutch.offsec:hutchdc$@HUTCH.OFFSEC
  isGlobalCatalogReady:
    TRUE
  supportedLDAPPolicies:
    MaxPoolThreads
    MaxPercentDirSyncRequests
    MaxDatagramRecv
    MaxReceiveBuffer
    InitRecvTimeout
    MaxConnections
    MaxConnIdleTime
    MaxPageSize
    MaxBatchReturnMessages
    MaxQueryDuration
    MaxDirSyncDuration
    MaxTempTableSize
    MaxResultSetSize
    MinResultSets
    MaxResultSetsPerConn
    MaxNotificationPerConn
    MaxValRange
    MaxValRangeTransitive
    ThreadMemoryLimit
    SystemMemoryLimitPercent
	serverName:
    CN=HUTCHDC,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=hutch,DC=offsec
  schemaNamingContext:
    CN=Schema,CN=Configuration,DC=hutch,DC=offsec
  isSynchronized:
    TRUE
  highestCommittedUSN:
    73800
  dsServiceName:
    CN=NTDS Settings,CN=HUTCHDC,CN=Servers,CN=Default-First-Site-Name,CN=Sites,CN=Configuration,DC=hutch,DC=offsec
  dnsHostName:
    hutchdc.hutch.offsec
  defaultNamingContext:
    DC=hutch,DC=offsec
  currentTime:
    20210907181510.0Z
  configurationNamingContext:
    CN=Configuration,DC=hutch,DC=offsec
	
# all objects in directory
>> connection.search(search_base='DC=hutch,DC=offsec', search_filter='(&(objectClass=*))', search_scope='SUBTREE', attributes='*')
True
>> connection.entries
# too big

# dump users info
>> connection.search(search_base='DC=hutch,DC=offsec', search_filter='(&(objectClass=person))', search_scope='SUBTREE', attributes='userPassword')
True
>>> connection.entries
[DN: CN=Guest,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:22.050518
, DN: CN=Rosaline Placidi,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:22.050554
, DN: CN=Otto Patry,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:22.050580
, DN: CN=Lyndsie Taunton,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:22.050606
, DN: CN=Arlyn Costello,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:22.050631
, DN: CN=Johnnie Sparwell,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:22.050656
, DN: CN=Ottilie Knee,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:22.050681
, DN: CN=Joan McKendry,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:22.050723
, DN: CN=Alexia Victoria,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:22.050755
, DN: CN=Jane Frarey,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:22.050780
, DN: CN=Editha Aburrow,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:22.050804
, DN: CN=Claus Luddy,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:22.050828
, DN: CN=Arthur Gitthouse,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:22.050852
, DN: CN=Freddy McSorley,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:22.050875
]

# fetching userPrincipalNames
>>> connection.search(search_base='DC=hutch,DC=offsec', search_filter='(&(objectClass=person))', search_scope='SUBTREE', attributes='userPrincipalName')
True
>>> connection.entries
[DN: CN=Guest,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:37.465500
, DN: CN=Rosaline Placidi,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:37.465542
    userPrincipalName: rplacidi@hutch.offsec
, DN: CN=Otto Patry,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:37.465571
    userPrincipalName: opatry@hutch.offsec
, DN: CN=Lyndsie Taunton,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:37.465596
    userPrincipalName: ltaunton@hutch.offsec
, DN: CN=Arlyn Costello,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:37.465621
    userPrincipalName: acostello@hutch.offsec
, DN: CN=Johnnie Sparwell,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:37.465650
    userPrincipalName: jsparwell@hutch.offsec
, DN: CN=Ottilie Knee,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:37.465673
    userPrincipalName: oknee@hutch.offsec
, DN: CN=Joan McKendry,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:37.465700
    userPrincipalName: jmckendry@hutch.offsec
, DN: CN=Alexia Victoria,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:37.465723
    userPrincipalName: avictoria@hutch.offsec
, DN: CN=Jane Frarey,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:37.465746
    userPrincipalName: jfrarey@hutch.offsec
, DN: CN=Editha Aburrow,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:37.465770
    userPrincipalName: eaburrow@hutch.offsec
, DN: CN=Claus Luddy,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:37.465793
    userPrincipalName: cluddy@hutch.offsec
, DN: CN=Arthur Gitthouse,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:37.465818
    userPrincipalName: agitthouse@hutch.offsec
, DN: CN=Freddy McSorley,CN=Users,DC=hutch,DC=offsec - STATUS: Read - READ TIME: 2021-09-07T11:24:37.465906
    userPrincipalName: fmcsorley@hutch.offsec
]
```
