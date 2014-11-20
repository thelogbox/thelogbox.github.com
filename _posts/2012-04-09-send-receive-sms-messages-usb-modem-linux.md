---
layout: linux

title:  Send and Receive SMS message using USB modem

description: Simple steps to setup your own SMS gateway in Linux

excerpt: 

tags:
- sms
- modem

author: Ted Hagos

---

This mini project was done on a Debian 5 Linux. It was tested on CrunchBang as well and it worked out fine. A USB modem with a post paid plan was used, but a stick with pre paid plan should as well, I think. I haven't tested that but I can see no reason why it should not work.

First, we need to pull some software from the repositories. We will need **gnokii-smsd-mysql** and the **mysql-server**. 

~~~~
sudo apt-get update
sudo apt-get install mysql-server
sudo apt-get install gnokii-smsd-mysql
~~~~

Connect the USB modem to PC and find out which port it is using. We will need some info about the modem. We will use that later in our configuration.

~~~
sudo lsusb
~~~

Another command to use could be

~~~
sudo dmesg | grep USB
~~~

What you are looking for is the **device name** for the modem. Usually the modem is at **/dev/tty0** but just to be sure, run either the **lsusb** command or the **dmesg** command as shown above. Take note of the device name. We will need that when we edit the configuration file for gnokii.

The configuration file for gnokii is at **~/.config/gnokii/config**. Edit the file and set the port number and the device model to their appropriate values. They should look something like this

~~~
port=/dev/tty0
model=AT
~~~

We need to set the value of the **model** attribute to AT because we will use a USB modem. The default value of the model attribute in some configuration file is **6510**, which is a phone. That is not the correct value for our project.

Just in case the gnokii configuration file was not created during the installation, you can simply create the config file manually and set the port/model attributes to their proper values.

~~~
sudo mkdir -p ~/.config/gnokii
sudo touch ~/.config/gnokii/config
~~~

After you have saved the configuration file, do a quick test so we can know if we missed something.

~~~
sudo gnokii --identify
~~~

If the command succeeds, it will give some diagnostics. If there are errors, revisit your steps above.



## Setting the Database

The gnokii-smsd-msyql package contains the SQL scripts necessary to create the table structure, but the database itself still needs to be manually prepared. 

~~~
mysql -u root -p
mysql> create database smsgw;
mysql> use smsgw;
mysql> \. /usr/share/doc/gnokii-smsd-mysql/sms.tables.mysql.sql;
~~~

## Sending and Receiving SMS

Run **smsgw** daemon process 

~~~
sudo smsd -u root -p smsgw -c localhost -m mysql
~~~

To send an SMS message, run the command

~~~
echo "Test message | gnokii --sendsmsd <+mobilenumber>
~~~

+mobilenumber is structured as **(country code) phone number**

If you send an SMS message to the number of the USB modem, all incoming messages are stored in the **inbox** table of the database

~~~
mysql -u root -p
mysql> use smsgw;
mysql> select * from inbox;
~~~



