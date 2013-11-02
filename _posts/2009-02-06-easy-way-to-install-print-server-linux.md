---
layout: linux

title: Installing a Print Server

description: Really basic steps on setting up a CUPS printer

except:

Tags:
- Printer
- Server

categories:
- Linux

---



##Objective

1. Make a printer available for sharing over a local area network
2. Use Linux as the print server
3. Make the printer available over IPP (internet printing protocol) and LPD (Linux Print Daemon)

##What to work with

1. Minimally installed Debian squeeze - print server
2. Samsung CLP-315 color printer
3. Single subnet local area network

##Steps

**Install CUPS** from the Debian repositories.. 

> CUPS is the standards-based, open source printing system developed by Apple Inc for Mac OSX and other UNIX-like operating systems
> <cite>[CUPS.org][1]</cite>

    $ sudo apt-get install cupssys

**Edit /etc/cups/cupsd.conf**. There is a lot of entries on the default cupsd.conf and it could be distracting. One way to ease the cupsd.conf configuration is to start with a clean slate.

    $ cd /etc/cups
    $ sudo cp cupsd.conf cupsd.conf.original
    $ sudo echo "" > cupsd.conf 

Line no. 2 above makes a copy of the original cupsd.conf and line no.3 wipes out the textual content of cupsd.conf, now you can edit cupsd.conf with minimal fuss. The contents of cupsd.conf is as follows


    LogLevel debug
    SystemGroup lpadmin
    # Allow remote access
    Port 631
    Listen /var/run/cups/cups.sock
    # Share local printers on the local network.
    Browsing On
    BrowseOrder allow,deny
    BrowseAddress @LOCAL

    #DefaultAuthType Basic

    <Location />
        Allow localhost
        Allow 192.168.0.*
        Allow all
        # Allow shared printing and remote administration...
        Order allow,deny
        Allow all
    </Location>
    <Location /admin>
        Allow 192.168.0.*
        Encryption Required
        Allow all
        Allow all
        # Allow remote administration...
        Order allow,deny
        Allow all
    </Location>
    <Location /admin/conf>
        Allow 192.168.0.*
        #  AuthType Default
        #  Require user @SYSTEM
        Allow all
        # Allow remote access to the configuration files...
        Order allow,deny
        Allow all
    </Location>

Obviously not a very tight and secure cups configuration. If this is your first time to install CUPS, this could a be a good way to start the configuration -- everything is open, then you can tighten it later on.  

