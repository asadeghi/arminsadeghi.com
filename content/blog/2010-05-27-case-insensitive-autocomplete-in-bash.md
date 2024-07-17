---
title: Case-insensitive Autocomplete in Bash
description: How to setup case-insensitive autocomplete in Bash
date: 2010-05-27
permalink: "/blog/case-insensitive-autocomplete-in-bash"
tags:
    - bash
---

I use auto complete on the command line all the time to avoid having to type the full name of a file. Love it. What I hate is how it&#8217;s case-sensitive in bash, so I can&#8217;t do `cd ~/desk` to go to the `~/Desktop` folder.

The fix for this is to use the shell input options file **.inputrc**

Just set this one option and restart your shell:

```bash
echo 'set completion-ignore-case On' >> ~/.inputrc
```

If you happen to have a system wide inputrc settings (`/etc/inputrc`) and want it included then you should add the following to your .inputrc file:

```
$include /etc/inputrc
```
