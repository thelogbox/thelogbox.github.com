---
layout: androidtutorial

title: Testing on AVD and Actual Device

description: Using a physical device or virtual device for Android development

excerpt: 

tags:
- Testing
- Virtual
- Device

categories:
- Android


---



By testing the android project, I mean running it. There is another concept testing which is **unit testing with JUnit**, that is not what I mean and that is not what we are going to do right now---we will tackle that much later. The test we will do actually involves deploying the project either in an AVD (Android Virtual Device) or a physical android device, so we can see it run. You need one or the other in order to run our android app.

# ANDROID VIRTUAL DEVICE (AVD)

The emulator needs to be configured. It is not configured for you when you installed the SDK. The reason for this is because there are various android API levels (Froyo is 2.2, Gingerbread is 2.3.3 etc). You will need to specify which API level an emulator is supposed to, well---emulate. You can create as many AVDs as you need, probably one for Froyo, one for Gingerbread, another one for Honeycomb so on and so forth. 

To create an AVD:

1. From a command line terminal, launch the android SDK Manager by typing <code class="codeblock">android</code>

2. Go to the **Tools** menu, then **Manage AVDs** 

<img class="shadow" src="/img/avd.png">



Click **New** to create a new AVD. The next screen will ask you a bunch of questions on the technical details of the AVD that want to create. Fill it up with what is applicable to you (screen resolutions, amount of RAM to dedicate etc) 

3. Launch the AVD when you are done

**CAUTION**: You will increasingly get annoyed by the AVD because it is painfully and excruciatingly slow. That is why I urge you to shell out some more bucks and get a real android device that you can use for testing

## If you will use an Android physical device 

1. Before you connect the device via a USB, you need to check some settings on the device.  

2. Go to **Settings**, then **Applications** then **Development**. You need to *enable USB debugging*

<img class="small" src="/img/usb-debugging.png">

3. Now you can connect the device to the development machine

## Running an Android app

Two ways you can do this, either one is okay.



	$ ant debug install

Or

	$ adb install bin/Hello-debug.apk

Either one of these commands should be ran from the root of your android project folder.

So much easier to just use the first one, but both should be okay--apk stands Android Package, in case you're wondering. 

At this point, you can now appreciate the Hello World project in all its glory as it runs on your mobile device. You should be able to see it on the list of your apps. 

<img class="small" src="/img/hello-deployed.png">

[Back to Android Programming Tutorial](/android-programming-tutorial/)
