---
layout: websphere

title: Liberty Profile Installation

description: 

excerpt: 

author: Ted Hagos

lastupdate: 


tags:


categories:

---

There are three ways to run the Liberty profile. First is to install it using the IBM Installation Manager. But this means you will have to install the base binaries of a WebSphere Application Server then install the Liberty profile. If your intention is to get acquainted with a true blue WAS installation, this might be the way to go. The Liberty profile has high fidelity with the WAS full profile as far as developers are concerned but it still not the full profile. 

If you choose to run the Liberty profile using the IBMIM, You will need your IBM id. If your work is on the admin or DevOps side of things, this is probably the ideal setup for you. 

The other two ways to run the Liberty Profile does not require the IBM Installation Manager. We simply need to grab a couple of jar files from the WAS Dev site and run the installation using the jar files. 

The Liberty profile can be ran and administered as a stand alone application using command line scripts that comes with it. It can also be integrated within an Eclipse IDE.

## 1 Command Line Installation

Grab the jar files from [WAS Dev site](https://developer.ibm.com/wasdev/). You can choose to download either the Beta or the GA (General Availability) release. Once you have downloaded the jar files, run the installer.

The **runtime** can be installed using the command below

~~~
java -jar wlp-beta-runtime-2014.11.0.0.jar
~~~

This archive install will prompt you to read the license, accept it and it will also prompt you where you would like to store the runtime files. The default location is the current directory.

If you need to develop applications that will use **Web Services, JMS, JCA, WebRTC or MongoDB**, you will need the extended runtime. That is a separate jar file.

~~~
java -jar wlp-beta-extended-2014.11.0.0.jar
~~~

Same process as when you installed the runtime,it will prompt you for the license acceptance and location where to store the files. 

The third jar file is for administration. At the time of writing, the admin is not very useful and quite limited in capability. It simply starts, stops and restarts the runtime. Those are things that are easy enough to do on the command line. But install it anyway if you would like to see it.

~~~
java -jar wlp-beta-admin-2014.11.0.0.jar
~~~

### 1.1 Installation Directory

You will need Administrative privileges when running and maintaining the Liberty profile runtime. It is best to install it where you have read/write/execute privileges and this folder is usually your home folder. 

1. **Windows** - This is usually somewhere in C:\Users\yourname\
2. **Linux** - ~/ or /home/yourname
3. **OSX** - ~/ or /Users/yourname


## 2 Eclipse Installation

The procedure for installing WAS Liberty Profile in Eclipse couldn't be simpler. The steps for installation is outlined below. For the purpose of this exercise, the Eclipse edition used is **JEE**

1. Launch Eclipse
2. Launch a web browser. Navigate to the [WAS Dev site](https://developer.ibm.com/wasdev/). Choose either the **GA** or the **Beta** release. Either way, there is an option for **online** installation. Look for an icon with a mouse pointer overlapping the Eclipse logo 
3. From the web page, drag and drop the Eclipse logo to any part of an open Eclipse window, the one you launched in step **1**
4. Accept the license and follow the prompts


Alternatively, you can also do the following steps to install in Eclipse

1. Launch Eclipse
2. From the **Help** menu, choose **Eclipse Market Place**
3. On the **Find** text box, type **WebSphere**
4. Liberty Profile can be installed for Eclipse Luna and Kepler. Find the entry that says **IBM WebSphere Application Server Liberty Profile for Luna**. Or Kepler if that is the Eclipse version you have
5. Accept the license and follow the prompts






