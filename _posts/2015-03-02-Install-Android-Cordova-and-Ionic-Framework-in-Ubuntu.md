---
layout: post
title: Install Android, Cordova, and Ionic Framework in Ubuntu
modified: 2015-03-02
tags: [Ionic, Android, Cordova, Ubuntu]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---



#### Requirements:


  *  Java JDK
  *  Apache Ant
  *  Android SDK
  *  NodeJS / NPM
  *  Apache Cordova
  *  Ionic Framework



#### Steps:


    * Download a shell script by clicking on this link 
    ** https://github.com/nraboy/ubuntu-ionic-installer/archive/master.zip  
    * Extract and goto extracted folder.
    * chmod 775 ubuntu_ionic_installer.sh 
    * sudo ./ubuntu_ionic_installer.sh
    * To download the necessary Android targets and platform tools you will need to enter `android` from a command prompt to launch the Android UI. You will need `Android API 19` for Ionic Framework, so install that when you’re able to.
    * ionic start ExampleProject maps
    * cd ExampleProject
    * ionic platform add android
    * ionic build android
    * That's It.
    
######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>    