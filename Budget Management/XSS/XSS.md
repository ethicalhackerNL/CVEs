# Budget Management  - Stored Cross-Site-Scripting -1
+ *Exploit Title:* Budget Management   - Stored Cross-Site-Scripting -1 - budget parameter
+ *Date:* 2024-05-05
+ *Exploit Author:* Asif Nawaz Minhas
+ *Vendor Homepage:* https://code-projects.org/budget-management-in-php-with-source-code/
+ *Software Link:* https://download.code-projects.org/details/1c10fce2-3260-479b-878f-b2107dec72f9
+ *Version:* 1.0
+ *Tested on:* Kali Linux + PHP 8.2.12, Apache 2.4.58
+ *CVE:* CVE-2024-33778

## Description:
Budget Management is a simple project developed using PHP. This project is an interesting project for calculating and creating expenses based on CRUD actions. 
The user can provide expenses details and expenses categories by adding their details. The user can edit the details if he/she wants to make some changes to the expense items/lists.
An attacker could exploit this issue to run arbitrary scripting code in an unsuspecting user's browser in the context of the affected site. 
This could allow an attacker to steal cookie-based authentication credentials and launch other attacks.

## Proof of Concept:
+ Go to http://localhost/PHP-Budget-Calculator/index.php
+ Add in Budget Title b2 and in Amount 111 and then click on the button Save.
+ Click now on the button edit and change b2 to <script>alert(1)</script>
+ Click now again on the button Update.
+ Now you will see the stored XSS popping up every time.


 ![XSS]( https://github.com/ethicalhackerNL/CVEs/blob/ee7c15c4a2579ba433dbc28011e7b24ea47fd61e/Budget%20Management/XSS/print%201.png )

 ![XSS]( [https://github.com/ethicalhackerNL/CVEs/blob/ee7c15c4a2579ba433dbc28011e7b24ea47fd61e/Budget%20Management/XSS/print%201.png](https://github.com/ethicalhackerNL/CVEs/blob/0793356fa3359d7ff8da998702593ffd225ffa81/Budget%20Management/XSS/print2.png) )

  ![XSS]( [https://github.com/ethicalhackerNL/CVEs/blob/ee7c15c4a2579ba433dbc28011e7b24ea47fd61e/Budget%20Management/XSS/print%201.png](https://github.com/ethicalhackerNL/CVEs/blob/0793356fa3359d7ff8da998702593ffd225ffa81/Budget%20Management/XSS/print3.png) )
