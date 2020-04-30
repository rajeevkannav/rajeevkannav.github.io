---
layout: post
title: Ionic Hide keyBoard
modified: 2015-03-21
tags: [Ionic, Android, Cordova, Ubuntu]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

On both Android and iOS, Ionic will attempt to prevent the keyboard from obscuring inputs and focusable elements when it
appears by scrolling them into view. In order for this to work, any focusable elements must be within a Scroll View or a
directive such as Content that has a Scroll View.

### Hide when keyboard shows

To hide an element when the keyboard is open, add the class hide-on-keyboard-open.

```
<div class="hide-on-keyboard-open">
  <div id="google-map"></div>
</div>
```


### Plugin Usage

Information on using the plugin can be found at https://github.com/driftyco/ionic-plugins-keyboard.

######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me </b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>