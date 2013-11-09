---
layout: androidtutorial

title: Background Info

description: A short history of the Android mobile platform

except:

tags:
- history

categories:
- Android

---


This section is probably the least interesting of all. I would guess that only programming instructors will leaf through these pages so we will keep it short. The section however, contains a bit more than history. It also discusses some foundational tech structure of Android, in that regard, I still suggest to read through it so that you can appreciate some architectural information about the platform.

#  Short History

Andy Rubin led a small startup team sometime in 2003. They were building a software that could power a smart phone. Google took notice of it and acquired Android Inc. The first attempts of Android were not very impressive but phone manufacturers took notice and jumped into the bandwagon.

Shortly thereafer, 200,000 android devices were being activated on a daily basis (at the time of writing, over half million android devices are activated each day). The small-ish mobile phone software began to make waves.

Android's snowball noticeably gained momentum sometime in 2008 - 2009---this is the time they began using sweet snack monikers on each version of Android; it has been unstoppable since then.

- **2003** - Android Inc., was founded by Andy Rubin
- **2005** - Android Inc was Acquired by Google*
- **2008** - version 1.0
- **2009** - version 1.1 
- **2009** - v1.5 (CupCake), v1.6 (Donut)
- **2009** - v2.0/2.1 (Eclair)
- **2010** - v2.2 (Froyo), v2.3 (GingerBread)
- **2011** - v3.0 (HoneyComb)
- **2011** - v4.0 (Ice Cream Sandwich)
- **2012** - v4.1 (Jelly Bean)

An article about Andy Rubin and Android, titled [Android Invasion](http://www.thedailybeast.com/newsweek/2010/10/03/how-android-is-transforming-mobile-computing.html) appeared on a NewsWeek article sometime in 2010. 

# Technology Stack

The Android is made up of a slew of tech but the most visible ones are *Linux* and *Java*. It is a complete operating system and it provides a container that can support rich applications. 

<img  src="/img/android-architecture.png" style="border: 1px solid gray">
<div id='lst'>Fig 1: Android Architecture</div>

Under the hood of Android is Linux. It was chosen for many reasons, but primarily because of it's stability. Out of the box, Android comes with a couple of useful libraries like *SQLite* for database programming, *OpenGL* for graphics, *Webkit* (the browser engine that power Safari and Chrome) and *SSL* for security.

The Android runtime consists of (some) core Java libraries and the Dalvik VM. The runtime is not the same JRE/JDK that you have on your desktop. This runtime has a subset of Apache Harmony which is an open source, free Java implementation from the Apache Software Foundation. The politics of why Android did not use the Oracle reference implementation of the JDK will not be part of this tutorial, I am sure you can find that information somewhere else.

Android also comes packaged with Application Frameworks. This is the part of the Android that you will see frequently. As a developer you will spend a great deal of time reading, studying, implementing and using these frameworks. 

**Next &raquo;** [Development Setup](/android-install-sdk-windows)
