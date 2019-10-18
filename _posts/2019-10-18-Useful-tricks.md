---
layout: post
date: 2019-10-18
title: Useful tricks!
excerpt_separator: <!--more-->
---
                                                                                                              
Greetings!
<!--more-->

This article will be more of a note or cheatsheet; both for me and for anyone coming here to learn something. I will keep updating here whenever I came across a useful trick or tip to use in my daily work as a developer.

Let’s get started!

COMMAND LINE TRICKS:
---

**Use case** : If you started your application and received a *"port already in use"* error, or you just forgot which port you were using and don't want to go through config files:

```
sudo lsof -i -P -n | grep LISTEN
```

will list each port currently in use and the application listening to it.


More tricks will be coming, Stay tuned...

Thank you!
