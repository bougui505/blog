---
title: "Use ProxyCommand with ssh to connect to host1 through host2"
layout: default
date: 2015-12-15
tags:
- ssh
- ProxyCommand
---

# Use ProxyCommand with ssh to connect to host1 through host2

Sometime an host (e.g. `host1`) cannot be reached directly with ssh. However,
`host2` can be reached via ssh, and `host2` can connect to `host1` via ssh.

I define:

- `username1`: your username for `host1`

- `username2`: your username for `host2`

However, `username1` and `username2` can be identical.

You can transparently connect to `host1` through `host2` with ssh by setting up
a ProxyCommand in `.ssh/config` file:

    Host host1
        User username1
        ProxyCommand ssh username2@host2 exec nc host1 22
