---
layout: post
title: Apple On-Demand Streaming Support with amazon cloudfront and Transcoding API   
excerpt: "Apple On-Demand Streaming Support"
modified: 2016-09-24
tags: [Apple, On-Demand Streaming, aws cloudfront, aws Transcoding ]
comments: true
---

### Apple On-Demand Streaming

In the on-demand streaming case, your video content is stored in S3. Your viewers
can choose to watch it at any desired time, hence the name on-demand. A complete
on-demand streaming solution typically makes use of Amazon S3 for storage, the Amazon
Elastic Transcoder for video processing, and Amazon CloudFront for delivery.

### CloudFront

Using Amazon CloudFront, You can deliver adaptive bitrate video in a scalable,
high performing and cost effective manner to audiences around the world with
format specification. 

### Amazon Elastic Transcoder 

Amazon Elastic Transcoder manages all aspects of the media transcoding
process for you transparently and automatically. There’s no need to administer
software, scale hardware, tune performance, or otherwise manage transcoding infrastructure.

### How To ?

To use CloudFront to stream media files in Apple HTTP Live Streaming (HLS) format,
perform the following tasks:

    * Transcode your media files into HLS format. You can use any transcoding
      application that supports HLS format, for example, Amazon Elastic Transcoder.

    * Create a CloudFront web distribution. No special settings are required.

    * (Upload your files to the origin that you specified when you created your distribution.

    * For links in your application (for example, a media player), specify the master playlist
      in the same format that you use for other objects that you're distributing using CloudFront.
      For more information, see Format of URLs for CloudFront Objects.
      
### References:      

 [Amazon Web Services Docs](https://aws.amazon.com/blogs/aws/using-amazon-cloudfront-for-video-streaming/)
######  And if you get stuck… [Ask Here](http://stackoverflow.com/)

<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
