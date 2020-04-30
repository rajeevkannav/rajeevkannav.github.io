---
layout: post
title: Hubot Introduction   
excerpt: "A Customizable, Life Embetterment Robot"
modified: 2016-08-20
tags: [hubot, open-source, github]
comments: true
---

## What is Hubot?

Hubot is your company's robot. Install him in your company
to dramatically improve and reduce employee efficiency.


Hubot is open source, written in CoffeeScript on Node.js,
and easily deployed on platforms like Heroku. More importantly,
Hubot is a standardized way to share scripts between everyone's
robots.

You will need node.js and npm. Once those are installed, we can
install the hubot generator:

{% highlight ruby %}
% npm install -g yo generator-hubot
% mkdir myhubot
% cd myhubot
% yo hubot

{% endhighlight %}

At this point, you'll be asked a few questions about who is creating the bot,
and which adapter you'll be using. Adapters are hubot's
way of integrating with different chat providers.

If you are using git, the generated directory includes a .gitignore, so you can
initialize and add everything:

{% highlight ruby %}
% git init
% git add .
% git commit -m "Initial commit"
{% endhighlight %}

{% highlight ruby %}
% bin/hubot
Hubot>
{% endhighlight %}

This starts hubot using the shell adapter, which is mostly
useful for development. Make note of Hubot>; this is the
name your hubot will respond to with commands.

{% highlight ruby %}
hubot> hubot help
{% endhighlight %}

You can deploy hubot to Heroku, which is the officially
supported method. Additionally you are able to deploy hubot
to a UNIX-like system or Windows.

##### We'll cover more Hubot features and build it for surein upcoming posts.  

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
