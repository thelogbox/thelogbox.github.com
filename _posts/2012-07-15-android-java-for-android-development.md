---
layout: androidtutorial

title: How Much Java Do I need for Android Programming

description: 

excerpt: 

tags:
- Readiness
- Java

---

Before diving into Android programming, there are a couple of skills you might want to look at. It is possible to simply jump into programming, build some basic screens by copying example codes from the internet or from other programmers. But you cannot go to the deep end. When you find yourself neckdeep in the not-so-trivial parts of Android programming and you feel stuck, that's probably because you haven't covered some bases.

The ideal set of skills to bring into Android development includes experience in AWT/Swing, JDBC, Collections, Network and Thread programming and a couple of others. But not many people will have this. For one reason, AWT and Swing went out of favor a long time ago. Most Java programmers right now have experience on web development but not desktop. 

##1. Object Oriented Concepts

The Android framework uses OOP heavily. You need to be comfortable with the idiomatic use of things like class/interface inheritance, polymorphism etc. Even the humble Hello World application in most Android textbooks involves the use inheritance. 

##2. Java fundamentals

You will need to be familiar with programming fundamentals in Java. Even if Android uses a different VM to run the apps, the language used for native apps development is Java. The more familiarity you have with basic programming concepts in Java, the better. You should at least know the concept of variables, constants, branching and looping, packaging and scope visibility, basic I/O and file persistence.

##3. Java Collections

Beyond simple variables, you will need some skills to handle collections of data. A basic familiarity with rudimentary data structures like arrays, maps and sets will be essential.

##4. Java Event model

Android applications are heavy on user interaction. For the most basic applications, you might be able to get away by simply knowing how to put the click handler on XML file. But for other gestures like long clicks, swipe etc, you will need to write Java codes to handle the event. The Java event model uses listeners and callbacks quite a lot.

##5. XML

A passing familiarity wih XML structures and validation rules should take you quite far in Android programming. You don't need to work much with XML programmatically. Your usual need for XML will arise when you define layouts and when configuring permissions for the app. If you have coded HTML before without using WYSIWYG tools, you should be fine.

##6. SQL

Some, if not most, of the applications you will make will need to store data. Some data might be simple and can be stored either via the preferences or the SD card. But some might need the facility of a relational database. The Android runtime includes the SQLite database. You will talk to it using the Structured Query Language. SQL is not a difficult language, its quite enjoyable to learn actually because of its declarative nature. It is almost English like.

##7. Build tools

An Android project is a compilation of various files e.g. XML, image resources, compiled byte codes, source codes etc. Getting all these resources to stick and work together cannot be done by hand, well actually it can be, but it will not be practical. That is why even the barebones SDK requires the use Apache Ant to help in compiling, building and deploying your applications. 

##8. Command line experience

Even if you plan to use a full blown IDE like Eclipse, Android Studio or NetBeans, its not a bad idea to invest some time getting some skills on the command line. They might take a while longer to learn than their GUI counterparts but the effort will pay off. When you run into some problems on the IDE, your CLI skills might save you. You don't need to be a ninja on the terminal, you can get by with some basics e.g. creating and deleting files, moving around directories, invoking ant scripts, using adb etc.
