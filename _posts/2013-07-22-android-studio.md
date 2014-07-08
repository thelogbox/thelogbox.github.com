---
layout: androidtutorial

title: Using Android Studio

description: Use the Android Studio for mobile programming

excerpt: Updated tutorial for Android Programming. The tutorial uses the Android Studio for development. This is a shortened version of a longer tutorial. The full tutorial is available to class participants.

tags:
- IDE


---


We will use the *Android Studio* for these examples. Android Studio is an IDE specifically designed for Android Development. It does the things that Eclipse + ADT does. It basically combined all the tools you use when working on an Android app.

It is based on IntelliJ, so you know it has pedigree. You don't need to switch to this IDE if you already are very comfortable with your current tool. Besides, at the time of writing, Android Studio is *Early Access* release. Which means it has problems. You can check it out, but you probably won't want to replace your primary development tool with it.

You can find the [installer for Android Studio here](http://developer.android.com/sdk/installing/studio.html). Once you have completed the download and ran the installer, you can launch it to create the first project.

Choose *New Project*

<img class="shadow" src="/img/androidstudio-1.png">

If you change the *Application Name*, you will notice that the other fields are adjusted too. If you are happy with the *Project Location*, you can keep the default folder setting. 

The *minimum required SDK* means that your app is guaranteed to run on that android version. 

<img class="shadow" src="/img/androidstudio-2.png">

If you checked the *Create custom launcher icon* in the last screen, this screen will appear so you can tweak the settings a bit more.

<img class="shadow" src="/img/androidstudio-3.png">

If you chose to include an Activity in your project, you can choose which kind of Activity in this screen. For our purpose, choose a blank activity.

<img class="shadow" src="/img/androidstudio-4.png">

The activity name in this screen will be the name of a Java class which *extends* the Android Activity. class. The *layout_name* is the name of the generated xml in */res/layout/*. You can change the appearance of your main Activity in this XML file.

<img class="shadow" src="/img/androidstudio-5.png">

Once you have completed the steps for creating a new project, *Gradle* kicks in to high gear to create your project. Gradle is build system, like Maven or ANT. Don't worry about the build system, this will be mostly invisible to you. You can mess with it later on when you are more familiar with Android Development.


<img class="shadow" src="/img/androidstudio-6.png">


You need to be connected to the internet when Gradle kicks in. It may download some files it needs to build your Android app. This might also take a while.

<img class="shadow" src="/img/androidstudio-7.png">


Click the *Project* tab on the left side of the IDE to reveal the project structure. You can see the name of the project on the left side. You can drill down on the node to reveal the Java source file for your first Activity class.


We are not going to make any modifications on the project for now. We just want to try it out. If you want to see this app on a device, plug an android device in your PC. Make sure that the device is properly setup for development &mdash; ensure that *USB Debugging* is enabled on it. 

Click the *Run* button. It's the green arrow on the top section of the IDE

<img class="shadow" src="/img/androidstudio-8.png">

You should be able to see the connected device in this screen. If you don't see it, try quitting the Android Studio IDE and unplug/plug the Android device again. 

<img class="shadow" src="/img/androidstudio-9.png">

You can see the progress of the compilation and installation on watch window of the IDE


<img class="shadow" src="/img/androidstudio-10.png">

You can use the built-in Android Device monitor (which includes DDMS) to view all application and system logs.


<img class="small" src="/img/first-1.png">

At this point, you should see the *First* application on your android device

<img class="small" src="/img/first-2.png">

It's a very un-exciting, uninspired and beaten down to death *Hello World*.

