---
layout: androidtutorial

title: Am I Ready for Android Programming

description:

except:

categories:
- android-programming

---



Android programming requires a couple of things, chief among them is your knowledge of the Java programming language. You don't need to cover all the knowledge base of Java because android applications are not made exactly the same way as mainstream Java apps. You wouldn't code an android app the same way you would code a web app, the android app would use a different set of libraries and a different set of tech stack.  

To (quickly) check your *android dev readiness*, you should be able to answer the following questions:

1. What do you use *@Override* annotation for?
2. Why would you use an anonymous inner class for event handling?
3. The *extends* keyword is used to inherit from a class while the *implements* keyword is used for what?
4. A *static* member belongs to what? An *instance* member belongs to what?
5. What is the difference between *Runnable* and *Thread*?
6. When is *finalize()* method called, and who calls it?
7. When will you use the *addActionListener()* method? Where do you usually use it?

These are pretty easy for an experienced Java programmer, if you were able to answer the above questions with confidence, you should be ready to dive into android programming.  

## But I am C# programmer

It's nice to know that you are interested in android, I would have thought that the logical step forward is Windows 8 mobile programming (maybe you are also doing that but are curious with android).  

You will not struggle a lot because Java and C# are actually more similar than they are different. You already are indoctrinated on OOP, know the difference between classes and objects and have the coded the basics of UI programming. 

You will miss Visual Studio, especially the GUI builder. Yes there are GUI builders for android but they are not to the same level of ease like VS. You will be alright and will probably coast through it. 

## But I am PHP web programmer

You will need a basic Java background. Programming native apps for android is more akin to developing desktop apps rather than web apps.  

To handle events in desktop apps, familiarity with the call-back concept is required (delegates for C# devs), as a web programmer you probably did not have a lot of chances to code this way. Web apps use the request-response mechanism of HTTP to handle events. 


# Getting ready for android development 

1. Install the android sdk. I put up a [small set of instructions here](/installing-android-sdk/). You must have installed a Java Development (JDK 1.5 or higher) enviroment before you install the android SDK 
2. Get a terminal window (Terminal.app if you're on a Mac, xterm or gnome-terminal on Linux and cmd on Windows)
3. Fire up the android SDK manager by typing **android**
4. Check your internet connection, you will need it to download the SDK tools and APIs
5. Select the API levels and the tools that you want to download. IF you want develop against android Gingerbread, you will select at a minimum the following **a) SDK tools b) platform-tools 3) Android 2.3.3**
6. Create an AVD (Android Virtual Device). You will need this to deploy and test your android applications. A better idea is to actually buy a (cheap) android physical device. The AVD is excruciatingly and painfully slow
7. You can develop using Eclipse, in which case you need to download the Eclipse ADT. If you will use the CLI (command line) then you are already set.

Next steps is to either get a book on android dev or follow the examples on [developer.android.com/training](http://developer.android.com/training/index.html) or maybe [attend an android workshop](/training-android-programming/) or all of the above. While you are deciding what to do next, you might want to read [A study plan for learning android programming](/blog-studying-and-practicing-android/)

Happy coding.



