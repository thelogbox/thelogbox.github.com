---
layout: androidtutorial

title: Android Screen Shooting

description: 

excerpt: 

categories:
- android-programming

---


1. You need the JDK (Java Development Toolkit). The Android development environment depends on Java, that is why you need this. Take note that you need the JDK not the JRE (Java Runtime Environment). If you install the JDK though, you would also have installed the JRE
2. You need to the *Android SDK*. It can be downloaded installed on your PC. I assume you are and android
3. Launch the *ddms* -- *$ ddms* or *c:\\>ddms>*. The path to the **android** executable has to be included in your PATH variable. If you forgot how to setup the Android dev environment, the [notes are on Official Android developer site](http://developer.android.com/sdk/installing.html). You do not need to follow all the steps in there, you only need to complete up until step No. 2.
4. Enable USB debugging on the Android device, before you connect it to the PC (or Mac, or Linux). This is usually done by accessing *Settings-->Applications-->Development*, there is a check box beside "Enable USB debugging". Connect the Android device to your PC via a USB cable
5. The connected device should now be visible within the DDMS window. Select it (just mouse click on it)
6. Press CTRL-a on your keyboard

This technique of screen shooting is not for the everyday Android User &mdash; not even for the power user. This technique is for Devs. You would use this technique because the captured image is captured on a PC. If you will do screenshooting using an App, you need to take care of the file transfer between the device and the PC.



