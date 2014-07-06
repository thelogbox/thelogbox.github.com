---
layout: linux

title:  Send-Receive SMS message via USB modem

description: Simple steps to setup your own SMS gateway in Linux

excerpt: 

tags:
- sms
- modem

categories:
- Linux

---


<div id="feature-button">
The Linux guide on how to setup Gnokii for sending and receiving SMS message has moved to 
<p/>

<a href="http://notes.tedhagos.com/linux/UsbModemLinux-SMS.html">notes.tedhagos.com/UsbModemLinux-SMS</a>   
<p/>

The original guide was left here for quick references only. This guide will no longer be updated here
</div>  

<hr/>


# What you need

1.  A Linux PC. Debian was used but I got to test it on Crunchbang as well, worked out fine. It should work fairly well on the Debian derivatives e.g. Ubuntu, Xubuntu, Mint etc
2.  A USB modem. A post paid plan was used for the project, but a USB stick on pre-paid should work just as well


# Installation

`sudo apt-get update`  
`sudo apt-get install mysql-server`  
`sudo apt-get install gnokii-smsd-mysql`

# Config

Connect the USB modem to PC and find out which port it is using

`sudo lsusb`

Another command to use could be

`sudo dmesg | grep USB`

What you are looking for is the device name for the modem. Usually, the modem is at `/dev/tty0`, but just to be sure, run either lsusb or the dmesg command as stated above. Remember the device name because you will need it when you edit `~/.config/gnokii/config` &#x2014; that is the configuration file for gnokii. 

On some Debian derivatives like Crunchbang, the gnokii config file was not created during the installation . If that is the case, just create the config file manually.

`sudo mkdir -p ~/.config/gnokii`  
`sudo touch ~/.config/gnokii/config`

Edit the **config** file. Set the port number and model to their appropriate values

    port=/dev/tty0
    model=AT

There might a default value for the model property, it could be 6510. That value corresponds to a Nokia phone. But we are not using a Nokia phone, we are using a USB modem, so set the model value to **AT**.

Once done with the configuration, just do a quick test so that we know things are working out fine. Gnokii has a command that can quickly tell us if we are doing things correctly.

`sudo gnokii --identify`

It should give us some diagnostics and a quick peek if we did something wrong on the configuration file.

# Database backend

The gnokii-smsd-msyql package contains the SQL scripts necessary to create the table structure, but the database itself still needs to be manually prepared. 

`mysql -u root -p`  
`mysql> create database smsgw;`  
`mysql> use smsgw;`  
`mysql> \. /usr/share/doc/gnokii-smsd-mysql/sms.tables.mysql.sql;`

# Sending and Receiving SMS

First, the daemon smsgw daemon process needs to run. Get another terminal window and run the daemon process from there

`sudo smsd -u root -p smsgw -c localhost -m mysql`

To send an SMS message, the command is

`echo "Test message | gnokii --sendsmsd +MobileNumber`

+MobileNumber is structured as <span class="underline">(country code) phone number</span>

If you send an SMS message to the number of the USB modem, all incoming messages are stored in the **inbox** table of the database

`mysql -u root -p`  
`mysql> use smsgw;`  
`mysql> select * from inbox;`




