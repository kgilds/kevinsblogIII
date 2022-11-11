---
title: Where are my keys
author: Kevin
date: '2021-07-23'
slug: []
categories:
  - R
tags:
  - git
---

Today, I had to relearn how to reset a git remote.

1.  [Happy Git with R](https://happygitwithr.com/ssh-keys.html#ssh-keys).
2.  [Great Link](https://docs.github.com/en/get-started/getting-started-with-git/managing-remote-repositories)

The problem:

Github was asking me a password when I have keys set up.

Step 1:

In the terminal

    git remote -v 

Okay the terminal is telling me that the remote is set to https:

    https://github.com/USERNAME/REPOSITORY.git

### The fix

    git remote set-url origin git@github.com:USERNAME/REPOSITORY.git

### Finish

My issue is that I was forgetting to include the origin.
