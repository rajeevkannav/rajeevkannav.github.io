---
layout: post
title: install PhoneGap pushPlugin 2.0.0 on ubuntu/Osx    
excerpt: "phonegap-plugin-push"
modified: 2017-06-27
tags: [ionic, cordova, pushplugin, cocoaPods]
comments: true
---

#### Problem

We're using `phonegap-plugin-push` to Register and receive push notifications to
ionic applications and unfortunately that's get updated.

Version 2.0.0, this plugin will support CocoaPods installation of the
Firebase Cloud Messaging library.


#### Solution   

Install CocoaPods and re-build the platforms is only the requirement
 
 To install CocoaPods, please follow the installation instructions here.
 
    sudo gem install cocoapods
 
 After installing CocoaPods, please run:
 
    pod setup

This will clone the required CocoaPods specs-repo into your home folder
at ~/.cocoapods/repos, so it might take a while.

    cordova plugin add phonegap-plugin-push@2.0.0
    
and do the build process for android and iOs. You also need a google-services.json
from Firebase to build apk(s). 

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)
                  
<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
