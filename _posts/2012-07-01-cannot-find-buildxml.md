---
layout: post

title: Cannot Find build.xml

description:

except:

categories:
- android-programming

---


This is an ANT script problem, at the time of writing, I am using ant 1.8.2. This can happen after immediately installing the android SDK or after performing an update using the SDK manager. 

If you invoke the **ant** tool and see something like the error below

<pre class='codeblock'>

	BUILD FAILED
	/Users/ted/workarea/android-training/practice
	/helloworld/	build.xml:83: Cannot find /Users/ted/
	progtools/android-sdk-macos/tools/ant/build.xml 
	imported from /Users/ted/workarea/android-training/
	practice/helloworld/build.xml

	Total time: 0 seconds

</pre>

Just read the error carefully and you will see. It cannot find the *build.xml* file on the SDK.DIR (the folder where you installed the android SDK). Line number 83 of build.xml inside your project folder is actually an import directive. It is importing a generic build.xml from SDK.DIR/tools/ folder. 

## HOW TO FIX

Check carefully that the directory entry on **local.properties** for the sdk.dir is actually correct. The local.properties file is on the root folder of the android project you created. For some reason (that I don't know yet), the sdk.dir value on the properties file incorrect. Just make the necessary adjustments, then try to run **ant** again. It should work by now. 




