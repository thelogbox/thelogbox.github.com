---
layout: linux

title: How to Connect Windows to a CUPS Print Server

description: How to hook up Windows to a Linux Print Server

excerpt: 

tags:
- Printer
- Server

categories:
- Linux

---

There are a couple of ways to print to a CUPS printer from a Windows machine. *CUPS* printer means it's a printer connected to either a UNIX, Linux or an OSX machine. CUPS is the system which these OSes use to share print services. 

One way to print from Windows is to use the  Samba features of your Linux server. Samba appears to be easier for the Windows users because Samba looks and feels just like another Windows box. I won't use Samba for this guide. Instead we will connect to the CUPS printer using internet printing protocol.

## Things you will need

1. A *driver* for your printer. I don't know what printer you have so I can't list generic resources here. You can use the CD/DVD that came with your printer, or you can get the latest drivers online (always better to get updated drivers). This approach assumes that the Windows machine contains the printer driver locally. This doesn't scale very well for enterprise settings, if you are looking for a setup where CUPS is the RIP (if you don't know what a RIP is, then it's probably not for you) by acting as a generic postscript printer by using PPDs and CUPS filter queues, you can head over to LinuxPrinting.org, printing with CUPS in Samba
2. A properly configured *CUPS printer*. If you haven not configured your CUPS printer yet, [read this one firsrt](/easy-way-to-install-print-server-linux), then come back here

## Configuration

1. Make sure the CUPS printer is powered on, connected, and that you can ping it from your windows machine.
2. From your Windows machine, go to the "Add printers" section--you know how to find this.
3. Choose *Add a network printer*. The CUPS won't be listed, so click "My printer isn't listed"
4. On the box provided, type <code class="codeblock">http://IpOrNameOfPrintServer:631/printers/nameofQueue</code> the "printers" subdirectory is pretty common for CUPS printers, the *nameofQueue* is something your Sys Admin (or you) would know, this the name of the printer added to CUPS, if you are not sure, launch a web browser and type http://IpOrNameOfPrintServer:631 then click "Printers" so that you can verify the name of the printer queue
5. After clicking "Next", you will be prompted to select a driver for your printer, just go on ahead and select it.
6. Print a test page
