---
layout: post
title: ionic appCache HTML5
excerpt: "ionic appCache HTML5 auto update via manifest"
modified: 2015-09-05
tags: [ionic, appCache, HTML5]
comments: true
image:
  feature: ionicCordova.jpg
  credit: Google Images
  creditlink: https://cdn-netcetera.netdna-ssl.com/img/bgservers.jpg
---

Recently I worked on IonicApp, AppCache @ HTML5 and thought it to update application assets in cache without updating app to Stores.

#### Requirements

  * Deploy an Ionic App to Heroku Refer [last blog](http://rajeevkannav.github.io/ionic-heroku-deploy/) √
  * Ionic app that display webView of server√

### update config.xml

##### update html tag on serving/Remote App

{% highlight ruby %}
<html manifest="remote.appcache">
{% endhighlight %}

###### Setup manifest to remote, carefully list files

{% highlight ruby %}
CACHE MANIFEST
# v2.9.901
/lib/ionic/css/ionic.css
/css/style.css
/lib/ionic/js/ionic.bundle.js
/js/app.js
/index.html
/#/


#CACHE:
/lib/ionic/css/ionic.css
/css/style.css
/lib/ionic/js/ionic.bundle.js
/js/app.js
/index.html
#/#

#NETWORK:
#*
 # nothing yet

FALLBACK:
#/index.html
 # nothing yet
{% endhighlight %}

#### considered Server address is http://appcacheionic.herokuapp.com, do following changes to your Ionic App

##### at config.xml

{% highlight html %}
  <content src="https://appcacheionic.herokuapp.com"/>
{% endhighlight %}

##### at index.html

{% highlight javascript %}
    <script>
      function onBodyLoad()
      {
        document.addEventListener("deviceready", function(){
          //one of these ip-addresses is normally used to address the host machine when using genymotion
          location.href = "https://appcacheionic.herokuapp.com/";
        }, false);
      }
    </script>
{% endhighlight %}

Do changes to application assets, kill application at simulator/device. Be careful on updating app, Cache Limits

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
