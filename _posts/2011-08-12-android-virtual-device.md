---
layout: androidtutorial

title: Android Virtual Device (AVD)

description: 

excerpt: 

categories:
- android-programming

---


The AVD is used for testing Android Projects. It is an emulator that mimics a real mobile device. There are a few things of course that it won't be able to emulate e.g. the accelerometer, but for the most application testing needs, you can get by with the AVD until you can procure a proper physical device. I don't really need to tell you the advantages of using a physical device, if I really have to, then the single most distinct advantage is **speed**. The AVD is notoriously slow, it will slow down your development.


# CONFIGURATION

The AVD can be configured from the Android SDK manager, so you will need to launch the SDK Manager first.

1. On a command line terminal, type <code class="codeblock">android</code>
2. Wait for the SDK manager window to appear, then go *Tools* then *AVD*
3. Click *New* to create an AVD.The next screen will ask you a bunch of questions on the technical details of the AVD that want to create. Fill it up with what is applicable to you (screen resolutions, amount of RAM to dedicate etc)
4. Launch the AVD when you are done

