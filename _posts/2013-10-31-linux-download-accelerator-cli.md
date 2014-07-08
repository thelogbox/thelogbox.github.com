---
layout: linux

title: Download Accelerator

description: Simple command line tool to accelerate downloading. Imagine wget on steroids

excerpt: 

tags:
- cli
- utility
- Debian

---


Axel is a CLI download accelerator. It's available on Linux repos. I am using Debian that's why the package manager is aptitude. Just use your own package manager and look for axel.


<pre class="codeblock">

$ sudo apt-get install axel 
$ axel -n 10 http://wordpress.org/latest.zip

</pre>

-n 10 means you want to use 10 simulateneous threads of download. 