---
title: "Encode DVD into a mkv file with different subtitles and languages"
layout: default
category: linux
date: 2014-11-20 22:03:42 CET
tags:
- linux
---

# Encode DVD into a mkv file with different subtitles and languages

First you have to find the chapter you want to encode and the ids for the subtitles and audio.
You can use the tool `lsdvd` for this:

{% highlight bash %}
$ lsdvd -as
Disc Title: FANTASTIC
Title: 01, Length: 01:23:17.050 Chapters: 25, Cells: 89, Audio streams: 03, Subpictures: 06
    Audio: 1, Language: en - English, Format: ac3, Frequency: 48000, Quantization: drc, Channels: 6, AP: 0, Content: Undefined, Stream id: 0x80
    Audio: 2, Language: fr - Francais, Format: ac3, Frequency: 48000, Quantization: drc, Channels: 6, AP: 0, Content: Undefined, Stream id: 0x81
    Audio: 3, Language: pt - Portugues, Format: ac3, Frequency: 48000, Quantization: drc, Channels: 6, AP: 0, Content: Undefined, Stream id: 0x82
    Subtitle: 01, Language: en - English, Content: Undefined, Stream id: 0x20, 
    Subtitle: 02, Language: fr - Francais, Content: Undefined, Stream id: 0x21, 
    Subtitle: 03, Language: nl - Nederlands, Content: Undefined, Stream id: 0x22, 
    Subtitle: 04, Language: pt - Portugues, Content: Undefined, Stream id: 0x23, 
    Subtitle: 05, Language: fr - Francais, Content: Undefined, Stream id: 0x24, 
    Subtitle: 06, Language: pt - Portugues, Content: Undefined, Stream id: 0x25, 

Title: 02, Length: 00:07:47.090 Chapters: 02, Cells: 03, Audio streams: 01, Subpictures: 02
        
        [...]

Longest track: 01
{% endhighlight %}

The longest track is the track one with English, Francais and Portugues languages and various subtitles.

First we'll define a variable with the movie title and create a directory:

{% highlight bash %}
mtitle="the_movie_title"
mkdir $mtitle
{% endhighlight %}

Now we encode the audio tracks, here English and French:

{% highlight bash %}
# English
mencoder dvd://1 -dvd-device /dev/dvd  -aid 128 -of rawaudio -oac mp3lame -ovc copy -o $mtitle/english.mp3
# French
mencoder dvd://1 -dvd-device /dev/dvd  -aid 129 -of rawaudio -oac mp3lame -ovc copy -o $mtitle/french.mp3
{% endhighlight %}

The audio id (`aid`) 128 and 129 are given by the Stream id 0x80 and 0x81 (hexadecimal notations $$8\times16$$ and $$8\times16+1$$)

The same for the subtitles:

{% highlight bash %}
# English subtitles
mencoder dvd://1 -dvd-device /dev/dvd -sid 1 -vobsubout $mtitle/subtitles_english -nosound -ovc frameno -o /dev/null
# French subtitles
mencoder dvd://1 -dvd-device /dev/dvd -sid 2 -vobsubout $mtitle/subtitles_french -nosound -ovc frameno -o /dev/null
{% endhighlight %}

And now the video without sound and subtitles (we put -sid 1000 to be sure to not have subtitles. Some DVD put subtitles as default.):

{% highlight bash %}
mencoder dvd://1 -dvd-device /dev/dvd  -sid 1000 -ovc x264 -nosound -o "$mtitle/video.avi"
{% endhighlight %}

Now we can merge all the files in the mkv file:

{% highlight bash %}
cd $mtitle
mkvmerge -o $mtitle.mkv video.avi english.mp3 french.mp3 subtitles_english.idx subtitles_french.idx
{% endhighlight %}

The full script below:

{% highlight bash %}
#!/usr/bin/env sh
mtitle="the_movie_title"
mkdir $mtitle
track=1 # track to encode
aid1=128 # first audio track
aid2=129 # second audio track
sid1=1 # first subtitles track
sid2=2 # second subtitles track
# first audio track
mencoder dvd://$track -dvd-device /dev/dvd -aid $aid1 -of rawaudio -oac mp3lame -ovc copy -o $mtitle/audio1.mp3
# second audio track
mencoder dvd://$track -dvd-device /dev/dvd -aid $aid2 -of rawaudio -oac mp3lame -ovc copy -o $mtitle/audio2.mp3
# first subtitles track
mencoder dvd://$track -dvd-device /dev/dvd -sid $sid1 -vobsubout $mtitle/subtitles1 -nosound -ovc frameno -o /dev/null
# second subtitles track
mencoder dvd://$track -dvd-device /dev/dvd -sid $sid2 -vobsubout $mtitle/subtitles2 -nosound -ovc frameno -o /dev/null
# Video without sound and subtitle
mencoder dvd://$track -dvd-device /dev/dvd -sid 1000 -ovc x264 -nosound -o "$mtitle/video.avi"
# The merging:
cd $mtitle
mkvmerge -o $mtitle.mkv video.avi audio*.mp3 subtitles*.idx
mv $mtitle.mkv ../.
# Eject the DVD:
eject /dev/dvd 2> /dev/null
{% endhighlight %}

To encode audio and video simultaneously:

{% highlight bash %}
#!/usr/bin/env sh
mtitle="the_movie_title"
track=1
aid1=128
sid1=1 # 1000 for no subtitles
mencoder dvd://$track -dvd-device /dev/dvd -sid $sid1 -aid $aid1 -oac mp3lame -ovc x264 -o "$mtitle.avi"
# Eject the DVD:
eject /dev/dvd 2> /dev/null
{% endhighlight %}
