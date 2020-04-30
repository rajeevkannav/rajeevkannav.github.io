---
layout: post
title: tempfile generation issue from user generated filename in ruby/OS     
excerpt: "ruby tempfile fix"
modified: 2017-03-31
tags: [tempfile, filename, ruby]
comments: true
---

#### Problem

We used a super simple code in ruby to generate tempfiles with dynamic filename.

    
    temp_file = Tempfile.new([title, '.pdf'])
    
where title is a variable value (Input taken from user).so if your insert special
or not allowed/expected character as a filename in any Operating system this code
will fail. Well this is not related to Ruby directly as its a filename constraint
in every Operating system but it happened to us via Ruby code.
    
    
#### Solution

    temp_file = Tempfile.new([title.gsub(/[^\w\.]/, '_'), '.pdf'])
    
Pretty simple solution to remove/Replace not allowed values there. This is very
minor thing to correct as well to take notes, but we had exception from production
and that is not acceptable at all.

 
######  And if you get stuck… [Ask Here](http://stackoverflow.com/)
                  
<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
