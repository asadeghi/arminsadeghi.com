---
id: 29
title: The D programming language
date: 2007-02-06T17:07:09+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2007/02/the-d-programming-language/
permalink: /the-d-programming-language/
categories:
  - General
---
<!-- google_ad_section_start -->

Is there really another single letter programming language? Yes, its called D . The D programming language comes from Walter Bright and Digital Mars. Its been around for a while, but with the recent v1.0 release its probably a good time to take a look.

<!--more-->

D is a systems programming language focused on taking the performance and power elements from C/C++ and combining them with the productivity of languages such as Ruby and Python. D compiles directly to native code and looks very much like C/C++. There is a good comparison of the language here.

If you want to get started, the first thing is to download the compiler. Then write a little sample code:
  
```
int main(char[][] args)
{
  printf("hello world\n");
  printf("args.length = %d\n", args.length);
  for (int i = 0; i < args.length; i++)
    printf("args[%d] = &#39;%s&#39;\n", i, cast(char *)args[i]);
  return 0;
}
```
  
Looks very similar to C on first inspection, with a few twists. In addition D provides for a garbage collector, contract programming, resizeable arrays, built-in strings, an inline assembler, and much more.

The built in strings are particularly useful. D introduces a new binary operator '~' for concatenation.
  
```
const char[5] abc = "world";
char[] str = "hello" ~ abc;
```
  
With contract programming D gives you not only asserts, but also pre and post contracts to validate function behaviour:
  
```
in
{
  ...contract preconditions...
}
out(result)
{
  ...contract postconditions...
}
body
{
  ...code...
}
```
  
So contract programming, built-in strings, resizable arrays&#8230; these things are not terribly new. They can often be implemented with some discipled programming and perhaps some extra C++ modules. So does D bring something serious to the playing table? I vote yes. Just as C# and the .Net framework enable developers to code at a higher level and be more productive (in certain applications of course), D could provide similar benefits to the lower level systems programming area where C/C++ still dominate.

<!-- google_ad_section_end -->
