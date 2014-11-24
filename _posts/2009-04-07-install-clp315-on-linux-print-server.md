---
layout: linux

title: Install CLP 315 on Debian

description: Get a Samsung color printer to work with a Linux Print server

except:

tags:
- Printer
- Server

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

These steps will install the Samsung CLP 315 on a headless Linux Server. 

You will need a properly configured CUPS server before proceeding. If you haven't configured a printer server yet, [read this one first](/easy-way-to-install-print-server-linux) then come back. You will also need an internet connection for this one. There are some files to download.

## Steps

1. Get the UnifiedLinuxDriver.tar either from the CD that came with the printer or from the [Samsung site](http://www.samsung.com). You need to navigate the site a little bit. Go to *Support and Downloads* page, then find the printer, there is a wizard
2. Find a way to SSH to your Linux Server, [Putty](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) should do it
3. Find a way to upload UnifiedLinuxDriver.tar.gz to your headless server. FTP or SCP or even Samba shares should do it
4. Unzip, or rather, untar the UnifiedLinuxDriver -- *$ sudo tar -xzvf UnifiedLinuxDriver.tar.gz*
5. Change directory to *cdroot*, this is one of the folders that is contained in the UnifiedLinuxDriver
6. Run the installer -- *$ sudo install.sh* . The installer was intended to be ran from GUI workstation, so it will give you some warnings that may look like errors. It will eventually detect that you are not running on a GUI and it will degrade gracefully to a text-based installation. We need to run the installer because we need a very specific file. That file is **rastertosamsungsplc**, it is the PPD file we need for the CLP 315 printer to function normally in Linux

## Configuration

<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- 468pxby60banner -->
<ins class="adsbygoogle"
     style="display:inline-block;width:468px;height:60px"
     data-ad-client="ca-pub-4627957463175380"
     data-ad-slot="5760679882"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>

Copy the rastertosamsungsplc ppd file to the */usr/lib/cups/filter* folder 

~~~~
$ cd /path/to/where/rastertosamsungsplc-is/
$ cp rastertosamsungsplc /usr/lib/cups/filterrastertosamsungsplc
$ sudo /etc/init.d/cupsd restart
~~~~

At this point, you can now start adding the CLP 315 as one of the printers to your CUPS server. Open a browser window (anywhere in your network) and type **http://NameOfPrintServer:631**. Click **Administration** &rarr; **Add Printer** 
