---
layout: androidtutorial

title: Key Concepts in Android

description: 

excerpt: 

author: Ted Hagos

lastupdate: 


tags:


categories:

---


Android applications are comprised of Java executable codes, XML files and other application resources like video, images and audio. These are all bundled together inside an .apk file.

You will write your program in the Java programming language and compile them using the  Android SDK (software development kit). When the app is compiled, it becomes an android package. An android package is an archive file with a .apk extension. Think of them like zipped files for Android.

When applications have been built and digitally signed, they can be distributed on market places like Google Play or Amazon. They don't have to be but these market places are frequented by a lot of people, your can benefit from exposure which the market places can offer. 

##1.  Architecture

Android may refer to many things, some people use it to refer to their mobile device and some others use the term to refer to the programming environment. That's fine. For our purpose, what we mean by Android is a platform which have runtime components where mobile apps can run.

This platform is special version of Linux that is optimized for mobile devices. The Linux part takes care system services e.g. network and file operations, concurrency etc. The platform includes a bunch of other
things like WebKit which is the same browser engine that powers Chrome and Safari. It also has SQLite which you can use for database programming. It has other components useful for application development, but instead of listing all of them here, I will point them out in later when we need to use them.

The one other thing to point out in the Android software stack is the framework. The framework lets us do things such as create screens, write code that runs in background, listen to some events that may happen on the mobile device (and do something about it). The platform enables us to do all these things by simply extending existing classes in the
Android SDK.

Extending classes means utilizing the inheritance mechanism of Java to reuse existing functionality. The Android development team already wrote codes to display buttons and textfields for example. All we need to do, is to reuse them, mash them up or mix it up so we can use them in our own applications.

The Android SDK is a collection of tools and code libraries. SDK is short for software development kit. You will need to download, install and configure the SDK before you can start any development work.

##2. Versions and API level

Android has been around for quite some time. It has evolved so many times and as a result, there are various versions of it.

A version number will correspond to a code name. Buyers of Android devices would probably recognize the android versions using the codename rather than the actual number. As a developer, we need to be familiar not only with both the version number and codename, we also need to know the API level.

The API level is what you will see on the Android SDK manager. You will use the SDK manager when updating your software development kit.

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="right" />

<col  class="left" />

<col  class="right" />
</colgroup>
<thead>
<tr>
<th scope="col" class="right">Version</th>
<th scope="col" class="left">Codename</th>
<th scope="col" class="right">API</th>
</tr>
</thead>

<tbody>
<tr>
<td class="right">2.2</td>
<td class="left">Froyo</td>
<td class="right">8</td>
</tr>


<tr>
<td class="right">2.3.3 - 2.3.7</td>
<td class="left">Gingerbread</td>
<td class="right">10</td>
</tr>


<tr>
<td class="right">4.0.3 - 4.0.4</td>
<td class="left">Ice Cream Sandwich</td>
<td class="right">15</td>
</tr>


<tr>
<td class="right">4.1.x</td>
<td class="left">Jelly Bean</td>
<td class="right">16</td>
</tr>


<tr>
<td class="right">4.2.x</td>
<td class="left">Jelly Bean</td>
<td class="right">17</td>
</tr>


<tr>
<td class="right">4.3</td>
<td class="left">Jelly Bean</td>
<td class="right">18</td>
</tr>


<tr>
<td class="right">4.4</td>
<td class="left">KitKat</td>
<td class="right">19</td>
</tr>
</tbody>
</table>

By the time you read this, there could be changes or additions to the Android platform. The official site of Android keeps an updated list of this info over at <https://developer.android.com/about/dashboards/index.html>. 

##3.  Fundamentals

1.  Creation of an app starts by creating an Android project. It is a simple folder that contains the Java sources, XML files, videos, audio, images etc. Depending on what IDE or tool you use, a project can be created and managed using either Ant, Maven or Gradle. These are called build tools and they are usually managed by the IDE. Most of the time, they are invisible to you
2.  Write the program logic using Java. Whether you would like to show something on the screen, listen to an event or do something in the background, Android has prebuilt classes to handle those. These prebuilt classes are part of the Android framework that lets us create rich apps by extending exisiting classes in the framework. We'll discuss Application components a bit more later
3.  The screen user interface is, usually, constructed using XML. Widgets like buttons, textfields and other UI components are declared in the XML. Things such as size, alignments and weights of each component can be declared in this file as well
4.  Most of apps are event driven. They wait for the user to enter or press something then then some processing happens. Program logic is usually written as response to an event. These codes are the ones you write using the Java language
5.  The Java source file are converted to an executable form and the XMl is flattened as a result of the compilation process. The XML is converted to byte code representation, this is what we mean by flattened
6.  If the compilation is not successful, the compiler will you what's wrong with it and you should fix it then compile again. If it compiles successfully, you will test the application by deploying it either an emulator or a real device connected to your computer

##4.  Application Components

###4.1 Activities

If you want to create a screen that can interact with the user, you can do that by creating an Activity class. It is called that because the class you will create will extend the existing Activity class that is part of the Android framework.

By extending this class, you will be able to create other components such as buttons, textfields, lists etc and contain them inside a screen. You can also react to some events such as when an incoming call interrupts the user while using your application. 

An Activity is basically a single screen that a user can see and interact with. Most applications will have more than one Activity. They have more than one screen. You can stitch Activities together using **Intents**. You can define a button on one Activity then write program logic such that when the button is clicked, it will launch another Activity. You will use Intents to launch other Activities.  

###4.2 Services

Sometimes you will need to write code that is invisible to the user. One that doesn't have a user interface. Surely you will need to launch it somehow from an Activity but once launched, the application just keeps on running. Even if the UI that launched it has already disappeared from view. A music player is such an example of this kind of app. A GPS enabled application which updates your location every now and then is another example.

If you need to build these kinds of apps, you will use **Services**. These are long running operations that are executed in the background. A Service is independent of the Activity that launched. Even if the UI screen that was used to launch the service has already died, the Service code just keeps on going.

###4.3 Content Providers

Each application runs on its own process. Its own virtual machine. This behavior of Android protects each application. If one badly written application goes wonky, it cannot bring the other running applications down. Its good for application stability. But this makes it nearly impossible for one application to access data from another. 

Content Providers solves the problem of data sharing between applications. It is possible for you to write an application and share whatever data it has with other applications. The **Contacts** and **Calendar** apps in Android are good examples of apps that have Content Providers.

Don't confuse Content Provider with your own database. If you create an application that uses a SQLite database, of course your application can access that. If, for example, you want to allow other applications to gain access to your app's data, you can build a Content Provider. Your application will make the data available to other apps using standard URIs. 

###4.4 Broadcast Receivers

Broadcast Receivers are used if you want to execute some program logic in your app as a response to events generated by either the Android system or other applications. You can, for example, inititate a database write when the phone receives an SMS message. You probably want to examine the SMS message and if it fits a certain criteria, you will record it to the database. This is one example of how to use Broadcast receivers.  

You can make your application listen to certain events. To do this, you need to register your application to listen to a specific event. Its the same concept when you subcribe to a mailing list. When there is a new mail, you get notified.

Apart from listening to broadcasted events, you can also make your application broadcast specific events. To do that, you will extend a specific Android class called the **BroadcastReceiver**.

BroadcastReceivers typically don't have user interfaces. But you can create notifications that will show up on the status bar.

###4.5 Android Manifest file

This is one of the most important parts of an Android app. The manifest is an XML file that needs be on the root folder of the application project. Every project needs one, and there can only be one per project. It needs to be named **AndroidManifest.xml**. The manifest declares lots of things like:

- the name of the application
- what kinds of components does the app have. Does it have Activities, what are their names. Does it listen to broadcast etc
- what kinds of things can it do with the mobile device? Can it access the network. The internet. Will it use the camera. Will it record a GPS location
- can other applications interact with this applcation. If so, what kinds of permission should these other applications have
- does this application use any external libraries (usually jar files that other people wrote)
- what versions of Android will this application run on. Will it run on Froyo (API level 8)

The Android manifest file is usually created by default when you start a new project. But it only provides some minimum declaration. Beyond the basic HelloWorld apps, you will need to learn how to work and manage the manifest file.

###4.6 Other Resources

Besides the programming components and the Android manifest file, your application may also include the following:

- **XML resource files** . XMLs are everywhere in Android. They are used to define screen layouts, manifest file, resource bundles etc.
- **Image Resources**. At a minimum, your app needs an icon that will appear on the Android apps menu
- **Video and Audio  Resources** .If you are building a game or a training application, your apps may contain lots of these
- **Third Party Libraries**. You include codes that other people built e.g. social media functionalities. These are included in the project in the form of jar files (Java archive)

##5.  Other ways to build Android apps

There are other ways to build an Android app. You can build apps using using languages other than Java. An app can be built using HTML, CSS, JavaScript and a middleware like the Cordova API, a good example of this is Phonegap. You can use C# to write apps and retarget the compilation to Android using a product called Xamarin. There are ways to build Android apps as well using Ruby or Python.  

There are tools or products that can build an Android app without coding or with minimal coding. MIT's App Inventor is a example of this kind of tool. There are other tools like AppyPie, MakeMeDroid and Como. These app making tools are far too many to list down here. And by the time you are reading this, some of these names could be out of business already and new app makers have taken their places. Just search Google for "android app builder no code 2014" if you happen to still be reading this text in 2015, just substitute the current year in search term.

Our focus in here, of course, is to write our app using the Java language and build it using the Android SDK.

<div id="footnotes">
<h2 class="footnotes">Footnotes: </h2>
<div id="text-footnotes">

<div class="footdef"><sup><a id="fn.1" name="fn.1" class="footnum" href="#fnr.1">1</a></sup> Uniform Resource Identifier is just a piece of string that is used to identify a resource, such as a data resource that you would like to export using a Content Provider. It can appear like this: content://yourapp/resourcename. It looks a lot like what you would type in a browser address bar, although technically, what you use in a browser is called a URL (Uniform Resource Locator). Becauase a URL specifies not only the name of the resource, it also specifies the manner on how to get the resource (http). But for all intents and purposes, a URL is also a URI.</div>


</div>
</div>
