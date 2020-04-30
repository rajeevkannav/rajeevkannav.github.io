---
layout: post
title: "unix linux shell script code snippet"
modified: 2015-07-11
excerpt: "unix linux shell script code snippet often used."
tags: [unix linux,shell script]
comments: true
---

### Generating script logs with timestamp

Just as the duration of script it's useful to have time-stampped log. Use following function to log time for every output.

{% highlight javascript %}
  log() {
       echo [`date +%Y-%m-%d\ %H:%M:%S`] $*
  }
{% endhighlight %}

Call the function as follows instead of simply "echo"ing.

{% highlight javascript %}
  log "my string to be logged"
{% endhighlight %}

#####  Reading variables from config file

Create a config file with contents as follows:

{% highlight javascript %}
key1=value1
key2=value2
{% endhighlight %}

Add following line in the beginning of the shell script:

{% highlight javascript %}
. configfile
{% endhighlight %}

This will load the key value pairs and you may verify & access the values as $key1 or $key2.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/) 

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>