---
layout: linux

title: Installing a Print Server

description: Really basic steps on setting up a CUPS printer

except:

Tags:
- Printer
- Server

---

This guide will walk through the steps on how to share a printer over a local network using a Linux server. It will use the *internet printing protocol* and the *linux print daemon*.  

For this guide, the materials used were:  **1)** a minimally installed Debian Linux **2)** a Samsung CLP-315 color printer. and; **3)** a single subnet local area network

## Steps

Install CUPS from the repositories

<pre class="codeblock">
$ sudo apt-get install cupssys
</pre>

Edit */etc/cups/cupsd.conf*. There are quite a few entries on the default *cupsd.conf* and it could be distracting. We will erase that and start with a simple configuration

<pre class="codeblock">
$ cd /etc/cups
$ sudo cp cupsd.conf cupsd.conf.original
$ sudo echo "" > cupsd.conf 
</pre>

Second line above makes a copy of the original cupsd.conf and the third line wipes out the textual content of *cupsd.conf*. After that we can edit cupsd.conf with minimal fuss. The new *cupsd.conf* looks like the following

{% highlight xml %}
LogLevel debug
SystemGroup lpadmin
#Allow remote access
Port 631
Listen /var/run/cups/cups.sock
#Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAddress @LOCAL

#DefaultAuthType Basic
<Location />
  Allow localhost
  Allow 192.168.0.*
  Allow all
  #Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>

<Location /admin>
  Allow 192.168.0.*
  Encryption Required
  Allow all
  Allow all
  #Allow remote administration...
  Order allow,deny
  Allow all
</Location>
    
<Location /admin/conf>
  Allow 192.168.0.*
  #AuthType Default
  #Require user @SYSTEM
  Allow all
  #Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>
{% endhighlight %}

Obviously not a very tight and secure CUPS configuration. You can harden it later when you know more about the configuration. For now, this will happily function as a basic, albeit, insecure print server. 

