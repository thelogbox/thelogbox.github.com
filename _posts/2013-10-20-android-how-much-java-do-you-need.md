---
layout: androidtutorial

title: Theoretical Minimum

description: Before you dive into Android Programming, know how much Java you really do need.

excerpt: 

tags:
- Java
- Requisite

---

<aside>
This document is no longer maintained. Go to <a href="/android/android-what-you-need-to-know-before">What you need to know before diving into Android</a>
</aside>

A list of things you need get a handle on before diving into Android programming.

- *Inheritance*. Knowledge of OOP is required not only in Android. You need to be very comfortable with this idiom or you will not go very far in Android programming. The most basic applications requires that you create an Activity class &mdash; that means you will create a class that inherits from android.app.Activity. You must be very familiar with the rules and characteristics of Java Inheritance. Java uses both *interface* and *class* inheritance. You need to understand both
- *Polymorphism*. Inheriting from android.app.Activity is one of the most fundamental skill you must have. Second to that is your ability to understand why you need to *override* some of its methods. Your knowledge of Polymorphism and how it is used in the Java language is part of a theoretical minimum for Android Programming. 
- *Callbacks*. Event handling is common place in many mobile apps. Beginning programmers maybe able to handle events without knowing callbacks &mdash; using only the XML files to hook the events &mdash; but you will not get far with this technique. The events you can handle without programmatic techniques are very limited. If I am not mistaken, it is only the *click* event. Modern mobile applications uses gestures, long clicks etc. Those needs to be handled programmatically. You need to know how to use the **Listeners** in Android.
- *XML*. This is easy and should not be much of a trouble. Even beginning programmers can handle this without breaking a sweat. Android uses XML extensively &mdash; more than I prefer, but I digress. Android uses this to define UIs and maintain its most important configurations. You need to know the basic rules and anatomy of an XML file.
- *Java fundamentals*. The usual Java stuff; primitive data types, objects and classes, flow of control, exception handling, overloading, access control, input/output, classes on the util package etc.
- *Database programming*. Basic SQL so you can CREATE, READ, UPDATE AND DELETE records. The Android way of database programming will feel a bit different than the usual JDBC, but that learning curve is not much trouble. It can be handled with minimum sweat. Android uses SQLite3, so if you will practice for Android, get acquainted with SQLite. 
- *Network programming*. Learn the basics of HttpClient. Going a bit deeper on socket programming can't hurt either. A mobile application is not always an offline application. Times are changing. Applications are getting more connected and consumes cloud-based services. Your familiarity with TCP and associated technologies will go a long way.
- *REST*. Web Services are shifting more and more to RESTful style. Get some familiarity with the associated technologies and idioms of this architecture. This may not be core Java, and in fact borders a lot on JavaScript. JSON (JavaScript Object Notation) is used heavily on RESTful apps.
- *Data structures*. Know the basics of an *array* and the *Array* class. That's the start. Go deeper with the other collection classes of Java. Know how to handle hash maps, vectors etc. 
- *Threads*. Modern devices are running on 4 cores. Android can take advantage of multiple cores. You need to know how to execute your code in the background, asynchronously.
- *Logging*. Old school debugging using printf and System.out will still be useful. But get some familiarity using Log classes. Be mindful that Android development is starkly different from Desktop or Web programming. Your codes will run on a device, not in your PC. The primary interface with the runtime and debug environment is Android's adb and ddms &mdash; short for android debugger and dalvik device monitor service, which has been replaced by the **monitor** tool now.
- *Tool chain*. You need to be familiar with the mainstream tools that Java programmer's use. If you will not use the IDEs such as Eclipse, Netbeans or Android Studio, you need to be well acquainted with Apache ANT. Android uses ANT for builds.
