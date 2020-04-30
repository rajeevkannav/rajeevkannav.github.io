---
layout: post
title: fastlane tools family introduction snapshot  
excerpt: "Automate taking localized screenshots of your iOS app on every device"
modified: 2015-10-17
tags: [Apple, deployment, iOs, snapshot]
comments: true
image:
  feature: ionicCordova.jpg
  credit: Google Images
  creditlink: https://cdn-netcetera.netdna-ssl.com/img/bgservers.jpg
---

[fastlane-Snapshot](!https://github.com/KrauseFx/snapshot) lets you Automate taking localized screenshots of your iOS app on every device. 

### Problem: You have an iPhone app. You support 20 languages. You updated the design. You want to release the update to the App Store. What's missing?

### Solution: You have to manually create 20 (languages) x 5 (devices) x 5 (screenshots) = 500 screenshots.

Or Use fastlane famliy tool `snapshot`

#### fastlane features


  *  Create hundreds of screenshots in multiple languages on all simulators
  *  Configure it once, store the configuration in git
  *  Do something else, while the computer takes the screenshots for you
  *  Integrates with fastlane and deliver
  *  Generates a beautiful web page, which shows all screenshots on all devices. This is perfect to send to Q&A or the marketing team
  *  snapshot automatically waits for network requests to be finished before taking a screenshot
     (we don't want loading images in the App Store screenshots)
  *  Support for advanced configuration, like preprocess macros or prefilling of data
  * 100% open source unlike Apple

After `snapshot` successfully created new screenshots, it will generate a beautiful html file to get a quick overview of all screens:

<figure>
	<img src="/images/snapshot.jpg">
</figure>


#### Start snapshot

  *  `cd [your_project_folder]`
  *  `snapshot`

Your screenshots will be stored in `./screenshots/` by default.

From now on, you can run snapshot to create new `screenshots` of your app.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
