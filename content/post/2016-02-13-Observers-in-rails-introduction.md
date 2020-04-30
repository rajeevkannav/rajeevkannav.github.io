---
layout: post
title: Observer in Rails
excerpt: "object life cycle callbacks"
modified: 2016-02-13
tags: [Ralis, Observer, callbacks, object-life-cycle]
comments: true
image:
  feature: rails.jpg
  credit: Google Images
  creditlink: http://www.gapintelligence.com/system/pictures/282/content_love-ruby.jpg
---

###  Rails observer 

Rails::Observers was introdused in Rails 3. They're another abstracted
way to watch/tarck an object life-cycle events while watching you may
trigger some/any other event.
 
It's a nice to have structure/solution(not recommanded) for fatty models.
Observer reduce the clutter that normally comes when the model class is 
Over-burdened with functionality.      

{% highlight ruby %}
class OrderObserver < ActiveRecord::Observer
  def after_create(order)
    OrderMailer.confirm("example@domain.com", "Your Order has been confirmed.", order).deliver
  end
end
{% endhighlight %}

This Order Observer sends an email when a Order#create is done.

{% highlight ruby %}
class OrderObserver < ActiveRecord::Observer
  def after_create(order)
    order.logger.info('New order added!')
  end

  def after_destroy(order)
    order.logger.warn("Order with an id of #{order.id} was destroyed!")
  end
end
{% endhighlight %}

This Observer uses logger to log when specific callbacks as given
order created/destroyed are triggered.
    
#### Available callback methods

The observer(s) can implement callback methods for each of the methods described
in the [Rails Callbacks](http://api.rubyonrails.org/v3.2.0/classes/ActiveRecord/Callbacks.html)
module.
    
#### Rails 4     

Observers are removed from rails core from Rails4. In Rails 4 it's an
seperate [gem](https://github.com/rails/rails-observers) 

###### To be continued note ...
    
I am digging more into Rails::Observers. I'll cover much more things in
upcoming blog series related to Rails::Observers with an implementation
of [Publish–subscribe pattern](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern.)
                           
######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
