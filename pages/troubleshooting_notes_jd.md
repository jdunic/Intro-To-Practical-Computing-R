---
layout: page
title: Troubleshooting - personal notes
description: Personal notes for troubleshooting in BIOL 653 - 2015
---

**Git was installed but is not found. Examples:**
1. ```git --version``` does not point at most recently installed version
    + e.g., pointing to the Apple default installed git
2. ```git``` error: 'command not found'  

To solve this you can add the following to your ~/.bash_profile

~~~
export PATH=/usr/local/git/bin:$PATH
~~~

Taken from [this StackOverflow answer](http://stackoverflow.com/questions/5545715/how-do-i-add-usr-local-git-bin-to-the-path-on-mac-osx)