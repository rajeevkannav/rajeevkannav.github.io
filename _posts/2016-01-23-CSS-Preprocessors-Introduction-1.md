---
layout: post
title: CSS Preprocessor (Introduction - 1).
excerpt: "Changing CSS Practices"
modified: 2016-01-23
tags: [css, Preprocessor, Abstraction]
comments: true
image:
  feature: rails.jpg
  credit: Google Images
  creditlink: http://www.gapintelligence.com/system/pictures/282/content_love-ruby.jpg
---

### stuff

    CSS preprocessors are awesome. they adds functionality to css mainly
    in the form of abstraction like variables, mixins and super powers :).
    that's how they make development quicker, easier, maintainable,
    scalable and blah blah blah (things you can't do with CSS).
        
    There are plenty of options for css preprocessor to choose. Top 3 
    choices are 
 
 * [LESS](http://lesscss.org/),
 * [Sass](http://sass-lang.com/), 
 * [Stylus](http://stylus-lang.com/)
    
### How they works - BackStage

    CSS preprocessors take code written in the preprocessed language and then convert
    that code into the same old css we’ve been writing for years. If you understand
    how ruby/php/jsp or any other server side programming language works it amounts to
    the same thing. 
   
### Basic Usage 

    Sass (.scss syntax) and what the css output would look like.

##### Variables — Interpolation — Operations 
    
    It should be obvious that changing the value of a variable once is much
    more maintainable than changing the many instances.

{% highlight css %}

/* -- Variables  .scss --  */
$color: #efefef;
body {background:  $color;}

/* -- resulting css -- */
body {background:  #efefef;}



/* -- Interpolation .scss --  */
$side: top;
border-#{$side): 1px solid #000;

/* -- resulting css -- */
border-top: 1px solid #000;



/* -- Operators .scss --  */
$navbar-width: 800px;
$items: 5;
#navbar li {width: $navbar-width/$items - 10px;}

/* -- resulting css -- */
#navbar li {width: 150px}

{% endhighlight %}

##### Mixins - Nesting

     Mixins :- DRY (DO NOT REPEAT YOUR-SELF). Principle allow for the easy reuse of blocks of code
     
{% highlight css %}
 /* -- .scss --  */
 @mixin rounded-corners {
   $radius: 5px;
 
   border-radius: $radius;
   -webkit-border-radius: $radius;
   -moz-border-radius: $radius;
 }
 
 #navbar li { @include rounded-corners; }
 #footer { @include rounded-corners; }
  
 /* -- resulting css -- */
 #header {
   border-radius: 5px;
   -webkit-border-radius: 5px;
   -moz-border-radius: 5px;
 }
 
 #footer {
   border-radius: 5px;
   -webkit-border-radius: 5px;
   -moz-border-radius: 5px;
 }
              
/* -- Nesting .scss -- */

#navbar {
width: 80%;
height: 25px;

ul { list-style: none; }

li {
 float: left;
 a { text-decoration: none; }
 &:hover { text-decoration: underline; }
}
}

/* -- resulting css -- */
#navbar {width: 80%; height: 25px;}
#navbar ul {list-style: none;}
#navbar li {float: left;}
#navbar li a {text-decoration: none;}
#navbar li a:hover {text-decoration: underline;}, 

{% endhighlight %}

    CSS Preprocessors aren’t css, so not bound by css's limitations.
    The preprocessed language can give you more functionality. We'll
    cover much more things in upcoming blog series related to CSS
    Preprocessors. 
                      
######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
