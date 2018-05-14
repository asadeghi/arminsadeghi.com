---
id: 14
title: Publisher 2007 PDF export loses text color
date: 2009-10-16T13:06:52+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2009/10/publisher-2007-pdf-export-loses-text-color/
permalink: /publisher-2007-pdf-export-loses-text-color/
categories:
  - General
---
<!-- google_ad_section_start -->

I ran into a bizarre issue yesterday. I had a Publisher 2007 document, with various different text colors utilized, and every time I exported it to PDF (using the 2007 Microsoft Office Add-in: Microsoft Save as PDF) all the colors were lost. I ended up with black and white text.

<!--more-->

Printing worked just fine, and printing to the Adobe PDF print driver worked fine, but I wanted to save to PDF directly from Publisher (which gave me the best control over image quality). After a bunch of testing it turned out that the problem was that I had a black and white laser printer set as my default printer. So even though I wasn't printing to it, Publisher picked up the color properties of the default printer and applied them to the PDF.

So in the future, remember to set your default printer to something with color before saving to PDF.

<!-- google_ad_section_end -->
