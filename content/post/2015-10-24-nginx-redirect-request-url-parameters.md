---
layout: post
title: Redirect request based on URL paramters via nginx
excerpt: "nginx re-write operations"
modified: 2015-10-24
tags: [backup Support, re-write, nginx]
comments: true
image:
  feature: webServer.jpg
  credit: Google Images
  creditlink: https://cdn-netcetera.netdna-ssl.com/img/bgservers.jpg
---

### Problem:

     We've an Enterprise level Mobile/iPad application and we did
     major changes to our backEnd (Rails App) so as a usual process
     we uploaded new app version and waiting to approve via app-Store,
     We don't when Apple is going to approve it, We have to support
     previous and upcoming version and Solution must be easy/Generic.

### Solution

    We configured our Mobile/iPad application to send a new parameter
    with every single request say version=1 Or Version=Beta then we 
    utilized nginx to redirect such request to servers who're capable
    to serve New Changes and Others we're to old machines

    This could be an Hack or Not so good implementation but for now
    this seems easy, affordable and long term too.
   

##### sudo/RAW solution to nginx configuration
    
{% highlight ruby %}
##########################################################################
    if ($arg_version) { // 
       rewrite ^/(.*) http://ip_addresss permanent; #new machine ip address
    }
##########################################################################`
{% endhighlight %}

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
