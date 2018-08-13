---
layout: post
title: managing node versions with n    
excerpt: "Interactively Manage Your Node.js Versions"
modified: 2017-06-30
tags: [n, node, versions]
comments: true
---

#### Node version management with n

Node version management with nvm is great yet there is one
new tool comes up which is n. Currently n supports only linux
and Osx not available for windows.

#### Installation   

###### already have `node`
   
    $ npm install -g n
   
###### Alternatively   

    git clone git@github.com:tj/n.git
    cd n
    make install

###### Third-party installer (Recommended)

    curl -L https://git.io/n-install | bash

#### Usage
   
###### Installing Versions
       
For installing version 0.8.14     
    
    $ n 0.8.14 
    
###### Activating Versions

Execute n on its own to view your currently installed
versions. Use the up and down arrow keys to navigate
and press enter or the right arrow key to select.


    $ n
    
      0.8.14
    ο 0.8.17
      0.9.6

###### Removing Versions

Remove some versions:
       
    $ n rm 0.9.4 v0.10.0

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)
                  
<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
