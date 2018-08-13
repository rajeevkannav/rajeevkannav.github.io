---
layout: post
title: Restrict nginx upload file size limit
excerpt: "maximum allowed size of the client request body"
modified: 2015-11-14
tags: [maximum allowed size, nginx]
comments: true
image:
  feature: webServer.jpg
  credit: Google Images
  creditlink: https://cdn-netcetera.netdna-ssl.com/img/bgservers.jpg
---

### Problem:

     We've an Enterprise level Rails application and we need to have 
     Upload size restrictions because this could lead to a DOS(denial-of-service)
     to the application via filling the HDD or utilizing web resources and 
     solution must be easy/Generic.

### Solution

    We updated our nginx configuration `client_max_body_size size` which
    sets the maximum allowed size of the client request body, specified
    in the “Content-Length” request header field. If the size in a request
    exceeds the configured value, the 413 (Request Entity Too Large) error
    is returned to the client. 

##### sudo/RAW solution to nginx configuration
    
{% highlight ruby %}
client_max_body_size 50m; # 50MB for file size restriction
{% endhighlight %}

    Syntax: 	client_max_body_size size;
    Default: 	client_max_body_size 1m;
    Context: 	http, server, location

### Please be aware that browsers cannot correctly display this error. Setting size to 0 disables checking of client request body size.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
