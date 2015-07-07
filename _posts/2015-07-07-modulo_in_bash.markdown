---
title: "Modulo in bash"
layout: default
category: linux
date: 2015-07-03
tags:
- linux
- bash
- shell
---

# Modulo in bash

The command below return the modulo 15 of variable `$i`:

    t=$(expr $i % 15)

For example:

    i=0
    for x in ????_protein.pdb; do
        my_command &
        ((i++))
        t=$(expr $i % 15 + 2)
        sleep $t
    done

allows to increment the sleep by `$i % 15 + 2` which can be convenient to wait for a long process in background and to avoid overloading of the machine.
