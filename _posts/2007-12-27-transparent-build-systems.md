---
id: 26
title: Transparent build systems
date: 2007-12-27T00:00:40+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2007/12/transparent-build-systems/
permalink: /transparent-build-systems/
categories:
  - General
---
<!-- google_ad_section_start -->

Whenever you deal with a software project, you deal with a build system. The method and process by which you turn your code into a product. This may involve many steps such as pre-processing, compiling, linking, moving files around, and signing among others. The trouble is that on some projects this system becomes an afterthought rather than a purposeful choice. Today I want to briefly talk about the benefits obtained from a good build system. 

<!--more-->

So why think seriously about a build system? Why not fire up Visual Studio, hit 'New Project', and just start coding? The simple answer is that you will eventually get stuck, and the last thing you want to get stuck with is a broken limiting build system that is difficult to decipher and extend. A good system will give you: 

  * A deterministic repeatable build. This will give you confidence that when you create a build it will actually work, the same way as on other machines, every time. No weird oddities or unexplainable results.
  * Complete transparency over the build. Including every step, action, process, parameters and files involved, dependencies, and the control by which to alter any of the these.

"Why is this good? NMake and command lines are painful, should we not have more abstraction?" you may ask. To a degree, yes, modern IDEs and some build tools make things easier, however they are generally designed to handle the common case, not anything complex. For example if your build involves building with different versions of a framework (such as a product targetting v1.1 and v2.0 of the .Net Framework), requiring input and output files in specific folders (seperating source files from generated ones is very helpful for both source control, tracking, and cleaning purposes), or being able to reproduce build steps individually for debugging.

So what should you do? Its easy, just think about your requirements, the complexity of your project (both now and future), and ensure that you have enough transparency in the build system so that you can get what you need done as well as have the ability to view/fix/extend when necessary. In particular make sure: 

  * Build settings are stored somewhere easy to view.
  * You have full control over where files are written to. The last thing you want is to have random temporary files generated all over your source tree (that you then, accidentally, check in to the depot). 
  * The build is deterministic. Deleting the output and rebuilding gives you the exact same thing every time.
  * You have visibility into each step of the build, so that when something goes wrong you can see what caused it.
  * You have control over the tools and dependencies used.

Basically as much transparency over the process as you can get. Other than that &#8211; don't be afraid of make /nmake /rake (or whichever dependency build utility applies to your project) and a command line. They work great!&nbsp; 

<!-- google_ad_section_end -->
