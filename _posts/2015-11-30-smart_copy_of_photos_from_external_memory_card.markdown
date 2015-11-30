---
title: "Smart copy of photos from external memory card"
layout: default
date: 2015-11-30
tags:
- photos
- linux
- shell
- zsh
---

# Smart copy of photos from external memory card

This script makes a directory hierarchy by date (`YYYY/MM/DD`) and do not
transfer photos already transfered.

## Dependencies:

- [pv](http://www.ivarch.com/programs/pv.shtml) (to install it: `sudo apt-get install pv`) (see this [blog post]({% post_url 2015-10-29-get_a_progress_bar_for_a_process_in_shell_with_pv_--_pipe_viewer_-- %}))
- zsh (but should be OK for other shells)

## Usage:

    ./get_photos.sh /path/to/the/mounted/memory/card

Don't forget to change the destination directory in the script...

{% gist 0aade36ec855acd8702a %}
