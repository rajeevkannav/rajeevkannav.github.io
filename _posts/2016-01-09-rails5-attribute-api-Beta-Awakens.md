---
layout: post
title: Rails 5 - beta Attribute API
excerpt: "a non-Active Record type"
modified: 2016-01-09
tags: [Rails5, newThings , Virtual attribute]
comments: true
image:
  feature: rails.jpg
  credit: Google Images
  creditlink: http://www.gapintelligence.com/system/pictures/282/content_love-ruby.jpg
---

### Rails-5-0-beta1:



     Rails-5.0-beta1 is available after tenth anniversary of Rails 1.0. still there are apps ruunning in production
     based on Rails-5.0-beta1 for Example Basecamp 3.
     
      
### Featured New Stuff

  * [Action Cable] (https://github.com/rails/rails/tree/master/actioncable)
  * [Rails API] (https://github.com/rails/rails/pull/19832)
  * [New Command Router] (https://github.com/rails/rails/issues/18878)
  * [Attributes API] (https://github.com/rails/rails/blob/8c752c7ac739d5a86d4136ab1e9d0142c4041e58/activerecord/lib/active_record/attributes.rb)
  * [Application Record] (https://github.com/rails/rails/pull/22567)
  * [ActiveRecord::Relation#or ] (https://github.com/rails/rails/pull/16052)

### Attributes API

    Your models are getting a new attribute class method in Rails 5, allowing you to easily define a relationship
    between the model and a non-Active Record type. No more misusing serialize!
   
   
{% highlight ruby %}

    # before
    # The type detected by Active Record can be overridden.
    
        # db/schema.rb
        create_table :store_listings, force: true do |t|
            t.decimal :price_in_cents
        end
        
        # app/models/store_listing.rb
        class StoreListing < ActiveRecord::Base
        end
        
        store_listing = StoreListing.new(price_in_cents: '10.1')
        
        store_listing.price_in_cents # => BigDecimal.new(10.1)
        
        class StoreListing < ActiveRecord::Base
            attribute :price_in_cents, :integer
        end
        
        store_listing.price_in_cents # => 10
    
    # after
    # Attributes do not need to be backed by a database column.
    
        class MyModel < ActiveRecord::Base
            attribute :my_string, :string
            attribute :my_int_array, :integer, array: true
            attribute :my_float_range, :float, range: true
        end
        
        model = MyModel.new(
            my_string: "string",
            my_int_array: ["1", "2", "3"],
            my_float_range: "[1,3.5]",
        )
        model.attributes
        # =>
        {
            my_string: "string",
            my_int_array: [1, 2, 3],
            my_float_range: 1.0..3.5
        }

{% endhighlight %}

           
######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
