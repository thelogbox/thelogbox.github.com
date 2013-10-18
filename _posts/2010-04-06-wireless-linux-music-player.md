---
layout: post

title: Wireless Linux Music Player

description: 

excerpt: 

categories:
- blog

---

# WHY

1. I didn't want to throw away my old notebook computer, so I looked for something it can still be useful for
2. I have wanted (sometime in the past) to play audio files and get the sound coming out of a proper stereo receiver and some decent speakers. Hooking up an iPod to the stereo receiver should do it, but I really wanted to do it using the notebook
3. I want to control the playlist from any computer. The Airport express from Apple should actually be able to do this, but what was I going to do with the old notebook? Besides, this solution has some advantage over the Airport Express option because the audio data is flowing directly from the notebook computer to the stereo receiver via a physical audio cable. In Airport Express, the audio data travels wirelessly. 


# WHO IS THIS FOR

This might suit you if you;

1. Have some extra time in your hands and;
2. Have an old notebook that you don't want to throw away and;
3. Are a bit handy on Linux and have some experience working on the Terminal

# WHAT IS NEEDED

1. An old notebook with wifi capability
2. Stereo receivers
3. Audio cable with a 3.5mm jack on one end and RCA jacks on the other (depending on the connections of your stereo receiver)

# HOW TO DO IT

1. Get the **MPD** (Music Player Daemon) -- *$ sudo apt-get install mpd mpc*
2. Edit the configuration file -- *$ sudo nano /etc/mpd.conf*.
3. Find the entry on the conf file where you are supposed to point to where you music files are
4. Press *CTRL-o* then *CTRL-x* when you are done making the changes (that is how to save files in nano
5. Restart the Music Player Daemon -- *$ sudo /etc/init.d/mpd restart*
6. Create the database for the first time to add all songs to the playlist -- *$ sudo mpd --create-db* then *$ sudo mpd add l*
7. Install MPD clients on your other computers. At the time I wrote this, I used **ncmpc**. Lots of things has changed since then, Wikia.com has a list of [MPD clients](http://mpd.wikia.com./wiki/Clients)

