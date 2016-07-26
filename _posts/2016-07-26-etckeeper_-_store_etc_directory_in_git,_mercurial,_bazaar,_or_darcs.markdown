---
title: "etckeeper - store etc directory in git, mercurial, bazaar, or darcs"
layout: default
date: 2016-07-26
tags:
- git
- linux
---

# etckeeper - store etc directory in git, mercurial, bazaar, or darcs

A very useful tool to backup locally `/etc`.

Below the man page:

    ETCKEEPER(8)                                                      ETCKEEPER(8)



    NAME
           etckeeper - store /etc in git, mercurial, bazaar, or darcs

    SYNOPSIS
           etckeeper command [-d directory]

    DESCRIPTION
           etckeeper  manages /etc be stored in a git, mercurial, bazaar, or darcs
           repository. By default each of the commands operates  on  /etc,  but  a
           different  directory can be specified to operate on a clone of the /etc
           repository located elsewhere.

    COMMANDS
           init   This initialises and sets up a git, mercurial, bazaar, or  darcs
                  repository (depending on the VCS setting in /etc/etckeeper/etck‐
                  eeper.conf). Typically this is run in /etc once when starting to
                  use  etckeeper on a machine. It can also be used to initialise a
                  clone of the /etc repository located elsewhere.

           commit [message]
                  Commits all changes in /etc to the repository. A commit  message
                  can  be specified. You may also use the underlying VCS to commit
                  manually.  (Note that etckeeper commit will notice if a user has
                  used sudo or su to become root, and record the original username
                  in the commit.)

           pre-commit
                  This is called as a pre-commit hook. It stores metadata and does
                  sanity checks.

           pre-install
                  This  is  called  by  apt's  DPkg::Pre-Install-Pkgs  hook, or by
                  equivalent hooks of other package managers. It allows committing
                  any uncommitted changes before packages are installed, upgraded,
                  etc.

           post-install
                  This is called by apt's DPkg::Post-Invoke hook, or by equivalent
                  hooks  of  other  package  managers.  It commits changes made by
                  packages into the repository. (You can also call  this  by  hand
                  after running dpkg by hand.)

           unclean
                  This returns true if the directory contains uncommitted changes.

           update-ignore [-a]
                  This  updates the VCS ignore file. Content outside a "managed by
                  etckeeper" block is not touched.  This  is  generally  run  when
                  upgrading to a new version of etckeeper. (The -a switch will add
                  a "managed by etckeeper" block if one is not present.)

           vcs subcommand [options ...]
                  You can use this to run any subcommand of the VCS that etckeeper
                  is configured to run. It will be run in /etc. For example, "etc‐
                  keeper vcs diff" will run "git diff", etc.

           uninit [-f]
                  This command DESTROYS DATA! It is the inverse of the  init  com‐
                  mand,  removing  VCS information and etckeeper's own bookkeeping
                  information from the directory. Use with caution. A typical  use
                  case  would  be  to  run  etckeeper  uninit,  then  modify etck‐
                  eeper.conf to use a different VCS, and then run etckeeper  init.
                  (The -f switch can be used to force uninit without prompting.)

    FILES
           /etc/etckeeper/etckeeper.conf is the configuration file.

           /etc/etckeeper  also  contains directories containing the programs that
           are run for each of the above commands.

    ENVIRONMENT VARIABLES
           ETCKEEPER_CONF_DIR path to configuration directory instead  of  default
           /etc/etckeeper.

    SEE ALSO
           /usr/share/doc/etckeeper/README.md.gz

    AUTHOR
           Joey Hess <joey@kitenet.net>



                                                                      ETCKEEPER(8)

