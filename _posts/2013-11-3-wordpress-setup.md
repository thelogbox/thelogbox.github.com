---
layout: wordpress

title: Setup

author: Ted Hagos


description: Simple step by step procedure on how to setup a development and testing environment for WordPress

excerpt: 

tags:
- setup

categories:
- WordPress

---

WordPress needs a web server capable of running PHP and a MySQL database. The more popular choice for the web server is Apache, although many others will suffice just as well. For our purpose we will use Apache. 

MySQL, PHP and Apache are open source software (OSS). They are widely available on popular platforms such as OSX, Linux and Windows. These instructions are for Windows because I think that most of the people who will read this are on that platform. 

There are plenty of ways to install these bunch and make them work together but as this guide is targeted towards people with minimum programming experience, I chose to use *WAMP*. Its an acronym for Windows, Apache, MySQL and PHP. It takes care of a lot of things but the most value is that it takes away our need for configuration.

Installing these software individually affords you the most control over the setup but it comes at a prie &mdash; you have to really know what you are doing to make them work together. The configuration part can be tricky at times and it can easily trip up a beginning developer. So, take the guess work out of your workflow for now and just install WAMP. 

WAMP installation involves just a few basic steps. Download it from the Apache site, install, configure and finally test it. 

***

Download the installer the from the [WAMP site]( http://www.wampserver.com/en/). Choose the appropriate installer for your platform. 

![WAMP installer](/img/wordpress/choose-installer-wamp.png)
<div id='lst'>WAMP Installer</div>

I wish I could be more precise in the details here but the issue is I don't know what kind of Windows installation you have. It is simply your responsibility to know that detail. You can find out easily though, simply access System Properties from the Windows control panel, then you can ascertain which kind of Windows you have installed.Choose the 64-bit version if you are using 64-bit Windows. 

***

Double click the the installer. By default, WAMP installer will put your files in *C:\wamp* – for Windows XP users, this is not generally a problem, but for Windows 7 or 8 users, it could be a problem because folders outside the Users folder generally needs an elevated privilege before you can access it. If you don’t mind running things as Administrator, then go ahead, install in C:\wamp, otherwise, change the installation folder to *C:\Users\yourname\wamp\*. After the installer has finished, WAMP should be sitting in your System Tray.


![System Tray](/img/wordpress/wamp-system-tray.png)
<div id='lst'>WAMP in the System tray</div>

The WAMP icon will change color in the course of usage. Initially, it will be red. That means the services (Apache and MySQL) are not running. It turns into green when both Apache and MySQL have already been started and are running without problems. Green is color you are looking for.

***

Hover your mouse on the system tray, right on top of WAMP icon. Click it to reveal the menu options. You will find options to start, stop and restart services.

![Starting WAMP](/img/wordpress/wamp-start.png)
<div id='lst'>Starting WAMP</div>
You will not see anything happen (yet) when you start WAMP. They are services after all and not desktop applications. Starting the services only means that the Apache Web Server is now ready to respond to HTTP request (usually browser request) and MySQL database is now ready to respond to SQL commands.

Launch a browser session (Chrome or Firefox if you have them, if you don’t , get them. IE has some quirks with the WAMP admin panel)


![WAMP Opening Screen](/img/wordpress/wamp-opening-screen.png)
<div id='lst'>WAMP opening screen</div>

When you see the opening screen, that means your WAMP server is working properly.





