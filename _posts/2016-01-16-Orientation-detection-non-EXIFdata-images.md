---
layout: post
title: Orientation detection for NON-EXIF data/Text Images.
excerpt: "OCR engine research"
modified: 2016-01-16
tags: [Orientation, OCR engine, NON-EXIF data,Text Images]
comments: true
image:
  feature: rails.jpg
  credit: Google Images
  creditlink: http://www.gapintelligence.com/system/pictures/282/content_love-ruby.jpg
---

### Problem:

    We've a Enterprise level application which process images from pdf(s). 
    We've to represent those images to exact image Orientation with intelligence.
    User May rotete images if Auto-Rotation Algorithm failed. 
      
### [TESSERACT](https://github.com/tesseract-ocr)

    tesseract(1) is a commercial quality OCR engine originally developed at 
    HP between 1985 and 1995.In 1995, this engine was among the top 3 evaluated
    by UNLV. It was open-sourced by HP and UNLV in 2005 and has been developed
    at Google since then.
   
{% highlight ruby %}
    `tesseract image - -psm 0`
     # > 
     # Orientation: 3
     # Orientation in degrees: 90
     # Orientation confidence: 4.76
     # Script: 1
     # Script confidence: 4.37   
{% endhighlight %}

#### Orientation in degrees is the required amount of Orientation required for image. You may use any imgae-processing library say [ImageMagick](https://github.com/ImageMagick/ImageMagick) example command given below

{% highlight ruby %}
    `convert -rotate #{Orientation in degrees} rotest.jpg rotest90.jpg`
{% endhighlight %}

           
######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
