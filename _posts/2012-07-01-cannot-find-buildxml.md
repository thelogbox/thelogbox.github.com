---
layout: androidtutorial

title: Cannot Find build.xml

description: How to fix the cannot find build.xml ant error on Android

except:

tags:
- Error
- Ant
- XML

---


## What does the error mean

It's a compilation error. The Android SDK refuses to compile the app because, literally, it cannot find **build.xml**. It may seem a bit tricky because if you look inside your android project, you will find a build.xml file. That is not the same xml file that the error is telling you about. The build.xml inside your project is actually importing another build.xml file. And it is looking for it in the **SDK.DIR/tools/ant** directory. That's the one it's saying it can't find. 

The **sdk.dir** is a variable which points to the folder location where you installed the Android sdk. This is also known as the **ANDROID\_HOME** folder. Usually, you don't need to mess around with this variable because it would have been set for you. So how did you get here? Lots of reasons but one thing is for certain. The sdk.dir variable is improperly set. It's not pointing to a valid folder where the Android sdk is installed. 

## How to Fix

Open the **local.properties** file in an editor. This file is on the root folder of your Android project so you should be able to find it without difficulty. Check the value of the sdk.dir, it should point to the actual folder where you installed the Android development kit. If it's not, fix it. Make it point to the right folder. 

Try the compilation again. It should work by now.

## Prevention

Did you notice the commented section of the local.properties file? It said "this file must not be checked into version control systems as it contains information specific to your local configuration etc". Follow that advice. Include the local.properties on the .gitignore file, if you are using git. If you are using another VCS, follow the method of your VCS on how to exclude certain files from being checked in.



