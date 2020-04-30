---
layout: post
title: Prawn ruby link annotation 
excerpt: "prawn ruby link annotation"
modified: 2016-06-18
tags: [pdf, ruby, Prawn, link-annotation ]
comments: true
---

#### Problem - Prawn
In Prawn pdf we need to put links on the Image text and fortunatley we're keeping 
required co-ordinates with objects. We tried to put Text link with anchor on text
available inside image but that wasn't cool because our images can rotate


#### Solution

Instead of marking text link above image text, we tried to put
link annotation.

Link annotation by Prawn are :

A convenience method for creating Link annotations. rect must be an
array of four numbers, describing the bounds of the annotation. The
options hash should include either :Dest (describing the target
destination, usually as a string that has been recorded in the
document's Dests tree), or :A (describing an action to perform on
clicking the link), or :PA (for describing a URL to link to).

Link annotation by Code - Sample:
{% highlight ruby %}
prawn_pdf = Prawn::Document.new(skip_page_creation: true)
link_coordinates = [:left, :top, :right, :bottom] # a.k.a coordinates
prawn_pdf.link_annotation(link_coordinates, :Dest => "target destination")
{% endhighlight %}




######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
