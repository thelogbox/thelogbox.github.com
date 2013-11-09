---
layout: linux

title: Connect to Ubuntu Remote Desktop (Windows)

description: How to remote control a Linux machine using Windows RDP

excerpt: 

tags:
- RDP

categories:
- Linux

---

1. Get the *tsclient*. <code class="codeblock">$ sudo apt-get install xnest</code>
2. Enable xdmcp. Edit */etc/gdm/gdm.conf* -- *$ sudo nano /etc/gdm/gdm,conf*
3. Uncomment *RemoteGreeter* in the daemon section -- delete the pound or sharp sign on the RemoteGreeter
4. Find the *xdmcp section*. Under the xdmcp section, change the value of *Enable* key, set it to *true*
5. Log out of Ubuntu in order to restart the *gdm*. If you don't want to logout, from the Terminal. <code class="codeblock">$ sudo /etc/init.d/gdm restart</code>

You can now connect from your Windows machine to an Ubuntu machine using Remote Desktop Protocol

