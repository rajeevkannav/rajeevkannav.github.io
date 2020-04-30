---
layout: post
title: Ionic cordova-Geolocation
modified: 2015-03-21
tags: [Ionic, Android, Geolocation, Cordova]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---



* Install cordova plugin by running this command
* Try to handle every possible situations like Location services disbaled / Or user don't allow permission to your application


`cordova plugin add org.apache.cordova.geolocation`


and Then

	.controller('YourCtrl', function (loadingService) {
		loadingService.show        
		var posOptions = {
			timeout: 10000,
			enableHighAccuracy: false
		}
		navigator.geolocation.getCurrentPosition(onPositionSuccess, onPositionError, posOptions)
		function onPositionSuccess(position) {         
			var _position = {
				latitude: position.coords.latitude,
				longitude: position.coords.longitude
			}
        //sucess handler code
        loadingService.hide()
		}
      function onPositionError(error) {
        //error handler code
        loadingService.hide()
      }
	})
    
    
###### More blogs posts will come very soon related to IonicPushNotifications. You just need to stay glued.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>