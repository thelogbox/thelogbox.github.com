---
layout: androidtutorial

title: Windows setup

description: Setup your Android Development Environment in Windows 

except:

tags:
- Windows
- SDK

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

This chapter will guide you through the setup process of an Android development environment.  There are a few things that you must have before you proceed any further. I am assuming that you already have setup JDK 1.5 or 1.6 and Apache Ant.

I'm assuming further that these tools are properly resolvable from any terminal window. That means the executable files are already part of the system path.

If you have JDK and Apache ANT already, you can proceed with the android sdk setup.

The android sdk setup requires that you download, install and configure from setup files. The configuration is where it sometimes gets messy and confusing especially for beginners. But these things are easily managed by simply following instructions. When the instructions on these pages fail you, I'm sure you will Google for them. The official site of android can be found [here](http://developer.android.com/sdk/index.html) and [here](http://developer.android.com/sdk/index.html). 

If that is still not clear enough, you can look at the [setup instructions I wrote for my students here](https://docs.google.com/document/d/1AS8OoJJnRIIyEvi8lG6I8iF0PEt1-UolvQGtVevrJg4/edit?usp=sharing)

**Download** the installer from [Android SDK from android.developer.com]( http://developer.android.com/sdk/index.html ). Choose your platform. The Windows platform offers two options, a zipped file and an .EXE file (which is recommended). If you know where the EXE installer will place the Android executables, go ahead and get the EXE version. If you want to control the location of the Android files

**Unzip** the downloaded file to a user directory (so that you will not need elevated privileges to use the executable files). The user directories are usually inside 

~~~
C:\User\yourname\ 
~~~

<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- 468pxby60banner -->
<ins class="adsbygoogle"
     style="display:inline-block;width:468px;height:60px"
     data-ad-client="ca-pub-4627957463175380"
     data-ad-slot="5760679882"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>

Try to remember the full path of the directory where you unzipped the Android SDK, from hereon forward, we will refer to that directory as **ANDROID_HOME**

**Get a terminal window**, launch cmd.exe. Go to the **ANDROID-HOME**/tools directory, then run the **android** command. This will launch the Android SDK Manager windows. 

The SDK manager needs an internet connection. It connects to the android.developer.com website and checks which SDK levels are installed in your machine. Naturally, if you have installed the SDK just now, there won't be much. Choose the API levels that you would like to install in your machine.

Each version or platform of Android (Froyo, Gingerbread etc) is a numbered API level. If you want to install the Froyo SDK, for example, then check the box next to API level 8 (Android version 2.2). If you have really fast internet connection and you are not sure which API to check, check them all. This will take some time to complete. 

**Update your system path**. Include the **ANDROID_HOME**/android tools and **ANDROID_HOME**/platform-tools folders in the system path. You will need it if you want to work with android using the command line.

There are two ways to set the PATH in Windows. The first method is via the command line (cmd.exe).

~~~
SET ANDROID_HOME=c:\>path\where\you\installed\android\
SET PATH=%PATH%;%ANDROID_HOME%\bin;%ANDROID_HOME%\platform-tools;%ANDROID_HOME%\tools;.
~~~

You will run these commands each time you will open a new terminal window. Those settings are not remembered by the shell.

If you want to permanently set the PATH to android tools, you need to do it in the System Properties dialog box. 

First, open Control Panel, go to System Properties, then Advanced System Settings then click the button **Environment variables**

<img class="shadow" src="/img/windows-environment-variables.png">

<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- 468pxby60banner -->
<ins class="adsbygoogle"
     style="display:inline-block;width:468px;height:60px"
     data-ad-client="ca-pub-4627957463175380"
     data-ad-slot="5760679882"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>


If you have local admin rights on the machine, click the **New** button on **System variables** section. On the variable name, type *ANDROID_HOME*. On the value textbox, type the full path where you installed the Android SDK. Close the dialog box. Next, scroll down the values on System variables, try to find **PATH**, then click the **Edit** button. Go to the last character of the existing entry, then append the following

~~~
%ANDROID_HOME%\bin;%ANDROID_HOME%\platform-tools;%ANDROID_HOME%\tools;.
~~~

Close the dialog window. To test if all the PATH is working as expected, get another cmd.exe window, then type "android", it should launch the SDK manager

Before you can deploy and test your apps, you need to setup either an android physical device or virtual device.


