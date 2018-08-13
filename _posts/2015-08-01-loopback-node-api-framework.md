---
layout: post
title: "loopback - The Node.js API Framework"
modified: 2015-08-01
excerpt: "LoopBack is a highly-extensible, open-source Node.js framework"
tags: [loopback,node.js,api,framework]
comments: true
---


We've Rails,Django and Node has yet to be established. Now, there is a powerful framework gaining steam: LoopBack, an 
open source API framework built by StrongLoop. StrongLoop is an important contributor to the latest Node version,
not to mention the current maintainers of Express, one of the most popular Node frameworks in existence.

<figure class="third">
	<img src="/images/loopback.svg">
</figure>

## About

  *  Quickly create dynamic end-to-end REST APIs.
  * Connect devices and browsers to data and services.
  * Use Android, iOS, and AngularJS SDKs to easily create client apps.
  * Add-on components for push, file management, 3rd-party login, and geolocation.
  * Use StrongLoop Arc to visually edit, deploy, and monitor LoopBack apps.
  * StrongLoop API Gateway acts an intermediary between API consumers (clients) and API providers to externalize, secure, and manage APIs.
  * Runs on-premises or in the cloud



### Install

Assuming you have already installed Node, Install the StrongLoop tools for LoopBack applications.

    $ npm install -g strongloop

##### Create a "Hello World" LoopBack application.

    $ slc loopback
    [?] Enter a directory name where to create the project: hello-world
    [?] What's the name of your application? hello-world

##### Create models

    $ cd hello-world
    $ slc loopback:model

The generator guides you through creating your model. Enter the values highlighted in blue.
To accept the default, just press Enter.

    [?] Enter the model name: person
    [?] Select the data-source to attach person to: db (memory)
    [?] Expose person via the REST API? Yes
    [?] Custom plural form (used to build REST URL): people

Let's add some person properties now. Define a firstname property for the person model

    Enter an empty property name when done.
    [?] Property name: firstname

Hit Enter to accept the default string type:

    [?] Property type: (Use arrow keys)
    ❯ string
      number
      boolean
      object
      array
      date
      buffer
      geopoint
      (other)

Make the property required.

    [?] Required? (y/N) y

Repeat these steps for lastname property.

Press Enter when prompted for a property name to finish up and create the model. 

##### Run the application

Run as you would any Node application.

    $ node .
    Browse your REST API at http://0.0.0.0:3000/explorer
    Web server listening at: http://0.0.0.0:3000/

When you're ready to think about moving to production, you can use slc start to run the app under the control of a local
instance of StrongLoop Process Manager. This enables you to profile, monitor, and control clustering for the app and
keep it running forever. See strong-pm.io for more information. Explore your REST API

Visit [localhost](http://0.0.0.0:3000/explorer)

The API Explorer enables you to exercise all the generated API endpoints. There are create, read, update, and delete (CRUD)
endpoints for the people model you just created. For more information, see the Using the API Explorer in the documentation.
You may also want to follow the Getting Started tutorial.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>