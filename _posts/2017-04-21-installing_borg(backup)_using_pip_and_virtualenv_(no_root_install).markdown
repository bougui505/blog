---
title: "Installing Borg(backup) using pip and virtualenv (no root install)"
layout: default
date: 2017-04-21
tags:
- python
- virtualenv
---

# Installing Borg(backup) using pip and virtualenv (no root install)

    virtualenv --python=python3 borg-env
    source borg-env/bin/activate
    # install Borg + Python dependencies into virtualenv
    pip install borgbackup
