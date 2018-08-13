---
layout: post
title: ionic Heroku Deploy
excerpt: "easy way to deploy ionic application to Heroku"
modified: 2015-08-22
tags: [ionic, Heroku, Deploy]
comments: true
image:
  feature: ionicCordova.jpg
  credit: Google Images
  creditlink: https://cdn-netcetera.netdna-ssl.com/img/bgservers.jpg
---

Recently I worked on IonicApp and thought it must be possible to run it over Heroku and that works.

#### Requirements

  * Heroku-Toolbet √
  * Ionic √
  * node √

###### Install express

{% highlight ruby %}
    npm install express --save
{% endhighlight %}

###### Setup App.json

Additional, a app.json is needed for some meta information about your app.

{% highlight ruby %}
{
    "name": "Ionic to Heroku Example",
    "description": "A simple Ionic app for Heroku",
    "repository": "https://github.com/yourUsername/repositoryName",
    "logo": "logoURL",
    "keywords": ["ionic", "Heroku", "whatever"]
}

{% endhighlight %}

###### Setup server.js

The last thing we need is the file which will be executed by Heroku. Heroku will look for a server.js,
so create this file as well on the top level of your ionic project and insert:

{% highlight ruby %}
var express = require('express'),
app = express();
app.use(express.static('www'));
app.set('port', process.env.PORT || 5000);
app.listen(app.get('port'), function () {
    console.log('Express server listening on port ' + app.get('port'));
});
{% endhighlight %}

Now you can test your app local. Instead of `ionic serve`, we will install the modules and run it with our express server,
so go ahead:

{% highlight ruby %}
npm install
npm start
{% endhighlight %}

If you receive no error, you can access your app on `http://localhost:5000/`. If you have problems, fix that at your local
Once application works fine, You're almost done! Make sure to commit/push these changes to your repo, so Heroku receives all files we just added.

Deploying your App on Heroku, The above workflow was just standard git stuff, now we make our Heroku deployment.
To use Heroku from the command line, you need to have the Heroku-Toolbelt installed.
If you are done, open your Terminal and type:

{% highlight ruby %}
heroku create
git push heroku master
{% endhighlight %}

This can take some time, depending on your project size. You can now try to open your app:

{% highlight ruby %}
heroku open
{% endhighlight %}


######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
