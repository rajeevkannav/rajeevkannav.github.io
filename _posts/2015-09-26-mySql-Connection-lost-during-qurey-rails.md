---
layout: post
title: Mysql2 Error Lost connection to MySQL server during query Rails Application
excerpt: "aws rds configurations"
modified: 2015-09-26
tags: [AWS, Rails, RDS, MySQL]
comments: true
image:
  feature: ionicCordova.jpg
  credit: Google Images
  creditlink: https://cdn-netcetera.netdna-ssl.com/img/bgservers.jpg
---

In our Rails Application we faced several exception(s) saying 

    Mysql2::Error: Lost connection to MySQL server during query

Usually it indicates network connectivity trouble and you should check the condition of your network if this error
occurs frequently. If the error message includes “during query,” this is probably the case you are experiencing. 

Sometimes the `during query` form happens when millions of rows are being sent as part of one or more queries. If you
know that this is happening, you should try increasing `net_read_timeout` from its default of 30 seconds to 60 seconds
or longer, sufficient for the data transfer to complete.
 
In our case luckily we're on Amazon Relational Database Machine(s), so it can be done easily and Quickly.
   
Visit `Parameter Groups` of your Amazon RDS machine. update `net_read_timeout` value of that group which is being used.
we make it 3600. default unit in mysql is seconds 

Re-booted the rds instance, though it was a down for a while. After that a new sun arise we've not face such exceptions 
yet. still we're investigating.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
