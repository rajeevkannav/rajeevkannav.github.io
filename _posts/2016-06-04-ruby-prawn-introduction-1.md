---
layout: post
title: Prawn ruby pdf creation basics introduction  
excerpt: "commonly mispronounced words"
modified: 2016-05-21
tags: [pdf, ruby, Prawn ]
comments: true
---


#### Prawn
Prawn is a pure Ruby PDF generation library that provides a lot of great
functionality while trying to remain simple and reasonably performant.

#### Sample Usage 

create/Initialize new document without having first page created :-

`prawn_pdf = Prawn::Document.new(skip_page_creation: true)`

adding new page with giving dimension :-
     
`prawn_pdf.start_new_page(size: [width,height])` 

adding a bounding box having a image into it :-

{% highlight ruby %}
prawn_pdf.bounding_box([0, 0], :width => width, :height => height) do
prawn_pdf.image "image_location", at: [0, 0]
end
{% endhighlight %}

adding a text annotation with content :-

`prawn_pdf.text_annotation([a,b,c,d], annotation_content)`

adding a links-anchor and registering destination :-

{% highlight ruby %}
prawn_pdf.text_box "<link anchor='anchor-#{anchor-identifier}'>THIS</link>",
                   inline_format: true, width: width, height: height
{% endhighlight %}
  
`prawn_pdf.add_dest("anchor-#{anchor-identifier}", prawn_pdf.dest_fit(prawn_pdf.page))`


######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
