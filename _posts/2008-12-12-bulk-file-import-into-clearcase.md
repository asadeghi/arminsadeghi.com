---
id: 22
title: Bulk file import into Clearcase
date: 2008-12-12T08:31:34+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2008/12/bulk-file-import-into-clearcase/
permalink: /bulk-file-import-into-clearcase/
categories:
  - General
---
<!-- google_ad_section_start -->

If you have used good source control systems such as [subversion](http://subversion.tigris.org/) or [perforce](http://www.perforce.com/), you will know that adding a whole pile of files (as you would at the beginning of a project) is a trivial task. In the case of subversion it's just two commands, svn add, svn commit, and you are done. If however you have the misfortunte to have to use IBM Rational Clearcase you are a little out of luck.

So before you go and start adding the two hundred files one by one using cleartool mkelem, take a look at this option:

`clearfsimport -nsetevent -recurse c:\tmp\srcfolder\new c:\views\destination_view_folder\srcfolder` 

<!--more-->

The catch is that the files must initially be stored somewhere outside your view, which is unlike other source control systems. With clearfsimport you have the files elsewhere and then 'import' them into your view. Clearfsimport also supports a '-preview' switch to tell you what it plans to do without doing it.

Now that you can do this easily, you may want to consider moving dependencies into source control. So if you depend on a particular version of some control or tool, add it to source control and wire your system to use the controlled item. Managing dependencies in this manner can alleviate all sorts of problems with dependencies and gives you an extra level of control over your development environment.

<!-- google_ad_section_end -->
