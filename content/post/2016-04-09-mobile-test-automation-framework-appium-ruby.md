---
layout: post
title: Mobile test automation framework appium introduction 
excerpt: "appium ruby ubuntu"
modified: 2016-04-09
tags: [appium, ruby, ubuntu]
comments: true
image:
  feature: rails.jpg
  credit: Google Images
  creditlink: http://www.gapintelligence.com/system/pictures/282/content_love-ruby.jpg
---

[Appium]('http://appium.io/') is an open source test automation tool for mobile applications. Which is capable to test
any kind of mobile application: native, hybrid and mobile web for iOs and android platform. It can also run the automated
tests on devices as well as emulators.

We all have our mobile applications in at least these two major platforms and we need such a beautiful automation tool
like `appium`. It allows testing cross platform. It seems easy as such same code base is sufficient enough for both different
frameworks.

The basic philosophy of `Appium` is that you should be able to reuse code between iOS and Android, and that’s why
when you see the API they are same across iOS and android. Another important thing to highlight here is that
unlike Calabash, `Appium` doesn’t modify your app or need you to even recompile the app.

You may choose any of your preferred language as it's an open source project there are wrappers available in every major
language.

# Appium Architecture

Let’s try to understand what happens behind the scenes.

`Appium` server which actullay you download is written in Node.js and that implements the Selenium WebDriver. It allows
one to use available WebDriver client to fire your tests and then your mobile app acts precisely like a web app where
the DOM is represented by View hierarchy.

So this server basically exposes REST api which performs the following actions:

     Receives connection from client
     Listen command
     Execute command
     Respond back the command execution status

In terms of architecture diagram, below is how `Appium` can be explained.

<figure class="half">
    <a href="/images/appium_architecture.jpg"><img src="/images/appium_architecture.jpg"></a>
    <figcaption>`Appium` Architecture</figcaption>
</figure>


We're going to dive into `appium` a bit more, and we'll be bind it to ruby in text series.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
