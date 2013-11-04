---
layout: post

title: iSSH and Vim

description: Why I don't like using iSSH on iOS

excerpt: 

tags:
- ssh
- terminal

author: Ted Hagos

categories:
- iOS

---


I needed to login to a linux machine using an iPad. Preferably, I should also be able to use a screen multiplexer for editing source files and for other stuff. This is the reason I bought iSSH, then eventually Prompt.

I had issues with iSSH, these are found below:

Could not get 256 colors to work. Elsewhere on the Internet (forums etc), the instruction were to set the 256 color on the Advanced settings and/or to set the *TERM* variable equal to *term-256color*, which I did, but still could not get it to work. The **Prompt** app though worked out of the box, I did not have to fiddle with anything

The Vim screen was wobbling when editing. The wobbling I think is being caused by Vim doing a little bit if intellisense on matching braces, quotes and parentheses. I think it was also being caused by the status line jittering. 

<img class="shadow" src="/img/issh-1.jpg">

Later, after inspecting my .vimrc on the target machine, I found out that I had a :set columns=100. This was causing the wobbling and the display of weird characters  in iSSH. My iSSH screen settings was not wide enough to accomodate 100 columns as set in my .vimrc. I did not want to change my .vimrc hence, I just enlarged my screen size in iSSH (how to do to this)

<img class="shadow" src="/img/issh-2.jpg">

The CTRL key doesn't work, I actually still don't know how to make it work. Yes, I have enabled Options Mapping. 

This is a deal killer, Vim uses this alot when switching   between split windows (C-w w). Tmux uses this a lot more. This is enough reason why I chose Prompt, the CTRL key works out-of-the-box

***

Prompt is another SSH client on the iPad. It is less capable in terms of bells and whistles, but it does have everything I need and none of the problems I have with iSSH. I don't use the iPad to VNC or to connect via Remote Desktop Connection anyway, just SSH

1. the CTRL keys work out of the box, using a bluetooth keyboard. I could not get it to work on iSSH. Despite trying a lot of acrobatics on the settings -- Yes. I did try enable Options Mapping. No joy!

2. Prompt appeared a bit faster too

If not for my frustration on the CTRL keys not working out of the box on iSSH, it would have been a better fit for my use, because;

- The size of the screen can configured via a slider control. This was not available on Prompt. You could choose the size of the font (but not the screen font itself)
- It was more intuitive if you need another SSH session, just press the plus sign (+) on the top portion of the screen
- It had lot more controls than Prompt.  

I bought the two apps anyway. It seems though, I find my self using the Prompt more than I use iSSH


[1]: http://www.flickr.com/photos/headtogs/6918694882/
[2]: http://www.flickr.com/photos/headtogs/7064778929/
