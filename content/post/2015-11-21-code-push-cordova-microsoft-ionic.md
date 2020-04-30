---
layout: post
title: CodePush Ionic Instant updates
excerpt: "Push code updates to your apps, instantly"
modified: 2015-11-21
tags: [maximum allowed size, nginx]
comments: true
image:
  feature: webServer.jpg
  credit: Google Images
  creditlink: https://cdn-netcetera.netdna-ssl.com/img/bgservers.jpg
---

### Problem:

     We're using an Mobile Application creator framework which need to update application instantly.
     Without using Store(s) Google-Play, App-store and as expected solution must be easy/Generic.
      
### Solution

#### CodePush 
    CodePush is a cloud service that enables Cordova and React Native developers to deploy mobile app updates directly
    to their users’ devices. It works by acting as a central repository that developers can publish certain updates to
    (e.g. JS, HTML, CSS and image changes), and that apps can query for updates from (using our provided client SDKs).

##### How to give it a Try.
    
###### Install the CodePush CLI
    
`npm install -g code-push-cli # may be with sudo`
    
###### Create a CodePush account

`code-push register`

###### doLogin()

`code-push login`

###### create a blank Ionic App, lets call it instantApp
    
`$ ionic start instantApp sidemenu`
    
###### CodePush-ify your mobile client

`cordova plugin add cordova-plugin-code-push`

###### Register your app with the service

`code-push app add instantApp` # you'll get deployment keys per environment
    
###### Create one deployment per target platform using the 
    
{% highlight ruby %}

<platform name="android">
    <preference name="CodePushDeploymentKey" value="YOUR-ANDROID-DEPLOYMENT-KEY" />
</platform>
<platform name="ios">
    <preference name="CodePushDeploymentKey" value="YOUR-IOS-DEPLOYMENT-KEY" />
</platform>

{% endhighlight %}

###### Allow access to the CodePush server:
 
 * In config.xml, add
 `<access origin="https://codepush.azurewebsites.net/ " />`
 * In your html pages where the plugin is used, add the server URL to your existing Content Security Policy (CSP) header:
 `<meta http-equiv="Content-Security-Policy" content="default-src https://codepush.azurewebsites.net/ 'self' ... ">`
    

###### doSomeCode It's Sample

{% highlight ruby %}

  var onError = function (error) {
      console.log("An error occurred. " + error);
  };

  var onApplySuccess = function () {
      console.log("Apply succeeded. Reloading the application...");
  };

  var onPackageDownloaded = function (localPackage) {
      localPackage.apply(onApplySuccess, onError);
  };

  var onUpdateCheck = function (remotePackage) {
      if (!remotePackage) {
          console.log("The application is up to date.");
      } else {
          console.log("A CodePush update is available. Package hash: " + remotePackage.packageHash);
          remotePackage.download(onPackageDownloaded, onError);
      }
  };

  window.codePush.checkForUpdate(onUpdateCheck, onError);

{% endhighlight %}

###### Create an application update package

 * Prepare your application
 `cordova prepare <platform>`
   
 
 We are not deploying binaries in updates, so prepare is enough for this step. The cordova build command works as well
 for this step, since it calls cordova prepare behind the scenes.
     
 * Deploy update using the CodePush CLI
 
   * For Android:  
   `code-push release <appName> path_to_your_app/platforms/android/assets/www <appStoreVersion> --deploymentName <AndroidDeploymentName>`
   
   * For iOS:
   `code-push release <appName> path_to_your_app/platforms/ios/www <appStoreVersion> --deploymentName <iOSDeploymentName>`
  

 * The service should now return an update when calling `codePush.checkForUpdate`.
    

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
