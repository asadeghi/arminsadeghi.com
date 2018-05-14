---
id: 62
title: Drupal to WordPress Migration
date: 2013-04-29T23:48:34+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/?p=62
permalink: /drupal-to-wordpress-migration/
categories:
  - General
---
Keeping up with security updates on Drupal is exhausting. Not because there are many updates, but because the update process is more time consuming than you would want for a simple blog. So as much as I like Drupal, it&#8217;s time I move this blog to WordPress (WP) and give that a go.

<!--more-->

So far so good. I Had WP up and running in minutes and my only concern was migration of content. There are some random scripts and also professional commercial solutions for this migration, but I wanted to stick with out-of-the-box options (that are free). So here is what I did:

  1. <span style="line-height: 14px;">Drupal has a great default front page RSS feed that it publishes to <strong><em>yoursite.com/rss.xml</em></strong>. So the first thing is to go into the <em>admin/content/rss-publishing</em> and change the settings to output as many pages as possible with <strong><em>Full</em></strong><em> <strong>Text</strong></em>. Then save down the rss.xml file for your site. This will give you an RSS file with all your basic posts.</span>
  2. Then on your WordPress site go to Tools -> Import -> RSS (you might have to download and enable the plugin). Then simply load up the rss.xml file you saved in step 1 and voila! You&#8217;ve got your posts in WP.
  3. Now go through and fix up any images your content used. These are not imported with this process so you&#8217;ll have to upload them into WP manually and edit your articles to include the images instead of broken links.

Catches:

  * <span style="line-height: 14px;">This only really works for basic content. All user details, comments, media and static pages are not migrated.</span>
  * The migration works fine with WP v3.5.1 and Drupal 6.x.
