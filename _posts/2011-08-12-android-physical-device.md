---
layout: androidtutorial

title: Physical Device

description: How to use a real Android device for mobile development

excerpt: 

tags:
- Device

categories:
- Android

---

If you will use a physical device for testing, you need to do a few things. Before you connect the device via a USB, check for some settings on the device. 

On your device, go to *Settings* &rarr; *Applications* &rarr; *Development*. You need to *enable USB debugging*

<img class="small" src="/img/usb-debugging.png"/>
<div id='lst'>Fig 3: Enable USB Debugging in your Phone</div>

You can now connect the device to the development machine. The screenshot above was done on a Samsung Galaxy Tab, your device may vary.

***

**LG Optimus** 

1. Go to settings
2. Then connections
3. Tap on the **USB connection**
4. Choose **Charge only**
5. Go back to the Settings screen
6. Enable **USB Debugging**. You need to do this while the device is not yet connected to the PC (it will be greyed out if the device is connected when you do this)

Run a simple <code class="codeblock">adb</code> or <code class="codeblock">logcat</code>command on the terminal to see if it's working. If it's not, the terminal will say *waiting for device…*

**NOTE** for Windows users. You may need to download a USB driver software for your physical device before you can use it to test and deploy applications to it. OSX and Linux users does not have such concerns.

**Next &raquo;** [Get Started](/android-getting-started)
