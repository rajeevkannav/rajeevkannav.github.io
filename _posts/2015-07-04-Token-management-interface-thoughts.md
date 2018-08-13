---
layout: post
title: "Token management thoughts reference WEB/REST"
modified: 2015-07-04
excerpt: "Token management thoughts reference WEB/REST devise token auth Design Pattern"
tags: [Token management, Web, Thoughts]
comments: true
---

### Conceptual Token Handling

Tokens should be invalidated after each request to the API. The following diagram illustrates this concept:

![Target](https://github.com/lynndylanhurley/ng-token-auth/raw/master/test/app/images/flow/token-update-detail.jpg)

During each request, a new token is generated. The access-token header that should be used in the next request is
returned in the access-token header of the response to the previous request. The last request in the diagram fails
because it tries to use a token that was invalidated by the previous request.

The only case where an expired token is allowed is during batch requests.

### About batch requests

By default, the API should update the auth token for each request (read more). But sometimes it's neccessary to make
several concurrent requests to the API, for example:

##### Batch request example

{% highlight javascript %}

  $scope.getResourceData = function() {  
    $http.get('/api/restricted_resource_1').success(function(resp) {
      // handle response
      $scope.resource1 = resp.data;
    });  
    $http.get('/api/restricted_resource_2').success(function(resp) {
      // handle response
      $scope.resource2 = resp.data;
    });
  };

{% endhighlight %}


In this case, it's impossible to update the access-token header for the second request with the access-token header of
the first response because the second request will begin before the first one is complete. The server must allow these
batches of concurrent requests to share the same auth token. This diagram illustrates how batch requests are identified
by the server:

![Target](https://github.com/lynndylanhurley/ng-token-auth/raw/master/test/app/images/flow/batch-request-overview.jpg)


The following diagram details the relationship between the client, server, and access tokens used over time when dealing
with batch requests:

![Target](https://github.com/lynndylanhurley/ng-token-auth/raw/master/test/app/images/flow/batch-request-detail.jpg)


Note that when the server identifies that a request is part of a batch request, the user's auth token is not updated.
The auth token will be updated for the first request in the batch, and then that same token will be returned in the
responses for each subsequent request in the batch (as shown in the diagram).


######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>