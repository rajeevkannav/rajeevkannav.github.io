---
layout: post
title: Prawn ruby Scalable Vector Graphics - SVG 
excerpt: "prawn ruby svg"
modified: 2016-07-09
tags: [pdf, ruby, Prawn, text-annotation ]
comments: true
---

#### Text Annotation - Pdf
Pdf(Portable document format) has beautiful feature called text annotation.
you can add detailed text information with available clipped images
 
Available annotations in current pdf spec are : 

<figure class="third">
	<img src="/images/annotations.png">
</figure>
  
#### Text Annotation - Prawn
Via prawn you can define Text annotations easily. A convenience method
for creating Text annotations. rect must be an array of four numbers,
describing the bounds of the annotation. contents should be a string,
to be shown when the annotation is activated. 

Text annotation by Code - Sample:
{% highlight ruby %}
prawn_pdf = Prawn::Document.new
prawn_pdf.text_annotation(rect, contents, options = {}) 
{% endhighlight %}


#### Ruby Select Quick note

if we need to grep some strings from an array with a defined pattern, 
it is advisable to use select. and this is how i used it.

{% highlight ruby %}
array = ['dhhjdfshgd', 'sadsdhjgsfgdhf   ', 'example@gmail.com']
array.select {|item| item[/\A([^@\s]+)@((?:[-a-z0-9]+\.)+[a-z]{2,})\Z/i]}
{% endhighlight %}

Quite useful for me.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
