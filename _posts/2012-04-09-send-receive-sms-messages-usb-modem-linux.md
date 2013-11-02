---
layout: linux

title:  Send-Receive SMS

description: Simple steps to setup your own SMS gateway in Linux

excerpt: 

tags:
- sms
- modem

categories:
- Linux

---

This small guide uses *gnokii-sms* to send and receive SMS messages using Linux PC. The project I was working on did not industrial grade throughput. That is the reason I cannot justify the cost of *WaveComm* *iTegra* type equipment. The SMS project was ran on a Debian Linux. If you are using a different distro, use the packaging mechanism of your distro.

There were a couple of other solution approaches but I went for *gnokii-sms*. I didn't have a lot of time, which ruled out whipping serial I/O codes and concocting SMS messages using Hayes AT command set.  

I could have used *Kannel* but it was so big. I only needed a simple mechanism to receve and send SMS message. I did not need a full gateway with all the bells and whistles.

GNOKii-SMS and Gammu were mature solutions. I went eventually with *gnokii-sms* but Gammu would have been a fit as well. 

Hence, this mashup uses *gnokii-sms*. It is a stand-alone application with a daemon and it uses MySQL database as a datastore.  I don't need to learn any API in order to integrate it with my application. All I need to do is to write an application that will query the *gnokii-sms* backend. I won't even alter the structure of the gnokii-sms database. My application will simply use gnokii for the SMS facility. No application logic will be added to gnokii-sms

You will need the items below to follow this guide.

1. DEBIAN linux
2. USB modem. A post-paid plan works better for me. I could have chosen pre-paid but I need to be mindful when the SIM is running out of pre-paid load credits.

# STEPS

Get gnokii-smsd and mysql-server from the Debian repositories.

<pre class="codeblock">

$ sudo apt-get install mysql-server
$ sudo apt-get install gnokii-smsd-mysql

</pre>

Connect the USB modem to Debian and find out which port it is using &mdash; <code class="codeblock">sudo lsusb</code> or <code class="codeblock">sudo dmesg | grep USB</code> should do the trick

What you are looking for is the device name for the modem. Usually, the modem is at */dev/tty0*, but just to be sure, run either *lsusb* or the *dmesg* command as stated above.

When you know the device name of the modem, edit the configurationt file of *gnokii-sms*. It is over at <code class="codeblock">~/.config/gnokii/config</code>. You need to make 2 changes on the config file &mdash the <code class="codeblock">PORT</code> and <code class="codeblock">model</code> entries. 

Set <code class="codeblock">port = /dev/tty0</code> (substitute your actual device name to tth0). Set <code class="codeblock">model = AT</code>, the default is *6510* which assumes you are using a Nokia phone. You are not. You are using a non-nokia USB modem.


## EXTRA NOTES

On some Debian variant like *CrunchBang*, the config file was not found at *~/.config* folder, it does not exist at all. There was a config file though at */etc/xdg/gnokii/config*. If this is your case, you can simply create the configuration file and directory manually

<pre class="codeblock">  

$ mkdir ~/.config
$ cd ~/.config
$ mkdir gnokii
$ cd gnokii
$ cp /etc/xdg/gnokii/config config

</pre>

Then make the edits on PORT and model just the same.  

## TESTING

To test if everything is in order, you can run <code class="codeblock">sudo gnokii --identify</code>. This should give you some diagnostics and some quick peek if something is wrong with the configuration file

## PREPARE THE DATABASE BACKEND

I chose the MySQL variant of the gnokii-smsd, if you use another database like PostgreSQL, you can do that too, but you need to install *gnokii-smsd-pgsql* instead of *gnokii-smsd-mysql*.  

Here is how to prepare the MySQL back-end

<pre class='codeblock'>

$ mysql -u root -p
$ mysql> create database smsgw;
$ mysql> use smsgw;
$ mysql>\. /usr/share/doc/gnokii-smsd-mysql/sms.tables.mysql.sql;

</pre>

Line No. 4 above is the SQL script that you need to run in order to create the MySQL table structures which gnokii-smsd expects to find. 

## TEST THE SMS GATEWAY

Run gnokii-sms as a daemon process &mdash; <code class="codeblock">sudo smsd -u root -p <MySQL Password> -d smsgw -c localhost -m mysql</code>

Try sending some SMS messages to the phone number of the USB modem, then view the messages on the MySQL database.

<pre class='codeblock'>

$ mysql -u root -p
$ mysql> use smsgw;
$ mysql> select * from inbox;

</pre>

Try sending some SMS messages from the command line to your phone using <code class="codeblock">echo "Test message" | gnokii --sendsmd +SMSNO</code>

Where *SMSNO* is structured as (countrycode) cell phone number



      


