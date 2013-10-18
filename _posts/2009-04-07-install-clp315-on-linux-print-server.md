---
layout: post

title: Install CLP 315 on Debian Linux Print Server

description:

except:

categories:
- blog

---



##Objective

1. Install the Samsung CLP 315 color laser printer
2. To do No.1 on Debian Squeeze
3. To do No. 2 on a headless server (no monitor, no keyboard -- it's a server)

##What you need

1. A Linux Server configured for printing (CUPS server). If you don't have this yet, read the instruction on [How to install a Linux print server](/easy-way-to-install-print-server-linux/)
2. The Samsung CLP 315, powered and plugged-in to one of the USB ports of your Linux Print server
3. An Internet connection, to download the driver from Samsung


##Installing the CLP 315 driver

1. Get the UnifiedLinuxDriver.tar either from the CD that came with the printer or from the [Samsung site](http://www.samsung.com). You need to navigate the site a little bit. Go to *Support and Downloads* page, then find the printer, there is a wizard
2. Find a way to SSH to your Linux Server, [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) should do it
3. Find a way to upload UnifiedLinuxDriver.tar.gz to your headless server. FTP or SCP or even Samba shares should do it
4. Unzip, or rather, untar the UnifiedLinuxDriver -- *$ sudo tar -xzvf UnifiedLinuxDriver.tar.gz*
5. Change directory to *cdroot*, this is one of the folders that is contained in the UnifiedLinuxDriver
6. Run the installer -- *$ sudo install.sh* . The installer was intended to be ran from GUI workstation, so it will give you some warnings that may look like errors. It will eventually detect that you are not running on a GUI and it will degrade gracefully to a text-based installation. We need to run the installer because we need a very specific file. That file is **rastertosamsungsplc**, it is the PPD file we need for the CLP 315 printer to function normally in Linux

##Second part of installation 

Copy the rastertosamsungsplc ppd file */usr/lib/cups/filter* folder 

    $ cd /path/to/where/rastertosamsungsplc-is/
    $ cp rastertosamsungsplc /usr/lib/cups/filter/rastertosamsungsplc
    $ sudo /etc/init.d/cupsd restart

At this point, you can now start adding the CLP 315 as one of the printers to your CUPS server. Open a browser window (anywhere in your network) and type *http://NameOfPrintServer:631*. Click *Administration --> Add Printer* 
