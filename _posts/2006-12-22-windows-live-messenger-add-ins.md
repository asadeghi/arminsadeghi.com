---
id: 31
title: Windows Live Messenger Add-Ins
date: 2006-12-22T19:45:32+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2006/12/windows-live-messenger-add-ins/
permalink: /windows-live-messenger-add-ins/
categories:
  - General
---
<!-- google_ad_section_start -->

When software applications do what they are advertised to do users are happy (generally), but what if you want to do more? Thats where you generally start looking for some method to extend the application. Not every application will allow this, but Windows Live Messenger (WLM) is one that does (at least currently with version 8.0). How, you ask? By writing your very own Add-In with the Messenger Add-In API &#8230;

<!--more-->

WLM only offers this one API (Application Programming Interface), so it&#8217;s not like Microsoft Excel where you have a vast array to pick from (i.e. .NET APIs, C APIs, COM Automation, VBA and XLM). You do get to pick a language that supports .NET and then proceed with the following:

  1. Download and install the .Net 2.0 SDK . This is a minimum requirement. You can also use Visual Studio .NET 2005, or Visual Studio Express (which is a free download), both of which come with the .NET 2.0 SDK.
  2. Write your Add-In. Compile and get the DLL. Full instructions, along with the special reg-key to set, and what to call your DLL to make things work are on MSDN .
  3. Add the Add-In to Windows Live Messenger.

The code is simple enough. Below is an example of an Add-In that updates your personal status message every few seconds to show how long you have been online.

<pre>using System;
using System.Timers;
using Microsoft.Messenger;
namespace WLM
{
  public class CounterAddIn : IMessengerAddIn
  {
    static MessengerClient m_client;
    static int m_cSeconds;
    Timer m_timer;

    void IMessengerAddIn.Initialize(MessengerClient client)
    {
      m_client = client;
      m_client.AddInProperties.FriendlyName = "CounterAddIn";
      m_cSeconds = 0;
      m_timer = new Timer(3000);
      m_timer.Elapsed += new ElapsedEventHandler(OnTimedEvent);
      m_timer.Enabled = true;
    }

  private static void OnTimedEvent(object source, ElapsedEventArgs e)
  {
    m_cSeconds += 3;
    m_client.AddInProperties.PersonalStatusMessage = "Online for " + m_cSeconds.ToString() + " seconds.";
    }
  }
}</pre>

You can also do things such as change your personal image, status, or even respond to users messages (although users always know that the Add-in is running) with automated replies.

<span style="line-height: 1.714285714; font-size: 1rem;">One important step is setting the magic registry key such that Messenger lets you add your own custom Add-In. When the key is set correctly Messenger provides controls on its Options page for Add-In support.</span>

Key: **HKEY\_CURRENT\_USER\Software\Microsoft\MSNMessenger\AddInFeatureEnabled**

Value: DWORD set to &#8220;1&#8221; to enable, and &#8220;0&#8221; to disable Add-Ins.

<!-- google_ad_section_end -->
