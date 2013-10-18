---
layout: androidtutorial

title: Creating A Project

description: 

excerpt: To create an android project, you will need a bunch of XML files, a couple of resources files, some make files and of course, the Java source code for your app. It may sound like a lot to do for a simple and useless Hello World app--it is--but most of the boiler-plate code for setting up a project can be taken cared of by a good IDE (Eclipse, NetBeans, IntelliJ or what have you, in our case, we will use the good old CLI). 

categories:
- android-programming

---



The *Hello World* application in android is very different from what you might remember when you created your first app in Java. Back then, you only needed a single source file where everything you need to output something to the screen was contained. The Hello World application in android requires full project. 

An android app will not run on your desktop, in fact, even just to test it, you will need an emulator. Android apps were meant to run on devices, not on desktops. The hardware architecture of mobile devices are starkly different from desktop PCs. This disparity is part of the reason why coding for android is contrastly different from coding a simple Java app.  

To create an android project, you will need a bunch of XML files, a couple of resources files, some make files and of course, the Java source code for your app. It may sound like a lot to do for a simple and useless Hello World app--it is--but most of the boiler-plate code for setting up a project can be taken cared of by a good IDE (Eclipse, NetBeans, IntelliJ or what have you, in our case, we will use the good old CLI). 

The android SDK came equipped with scripts that will help you create, debug, test and deploy android projects. We will use some of those tools in this tutorial. Make sure you have [properly installed the android SDK] (/installing-android-sdk/) before proceeding.

## Hello World, our first project 

1. Choose a working directory for your project. Open a terminal (Terminal.app on OSX, cmd on Windows and xterm, gnome-terminal etc on Linux)

2. You might want to put this project under source control. This is completely optional at this point, but I encourage you to start getting into the habit of putting your dev works under source control, it will save you a lot of heartaches in the future. You can still proceed with the tutorial even if you don't have source control though

3. Use the <span class="boxed">android create project</span> command to setup the project. On the terminal, type

	android create project --target 8 path helloworld --activity Hello --package com.thelogbox

The **android create project** command is available if you have properly setup your PATH variables. If you get an error such as "Bad command or filename" or "command not found" or something to that effect, that is your just OS telling you that the <span class="boxed">android</span> executable is not properly setup. Go back to [installing the android SDK](/installing-android-sdk/)

There's quite a bit going on in here, so let's slow down and take look what those flags mean. 

**--target** expects an integer value. This value stands for a unique API level for a specific android version. In our example above, *level 8* was specified because I intend to target android 2.2 (Froyo). Gingerbread will have a different value, Honeycomb will have a different one as well. If you want to see all the possible targets, you can type <span class="boxed">android list targets</span>

**--path** specifies the name of top level folder for your project. Think of it as a project folder. It will be the root directory of your project

**--activitity** will cause our project to create a class that extends from the the Activity class. An Activity is commonly used if we need a user-facing class. Think of it as UI 2 mechanism in android. In our example, *--activity Hello* means that our project will have class named Hello and is a child class of the base class Activity

**--package** an android project will be comprised of various XML files, resource files and Java source files. The Java source files will be stored using the package directive that we specify in the option. The package directive will only affect the location of Java source files, it will not affect the location and storage of the other android resources (i.e. XML files)

If the command completed successfully, you are supposed to have a directory similar to this one

What the *android create project* generated

	├── AndroidManifest.xml
	├── ant.properties
	├── bin
	├── build.xml
	├── libs
	├── local.properties
	├── proguard-project.txt
	├── project.properties
	├── res
	│   ├── layout
	│   │   └── main.xml
	│   └── values
	│       └── strings.xml
	└── src
 	   └── com
 	       └── thelogbox
 	           └── Hello.java



It's quite a mouthful and probably enough to stop a beginning programmer to his tracks and pack up, but don't do that. We will explore each and everyone of those files and folders in the succeeding tutorials. You can safely ignore them for now. We are just trying to get a feel of how to create a project---remember?

For now, just play around the project. Open the generated files--don't worry, they are all text files--see what they look like. They might fly over your head at this point, that's okay, that's expected. 

The **android create project** script actually generated a Java class source file for us, the *Hello.java*. This is an Activity class, for now just think of an Activity as some sort of window---it is more than that actually, but for now just think of it like a window so we don't have to deal with the complications.  You would normally use an Activity class if you want **"the user to do something"**. In this case, we want to show him a simple "Hello World" message. 


