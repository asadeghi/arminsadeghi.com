---
id: 19
title: TSVNCache.exe process slowing down Windows
date: 2009-04-29T17:27:52+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2009/04/tsvncache-exe-process-slowing-down-windows/
permalink: /tsvncache-exe-process-slowing-down-windows/
categories:
  - General
---
I regularly use [Subversion](http://subversion.tigris.org/) (version control system) along with the [Tortoise SVN](http://tortoisesvn.tigris.org/) shell client. I mostly stick to the command line tools, but its nice to have some shell integration occasionally. Tortoise SVN provides this integration well.

<!--more-->

Just recently however I noticed a runaway process called &#8220;TSVNCache.exe&#8221; using up a lot (in my case one whole processor) of CPU cycles. I saw this happen on both Windows XP and Vista. TSVNCache.exe is the Tortoise SVN process that is responsible for all those [icon overlays](http://tortoisesvn.net/node/138) in Explorer when you view your SVN repository. The process sits there and scans the status of your files and updates them with appropriate icons to indicate state (i.e. modified, added, etc). For some reason it started misbehaving on my machine and grinding everything to a halt (Tortoise SVN version 1.6.1).

[<img class="alignnone size-full wp-image-43" src="http://www.arminsadeghi.com/wp-content/uploads/2009/04/tsvncache.jpg" alt="tsvncache" width="524" height="346" srcset="http://www.arminsadeghi.com/wp-content/uploads/2009/04/tsvncache.jpg 524w, http://www.arminsadeghi.com/wp-content/uploads/2009/04/tsvncache-300x198.jpg 300w" sizes="(max-width: 524px) 100vw, 524px" />](http://www.arminsadeghi.com/wp-content/uploads/2009/04/tsvncache.jpg)

The simple workaround is to turn these overlays off. You can do this by going to the Settings menu (right click somewhere in your repository and select TortoiseSVN->Settings), and turning &#8220;Status cache&#8221; to None (see above).

There are three settings for the overlay cache:

  * **Default**: Uses TSVNCache.exe to process icon overlays
  * **Shell**: Lets the explorer process handle and cache overlays
  * **None**: Turns overlay status cache off

In my case I didn&#8217;t care too much for the overlays so I just turned them off. You still get the green tick for checked in folders, but nothing else. Alternatives for improving the performance are to exclude and include paths for Tortoise SVN to monitor (in the same settings dialog again), and/or to show overlays only in Explorer (top checkbox).
