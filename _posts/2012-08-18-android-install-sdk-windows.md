---
layout: androidtutorial

title: Dev Setup on Windows

description:

except:

categories:
- android-programming

---



1. Download the [Android SDK from android.developer.com]( http://developer.android.com/sdk/index.html ). Choose your platform. The Windows platform offers two options, a zipped file and an .EXE file (which is recommended). If you know where the EXE installer will place the Android executables, go ahead and get the EXE version. If you want to control the location of the Android files

2. Get the zipped file. Unzip the file to a user directory (so that you will not need elevated privileges to use the executable files). The user directories are usually inside **C:\\User\yourname\**. Try to remember the full path (including C:\\) of the directory where you unzipped the Android SDK, this will be your ANDROID_HOME


3. Get a command line (cmd.exe) CD to your ANDROID-HOME/tools, launch the *android* executable. This will launch the Android SDK Manager. The android SDK needs an internet connection. It connects to the android.developer.com website and checks which SDK levels are installed in your machine. Naturally, if you have installed the SDK just now, there won't be much. Choose the API levels that you would like to install in your machine.

Each version or platform of Android (Froyo, Gingerbread etc) is a numbered API level. If you want to install the Froyo SDK, for example, then check the box next to API level 8 (Android version 2.2). If you have really fast internet connection and you are not sure which API to check, check them all---be warned though, you will wait for a long time for it to finish.


4. Include the android tools and platform tools in your shell's path. You will need it if you want to work with android using the command line. The two folders of interest are **ANDROID-HOME/tools** and **ANDROID-HOME/platform-tools**

There are two ways to set the PATH in Windows. The first method is via the command line (cmd.exe).

<pre class='codeblock'> 

  SET ANDROID_HOME=c:\>path\where\you\installed\android\
  SET PATH=%PATH%;%ANDROID_HOME%\bin;%ANDROID_HOME%\platform-tools;%ANDROID_HOME%\tools;.

</pre>

You will need to run those commands though, each time you will open a new CMD.exe. Those settings are not remembered by the shell.

If you want to permanently set these PATHS, you need to do it in the System Properties dialog box. First, open Control Panel, go to System Properties, then Advanced System Settings then click the button *Environment variables*

<img class="small" src="/img/windows-environment-variables.png">


If you have local admin rights on the machine, click the *New* button on *System variables* section. On the variable name, type *ANDROID_HOME*. On the value textbox, type the full path where you installed the Android SDK. Close the dialog box. Next, scroll down the values on System variables, try to find *PATH*, then click the *Edit* button. Go to the last character of the existing entry, then add <code class="codeblock">%ANDROID_HOME%\bin;%ANDROID_HOME%\platform-tools;%ANDROID_HOME%\tools;.</code>

Close the dialog window. To test if all the PATH is working as expected, get another cmd.exe window, then type "android", it should launch the SDK manager



