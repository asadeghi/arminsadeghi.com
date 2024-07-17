---
title: Software shortcuts
description: Simple command line helpers to look through text files
date: 2009-03-31
guid: http://www.arminsadeghi.com/2009/03/software-shortcuts/
permalink: "/blog/software-shortcuts"
tags:
    - general
---

How many times have you used your code editor to look for some text and either didn&#8217;t find what you were after, or worse yet &#8211; were told that it&#8217;s not there when in fact it was? I bet this has happened to us all at some stage, and after some struggle you master the editor and life goes on, however I want to go over some basic tools/commands that you can always fall back to.

One of the most useful is searching through files. In the windows world you should all know about **findstr**. In particular the following variation:

```dos
findstr /snip /c:"string to look for" *.cpp
```

This command will go through all sub directories, ignoring case, looking through all cpp files for the specified string. And it never lies. In the linux world you want to use something like this:

```bash
find . | xargs grep 'string to look for'
```

If you find yourself repeating steps like this often, place the command in a script. Here is the one I use (it ignores SVN hidden folders and uses color output):

```bash
#!/bin/bash
find . ! -path "*.svn*" | xargs grep "$1" --color=always
```

You can perform all the above searching by using only grep as well:

```bash
grep 'string to find' * --exclude-dir=".svn" -R --color=always`
```
