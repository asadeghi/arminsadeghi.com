---
id: 36
title: Content management systems and Drupal
date: 2006-10-31T20:33:37+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2006/10/content-management-systems-and-drupal/
permalink: /content-management-systems-and-drupal/
categories:
  - General
---
<!-- google_ad_section_start -->

A content management system (CMS) is a computer software system that allows for easy content creation, collaboration, and management. Web content such as this very web site, or the myriad of other news and blog sites on the web are all supported by a CMS system. The chances are that you have already seen and used a CMS, and as I have just set one up for this site I thought it a fitting first subject.

<!--more-->

Using a CMS allows for the author (and, if desired, the site users) to create site content easily without having to author static web pages or use special tools. The site and content can be administered right from within the web browser. In addition the actual content is seperated from the visual representation, such that the visual elements can be altered seperately and consistently. This is usually achieved by placing the actual content into a database such as [MySQL](http://www.mysql.com/).

When you get to picking a CMS there are many options to chose from. There is a good comparison of them in [Wikipedia](http://en.wikipedia.org/wiki/Comparison_of_content_management_systems). This web site is currently running on [Drupal](http://drupal.org/) (the CMS) with a MySQL back end to store the content. This was largely due to some personal recommendations, and so far Drupal has been doing a great job. Drupal is very extensible and provides enough modules and flexibility to make anything from simple blogging sites to full fledged collaboration tools.

Simplified steps for setting up a Drupal CMS:

  1. Download and uncompress the latest install from drupal.org.
  2. Upload the files to your web server (its essentially a bunch of [PHP](http://www.php.net/) scripts)
  3. Set up the database (create, import tables, create user). There is a good [video tutorial](http://drupal.org/videocasts/installing-4.7) for this portion.
  4. Tell Drupal about the database (just one line change in one PHP file).
  5. Install and set up any extra modules for Drupal. I'd recommend at least the _tinymce_, _print_, _textimage_, _captcha_ and _image_ modules.
  6. Spend zero to infinite time messing with the themes and colors.
  7. Realize that different browsers can potentially behave and render pages differently so proceed to install all the popular ones just to test out your pages. In the process realizing that I.E. users have a major [pain](http://drupal.org/node/6696) logging into Drupal unless you mess with one more PHP file and comment out a session\_regenerate\_id() call. Phew&#8230;

And voila! You're done. One CMS system set up and ready to roll.

<!-- google_ad_section_end -->
