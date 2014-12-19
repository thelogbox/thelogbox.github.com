---
layout: androidtutorial

title: Android Virtual Device

description: Simple steps to setup an Android emulator for development

lastupdated: December 18, 2014

tags:
- android virtual device

---


You can create an AVD for any android version provided that you have downloaded a system image for it. System images can be downloaded using the android sdk manager.

**1. Check your available android images**

You can create an emulator for a specific android version only if you have downloaded a system image for it. You can list the available system images that are installed in your development machine by running the following command in a terminal window 

~~~
android list targets
~~~

The **list targets** command will output libraries and system images of all available android versions installed on your machine. Below is a snippet of what the command has outputted.

~~~
id: 11 or "android-19"
     Name: Android 4.4.2
     Type: Platform
     API level: 19
     Revision: 4
     Skins: HVGA, QVGA, WQVGA400, WQVGA432, WSVGA, WVGA800 (default), WVGA854, WXGA720, WXGA800, WXGA800-7in
 Tag/ABIs : default/armeabi-v7a, default/x86
~~~

The system image you are looking for is usually on the **ABI** line. In the example snippet above, it means I have the libraries to develop an application for API level 19, the KitKat version and that I also have two system images for it, the armeabi-v7a and the x86. 

**2. Decide which version of android** 

**2.1 Create the AVD**

~~~
android create avd --name kitkat --target android-19 --abi default/x86
~~~

This command will create an emulator for android level 19. 

**--name** The name option is something that you choose. It will become the label of the emulator. I chose "kitkat" because it is descriptive, after all, we are creating an emulator for the KitKat version of android

**--target** This refers to the id of the android library as it is stored in your machine. You will get this from the output of the **android list targets** command. In our example, the target is android-19 which is the KitKat version 

**--abi** This refers to the name of the system image. You will also get this from the output of **android list targets** command. In our case, we chose to use the default/x86 which is an Intel image

The **create avd** command has a couple more options we can use, but we only used three of them here. You can pass other options that will affect things like skin and the amount of sd card storage. You can learn the other options of this command by typing **android create avd** in a terminal window. That will display a help file.

If you need to create an emulator for another android version, just follow these steps all over again.

**2.2 Download System Images** if necessary

If you need additional android versions and system images, use the sdk manager to download them. Launch the android sdk manager. Chose the android version or API level you want to download. Mark it for installation 

![PIC sdk manager](/img/sdk-manager-system-image.png)

Click the "Install" button. You will need to accept the license agreements before you can continue to download.

**3. Another Way to Create an Emulator**

Alternatively, we can also create an avd using graphical tool of the android sdk manager. Launch the sdk manager like you did before, click **Tools** &rarr; **Manage AVDs**


![PIC manage avds](/img/avd-creation.png)



**4. Testing**

We can test the emulator by launching it either from the terminal window or from the graphical avd tool

~~~
emulator -avd kitkat
~~~

The **-avd** name is the value you specified as the **--name** value when you created the emulator.

![PIC avd launched](/img/avd-launched.png)




