---
layout: post
title: Force Node/Heroku Application to https    
excerpt: "http to https redirection"
modified: 2017-01-03
tags: [heroku, ssl, node, angular, http, https]
comments: true
---

#### Problem

WE deployed our angular app to Heroku with custom domain. There are Heroku
Add-ons by which SSL can be enabled but our problem was to enforce http
requests to https. 


#### Solution   

Inside your `server.js` (in our case) put the following code after
app or express (in our case) app variable.

    /* Redirect http to https */
    app.get('*',function(req,res,next){
      if(req.headers['x-forwarded-proto']!='https'&&process.env.NODE_ENV === 'production')
        res.redirect('https://'+req.hostname+req.url)
      else
        next() /* Continue to other routes if we're not redirecting */
    });


In the `if` block, `req.headers['x-forwarded-proto']` should be equal to `https`.
On the other hand, we don’t want the redirection on localhost as we don’t have a 
ssl certificate set up locally that's why we used `process.env.NODE_ENV === 'production'`
inside the condition to make sure that this will only run on Heroku/Production,
which has the `NODE_ENV` environment variable set to `production`.


If both these conditions are true, this means someone is trying to access
our app though `http`. We need to swap `http` for `https` and redirect them to
the new url. To reform the url that they are trying to call we use
`req.hostname` in combination with `req.url`.

And finally we redirect using `res.redirect()`.


######  And if you get stuck… [Ask Here](http://stackoverflow.com/)
                  
<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
