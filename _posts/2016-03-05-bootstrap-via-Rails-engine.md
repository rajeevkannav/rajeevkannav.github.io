---
layout: post
title: using twitter-bootstrap via rails engine. 
excerpt: "make your rails engine interface more beautiful"
modified: 2016-03-05
tags: [ twitter-bootstrap , rails , engine]
comments: true
image:
  feature: rails.jpg
  credit: Google Images
  creditlink: http://www.gapintelligence.com/system/pictures/282/content_love-ruby.jpg
---

We're developing a Rails engine [Message Broker](https://github.com/rajeevkannav/message_broker/) which will do some
awesome things. As User Interface proposed by me is rejected from the scratch (May be you know the person) hence we opted
Twitter-Bootstrap for Engine User Interface for simplicity. following are the steps which need to be done to use
Twitter-Bootstrap.


 * add following to your engine_name.gemspec
   
   {% highlight ruby %}
   
     s.add_dependency 'bootstrap-sass', '~> 3.2.0'        
     s.add_dependency 'sass-rails'
   
   {% endhighlight %}

 * require bootstrap to lib/engine_name.rb `require 'bootstrap'` 

 * Rename application.css to application.css.sass and add following code

   {% highlight ruby %}
        @import 'bootstrap-sprockets'        
        @import 'bootstrap'
   {% endhighlight %}

 * add `//= require bootstrap-sprockets` to your application.js after   

   {% highlight ruby %}
        //= require jquery        
        //= require jquery_ujs
   {% endhighlight %}
        
 * apply changes to your application layout and views 
  
 * Restart Rails Server 

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
