---
layout: post
title: ionic autoupdate application noDeploy
modified: 2015-08-08
tags: [ionic, autoUpdate, noDeploy]
comments: true
image:
  feature: ionicCordova.jpg
  credit: Google Images
  creditlink: https://cdn-netcetera.netdna-ssl.com/img/bgservers.jpg
---

## cordova-app-loader
Remote update your Cordova App, Write a manifest.json to bootstrap.js your app. Build and deploy your app.

A little later...

Upload an update to your server (manifest.json + files)
Use CordovaAppLoader to

{% highlight ruby %}

    check() for a new manifest
    download() files
    update() your app!

{% endhighlight %}

Check out [Cordova App Loader](http://data.madebymark.nl/cordova-app-loader/index.html) in Chrome for a demo! (Chrome only!)

Or run on your own computer:

{% highlight ruby %}

    git clone git@github.com:markmarijnissen/cordova-app-loader.git
    cd cordova-app-loader
    cordova platform add ios@3.7.0
    cordova plugin add org.apache.cordova.file
    cordova plugin add org.apache.cordova.file-transfer
    cordova run ios

{% endhighlight %}

All code is in the `www` directory. Modify serverRoot in `www/app.js` to run your own server.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
