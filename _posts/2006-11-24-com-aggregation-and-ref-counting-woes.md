---
id: 33
title: COM aggregation and ref counting woes
date: 2006-11-24T01:28:04+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2006/11/com-aggregation-and-ref-counting-woes/
permalink: /com-aggregation-and-ref-counting-woes/
categories:
  - General
---
<!-- google_ad_section_start -->

Why are we talking about [Component Object Model](http://en.wikipedia.org/wiki/Component_Object_Model) (COM), isn't that old dead technology? Well&#8230; no. There are still so many COM objects in use today, in many projects, that you will run into them sooner or later. As a software engineer you might even have to resolve bugs in these components. Today I want to draw attention to ref counting bugs that can creep in when using aggregation within these objects. 

<!--more-->

COM objects use reference counting to control their lifetime. This is achieved through the implementation of an _IUnknown_ interface by each and every object. This interface contains (quick &#8211; what are the first three v-table entries?) _IUnknown::QueryInterface_, _IUnknown::AddRef_ and _IUnknown::Release_. So after you add a reference to an object with _AddRef_, you are expected to call _Release_ when you are finished. Reference counting bugs can crop up in object clients when someone forgets this rule and are usually a real pain to find. This difficulty can be compounded even further if the object itself messes up its implementation of _AddRef_. 

The implementation of _AddRef_ is typically simple (just increment an internal counter), however when the object aggregates other objects in its internal implementation (another form of object reuse as opposed to using containment) it becomes more complex. In these cases you have to ensure that AddRef and Release calls operate on the correct object. 

Lets take the example of a hypothetical AIRPLANE object. An AIRPLANE is implemented by aggregating WING, and ENGINE objects. WING implements _IWing_ and _IUnknown_, ENGINE implements _IEngine_ and _IUnknown._ Now clients of the AIRPLANE object would expect that _IWing::AddRef_, and _IEngine::AddRef_ both control the lifetime of the outer object (the component/object doing the reusing &#8211; in this case AIRPLANE). This is fair and reasonable, however the only way this can happen is if the inner objects (WING and ENGINE) are aware of the outer object. So when WING and ENGINE are created, AIRPLANE passes a pointer to its _IUnknown_ implementation (called the controlling unknown) down to the inner objects. If they support aggregation then they will use this pointer to handle any _IUnknown_ calls that come in through _IWing_ and _IEngine_. If they do not support aggregation they will return CLASS\_E\_NOAGGREGATION and fail creation. However ENGINE and WING must not delegate to the controlling unknown for any _AddRef_ and _Release_ calls that come in through _IUnknown_ itself, as this is what the outer object will use to control their lifetime. 

These are just the basic rules of aggregation that when applied ensure that object lifetime is still managed correctly. Common problems arise when the inner objects forget to delegate the _AddRef_ and _Release_ calls to the controlling unknown, or do so in the wrong case (i.e. when called through _IUnknown::AddRef_). In this case the client of AIRPLANE may see what appears to be a ref counting bug on their side, but is actually an internal issue with the aggregation. 

&#8230; no wonder people like managed code and .NET. Ref counting bugs can get tricky. 

&nbsp; 

<!-- google_ad_section_end -->
