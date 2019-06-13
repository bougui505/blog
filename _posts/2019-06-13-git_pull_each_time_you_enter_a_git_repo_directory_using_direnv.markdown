---
title: "git pull each time you enter a git repo directory using direnv"
layout: default
date: 2019-06-13
tags:
- direnv
- git
---

# git pull each time you enter a git repo directory using direnv

Just add the following line in the directory .envrc file:

    (date && git pull) >> pull.log

The date and the pull stdout will be logged in `pull.log` file.
