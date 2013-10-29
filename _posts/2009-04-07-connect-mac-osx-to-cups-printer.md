---
layout: post

title: How to Connect OSX to a CUPS Print Server

description: How to hookup the Mac to a Linux Printer Server

excerpt: 

tags:
- mac
- Printer

categories:
- OSX


---



1. Open **System Preferences** dialog. You can reach this dialog by clicking the small Apple logo at upper-left most corner of your desktop, 
2. Click **Print and Fax**
3. On Printers column, click the plus sign to add a printer (There is a **+** sign at the lower left portion of the dialog window
3. The "Protocol dropdown will say "Line Printing Daemon" or LPD, you need to change this to "Internet Printing" or "IP", click the drop down and find "Internet Printing"
4. On the address field, type the IP address or the hostname of the CUPS server, just write the hostname, don't include the protocol. Hence you would write **cupsipaddress**, not **ipp://cupsipaddress**
5. On the queue input field, type the queue name of the target printer attached to the CUPS server, the queue name of printers in a CUPS server is always prefixed by the word *printers/* -- you need to ask your administrator what is the name of the printer as defined on the CUPS server. If you are the administrator, the name of the queue name is the same as what you typed on the name field of a printer when you were installing your printer to the CUPS server. What you need to type on the queue input field is **printers/nameofprinteroncups**
6. On the name field, type something that you can easily recognize, when you have several printers installed on your MAC, it helps if the printer names are easily recognizable.
7. On the "print using" field, choose "select a driver to use", and just choose your appropriate driver .

That should work now. Your Mac OSX is actually a CUPS server itself, there is a UNIX-ish way of installing printers on OSX, just open Safari, and type <span class='codeblock'>http://localhost:631</code>

you will be greeted by the CUPS opening page.

That's it, now your OSX can print to a remote CUPS server.
