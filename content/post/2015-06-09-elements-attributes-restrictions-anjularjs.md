---
layout: post
title: "AngularJs Directives Restrict to Elements and Attributes"
modified: 2015-06-09
excerpt: "AngularJs, Best Practice, Beginner good to read resource"
tags: [AngularJs, Best Practice, Directives]
comments: true
---

At a high level, directives are markers on a DOM element (such as an attribute, element name, comment or CSS class) that
tell AngularJS's HTML compiler ($compile) to attach a specified behavior to that DOM element or even transform the DOM
element and its children.

<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- Github Page Add 1 -->
<ins class="adsbygoogle"
     style="display:block"
     data-ad-client="ca-pub-1411898088670168"
     data-ad-slot="3525987534"
     data-ad-format="auto"></ins>
<script>
    (adsbygoogle = window.adsbygoogle || []).push({});
</script>

### Best Practice: 

Prefer using directives via tag name and attributes over comment and class names. Doing so generally makes it easier to 
determine what directives a given element matches.


{% highlight javascript %}
<!-- avoid -->
<div class="my-range-slider"></div> 

/* avoid */
angular
    .module('app.tools')
    .directive('myRangeSlider', myRangeSlider);

function myRangeSlider() {
    var directive = {
        link: link,
        templateUrl: '/template_path/filenamehtml',
        restrict: 'C'
    };
    return directive;

    function link(scope, element, attrs) {
      /* */
    }
} 

<!-- recommended -->
<my-range-slider></my-range-slider>
<div my-range-slider></div>

 

 /* recommended */
angular
    .module('app.tools')
    .directive('myRangeSlider', myRangeSlider);

function myRangeSlider() {
    var directive = {
        link: link,
        templateUrl: '/template_path/filename.html',
        restrict: 'EA'
    };
    return directive;

    function link(scope, element, attrs) {
      /* */
    }
}

{% endhighlight %}
 
#### Note: EA is the default for AngularJS 1.3 +

######  And if you get stuck… [Ask Here](http://stackoverflow.com/) 

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>