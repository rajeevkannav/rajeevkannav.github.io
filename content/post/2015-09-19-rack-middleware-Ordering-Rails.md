---
layout: post
title: Ordering Rack Middleware Rails Application
excerpt: "Rack Middleware sequence"
modified: 2015-09-05
tags: [middleware, Rails, Rack]
comments: true
image:
  feature: ionicCordova.jpg
  credit: Google Images
  creditlink: https://cdn-netcetera.netdna-ssl.com/img/bgservers.jpg
---


Rack middleware is a simply bigger thing then rails. It's look-alike rack application that you can use to filter,
process, or otherwise mess with responses.There is middleware like warden - devise, to work on catch and log exceptions,
deal with cookies, SSO, and pretty much anything else you can think of. And in case you missed it,
rails is a rack application. Create a new rails app and run

{% highlight ruby %}
    rake middleware
{% endhighlight %}

It will display results like this :

{% highlight ruby %}
    use Rack::Cors
    use Rack::Sendfile
    use ActionDispatch::Static
    use Rack::Lock
    use #<ActiveSupport::Cache::Strategy::LocalCache::Middleware:0x00000007238168>
    use Rack::Runtime
    use Rack::MethodOverride
    use ActionDispatch::RequestId
    use Rails::Rack::Logger
    use ActionDispatch::ShowExceptions
    use ActionDispatch::DebugExceptions
    use ActionDispatch::RemoteIp
    use ActionDispatch::Reloader
    use ActionDispatch::Callbacks
    use ActiveRecord::Migration::CheckPending
    use ActiveRecord::ConnectionAdapters::ConnectionManagement
    use ActiveRecord::QueryCache
    use ActionDispatch::Cookies
    use ActionDispatch::Session::CookieStore
    use ActionDispatch::Flash
    use ActionDispatch::ParamsParser
    use Remotipart::Middleware
    use Rack::Head
    use Rack::ConditionalGet
    use Rack::ETag
    run Banana::Application.routes
{% endhighlight %}

### Okay so what's the problem?

let's you have an middleware say AwesomeMe. The AwesomeMe is calculated after the response time is injected,
so that's fine (imagine if the etag middleware was at the bottom). What about poor ExceptionNotifier?
What if there is an exception thrown in the ResponseTimeInjector or AwesomeMe middleware? ExceptionNotifier isn't
going to catch it! The ExceptionNotifier middleware doesn't modify anything in the response,
so it needs to be up higher; it needs to be first.

### Solution

You can add a new middleware to the middleware stack using any of the following methods:

  * config.middleware.use(new_middleware, args) - Adds the new middleware at the bottom of the middleware stack.

  * config.middleware.insert_before(existing_middleware, new_middleware, args) -
    Adds the new middleware before the specified existing middleware in the middleware stack.

  * config.middleware.insert_after(existing_middleware, new_middleware, args) -
    Adds the new middleware after the specified existing middleware in the middleware stack.

{% highlight ruby %}
# config/application.rb

# Push Rack::BounceFavicon at the bottom
config.middleware.use Rack::BounceFavicon

# Add Lifo::Cache after ActiveRecord::QueryCache.
# Pass { page_cache: false } argument to Lifo::Cache.
config.middleware.insert_after ActiveRecord::QueryCache, Lifo::Cache, page_cache: false
{% endhighlight %}

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
