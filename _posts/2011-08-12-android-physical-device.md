---
layout: androidtutorial

title: Setting Up a Physical Device for Testing

description: How to use a real Android device for mobile development. Samsung Galaxy and LG Optimus

lastupdated: December 18, 2014

tags:
- Device

---

The use of an actual android device during development and testing has many advantages over simply using an emulator or the avd. There are things you cannot test on the emulator like the accelerometer or testing the cellular data connection. Another big reason for using an actual device is that it gives you better appreciation of how the real app will look and feel. 


## 1 Samsung Galaxy Tab

1.1 **Disconnect the android device** from the PC

1.2 **Go to Settings** &rarr; Applications &rarr; Development

1.3 **Enable USB Debugging**. This is usually a check box 

[PIC: USB Dev Settings for Samsung Galaxy](/img/usb-debugging.png)

1.4 **Connect the device to the PC** to start development and testing

## 2 LG Optimus

On some android devices, the steps could be slightly different from the ones above. On an LG Optimus device for example, the steps are as follows.

2.1 **Go to Settings** &rarr; Connection, then tap **USB Connection**

2.2 Choose **Charge only**

2.3 **Go back** to the Settings screen

2.4 Enable **USB Debugging**. 

You need to do this while the device is disconnected from the PC otherwise, this option will be greyed out which means it is not possible to make any modification on the setting

## 3 Testing

Once you have connected the device the PC, you can run a command on a terminal window to check if the device will be recognized by the android tool. 

~~~
adb logcat
~~~

If the device is recognized by the android tools, a bunch of messages will hurriedly scroll through your terminal window. You can stop it by pressing **CTRL C**. If the device was not recognized, you will see a message saying "waiting for the device".
