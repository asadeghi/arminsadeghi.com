---
id: 35
title: Windows PowerShell
date: 2006-11-02T19:36:38+00:00
author: armin
layout: post
guid: http://www.arminsadeghi.com/2006/11/windows-powershell/
permalink: /windows-powershell/
categories:
  - General
---

Power users love shells. Not the seafood kind, but the command line interface, computer command scripting kind. Even MacOS which was traditionally GUI driven, now has a shell (albeit somewhat hidden), due to its makeover in OS X. With a shell the user can input text commands to manipulate the computer. The most obvious use of which is the ability to script common operations, or perform functions faster than perhaps the user-interface driven counterpart operation.

MS Windows based operating systems have been using cmd.exe as their shell for quite some time, until PowerShell came along. [Windows PowerShell](http://www.microsoft.com/windowsserver2003/technologies/management/powershell/default.mspx) currently has an RC2 release available for [download](http://www.microsoft.com/technet/scriptcenter/topics/msh/download.mspx). Whats so special about Windows PowerShell?.. where do I start? 🙂

<!--more-->

The biggest change is in the object pipeline. No longer do commands output text, now its all objects. So when you do something like:

`Get-Process | Format-Wide`

The output of _Get-Process_ is piped, as objects, to the next command. In this case _Format-Wide_ takes the objects and formats them in a particular way. You could have used _Format-List_, or a multitude of other variations. Passing objects allows much richer communication between functions in the command pipeline as well as other shell operations. So you can imagine what something like this may do:

`Get-Process m* | dir`

Yes you guessed it, it actually lists the folder location of all currently running processes that start with the letter m.

Windows PowerShell also has a whole new syntax. Commands have verb-noun type names which provides for clear, consistent, and easily discoverable functionality (and if you are ever lost, just type "_help_", or append "_-?_" to a command). To help people transition from other shells there are aliased commands, so commands such as "cd", "dir", "more" are aliased to their corresponding commands and work just fine.

I could go on for pages and pages about all the cool new things, but lets just cover two more items, PowerShell drives, and COM object scripting (that I thought was very cool). Have you ever wanted to query the registry and manipulate it right from a script instead of messing with regedit and .reg files? Well try this out:

`cd HKLM:\Software`

and now you have navigated to HKEY_LOCAL_MACHINE\Software. Well what else can you do? Just try "_Get-PSDrive_" to see a list of all the other mapped PowerShell drives you can navigate.

So what if you have a COM Automation object that you want to work with? Lets say you need to boot Excel, do a few calculations and retrieve the result? Prior to Windows PowerShell this was not trivial but now all you need is a few lines similar to this:

```
$xl = New-Object -ComObject Excel.Application
$xl.Workbooks.Add()
$xl.Range("A1").Value2 = 5
$xl.Range("A2").Value2 = 6
$xl.Range("A3").Value2 = "=Sum(A1, A2)"
$output = $xl.Range("A3")
$xl.Quit()
```

It looks similar to C#, but being able to run this straight from a command line script is just great.

<!-- google_ad_section_end -->
