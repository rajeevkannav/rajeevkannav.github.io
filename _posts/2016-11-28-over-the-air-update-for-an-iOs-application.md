---
layout: post
title: over the Air Test version app for Apple   
excerpt: "Over the air"
modified: 2016-11-28
tags: [Apple, Over-the-air]
comments: true
---

### Apple App Distribution

  Distributing an iPhone application is a headache. We(our iOs Team) use a service called
  [Diawi](https://www.diawi.com/) to deploy Development and In-house applications directly
  to the devices. We must need to add allowed devices already to those provisioning profile
  and these files with ipa to diawi.
 
### Problem
 
  [Diawi](https://www.diawi.com/) provides a link with an expiry time and we need to share
  provisioning profile and certificates with them too. Everytime they produce a new link.
   
### Solution
  
  * generate an IPA via xcode/CLI
  * get the link of the IPA and add in the plist
  * place generated plist file in drop box
  * get the link from the dropbox
  * construct an items link with the dropbox 
  
  You can send the items link to the testing team to use the file for testing.
  This setting up is an one time process and for further changes and the updates
  you just replace the IPA file is the already uploaded path. The testing team
  in the remote can fetch the updated file with the same link path.
  
  A sample items link is given below.
    
    itms-services://?action=download-manifest&url=https://myWebsite/myApp/myApp.plist
    
    itms-services://?action=download-manifest&url=<Dropbox URL>
    

#### Note: 
    We haven't implemented this yet to our iOS Team app distibution process, We got this excellent
    idea from the reference given below, By this way, for sure we'll solve the issue of testing of
    iOS apps with the team in a remote location.

### References:      

 [Mallow Technologies Private Limited](http://54.173.149.226/2016/09/how-to-send-test-version-over-the-air-ota/)

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
