---
layout: androidtutorial

title: Cannot Find build.xml

description:

except:

tags:
- Error
- Ant
- XML

---

This is a build script problem, at the time of writing, I am using Apache Ant 1.8.2. This can happen after immediately installing the android SDK or after performing an update using the SDK manager. 

<pre class='codeblock'>

BUILD FAILED
/Users/ted/workarea/android-training/practice
/helloworld/	build.xml:83: Cannot find /Users/ted/
progtools/android-sdk-macos/tools/ant/build.xml 
imported from /Users/ted/workarea/android-training/
practice/helloworld/build.xml

Total time: 0 seconds

</pre>

Just read the error carefully and you will see. It cannot find the `build.xml` file on the SDK.DIR (the folder where you installed the android SDK). Line number 83 of build.xml inside your project folder is actually an import directive. It is importing a generic build.xml from SDK.DIR/tools/ folder. 

## What to do

Check carefully that the directory entry on the file `local.properties` for the SDK.DIR is correct. The local.properties file is on the root folder of the android project you created. For some reason (that I don't know yet), the SDK.DIR value on the properties file was incorrect. Just make the necessary adjustments, then run `ant`  again. It should work by now. 




