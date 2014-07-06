---
layout: linux

title: Rip YouTube Vids

description: Download YouTube videos like a geek

excerpt: 
- YouTube
- Linux
- Ripping

categories:
- OSX

---

**youtube-dl** is a command line tool to rip youtube videos. Works on OSX and Linux. There could be a way to make this work on Windows but I did not try that.

In Linux you can pretty much just get it from the repositories.

`sudo apt-get install ffmpeg lame youtube-dl`

In OSX you can get it either via brew, macports or fink. I used brew.

`brew install youtube-dl`

`brew install ffmpeg`

`brew install lame`


# Usage

1. Find the url of the youtube video you want to rip
2. use youtube-dl to rip the content -- `youtube-dl http://YoutubeVideo Address`
3. The downloaded file is a .webm file, transform it to wav &mdash; `ffmpeg -i <DownloadedFileName.webm> <TargetFileName.wav>`
4. If .wav is okay for you, you can stop now. If you want to transform further to MP3 format use the lame utility -- `lame <FileName.wav> <FileName.mp3>`



