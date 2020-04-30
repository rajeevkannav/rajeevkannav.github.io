---
layout: post
title: Gemfile audits in rails    
excerpt: "bundler and gems"
modified: 2017-02-12
tags: [rails, bundler, rubygems]
comments: true
---

#### Problem

Ruby, majorly well-known for rapid web-development via rails.
there are number of `rubygems` coming everyday and un-countable 
versions of existing `rubygems` are released per day. these 
updates may have problems like outdated support,vulnerabilities, bugs
or deprecated features (In general it doesn't happen).This may
end-up project or major downtime.
   
#### Solution

A very useful tool is built into bundler: `bundle outdated`. 
You can see lists installed gems with newer versions available. 
Running bundle outdated looks like this:

        % bundle outdated
        Fetching gem metadata from https://rubygems.org/...........
        Fetching version metadata from https://rubygems.org/..
        Fetching dependency metadata from https://rubygems.org/.
        Resolving dependencies....
        
        Outdated gems included in the bundle:
          * gemname (newest 0.11.1, installed 0.9.0) in group "production"
          
          
There are two more gems, those help a-lot and must try those are
           
  * [Gemnasium]('https://gemnasium.com/')          
  * [bundler-audit]('https://github.com/rubysec/bundler-audit')          
   

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)
                  
<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
