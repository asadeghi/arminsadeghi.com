---
id: 16
title: Adding Flash video to your website
date: 2009-05-29T12:55:06+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2009/05/adding-flash-video-to-your-website/
permalink: /adding-flash-video-to-your-website/
categories:
  - General
---
<!-- google_ad_section_start -->

If you want to set up a Flash video on your website, and you are using Linux, then this post is for you. I&#8217;ll cover the steps one by one. Keep in mind that there are many different solutions and I have only documented one.

<!--more-->

**1. Istanbul Desktop Session Recorder**
  
Download [Istanbul](http://live.gnome.org/Istanbul) using &#8220;sudo apt-get install istanbul&#8221;. Istanbul will let you record either complete windows, or regions of the screen, and save them as [Ogg media files](http://www.xiph.org/ogg/). Use it to record your desired video.

**2. FFmpeg**
  
Download [FFmpeg](http://www.ffmpeg.org) and use it to convert the Ogg file to a Flash video file (.flv).
  
`ffmpeg -i input_file.ogg -f flv output_file.flv` 
  
**3. Flowplayer**
  
Now all you need is a Flash player to embed into your HTML page and play the Flash video file (this lets users pause, rewind, etc). There are many different options here, but one good option is [Flowplayer](http://flowplayer.org). Download the package from their website. Place the following files from Flowplayer onto your website:

  * flowplayer-3.1.0.min.js
  * flowplayer-3.1.0.swf
  * flowplayer.controls-3.1.0.swf

Also upload your flash video file (output_file.flv in our example) up to your website. Note that Flowplayer won&#8217;t run by default if you try and run it locally. Then just add the following into your HTML page:
  
```
<script src="flowplayer-3.1.0.min.js"></script>
<a href="output_file.flv" style="display:block;width:425px;height:300px;" id="player"></a>
<script language="JavaScript">
flowplayer("player", "flowplayer-3.1.0.swf");
</script>
```
  
Note that the &#8220;player&#8221; parameter to flowplayer() must match the id value in the <a> tag. You can change the size around as much as you like.

<!-- google_ad_section_end -->
