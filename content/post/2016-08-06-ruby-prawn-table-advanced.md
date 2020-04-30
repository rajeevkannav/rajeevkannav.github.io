---
layout: post
title: Prawn table in ruby advanced  
excerpt: "ruby prawn table"
modified: 2016-08-06
tags: [pdf, ruby, Prawn, table ]
comments: true
---

## Prawn table content and subtable

As we discussed in last post about Prawn Table via ruby. Today we're
giving dive more deeper. In Prawn table there are five kind of objects
which can be put in table cells:

    • String: produces a text cell
    • Prawn::Table::Cell
    • Prawn::Table
    • Array
    • Images

whenever a table or an array is provided as a cell, a subtable will be 
created(a table within a cell). if you'd like to provide a cell or table
directly, the best way is to use the `make_cell` and `make_table`
methods as they don't call `draw` on the created object. To insert an
image just provide a hash with an `:image` key pointing to the image path.
   
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

## Prawn table Flow and Header

if the table cannot fit on the current page it will flow to the next
page just like free flowing text. if you would like to have the first
row treated as a header which will be repeated on subsequent pages set
the :header option to true

{% highlight ruby %}
data = [["This row should be repeated on every new page"]]
data += [["..."]] * 30
table(data, :header => true)
{% endhighlight %}

##### Output will be like as:  

<figure class="full">
	<a href="javascript:void(0);"><img src="/images/prawn_flow_and_header.png"></a>
</figure>

##### We'll cover more prawn and prawn table features in upcoming posts.  

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
