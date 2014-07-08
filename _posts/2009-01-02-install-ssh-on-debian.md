---
layout: linux

title: Install SSH

description: Get an SSH server running

excerpt: 

tags:
- Ubuntu
- SSH


---

To install SSH on Debian or its derivatives, get it from the repositories &mdash; <code class="codeblock">sudo apt-get install ssh</code>

If you prefer to do it in GUI mode and you are running a desktop program in Linux like Gnome, Unity, LXDE etc, you could do it using **synaptic**, search ssh and you should be on your way -- but then again, you are running a server, why would you have a GUI running in it? 

That's it, you don't even have to restart your server. While you are at it, why don't you install *sysv-rc-conf* as well. Why? so that you have an easy way to start, stop, and restart services on your server.

To install sysv-rc-conf, get it via aptitude &mdash; <code class="codeblock">$ sudo apt-get install sysv-rc-conf</code>

It's a good idea to test if you can really connect to your server via SSH, before you remove the monitor and keyboard. If you are using an OSX or a Linux or a UNIX workstation, you can simply type <code class="codeblock">$ ssh yourUserName@ServerNameOrIp</code>
    
Replace *yourUserName* with a user defined in your server and *ServerNameOrIp* with the hostname or IP address of your  server. If this the first time you will connect to the server, it will ask you a question whether you'd like to store an on entry on your */homefolder/.ssh/known_hosts*. Say "yes" to this question.

If you are using Windows XP or Vista, you can download Putty. Putty is a windows client software that allows you to connect to remote systems using SSH and Telnet, in our case, we'll use SSH.
