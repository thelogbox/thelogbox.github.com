---
layout: post

title: Problems with iSSH + Vim on the iPad

description: 

excerpt: 

categories:
- blog

---



## Motivations

1. To login remotely to a Linux machine via SSH using the iPad
2. To use tmux (screen multiplexer) and vim to edit source files

## Problems encountered when using iSSH


1. Couldn not get 256 colors to work. Elsewhere on the Internet (forums etc), the instruction were to set the 256 color on the Advanced settings and/or to set the *TERM* variable equal to *term-256color*, which I did, but still could not get it to work. The **Prompt** app though worked out of the box, I did not have to fiddle with anything

2. The Vim screen was wobbling when editing. The wobbling I think is being caused by Vim doing a little bit if intellisense on matching braces, quotes and parentheses. I think it was also being caused by the status line jittering. 

<img class="shadow" src="/img/issh-1.jpg">

Later, after inspecting my .vimrc on the target machine, I found out that I had a :set columns=100. This was causing the wobbling and the display of weird characters  in iSSH. My iSSH screen settings was not wide enough to accomodate 100 columns as set in my .vimrc. I did not want to change my .vimrc hence, I just enlarged my screen size in iSSH (how to do to this)


<img class="shadow" src="/img/issh-2.jpg">


3. The CTRL key doesn't work, I actually still don't know how to make it work. Yes, I have enabled Options Mapping. 

This is a deal killer, Vim uses this alot when switching   between split windows (C-w w). Tmux uses this a lot more. This is enough reason why I chose Prompt, the CTRL key works out-of-the-box



## Why I chose Prompt over iSSH, despite iSSH being cheaper. 

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
