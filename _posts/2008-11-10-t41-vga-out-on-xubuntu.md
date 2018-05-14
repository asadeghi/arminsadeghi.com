---
id: 23
title: T41 VGA out on Xubuntu
date: 2008-11-10T20:24:41+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2008/11/t41-vga-out-on-xubuntu/
permalink: /t41-vga-out-on-xubuntu/
categories:
  - General
---
<!-- google_ad_section_start -->

Video output to an external monitor is easy right? Well it was on Windows XP, but with Xubuntu (8.04 Hardy Heron) running on an IBM Thinkpad T41 turned out to be a little trickier than hitting function-F7.

<!--more-->

Firstly hitting function-F7 doesn't do anything, even though all the other function buttons (keyboard light, screen brightness, etc) work fine. If you leave the external monitor plugged in, and reboot, you should see the port come to life. Next you run your favourite video player (like VLC) and notice that the video only appears on the laptops LCD display, and not on the external monitor. To solve this simply:

  1. sudo apt-get install xvattr
  2. xvattr -a XV_CRTC -v 1

Done. That should switch the video output to the VGA port. To switch back use this:

  1. xvattr -a XV_CRTC -v -1 

If you haven't had a chance to look at Xubuntu, you should check it out. It's essentially Ubuntu but with the Xfce desktop manager. Much smaller and faster than Gnome and Kde. Great for old hardware (like my T41).

<!-- google_ad_section_end -->
