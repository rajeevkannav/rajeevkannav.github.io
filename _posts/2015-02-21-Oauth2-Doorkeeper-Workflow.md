---
layout: post
title: Oauth2 Doorkeeper WorkFlow
modified: 2015-04-25
tags: [Oauth2, Doorkeeper]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---


### An Introduction to OAuth 2
###### Introduction

OAuth 2 is an authorization framework that enables applications to obtain limited access to resources on an HTTP service,
such as Facebook, GitHub, and DigitalOcean. It works by delegating user authentication to the service that hosts the
resource, and authorizing third-party applications to access the resource. OAuth 2 provides authorization flows for web
and desktop applications, and mobile devices.

###### OAuth Roles
    OAuth defines four roles:

        * Resource Owner
        * Client
        * Resource Server
        * Authorization Server

We will detail each role in the following subsections.
###### Resource Owner: User

The resource owner is the user(resource) who authorizes an application to access their account. The application's access
to the user's account is limited to the "scope" of the authorization granted (e.g. read or write access).

###### Resource / Authorization Server: API

The resource server hosts the protected user accounts, and the authorization server verifies the identity of the user
then issues access tokens to the application. From an application developer's point of view, a service's API fulfills
both the resource and authorization server roles. We will refer to both of these roles combined, as the Service or API role.

###### Client: Application

The client is the application that wants to access the user's account. Before it may do so, it must be authorized by the
user, and the authorization must be validated by the API.

###### Abstract Protocol Flow

Now that you have an idea of what the OAuth roles are, let's look at a diagram of how they generally interact with each other:

![Abstract Protocol Flow](https://assets.digitalocean.com/articles/oauth/abstract_flow.png "Abstract Protocol Flow")


######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>