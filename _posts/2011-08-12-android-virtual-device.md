---
layout: androidtutorial

title: Virtual Device (AVD)

description: Simple steps to setup an Android emulator for development

excerpt: 

tags:
- avd

categories:
- Android

---

You will need a runtime environment to complete your development setup. The SDK will allow you write and compile android programs. But to test them, you need a place where to deploy and test those programs. 

The AVD is used for testing Android Projects. It is an emulator that mimics a real mobile device. There are a few things of course that it won't be able to emulate e.g. the accelerometer, but for the most application testing needs, you can get by with the AVD until you can procure a proper physical device. I don't really need to tell you the advantages of using a physical device, if I really have to, then the single most distinct advantage is **speed**. The AVD is notoriously slow, it will slow down your development.

# CONFIGURATION

The AVD can be configured from the Android SDK manager, so you will need to launch the SDK Manager first.

1. On a command line terminal, type <code class="codeblock">android</code>
2. Wait for the SDK manager window to appear, then go *Tools* then *AVD*
3. Click *New* to create an AVD.The next screen will ask you a bunch of questions on the technical details of the AVD that want to create. Fill it up with what is applicable to you (screen resolutions, amount of RAM to dedicate etc)
4. Launch the AVD when you are done

Use the AVD if you only don't have access to a physical android device. The AVD is slow and quite limited for testing real world apps. 

**Next &raquo;** [Setting up a Physical Device](/android-physical-device)