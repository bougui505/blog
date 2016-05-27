---
title: "Configure ssmtp to use the mail Linux command line to send email with gmail"
layout: default
date: 2016-05-27
tags:
- linux
- gmail
- ssmtp
---

# Configure ssmtp to use the mail Linux command line to send email with gmail

First of all, install the `ssmtp` package:

    bougui@aldebaran ~> sudo apt-get install ssmtp

Then edit the file `/etc/ssmtp` and just pust that content to the file:

    #Debug=YES
    root=USER@gmail.com
    AuthUser=USER@gmail.com
    AuthPass=YOUR_GMAIL_PASSWORD
    FromLineOverride=YES
    mailhub=smtp.gmail.com:465
    UseTLS=YES

Then, a quick test:

    bougui@aldebaran ~> echo "This is a test" | mail -s "Test" USER@gmail.com

For sure, just replace `USER` by your Gmail username, in the configuration file
and in the test command line.
