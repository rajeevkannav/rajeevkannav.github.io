---
layout: post
title: "ReactJS - To start guide for Rails developers. Part - 1"
modified: 2015-05-30
excerpt: "ReactJS is the new popular guy around the JavaScript Frameworks block, and it shines for its simplicity."
tags: [ReactJS, Rails, JavaScript Frameworks]
comments: true
---

### Introduction to React.js

React is a JavaScript library for creating user interfaces by Facebook and Instagram. Many people choose to think of
React as the V in MVC. We built React to solve one problem: building large applications with data that changes over
time. To do this, React uses two main ideas. For more details [visit](https://facebook.github.io/react/docs/why-react.html)

### A mock expense tracking app
For this guide, we are building a small application from scratch to keep track of our expenses; each record will consist
of a date, a title and an amount. A record will be treated as Credit if its amount is greater than zero, otherwise it
will be treated as Debit. Here is a mockup of the project:

![Target](https://i.imgur.com/QB8S7ap.png)

Summarizing, the application will behave as follows:

   * When the user creates a new record through the horizontal form, it will be appended to the records table
   * The user will be able to inline-edit any existing record
   * Clicking on any Delete button will remove the associated record from the table
   * Adding, editing or removing an existing record will update the amount boxes at the top of the page


### Let's Start
{% highlight ruby %}
# First things first we need to started our brand new Rails project
rails new reactExample

# Add react-rails to your Gemfile.
gem 'react-rails', '~> 1.0'
{% endhighlight %}

react-rails comes with an installation script, which will create a components.js
file and a components directory under app/assets/javascripts where our React components will live.

{% highlight ruby %}
  rails g react:install
{% endhighlight %}

If you take a look at your application.js file after running the installer, you will notice three new lines:

{% highlight ruby %}
//= require react
//= require react_ujs
//= require components
{% endhighlight %}


{% highlight ruby %}
rails g resource Record title date:date amount:float # Creating the Resource

rake db:create db:migrate
{% endhighlight %}

##### db/seed.rb

{% highlight ruby %}
Record.create title: 'Record 1', date: Date.today, amount: 500
Record.create title: 'Record 2', date: Date.today, amount: -100

rake db:seed
{% endhighlight %}

### Nesting Components: Listing Records

#####  app/controllers/records_controller.rb
{% highlight ruby %}
class RecordsController < ApplicationController
  def index
    @records = Record.all
  end
end
{% endhighlight %}

#####  app/views/records/index.html.erb
{% highlight ruby %}
<%= react_component 'Records', { data: @records } %>
{% endhighlight %}


##### app/assets/javascripts/components/records.js.coffee
{% highlight ruby %}
    @Records = React.createClass
      getInitialState: ->
        records: @props.data
      getDefaultProps: ->
        records: []
      render: ->
        React.DOM.div
          className: 'records'
          React.DOM.h2
            className: 'title'
            'Records'
          React.DOM.table
            className: 'table table-bordered'
            React.DOM.thead null,
              React.DOM.tr null,
                React.DOM.th null, 'Date'
                React.DOM.th null, 'Title'
                React.DOM.th null, 'Amount'
            React.DOM.tbody null,
              for record in @state.records
                React.createElement Record, key: record.id, record: record
{% endhighlight %}



##### app/assets/javascripts/utils.js.coffee
{% highlight ruby %}
     @amountFormat = (amount) ->
       '$ ' + Number(amount).toLocaleString()
{% endhighlight %}


##### app/assets/javascripts/components/record.js.coffee
{% highlight ruby %}
     @Record = React.createClass
       render: ->
         React.DOM.tr null,
           React.DOM.td null, @props.record.date
           React.DOM.td null, @props.record.title
           React.DOM.td null, amountFormat(@props.record.amount)
{% endhighlight %}



![Current State](https://i.imgur.com/vETiEeF.png)


You can take a look at the resulting code of this section [here](https://github.com/rajeevkannav/reactExample),
And Please wait for Part-2.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/) 

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>