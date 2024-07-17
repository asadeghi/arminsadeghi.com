---
title: Manual vs automatic memory management
description: Differences between manual and automatic memory management
date: 2006-12-16
guid: http://www.arminsadeghi.com/2006/12/manual-vs-automatic-memory-management/
permalink: "/blog/manual-vs-automatic-memory-management"
tags:
    - general
---

Good memory management is essential for writing software applications that perform well. If the application takes too long to start or frustrates you as it completes operations, it doesn't make for a good experience. And there are many factors such as response time, working set, and hardware requirements to consider when dealing with performance. However memory management is a key ingredient, and deciding between manual and automatic systems can make a big difference.

This is such a large topic. Where should I start? ...

Lets start with some definitions. [Manual memory management](http://en.wikipedia.org/wiki/Manual_memory_management) is when the programmer manually controls the lifetime of allocated memory by specifically allocating and freeing it in a deterministic fashion. Alternatively, automatic memory management tries to determine what memory is no longer used and frees it automatically instead of relying on the programmer to identify it. Automatic memory management is sometimes referred to as [Garbage Collection](http://en.wikipedia.org/wiki/Garbage_collection_%28computer_science%29) (GC), however "garbage" could be defined as anything, so the term is a little vague. GC often refers to tracing garbage collection, one form of automatic memory management. Reference counting is an alternative automatic memory management method (when you Release an object it isn't necessarily freed, it all depends on the reference count, so as a consumer you do not control memory deallocation). The choice here is mostly independent of programming language. There are some languages that support manual management (such as C, C++), others that support automatic management with tracing GCs (such as Java, and C#), and others still that support both (like [D](http://en.wikipedia.org/wiki/D_programming_language)).

So which one is better? Well the truth is that it all depends. There are many pros and cons to each method (discussed at length on [wikipedia](http://en.wikipedia.org/wiki/Memory_management)). In the end you have to pick the solution based on your specific requirements. However today lets talk about performance in particular. If you have some crazy high performance requirements (perhaps a real-time application), what do you do? ... you get more control.

By using manual memory management you are gaining more control over when memory is allocated and deallocated, giving you, the developer, more control over how to deal with it. You can then be mindful of such things as memory locality, consumption in tight loops, and memory reuse, while avoiding indeterministic deallocation (tracing garbage collectors). You can still have enough control with automatic memory management if you stick with ref counting as a means to control memory/object lifetime. However there is a cost to be paid for these advantages, mostly in development difficulty - the more control you have, the more likely you are to make mistakes (mistakes here lead to memory leaks). And mistakes are bugs.. some bad, some really bad.
