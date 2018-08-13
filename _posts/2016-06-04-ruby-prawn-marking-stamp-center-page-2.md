---
layout: post
title: Prawn ruby marking stamp at page center  
excerpt: "prawn ruby stamping"
modified: 2016-06-11
tags: [pdf, ruby, Prawn, stamp ]
comments: true
---

#### Problem - Prawn
We have to put a default text on every page center if we're not able to
insert image at it's bounding box.

#### Sample Usage 

define a stamp :-

{% highlight ruby %}
prawn_pdf.create_stamp("stamp") {
prawn_page.fill_color '#4a8bc2'
prawn_page.text_box '[Image not available.]',
:width  => bounds.width,
:height => bounds.height,
:align  => :center,
:valign => :center,
:at     => [0, bounds.height],
:rotate => 45,
:rotate_around => :center
}
{% endhighlight %}

mark stamp at any page by just calling it by name :-

`prawn_page.stamp("stamp")`

#### Things to take care

 * stamp name should be unique.
 * should be take care of stamp dimension and its content.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
