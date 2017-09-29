---
title: "Automatically change the tmux pane color for SSH session"
layout: default
date: 2017-09-29
tags:
- tmux
- ssh
---

# Automatically change the tmux pane color for SSH session

Add this line to your `.zshrc` (should also work with bash -- `.bashrc`)

    function color_ssh() {
        trap "tmux select-pane -P 'bg=default'" 0 1 2 3 4 5 6
        tmux select-pane -P 'bg=colour230'
        ssh $@
    }
    alias ssh=color_ssh
