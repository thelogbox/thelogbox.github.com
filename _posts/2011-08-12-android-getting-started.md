---
layout: androidtutorial

title: Getting Started

description: Create, build and deploy your first Android application

excerpt: 

tags:
- HelloWorld
- Activity
- Compilation
- Build

---

One of the best, if not the best way to learn something is to start doing it. Get your feet wet. Your hands dirty, so to speak.

What will happen in the next couple of minutes, maybe hours is  that you will read some code, some theories, some explanations. Not all of them will make sense, not all at once. That's okay. You're not alone on that one. Most people who are not at genius level go through that learning experience. There is confusion, maybe even frustration. You cannot dodge that, that's part of the learning experience. Recognizing that difficulty, I thought it might serve us better to start with really simple constructions, they maybe useless pieces of code, something you won't even use in production. These sample codes may not be industrial strength, but they are not meant to be. Simple examples ease our brain into the subject. That's the goal.

We will still do the **Hello World** example, not really to observe the time honoured tradition of the *C Programming Language*, but because it is the simplest example that we first have to hurdle.

The Hello World in Android is way more involved than simply creating a basic class, defining a static main() and invoking the out.println(). It is way more involved than that. You will need to create an *Activity* object, override its *onCreate()* method, invoke the *ant* build tool, define an AVD (Android Virtual Device) and install the *.apk* (Android Package) either into the AVD or a physical Android Device. That's how messy the **Hello World** program is in Android. Be mindful that you are not writing desktop programs, you are writing mobile applications. You maybe familiar with the language &mdash; Java &mdash; but the tools and programming workflow are different.

# The Hello World project

We need to create a project. An Android project is a collection of files which are structured and nested in a very specific way so that the build tools can work with them properly. This is the reason why it is not advisable to build the structure by hand, manually. Use the SDK tools.

<pre class="codeblock">

mkdir workarea

cd workarea

android create project --target 8 path first --activity First --package com.thelogbox 

</pre>

If the Android SDK tools were properly installed, that last command should complete without problems and it would have created a folder named *first* on the current directory. If you get an error such as *Bad command or filename* or *command not found* or something to that effect, that is your just OS telling you that the <code class="codeblock">android</code> executable is not properly setup. Check your installation and configuration. See if the *android tools* and *android platform tools* are in your *SYSTEM PATH*.

The folder structure of an android project is shown below

<img class="default" src="/img/android-project-structure.png">
<div id='lst'>Folder Structure of an Android project</div>

# How to create a project

**--target** expects an integer value. This value stands for a unique API level for a specific android version. In our example above, level 8 was specified because I intend to target android 2.2 (Froyo). Gingerbread will have a different value, Honeycomb, ICS and Jekllybean will have a different ones as well. 

<aside>
If you want to see all the possible targets, you can type <code class="codeblock">android list targets</code>
</aside>

**--path** specifies the name of top level folder for your project. Think of it as a project folder. It will be the root directory of your project

**--activity** will cause our project to create a class that extends from the the Activity class. An Activity is commonly used if we need a user-facing class. Think of it as UI 2 mechanism in android. In our example, <code class="codeblock">--activity First</code> means that our project will have class named First and is a child class of the base class Activity

**--package** an android project will be comprised of various XML files, resource files and Java source files. The Java source files will be stored using the package directive that we specify in the option. The package directive will only affect the location of Java source files, it will not affect the location and storage of the other android resources (i.e. XML files)

# How to test and run

On the command terminal, make sure you are at root directory of the project, run the command <code class="codeblock">ant debug install</code>. That should compile, build then install the empty project we just created.

Just in case you wondered why use <code class="codeblock">ant debug install</code> instead of simply <code class="codeblock">ant install</code>. We used the *debug target* so that we can side step Android's requirement to setup security keys and signing our applications with that key. Let's deal with the application signing later on when we get to deploying and releasing our mobile app into the wild.

The *debug target* of ANT generated a debug key that served as the security key for our app. This is good enough for now because we are just trying to get our feet wet. If you release your real app, you should generate real security keys and signature.

You should see a bunch of scrolling echo messages in the terminal. Look for a message (right towards the end) that says something like *BUILD SUCCESSFUL*. It should be successful for now because we haven't messed around with it yet. There is no reason at this point for the build to fail. 

Right after the compilation process, there are lots of changes within our project directory. Quite noticeably, there are now lots of files inside the **bin** and **gen** folders. Somewhere in these jungle lies the executables that we can actually deploy to a real device &mdash; but save that for later. Right now, the goal is to just be comfortable with the project creation, compilation and deployment process. 







