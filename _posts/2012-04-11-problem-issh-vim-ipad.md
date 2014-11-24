---
layout: mac

title: iSSH and Vim

description: Why I don't like using iSSH on iOS

excerpt: 

tags:
- ssh
- terminal

author: Ted Hagos

---

<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- 468pxby60banner -->
<ins class="adsbygoogle"
     style="display:inline-block;width:468px;height:60px"
     data-ad-client="ca-pub-4627957463175380"
     data-ad-slot="5760679882"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>

I needed to login to a linux machine using an iPad. Preferably, I should also be able to use a screen multiplexer for editing source files and for other stuff. This is the reason I bought iSSH, then eventually Prompt.

## Issues with iSSH

I could not get 256 colors to work. A quick research &mdash; by that I mean quick Googling &mdash; I found some instructions to set the 256 color on the Advanced settings and/or to set the *term* variable equal to *term-256color*.  Which I did. But still could not get it to work. The *Prompt* app though worked out of the box, I did not have to fiddle with anything

Vim's screen was wobbling when editing. The wobbling I think is being caused by Vim doing a little bit if intellisense on matching braces, quotes and parentheses. I think it was also being caused by the status line jittering. 

<img class="shadow" src="/img/issh-1.jpg">

Later, after inspecting my *.vimrc* on the target machine, I found out that I had a <code class="codeblock">:set columns=100</code>. This was causing the wobbling and the display of weird characters  in iSSH. My iSSH screen settings was not wide enough to accomodate 100 columns as set in my .vimrc. I did not want to change my .vimrc hence, I just enlarged my screen size in iSSH (how to do to this)

<img class="shadow" src="/img/issh-2.jpg">


<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- 468pxby60banner -->
<ins class="adsbygoogle"
     style="display:inline-block;width:468px;height:60px"
     data-ad-client="ca-pub-4627957463175380"
     data-ad-slot="5760679882"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>

The CTRL key doesn't work, I actually still don't know how to make it work. Yes, I have enabled Options Mapping. 

This is a deal killer, Vim uses this alot when switching   between split windows (C-w w). Tmux uses this a lot more. This is enough reason why I chose Prompt, the CTRL key works out-of-the-box

## Prompt

Prompt is another SSH client on the iPad. It is less capable in terms of bells and whistles, but it does have everything I need and none of the problems I have with iSSH. I don't use the iPad to VNC or to connect via Remote Desktop Connection anyway. I just needed it for SSH

1. the CTRL keys work out of the box, using a bluetooth keyboard. I could not get it to work on iSSH. Despite trying a lot of acrobatics on the settings &mdash; Yes. I did try enable Options Mapping. No joy!
2. Prompt appeared a bit faster too

If not for the the CTRL keys not working out of the box on iSSH, it would have been a better fit for my use, because;

- The size of the screen can configured via a slider control. This was not available on Prompt. You could choose the size of the font (but not the screen font itself)
- It was more intuitive if you need another SSH session, just press the plus sign (+) on the top portion of the screen
- It had lot more controls than Prompt.  

I bought the two apps anyway. It seems though, I find my self using the Prompt more than I use iSSH

