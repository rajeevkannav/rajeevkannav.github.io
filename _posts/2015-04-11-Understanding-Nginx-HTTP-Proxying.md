---
layout: post
title: Understanding Nginx HTTP Proxying
modified: 2015-04-11
tags: [nginx, HTTP Proxy]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

### General Proxying Information 

One reason to proxy to other servers from Nginx is the ability to scale out your infrastructure. Nginx is built to handle many concurrent connections at the same time. This makes it ideal for being the point-of-contact for clients. 


 
###### Deconstructing a Basic HTTP Proxy Pass


Let's take a look at an example:

```
# server context

location /match/here {
    proxy_pass http://example.com;
}

```

In the above configuration snippet, For definitions that fit this pattern, the URI requested by the client will be passed to the upstream server as-is.

For example, when a request for `/match/here/please` is handled by this block, the request URI will be sent to the `example.com` server as `http://example.com/match/here/please`.


Let's take a look at the alternative scenario:

```
# server context

location /match/here {
    proxy_pass http://example.com/new/prefix;
}
```

In the above example, the proxy server is defined with a URI segment on the end (`/new/prefix`). When a URI is given in the proxy_pass definition, the portion of the request that matches the location definition is replaced by this URI during the pass.

For example, a request for `/match/here/please` on the Nginx server will be passed to the upstream server as `http://example.com/new/prefix/please`. The `/match/here` is replaced by `/new/prefix`. This is an important point to keep in mind.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>