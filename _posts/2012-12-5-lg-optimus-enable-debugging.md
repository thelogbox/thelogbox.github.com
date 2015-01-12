---
layout: androidtutorial
title: How to Prepare an LG Optimus Phone for Android Development

description: Prepare LG Optimus for Android Development

categories: 
- Android

tags:
-  Device

description: Enable the USB debugging settings of the LG Optimus. You need to do this before you can use the device for testing.

---

1. Go to settings
2. Then connections
3. Tap on the **USB connection**
4. Choose **Charge only**
5. Go back to the Settings screen
6. Enable **USB Debugging**. You need to do this while the device is not yet connected to the PC (it will be greyed out if the device is connected when you do this)

Run a simple **adb** or **logcat** command to see if it's working. If it's not, the terminal will say *waiting for device…*


