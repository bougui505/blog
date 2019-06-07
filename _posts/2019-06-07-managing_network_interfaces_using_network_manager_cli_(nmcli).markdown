---
title: "Managing network interfaces using network manager CLI (nmcli)"
layout: default
date: 2019-06-07
tags:
- nmcli
- linux
- gnome
---

# Managing network interfaces using network manager CLI (nmcli)

## List available connections

    nmcli connection show

## Connect to a network

    nmcli c up uuid UUID

Where UUID is given by the command `nmcli connection show`
