---
id: 12
title: Case-insensitive Autocomplete in Bash
date: 2010-05-27T16:50:44+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2010/05/case-insensitive-autocomplete-in-bash/
permalink: /case-insensitive-autocomplete-in-bash/
categories:
  - General
---
I use auto complete on the command line all the time to avoid having to type the full name of a file. Love it. What I hate is how it&#8217;s case-sensitive in bash, so I can&#8217;t do &#8220;cd ~/desk&#8221; to go to the &#8220;~/Desktop&#8221; folder.

The fix for this is to use the shell input options file: **.inputrc**
  
Just set this one option and restart your shell:

<pre>echo 'set completion-ignore-case On' &gt;&gt; ~/.inputrc</pre>

If you happen to have a system wide inputrc settings ( /etc/inputrc ) and want it included then you should add the following to your .inputrc file:

<pre>$include /etc/inputrc</pre>