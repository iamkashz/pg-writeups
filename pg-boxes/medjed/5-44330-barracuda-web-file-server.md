# 5 :44330 Barracuda Web-File-Server

```
https://192.168.154.127:44330/rtl/protected/wfslinks.lsp
File Server Links | Access Rights
/fs/ | read - write

https://192.168.154.127:44330/fs/
# we have full access to file system
# can read Admin flag => service is running as some admin user.

We know the error on http://192.168.154.127:33033/assets
Rails.root: C:/Sites/userpro

https://192.168.154.127:44330/fs/2ad058fc612168e0/C/Sites/userpro/db.sql
# schema is 
# id | fullname | username | password_digest | bio | created_at | updated_at | avatar | reminder
INSERT INTO `users` VALUES
(1,'Evren Eagan','evren.eagan','$2a$12$ojvpmLJ4rT8A10Iz98FptOWyw5W2miGIkFCuNk/hy57YNJCr8LvL.','Impossible is just an opinion.','2020-11-02 14:44:18.672908','2020-11-02 16:51:17.757034',NULL,'4qpdR87QYjRbog'),
(3,'Joe Webb','joe.webb','$2a$12$DJlbsfExOXIKTKZlcMbpqu/HwLfA/dGktEWWAl7JXE3riqqhdoexS','Hold the vision, trust the process','2020-11-02 15:58:29.535699','2020-11-02 16:52:00.116108',NULL,'4qpdR87QYjRbog'),
(4,'Jerren Valon','jerren.devops','$2a$12$Cb5cpzp.pLZU2AqwiszWPut5erYzGaphhZFWjUdEBXg/wdWa3pWEK','Only the paranoid survive.','2020-11-02 16:04:15.949376','2020-11-02 16:50:27.285264',NULL,'paranoid'),
(6,'Kenneth Dooley','kenneth.dooley','$2a$12$dBG4TsYsDFEHVH9zUU4rgu6zexKbPPxQz2ecb.HFG/C8d.cBv5aNa','Just another Magic Monday','2020-11-03 19:23:29.947808','2020-11-03 19:26:10.032259',NULL,'xuk1EuP3N/rCpA'),
(7,'Laura Lauer','laura.lauer','$2a$12$m8bhpyBs40mhfkRWJXl1BO7ZKFFOGaSzBa77eqjEdLZ5BVMVTtWbS','One day or day one. You decide.','2020-11-03 19:25:35.310884','2020-11-03 19:25:35.342046',NULL,'AJqKXnKVwhcSkg'),
(8,'Christopher Mouser','christopher','$2a$12$EObZ3ExrLTmlH1zbWmiKZOSq5jmTAzSsf.OGXg322lteuJDDmSvS.','You have brains in your head. ','2020-11-03 19:27:45.899707','2020-11-03 19:28:12.685493',NULL,'WgsjOZwtOyCRSg');
# cracking

https://192.168.154.127:44330/fs/C/Sites/
file: run.bat
@echo off
cd C:\Sites\userpro
rails s -b 0.0.0.0 -p 33033


```
