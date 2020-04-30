---
layout: post
title: Prawn ruby table introduction - 1 
excerpt: "ruby prawn table"
modified: 2016-07-30
tags: [pdf, ruby, Prawn, table ]
comments: true
---

#### Table via Prawn in ruby for Pdf

Prawn comes with table support out of the box. Tables can be styled in whatever way you see fit.
The whole table, rows, columns and cells can be styled independently from each other.
The examples show:
  • How to create tables
  • What content can be placed on tables
  • Subtables (or tables within tables)
  • How to style the whole table
  • How to use initializer blocks to style only specific portions of the table
  

#### Sudo-Code 


{% highlight ruby %}

cell_1 = make_cell(:content => "this row content comes directly ")
cell_2 = make_cell(:content => "from cell objects")
two_dimensional_array = [ ["..."], ["subtable from an array"], ["..."] ]
my_table = make_table([ ["..."], ["subtable from another table"], ["..."] ])
image_path = "#{Prawn::DATADIR}/images/stef.jpg"
table([ ["just a regular row", "", "", "blah blah blah"],
 [cell_1, cell_2, "", ""],
 ["", "", two_dimensional_array, ""],
 ["just another regular row", "", "", ""],
 [{:image => image_path}, "", my_table, ""]])
 
{% endhighlight %}

##### Output will be like as:  

<figure class="full">
	<a href="javascript:void(0);"><img src="/images/prawntable.png"></a>
</figure>

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
