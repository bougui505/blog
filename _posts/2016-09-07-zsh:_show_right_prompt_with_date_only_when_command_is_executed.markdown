---
title: "zsh: show right prompt with date ONLY when command is executed"
layout: default
date: 2016-09-07
tags:
- zsh
---

# zsh: show right prompt with date ONLY when command is executed


    # show right prompt with date in red ONLY when command is executed
    preexec () {
        RED='\033[0;31m'
        NC='\033[0m' # No Color
        DATE=$( date +"[%H:%M:%S]" )
        local len_right=$( strlen "$DATE" )
        len_right=$(( $len_right+1 ))
        local right_start=$(($COLUMNS - $len_right))
        local len_cmd=$( strlen "$@" )
        local len_prompt=$(strlen "$PROMPT" )
        local len_left=$(($len_cmd+$len_prompt))
        RDATE="\033[${right_start}C ${DATE}"
        if [ $len_left -lt $right_start ]; then
            # command does not overwrite right prompt
            # ok to move up one line
            echo -e "${RED}\033[1A${RDATE}${NC}"
        else
            echo -e "${RED}${RDATE}${NC}"
        fi
    }
    # else show right prompt with current date in green
    RPROMPT='%{$fg[green]%}[%D{%H:%M:%S}]'

NB: From the [zsh documentation on hook functions](http://zsh.sourceforge.net/Doc/Release/Functions.html#Hook-Functions):

`preexec`

Executed just after a command has been read and is about to be executed. If the
history mechanism is active (regardless of whether the line was discarded from
the history buffer), the string that the user typed is passed as the first
argument, otherwise it is an empty string. The actual command that will be
executed (including expanded aliases) is passed in two different forms: the
second argument is a single-line, size-limited version of the command (with
things like function bodies elided); the third argument contains the full text
that is being executed.
