---
layout: androidtutorial

title: Setting Up the Development Environment

description: Simple steps to prepare a workstation for Android Development

excerpt:

tags:
- Programming
- Environment 

---



1. Download the [Android SDK from android.developer.com]( http://developer.android.com/sdk/index.html ). Choose your platform. In my case, it was a zipped file

2. Place the unzipped file somewhere in your directories. It is best not to put in a directory that contains white space. I placed mine inside /Users/myname/prgtools/android-sdk (this is your ANDROID-HOME)

3. Go to your ANDROID-HOME/tools, launch the  <code class="codeblock">android</code> executable. This will launch the Android SDK Manager. The android SDK needs an internet connection. It connects to the android.developer.com website and checks which SDK levels are installed in your machine. Naturally, if you have installed the SDK, there won't be much. Choose the API levels that you would like to install in your machine.

Each version or platform of Android (Froyo, Gingerbread etc) is a numbered API level. If you want to install the Froyo SDK, for example, then check the box next to API level 8 (Android version 2.2). If you have really fast internet connection and you are not sure which API to check, check them all---be warned though, you will wait for a long time for it to finish.

4. Include the android tools and platform tools in your shell's path. You will need it if you want to work with android using the command line. The two folders of interest are **ANDROID-HOME/tools** and **ANDROID-HOME/platform-tools**

In OSX, you can add the following entries in th *~/.bash_profile*


~~~
export ANDROID_HOME=/path/to/android-sdk
export PATH=$PATH:$ANDROID_HOME/tools:.
export PATH=$PATH:$ANDROID_HOME/platform-tools:.
~~~


In Linux, add the following lines to *~/.bashrc*, if you are using bash


~~~
export ANDROID_HOME=/path/to/android-sdk
export PATH=$PATH:$ANDROID_HOME/tools:.
export PATH=$PATH:$ANDROID_HOME/platform-tools:.
~~~



Close the terminal, then launch it again in order to reflect the changes we made to the PATH variable. Try to type **android** from the command line. If it launches the android SDK manager, then you have set the android paths correctly.

If you are using Eclipse, see the steps on [how to configure android for eclipse](/android-install-eclipse-plugin/)


