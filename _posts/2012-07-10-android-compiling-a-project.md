---
layout: androidtutorial

title: Compiling

description:

except:

categories:
- android-programming

---



Gone are the days when we can simply compile a practice project with simple <span class="boxed">javac</span>, then fire the the JRE to appreciate our code at runtime. A lot of the Java projects have fallen victim to unnatural stretching because of increasing complexity---android projects are not immune to this stretching. As the complexity of Java projects got higher and higher, we coped with tools and frameworks. One of these tools is **ant**. 

Ant allows us to tame the complexity of project builds. Ant is a widely used build tool for Java projects, I'm willing to bet that you have seen or used this sometime in the past.  

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


Notice the **build.xml** on the root folder of our project? That is an ant build file. The project creation script generated that for a reason, we are supposed to use ant to compile, build and deploy our android projects. 

## Compiling the android project

1. If you haven't closed the terminal yet, go to it. If you have closed it, open the terminal again and navigate to the root folder of the android project

2. Try typing <span class="boxed">ant</span> on the terminal. It should echo a bunch of possible targets. We will use the **debug** target to build our android app. 

We will use the debug target so that we can side step android's requirement to setup security keys and signing our applications with that key. Let's deal with the application signing later on when we get to deploying and releasing our mobile app in the wild.

If we use the **debug** target, ant will generate a debug key that will serve as the security key for our app. This is good enough for now because we are just fooling around. Compile the app by typing

	$ ant debug

You should see a bunch of scrolling echo messages in the terminal. Look for a message (right towards the end) that says something like *BUILD SUCCESSFUL*. It should be successful for now because we haven't messed around with it yet. There is no reason at this point for the build to fail. 

	.
	├── AndroidManifest.xml
	├── ant.properties
	├── bin
	│   ├── AndroidManifest.xml
	│   ├── AndroidManifest.xml.d
	│   ├── Hello-debug-unaligned.apk
	│   ├── Hello-debug-unaligned.apk.d
	│   ├── Hello-debug.apk
	│   ├── Hello.ap_
	│   ├── Hello.ap_.d
	│   ├── build.prop
	│   ├── classes
	│   │   └── com
	│   │       └── thelogbox
	│   │           ├── BuildConfig.class
	│   │           ├── Hello.class
	│   │           ├── R$attr.class
	│   │           ├── R$layout.class
	│   │           ├── R$string.class
	│   │           └── R.class
	│   ├── classes.dex
	│   ├── classes.dex.d
	│   ├── jarlist.cache
	│   ├── proguard.txt
	│   └── res
	├── build.xml
	├── gen
	│   ├── R.java.d
	│   └── com
	│       └── thelogbox
	│           ├── BuildConfig.java
	│           └── R.java
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

	15 directories, 30 files

Right after the compilation process, there are lots of changes within our project directory. Quite noticeably, there are now lots of files inside the **bin** and **gen** folders. Somewhere in these jungle lies the executables that we can actually deploy to a real device---but save that for later. Right now, the goal is to just be comfortable with the compilation process.

In case you encounter a "Cannot find build.xml" error, take a look at your SDK setup. This is usually a config error on the *local.properties* file. [Look here for details of the error](/cannot-find-buildxml/)











