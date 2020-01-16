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

COMMAND LINE TRICKS
---

**Use case** : If you started your application and received a *"port already in use"* error, or you just forgot which port you were using and don't want to go through config files:

```
sudo lsof -i -P -n | grep LISTEN
```

will list each port currently in use and the application listening to it.

USEFUL GITHUB COMMANDS
---

**Use case** : In your daily job as a developer you usually find yourself creating a new branch to add a feature or fix a bug. Once done, you push your changes and create a Pull Request to merge your branch into Master. (If you don't use this process... well you should!). After some back and forth, your PR will be merged and the remote branch will be deleted. but what about your local branch?

To clear things up, there are 3 type or branches we're talking about : 

* Local branch: which is the branch on you local machine.
* Remote branch: The branch on your Git Server.
* Remote tracking branch: a local copy of your local branch set to track the remote (synchronized with remote by `git fetch` or `git pull`)

You can list all local branches on your project with `git branch`. Adding `-r` will list all remote tracking branches and `-a` will list both. (if you couldn't exit the terminal use `:q` (vi again...))

To remove deleted remote branches from your remote tracking branch list. use the command `git fetch --all --prune`. finally you can delete the local branch with `git branch -d branch_name` (or with `-D` instead to force delete)

More tricks will be coming, Stay tuned...

Thank you!
