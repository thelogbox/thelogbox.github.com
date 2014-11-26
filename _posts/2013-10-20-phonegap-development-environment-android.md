---
layout: phonegap

title: Android Setup for OSX

description: How to setup the Android SDK in preparation for PhoneGap Development

excerpt: 

author: Ted Hagos

lastupdate: 2013-11-11

tags:
- Android
- Setup

lastupdate: 2013-11-10

---

This chapter will walk through the steps to setup an Android development environment. The Android SDK requires that a Java development environment and Apache Ant are installed. 

**Setup the JDK**

Download [the JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html) from the Oracle site. More than likely it will be a *.dmg* file. You can install that by simply double clicking.

The path to Java executables will be taken cared of by the installer. The *java compiler* and other command line utilities of the JDK will be automatically added to the system path.

**Setup Apache Ant**

Download the installer from [ant.apache.org](http://ant.apache.org/). Look for the download section. Apache Ant can be downloaded either in source or binary form. We have no use for the source distribution for now. Just download the binary format. At the time of writing, there are three formats for binary distribution &mdash; *zip, tar.gz* and *bz2*. 

After the download is finished, choose directory where you will install *ant*. For the purpose of this chapter, we will install it in a user directory. 

~~~
$ cd ~/
$ mkdir progtools
$ cd progtools
$ cp ~/Downloads/apache-ant-1.9.2-bin.zip
$ unzip apache-ant-1.9.2-bin.zip
~~~

Your version of ant might not be exactly *1.9.2*, so substitute accordingly.

**Setup Android SDK**

Download the SDK from [developer.android.com](http://developer.android.com/sdk/index.html). The web page might display the *ADT* bundle more prominently. It's not the ADT we need. Find the link for "Existing IDE" 

![other IDE](/img/phonegap/download-android-sdk.png)

Copy the zipped file to your users directory just like what we did with Apache ant.

~~~
$ cd ~/progtools
$ cp ~/Downloads/android-sdk_r22.3-macosx.zip
$ unzip android-sdk_r22.3-macosx.zip
~~~



**Setup the NodeJS Package Manager**

Node package manager is part of the **NodeJS** installation. Download them from [nodejs.org](http://nodejs.org). The downloaded package will most likely be in *pkg* format. They can be installed by simply double clicking.

**HomeBrew**

If you have performed the PhoneGap installation for iOS, then you have everything you need to install HomeBrew. Brew is a package management system for OSX, just like MacPorts and Fink. You can find instructions on how to install Brew at their website [brew.sh](http://brew.sh). I've pasted the instruction in this section to save you time. To install Brew now, paste the following code in a terminal window

~~~
ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"
~~~

**Update the System Path**

Open your startup script for editing. It's located at ~/.bash_profile. Add the following entries

~~~
export ANT_HOME=~/progtools/apache-ant-1.9.2
export ANDROID_HOME=~/progtools/android-sdk_r22.3-macosx
export PATH=$PATH:$ANDROID_HOME/platform-tools:.
export PATH=$PATH:$ANDROID_HOME/tools:.
export PATH=$PATH:$ANT_HOME/bin:.
~~~

Quit the terminal then re-open it. This gives your startup script a chance to execute. From now on, all these PATH settings are available to you whenever you open a terminal window.

**PhoneGap and Cordova Tools**

The last remaining pieces of the setup is to get both the PhoneGap and Cordova command line utilities. If your terminal window is still open, type these

~~~
$ sudo npm install -g phonegap
$ sudo npm install -g cordova
~~~

**Android Manager**

The Android SDK setup is not yet complete. You will need to download a lot more software and you will do so using the Android SDK Manager. From a terminal window, type **android**

![android manager](/img/phonegap/android-manager.png)


At a minimum you will need to install the SDK tools, platform tools and a couple of API levels. It depends on what platform of Android you are targeting. If you want to develop for Jellybean, get API level 19, 18,17 and 16. Ice Cream Sandwich is API level 15 and Honeycomb is 13. Get the *SDK platform* and the *ARM EABI system image* for each API level that you choose. You need the system images for building the *android virtual device* which you will use for testing later on.

Select that packages that you need and click the *Install packages* button. That may take a while.

**Test the Setup**

Create a throw away project, then try to compile it using the PhoneGap CLI tools

~~~
$ mkdir ~/workarea
$ cd ~/workarea
$ phonegap create first
$ cd first
$ phonegap build android
$ cd platforms
~~~

An android project folder should have been created inside the platforms folder. This folder contains the necessary android project structure for testing and deployment.

