---
layout: post
title: Object-based searching rails Active-Record
excerpt: "rails search activerecord"
modified: 2016-05-14
tags: [rails, search, activerecord]
comments: true
---


#### Problem
We have listing of all Users and other data list at our admin panels per application.
A basic Search functionality was required with less efforts and adjustable quickly.


#### Solution

In your Gemfile, for the last officially released gem:
    `gem 'ransack'`

##### In your controller

{% highlight ruby %}
def index
  @q = Person.ransack(params[:q])
  @people = @q.result(distinct: true)
end
{% endhighlight %}


##### In your view

{% highlight ruby %}
<%= search_form_for @q do |f| %>

  # Search if the name field contains...
  <%= f.label :name_cont %>
  <%= f.search_field :name_cont %>

  # Search if an associated articles.title starts with...
  <%= f.label :articles_title_start %>
  <%= f.search_field :articles_title_start %>

  # Attributes may be chained. Search multiple attributes for one value...
  <%= f.label :name_or_description_or_email_or_articles_title_cont %>
  <%= f.search_field :name_or_description_or_email_or_articles_title_cont %>

  <%= f.submit %>
<% end %>
{% endhighlight %}

cont (contains) and start (starts with) are just two of the
available search predicates. See [Constants](https://github.com/activerecord-hackery/ransack/blob/master/lib/ransack/constants.rb) for a full list
and the [wiki](https://github.com/activerecord-hackery/ransack/wiki) for more information.


##### Ransack's sort_link helper creates table headers that are sortable links

<%= sort_link(@q, :name) %>



######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
