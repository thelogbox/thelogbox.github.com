---
layout: linux

title: Wireless Linux Music Player

description: Music Player Daemon in Linux. Don't throw away that old notebook

excerpt: 

tags:
- hack
- mpd

---

This project will let you control a music player daemon running on a Linux box. The Linux box (headphone jack) will be connected into a stereo receiver (input) &mdash; It's an over engineered music player. But if you don't have anything better to do with an old notebook, this might save it from the junk yard.

For this project, I used 1) an old notebook with WiFi still working 2) an old stereo receiver with 3.5mm stereo jack input 

## Installation and Configuration

1. Get the **MPD** (Music Player Daemon) -- *$ sudo apt-get install mpd mpc*
2. Edit the configuration file -- *$ sudo nano /etc/mpd.conf*.
3. Find the entry on the conf file where you are supposed to point to where you music files are
4. Press *CTRL-o* then *CTRL-x* when you are done making the changes (that is how to save files in nano
5. Restart the Music Player Daemon -- *$ sudo /etc/init.d/mpd restart*
6. Create the database for the first time to add all songs to the playlist -- *$ sudo mpd --create-db* then *$ sudo mpd add l*
7. Install MPD clients on your other computers. At the time I wrote this, I used **ncmpc**. Lots of things has changed since then, Wikia.com has a list of [MPD clients](http://mpd.wikia.com./wiki/Clients)

