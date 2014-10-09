---
layout: androidtutorial

title: Android Project Creation CLI
author: Ted Hagos

tags:
categories:
description:

---


You need a bunch of files to build a project. XML files are used for both configuration and defining screens. Images and other resources like video and audio may also need to be included, depending on the kind of project you are building. Last and most importantly will be the Java source files where you will write the program logic. All of these things come together inside an Android project. 

The SDK includes executable tools and utilities that you can use to create and manage android projects. If you properly installed the SDK and included the folders **tools** and **platform-tools** to your system path, you can start an Android project using the **android create project** command.  

    android create project --target 8
                           --path Hello
                           --package com.thelogbox
                           --activity Main

The command is meant to be ran on a terminal window like xterm, Terminal.app or cmd.exe. You will type them in one continuous line, not like how you see it here. They are written on 4 lines for formatting purposes only. You need to pass the four options shown above as a minimum in order to create a project, they don't have to be in the order you see them here but they all need to be there.

The **&#x2013;target** option tells the tool what Android version will your app run on. It expects an integer argument. The number 8 in our example means we are targetting the Froyo version of Android. The number stands for an API level.

The **&#x2013;path** option dictates the name of the folder where all your programming assets e.g. source, xml and images will be located. In our example, we would like to create a folder named "Hello". This is where we will store all the things we need to build the project.

The **&#x2013;package** option is what Android will use to organize the Java source file. If you are familiar with Java packages, it is exactly what this option means. The package name will also be used if you decide to sell your applications to market places like Google Play or Amazon. It becomes your namespace. The package name is usually the name of your website in reverse notation.

The **&#x2013;activity** option instructs the tool to automatically create a class that extends the Activity class of the Android framework 

# Errors you might have encountered

-   **Command not found or Bad command or file name**. The command **android** cannot be found within the places where your shell looks for executable file. Either you have not included the folders **tools** and **platform-tools** of the Android SDK into your system path. Either that or you made some spelling mistakes when you included them in the path.
-   **Android create project command won't complete**. This is most likely a spelling error when typing the commands as shown earlier. Take care that you use a double dash when specifying the option. There is no space between the double dash and the option. Take note that there is a space between the option and the argument


<div class="video-container">
<iframe width="420" height="315" src="//www.youtube.com/embed/r2oPAHUY1MY" frameborder="0" modestbranding="0" showinfo="0" vq="hd720" rel="0" allowfullscreen></iframe>
</div>
