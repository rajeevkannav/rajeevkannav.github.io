---
layout: post
title: Bad to worse rails practice    
excerpt: "all is not realall"
modified: 2017-02-03
tags: [rails, migration, scope]
comments: true
---

#### Problem

We used ruby gem `paranoia` to soft delete our active-records. which is super easy
to integrate with a rails application. Our migrations consists such code to update
all `User/Project`. While running migrations to a new created DB following code
will break due to `paranoia` expectations of having `deleted_at` column, which is
being added in later migrations. Now that sucks, I've to comment out 
`acts_as_paranoid` every time while running migrations to new db.

#### Solution   

`User.all` update should be `User.unscoped.all.` updates. Well this is not related
to only `paranoia`. We should keep this always in mind,  In Case we want to update
or operate all (all i mean) we must use `unscoped` *always*. Second thing, We should
not use such code into migrations. This could be very obvious but i've seen such
ignorance ever.
  

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)
                  
<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
