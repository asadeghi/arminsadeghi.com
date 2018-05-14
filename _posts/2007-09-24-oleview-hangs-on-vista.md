---
id: 27
title: Oleview hangs on Vista
date: 2007-09-24T23:27:07+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2007/09/oleview-hangs-on-vista/
permalink: /oleview-hangs-on-vista/
categories:
  - General
---
<!-- google_ad_section_start -->

Those who have upgraded to Vista may have many issues to discuss, however today I just wanted to mention one in particular. Typelibs. In particular how to view them. 

<!--more-->

As you may know a typelib is simply a file containing type information. Information such as data types, interfaces, object classes, member functions, etc. All the things you need to know about to use an OLE object. Now once compiled in their binary form (tlb files) these are a little hard to read so its nice to transform a type library back to Interface Definition Language (IDL). 

There are of course many such tools, however Oleview.exe, which comes with Visual Studio, does this for you (File->View TypeLib). This is very handy indeed. However it seems there is an issue with running Oleview from an elevated command prompt in Vista&#8230; it hangs. There are a few suggestions on the web but the one that worked for me was thanks to Shri Borde. I.e. don't run Oleview from an elevated command prompt. I'd be curious to find out why this is the case. 

<!-- google_ad_section_end -->
