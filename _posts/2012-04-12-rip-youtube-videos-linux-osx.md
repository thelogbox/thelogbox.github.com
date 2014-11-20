---
layout: linux

title: How to rip YouTube videos

description: Download YouTube videos like a geek

excerpt: 
- YouTube
- Linux
- Ripping

---

You can rip YouTube videos from the command line in Linux and OSX. There could be ways to do this in Windows via Cygwin, but I did not try that. 

In Debian Linux, or any other distribution that uses the **apt** or **aptitude** package manager, you can get the **youtube-dl** program by pulling them from the repositories. Run the following command on a terminal window

~~~~
sudo apt-get install ffmpeg lame youtube-dl
~~~~

For OSX users, if you are using **HomeBrew**, you can get youtube-dl by running the commands

~~~~
brew install youtube-dl
brew install ffmpeg
brew install lame
~~~~

**Usage**

~~~~
youtube-dl http://<youtubevideoaddress>
~~~~

The downloaded file could be have **.webm** extension, you can convert it to **wav** using the command

~~~~
ffmpeg -i <DownloadedFileName.webm> <TargetFileName.wav>
~~~~

You can convert the resulting wav file to mp3 format with the following command

~~~
lame <FileName.wav> <FileName.mp3>
~~~





