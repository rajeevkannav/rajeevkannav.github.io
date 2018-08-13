---
layout: post
title: Cordova/Ionic Error page Html Handling
excerpt: "Cordova/Ionic Error page Html Handling"
modified: 2015-09-05
tags: [ionic, appCache, HTML5]
comments: true
image:
  feature: ionicCordova.jpg
  credit: Google Images
  creditlink: https://cdn-netcetera.netdna-ssl.com/img/bgservers.jpg
---

Recently I worked on Hybrid Mobile Application and got Network Dependency to Start Application. Also What if Internet now available.
So it's pretty simple without writing own code and using Cordova Configuration.


#### cordova-error-page.html

  Have such (Any name) html page to your application www folder. Write information which you need to share to user.

### update config.xml

##### For iOs

{% highlight ruby %}
  <platform name="ios">
    <preference name="ErrorUrl" value="cordova-error-page.html"/>
  </platform>
{% endhighlight %}


##### For Android

{% highlight ruby %}
    <platform name="android">
        <preference name="ErrorUrl" value="file:///android_asset/www/cordova-error-page.html"/>
    </platform>
{% endhighlight %}


######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
