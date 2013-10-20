---
layout: phonegap

title: Android Setup

description:

excerpt: 

categories:
- phonegap
---

Setup your JDK and Apache ANT before setting up the Android SDK. Once Java and Apache ANT are out of the way, the process simply involves downloading, installing and configuring the SDK. The configuration is where it sometimes gets messy and confusing especially for beginners. But these things are easily managed by simply following instructions. When the instructions on these pages fail you, I'm sure you will Google for them. The official site of android can be found [here](http://developer.android.com/sdk/index.html) and [here](http://developer.android.com/sdk/index.html). 

If that is still not clear enough, you can look at the [setup instructions I wrote for my students here](https://docs.google.com/document/d/1AS8OoJJnRIIyEvi8lG6I8iF0PEt1-UolvQGtVevrJg4/edit?usp=sharing)

# ANDROID SDK SETUP

**DOWNLOAD THE INSTALLER** from [Android SDK from android.developer.com]( http://developer.android.com/sdk/index.html ).

You might be tempted to get the ADT bundle because the link on that one is prominently displayed, that is not the one you need, that is for Eclipse users. Download just SDK, not the bundle.

**GET THE ZIPPED FILE**. Unzip the file to a user directory so that you will not need elevated privileges to use the executable files. 


The user directory in Windows is usually inside <code class="codeblock">C:\User\yourname\</code>. Try to install on a folder without a white space. White spaces in Windows can become very troublesome when working on the command line. In OSX it will be inside <code class="codeblock">/Users/yourname/</code>.

Try to remember the full path of the directory where you unzipped the Android SDK, this will be the **ANDROID_HOME**. 

**GET A TERMINAL WINDOW** &mdash; cmd.exe in Windows and Terminal.app in OSX. Go to the ANDROID-HOME/tools directory, run the <code class="codeblock">android</code> executable. This will launch the Android SDK Manager. 

The SDK manager needs an internet connection. It connects to the android.developer.com website and checks which SDK levels are installed in your machine. Naturally, if you have installed the SDK just now, there won't be much. Choose the API levels that you would like to install in your machine.

Each version or platform of Android (Froyo, Gingerbread etc) is a numbered API level. If you want to install the Jellybean SDK, for example, then check the box next to API level 17. 

If you have really fast internet connection and you are not sure which API to check, check them all. This will take some time to complete though.

**MODIFY THE SYSTEM PATH**. Include the *android tools* and *platform tools* in the executable path. You will need it if you want to work with android using the command line. The two folders of interest are **ANDROID-HOME/tools** and **ANDROID-HOME/platform-tools**

## WINDOWS 

There are two ways to set the PATH in Windows. The first method is via the command line (cmd.exe).

<pre class='codeblock'> 

SET ANDROID_HOME=c:\>path\where\you\installed\android\
  
SET PATH=%PATH%;%ANDROID_HOME%\bin;%ANDROID_HOME%\platform-tools;%ANDROID_HOME%\tools;.

</pre>

You will run these commands each time you will open a new terminal window. Those settings are not remembered by the shell.

If you want to permanently set the PATH to android tools, you need to do it in the System Properties dialog box. 

First, open Control Panel, go to System Properties, then Advanced System Settings then click the button *Environment variables*

<img class="shadow" src="/img/windows-environment-variables.png">

If you have local admin rights on the machine, click the **New** button on **System variables** section. On the variable name, type *ANDROID_HOME*. On the value textbox, type the full path where you installed the Android SDK. Close the dialog box. Next, scroll down the values on System variables, try to find *PATH*, then click the *Edit* button. Go to the last character of the existing entry, then add <code class="codeblock">%ANDROID_HOME%\bin;%ANDROID_HOME%\platform-tools;%ANDROID_HOME%\tools;.</code>

Close the dialog window. To test if all the PATH is working as expected, get another cmd.exe window, then type "android", it should launch the SDK manager

Before you can deploy and test your apps, you need to setup either an android physical device or virtual device.

## OSX 

Edit **~/.bash_profile** and export the Android SDK directories

<pre class="codeblock">

export ANDROID_HOME=/Users/ted/progtools/adnroid-sdk-macosx

export PATH=$PATH:$ANDROID_HOME/platform-tools:.

export PATH=$PATH:$ANDROID_HOME/tools:.

</pre>

<div id='lst'>/.bash_profile</div>


# PHONEGAP TOOL CHAIN

**Node Package Manager**. You need the node packager manager to proceed. You can download it at the [NodeJS site](http://nodejs.org). On OSX, another way of getting **npm** is either via [HomeBrew](http://brew.sh) or [MacPorts](http://macports.org), I personally use BREW. It is a good idea to setup the BREW package manager because you will use it to get other tools that we need for PhoneGap.

When you are done with the npm installation, you can get the PhoneGap installers. Get a terminal window &mdash; cmd.exe for Windows and Terminal.app for OSX

<pre class="codeblock">

npm install -g phonegap

npm install -g cordova

</pre>

# QUICK TEST

<pre class="codeblock">

$ mkdir ~/workarea

$ cd ~/workarea

$ phonegap create first

$ cd first

$ phonegap build android

$ cd platforms

</pre>

An android project folder should have been created inside the platforms folder. This folder contains the necessary android project structure for testing and deployment.

