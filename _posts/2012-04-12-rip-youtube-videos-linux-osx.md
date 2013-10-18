---
layout: post

title: Rip YouTube Video via cmd (Linux and OSX)

description: 

excerpt: 

categories:
- blog

---


1. To save youtube videos locally in the hard drive
2. To rip the audio portion of the youtube videos
3. To do No. 1 and No. 2 without using browser plugins
4. To dno No. 1 and No. 2 using command line utilities


# WHAT YOU NEED


1. [youtube-dl](http://rg3.github.com/youtube-dl/) - This pull the youtube content, ala curl or wget
2. [ffmpeg](http://ffmpeg.org) and [lame](http://lame.sourceforge.net) - These two you will need to transform the downloaded content because youtube-dl will pull a .webm file, if you have capability to play a .webm file, you may not need to transform them. In Lubuntu, the .webm is supported

This method used the Debian apt-get installer, it will be different for other Linux distros


**FOR LINUX**, get the *youtube-dl* from the repositories &mdash; <code class="codeblock">$ sudo apt-get install ffmpeg lame youtube-dl</code>

**FOR OSX**, You can choose to use either HomeBrew or MacPorts. I used BREW

<pre class='codeblock'>
  
$ sudo brew install youtube-dl
$ sudo brew install ffmpeg
$ sudo brew install lame


</pre>

# HOW TO RIP

1. Find the url of the youtube video you want to rip
2. use youtube-dl to rip the content -- *$ youtube-dl {http://YoutubeVideo Address}*
3. The downloaded file is a .webm file, transform it to wav &mdash; <code class="codeblock">*$ ffmpeg -i {DownloadedFileName.webm} {TargetFileName.wav}*</code>
4. If .wav is okay for you, you can stop now. If you want to transform further to MP3 format use the lame utility -- *$ lame {FileName.wav} {FileName.mp3}*



