---
layout: androidtutorial
title: Setting Up an Eclipse Development Environment

description: How to use Eclipse for Android development

tags:
- Eclipse

categories:
- Android

---



Make sure you have already installed the ANDROID SDK and that you have properly configured the PATHs to tools and platform-tools. Make sure also that you have properly installed and configured Apache ANT.

Download Eclipse from [eclipse.org](http://eclipse.org), This is usually zipped or tgz'ed file. You will need to extract eclipse to a folder of your choice and setup the correct links/PATH


## Get the ADT

1. Launch Eclipse
2. Go to **Help** &rarr; **Install new software**
3. Click the **Add** button
3. On the *Location* text field, type https://dl-ssl.google.com/android/eclipse/, you can type whatever you want on the *Name* textfield, but I suggest that you name it "Android DT" or something descriptive
4. Click **Ok** then follow the prompts, it is straightforward from there.
5. Eclipse will restart after the plugin has been completely downloaded


## Create a project

Go to **File** &rarr; **New Project** &rarr; *Android* &rarr; *Android application project*. It will be a series of dialog screens, but what you need to remember are the following;

1. *Application Name* - Choose a name for this. This is an Eclipse construct, it needs it to manage projects
2. *Project name* - Put whatever you like
3. *Package name* - this is usually a reverse DNS notation of your domain name. The domain does not have to exist, so you can put whatever you like e.g. com.thelogbox.HelloWorld
4. *Minimum required SDK* - The lowest version of Android that your application is guaranteeing to run on; be careful here, the older release of Android is not guaranteed to be compatible with the newer versions of Android. Unless you absolutely know what you are doing, put exactly the same values on all the SDK fields in this dialog screen
5. On the next screen, you will have an option to *create an Activity*, leave it on if you want to have a default Activity class when the project is created
6. Follow the prompts to fill out some more project details



## Test

If you don't have a physical Android device, you can use the AVD (Android Virtual Device) but I strongly suggest that you get a physical device because the AVD is painfully slow. You need to get the AVD setup first before you can run anything, there are detailed instructions and information about the AVD on [android developer site](http://developer.android.com/tools/devices/managing-avds.html). You will need either the AVD or a physical device because Android applications are meant to run on an environment that is very different from your PC, that is why you need at least an emulator. 

If you have a physical Android device, there are somethings you need to note before you can use it. 

1. You need to enable the **USB Debugging** option on the physical device itself. This procedure will differ from one device brand to another, so you really need to know how to work this for your specific device brand
2. If you are using OSX, then you can stop here, you all setup. All you've got to do is to plug your device into the USB of the PC, and off you go. If you are using Windows or Linux, read on to step no. 3
3. You need to properly configure the USB settings on your machine before you can plug in your Android device and use it for development. There are detailed instructions on the [android developer site](http://developer.android.com/tools/device.html), read through it and follow it
4. Once the setup is done, as soon as you click **Run** on the eclipse menu (CTRLF11), the new android project will be deployed to the physical machine &mdash; as if you ran **ant debug install** from the command line

## References

1. [developer.android.com/AVD](http://developer.android.com/tools/devices/managing-avds.html) - Managing AVDs. Google, 2012
2. [developer.android.com/tools/device](http://developer.android.com/tools/device.html) - Setting up USB devices for Android testing. Google, 2012
