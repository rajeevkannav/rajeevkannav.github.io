---
layout: post
title: Javascript multiple Div/Elements selection and sorting
excerpt: "javascript multiple sorting"
modified: 2016-04-23
tags: [javascript, multiple sorting]
comments: true
---

[jquery.multisortable]('https://github.com/shvetsgroup/jquery.multisortable') is an open source Extension of jQuery
UI Sortable, which works with multiple selected elements.

#### Usage
{% highlight ruby %}
// simple case
$('ul').multisortable();

// some of the advanced usages
$('div.container').multisortable({
    items: "div.item",
    selectedClass: "selected",
    click: function(e){ console.log("I'm selected."); }
    stop: function(e){ console.log("I've been sorted."); }
});
{% endhighlight %}

#### Options

    selectedClass: class which will be assigned to selected items.

#### Events

  *  mousedown: this event will be fired when user starts to drag item(s).
  *  click: this event will be fired when user clicks item(s).
  *  start: this event will be fired when user starts to drag item(s).
  *	 stop: this event will be fired when user stop to drag item(s).
  *	 sort: this event will be fired when user sort item(s) after drag stop.

#### Demo

[js.fiddle]('http://jsfiddle.net/neochief/KWeMM/')


######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
