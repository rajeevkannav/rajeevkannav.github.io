---
layout: post
title: CSS Preprocessor @-Rule import 
excerpt: "AT Rule scss workflow"
modified: 2016-02-06 
tags: [css, Preprocessor, AT Rule]
comments: true
---

### stuff

#####    CSS @import Rule

CSS @-rule have @import directive which is one of the most popular and
helpful directive for web developer(s)/designer(s). Sass also extends the
CSS @import rule to allow it to import SCSS and Sass files. All imported
SCSS and Sass files will be merged together into a single CSS output file.
In addition, any variables or mixins defined in imported files can be used
in the main file.

Sass preprocessors automatically consider all .scss or .sass files inside the
current directory or given `load_paths` for compliation .but if you need to 
import you may not need to compile it directly, for that you need to inform
preprocessors to not compile a file. put an underscore to the start of that
file name, Sass preprocessors will ignore it for compilation. for example 
rename `extended.scss` to `extended.scss`

Files named this way are called `partials` in Sass terminology.
    
    
### How they works - BackStage

##### Rules for include style into our styles

 `@import` takes a filename to import. By default, it looks for a Sass file to import
 directly, but there are a few circumstances under which it will compile to a CSS
 `@import` rule:
 
 * If the file’s extension is .css.
 * If the filename begins with http://.
 * If the filename is a url().
 * If the @import has any media queries.

##### ways for include style into our styles

{% highlight css %}
@import "extended.scss"; 
{% endhighlight %}
OR
{% highlight css %}
@import "extended.scss"; 
{% endhighlight %}
would both import the file extended.scss, whereas

{% highlight css %}
@import "foo.css";
@import "foo" screen;
@import "http://foo.com/bar";
@import url(foo);
{% endhighlight %}

would all compile to

{% highlight css %}
@import "foo.css";
@import "foo" screen;
@import "http://foo.com/bar";
@import url(foo);
{% endhighlight %}

To import multiple files in one import.
{% highlight css %}
@import "rounded-corners", "text-shadow";
{% endhighlight %}

         
######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
