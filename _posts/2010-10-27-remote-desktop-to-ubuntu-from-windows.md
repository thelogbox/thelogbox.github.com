---
layout: post

title: Connect to Ubuntu Remote Desktop (Windows)

description: 

excerpt: 

categories:
- blog

---


1. To connect to an Ubuntu machine and control its desktop
2. To do No. 1 from a Windows machine
3. To do No. 1 and not use VNC - for some reason, I just don't like VNC
4. Because logmein.com is not an option for Linux
5. To do No. 1 without installing FreeNX on Windows 7, or without some Cygwin acrobatics on Windows. 

# HOWTO

**Get tsclient** on Ubuntu &mdash; <code class="codeblock">$ sudo apt-get install xnest</code>

**Enable xdmcp**

1. Edit */etc/gdm/gdm.conf* -- *$ sudo nano /etc/gdm/gdm,conf*
2. Uncomment *RemoteGreeter* in the daemon section -- delete the pound or sharp sign on the RemoteGreeter
3. Find the **xdmcp section**Under the xdmcp section, change the value of **Enable** key to *true*
4. Log out of Ubuntu in order to restart the *gdm*. If you don't want to logout, from the Terminal -- *$ sudo /etc/init.d/gdm restart* 

You can now connect from your Windows machine to an Ubuntu machine using **RDP** or Renmote Desktop Protocol

