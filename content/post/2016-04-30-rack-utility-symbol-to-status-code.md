---
layout: post
title: Rack::Utils Basic information
excerpt: "Rack Utils usage"
modified: 2016-04-23
tags: [rails, rack, middleware]
comments: true
---


#### Problem
Every HTTP statuses code are available in form of symbol in Rails in a slightly more readable form. You may heard few of
them like

{% highlight ruby %}
    :ok
    :not_modified
{% endhighlight %}

We're interested to use every status to symbol which looks good to me. Following can be found on Rails Console/Documentation
 via

{% highlight ruby %}
 Rack::Utils::SYMBOL_TO_STATUS_CODE

  => {
        :continue=>100, :switching_protocols=>101, :processing=>102,
        :ok=>200, :created=>201, :accepted=>202,
        :non_authoritative_information=>203, :no_content=>204,
        :reset_content=>205, :partial_content=>206, :multi_status=>207,
        :already_reported=>208, :im_used=>226, :multiple_choices=>300,
        :moved_permanently=>301, :found=>302, :see_other=>303,
        :not_modified=>304, :use_proxy=>305, :temporary_redirect=>307,
        :permanent_redirect=>308, :bad_request=>400, :unauthorized=>401,
        :payment_required=>402, :forbidden=>403, :not_found=>404,
        :method_not_allowed=>405, :not_acceptable=>406,
        :proxy_authentication_required=>407, :request_timeout=>408,
        :conflict=>409, :gone=>410, :length_required=>411,
        :precondition_failed=>412, :payload_too_large=>413,
        :uri_too_long=>414, :unsupported_media_type=>415,
        :range_not_satisfiable=>416, :expectation_failed=>417,
        :unprocessable_entity=>422, :locked=>423, :failed_dependency=>424,
        :upgrade_required=>426, :precondition_required=>428,
        :too_many_requests=>429, :request_header_fields_too_large=>431,
        :internal_server_error=>500, :not_implemented=>501, :bad_gateway=>502,
        :service_unavailable=>503,:gateway_timeout=>504,
        :http_version_not_supported=>505, :variant_also_negotiates=>506,
        :insufficient_storage=>507, :loop_detected=>508, :not_extended=>510,
        :network_authentication_required=>511
  }

{% endhighlight %}


Rack::Utils contains a grab-bag of useful methods for writing web applications adopted from all kinds of Ruby libraries.
It contains methods like -
{% highlight ruby %}
 .add_cookie_to_header(header, key, value) ⇒ Object
 .add_remove_cookie_to_header(header, key, value = {}) ⇒ Object
{% endhighlight %}

which sound quite handy to play with header cookies and there are lots of more stuff.


######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
