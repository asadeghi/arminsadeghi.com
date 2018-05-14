---
id: 13
title: Enable HTTP Authentication on Dreamhost
date: 2010-05-21T11:33:44+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2010/05/enable-http-authentication-on-dreamhost/
permalink: /enable-http-authentication-on-dreamhost/
categories:
  - General
---
<!-- google_ad_section_start -->

If you are using Dreamhost, or other similar shared server host, and are having problems with HTTP authentication then this is something to try. In my case I had a RAILS application where I was positive I was sending the appropriate HTTP Basic Authorization header (from PHP) like so:
  
```
$urlNew = curl_init();
...
curl_setopt($urlNew, CURLOPT_USERPWD, $strAuth);
curl_setopt($urlNew, CURLOPT_HTTPAUTH, CURLAUTH_BASIC);
...
``` 
  
However the server would repeatedly reply with Not Authorized (401 error). It turned out that the Authorization header was not being passed from Apache to the FastCGI application. So where I had this rewrite rule in /public/.htaccess:
  
```
RewriteRule ^(.*)$ dispatch.fcgi [QSA,L]
```
  
I just changed it to this:
  
```
RewriteRule ^(.*)$ dispatch.fcgi [E=X-HTTP_AUTHORIZATION:%{HTTP:Authorization},QSA,L]
```
  
And all was well.

<!-- google_ad_section_end -->
