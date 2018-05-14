---
id: 24
title: Ruby on Rails
date: 2008-01-26T22:59:41+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2008/01/ruby-on-rails/
permalink: /ruby-on-rails/
categories:
  - General
---
<!-- google_ad_section_start -->

So have you played with Ruby or Rails yet? No? Well you might want to give it check it out. The Ruby language is very interesting and Rails, which is built with Ruby, is a very powerful web application development framework. 

<!--more-->

To get you started take a look at these sites:
  
<http://www.rubyonrails.org/> &#8211; All about rails.
  
<http://www.ruby-lang.org/en/> &#8211; All about ruby. 

Then you should check out the fifteen minute hands-on tutorial [here](http://tryruby.hobix.com/). This is a great overview of the language and will get you started. If you are interested and want to get an environment set up, there are instructions on rubyonrails.org for various platforms. The only additional tool I would recommend is [RadRails](http://www.aptana.com/rails/) from Aptana, especially if you are already familiar with Eclipse. 

Ruby is a dynamic, duck-typed, programming language. Firstly take a look at this: 

```
class Dummy
end

dummyA = Dummy.new
Dummy.send(:define_method, :hi) do
  print "Hello world!\n"
end

dummyA.hi
```
  
**<font face="times new roman,times">~/ruby$ ruby dynamic.rb<br /> Hello world!</font>** 

Here we have dynamically defined a method on **Deal** called **hi**. Pretty straight forward. Now combine this with method_missing, which is called when&#8230; you guessed it.. you call a method on a class that doesn't exist. 

```
class Dummy
  def method_missing(m, *args)
    puts("There&#39;s no method called #{m} here please try again.")
  end
end
```

So now we have a way of creating new methods dynamically, and also knowing what the user tried to call and being able to intercept those calls. So when the user does something like this: 

`User.find_by_name_and_email(&#39;someone&#39;, &#39;someone@test.com&#39;)`

You can generate the **find\_by\_name\_and\_email** method to go look up the database, find a user table, look to see if it has columns called name and email, and then do a query. This ability gives Rails incredible power to make life easier for the developer as I am sure you can appreciate. 

<!-- google_ad_section_end -->
