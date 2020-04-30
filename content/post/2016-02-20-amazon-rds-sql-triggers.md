---
layout: post
title: Using SQL triggers in AWS Relational Database Service (RDS). 
excerpt: " database triggers halt Amazon Relational Database Service."
modified: 2016-02-20
tags: [ SQL , triggers , AWS, RDS]
comments: true
image:
  feature: rails.jpg
  credit: Google Images
  creditlink: http://www.gapintelligence.com/system/pictures/282/content_love-ruby.jpg
---

Few months ago we've tried to create SQL database triggers for an AWS RDS
instance and got following error.

    ERROR 1419 (HY000) at line #: You do not have the SUPER privilege
    and binary logging is enabled (you might want to use the less safe
    log_bin_trust_function_creators variable).


Amazon RDS disable all user defined SQL code be default, as binary
procedures could compromise the RDS architecture. And for this purpose, Amazon
blocked granting the missing `SUPER` privileges to any database user except the
`rdsadmin` user owned by Amazon itself.


As a workaround, there is an option to set the mysterious parameter
`log_bin_trust_function_creators` to 1, that prevents the database
from complaining against simple and inoffensive triggers. Though,
setting this parameter requires following steps:


 *   Open the RDS web console Goto the `Parameter Groups` tab.
 *   Create a new Parameter Group. On the dialog, select the MySQL
 family compatible to your MySQL database version, give it a name and confirm.
 *   Select the just created Parameter Group and issue `Edit Parameters`.
 *   Look for the parameter `log_bin_trust_function_creators` and set its value to `1` and Save the changes.
 *   Open the `Instances` tab. Expand your MySQL instance and issue the `Instance Action`
 named `Modify`.
 *   Select the just created Parameter Group and enable `Apply Immediately`.
 *   Click on `Continue` and confirm the changes.
 *   Again, open the `Instances` tab. Expand your MySQL instance and issue the
 `Instance Action` named `Modify`.
 *   Dont forget: Open the `Instances` tab. Expand your MySQL instance and issue
 the `Instance Action` named `Reboot`.
                           
######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
