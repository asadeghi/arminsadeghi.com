---
id: 21
title: Software shortcuts
date: 2009-03-31T14:02:05+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2009/03/software-shortcuts/
permalink: /software-shortcuts/
categories:
  - General
---
<!-- google_ad_section_start -->

How many times have you used your code editor to look for some text and either didn&#8217;t find what you were after, or worse yet &#8211; were told that it&#8217;s not there when in fact it was? I bet this has happened to us all at some stage, and after some struggle you master the editor and life goes on, however I want to go over some basic tools/commands that you can always fall back to.

<!--more-->

One of the most useful is searching through files. In the windows world you should all know about **findstr**. In particular the following variation:

```
findstr /snip /c:"string to look for" *.cpp
```
  
This command will go through all sub directories, ignoring case, looking through all cpp files for the specified string. And it never lies. In the linux world you want to use something like this:

```
find . | xargs grep 'string to look for'
```
  
If you find yourself repeating steps like this often, place the command in a script. Here is the one I use (it ignores SVN hidden folders and uses color output):
  
```
#!/bin/bash
find . ! -path "*.svn*" | xargs grep "$1" --color=always
```
  
You can perform all the above searching by using only grep as well:
  
```
grep 'string to look for' * --exclude-dir=".svn" -R --color=always`
```

<!-- google_ad_section_end -->
