---

layout: androidtutorial
title: Android Project Workflow

description: Here are the steps that a developer generally goes through from creating an android app, until signing it and releasing it to the public

tags:
- Workflow
- Project

categories:
- Android

---


# CREATE THE PROJECT

*android create project --path <project folder> --target <API level> --package <package name> --Activity <Activity name>*


# WORK THE MANIFEST


If necessary, modify the **AndroidManifest.xml*. There will be certain applications that will require explicit permissions to be declared on manifest e.g. use of camera, use of the MIC for media recording etc


# SOURCE CONTROL

This is for bitbucket.org, adjust the url accordingly for github.com

<pre class="codeblock">

$ cd /path/to/your/project
$ git init
$ git remote add origin https://yourname@bitbucket.org/yourname/yourproject.git

</pre>

# ADD .gitignore and README file

cd to project folder, create a .gitignore file. You don’t want all of the files to be under source control e.g. location of the build.xml and the android-SDK, these information are specific to developer workstation and may not be true for all developers. Also, you don’t want generated files to be part of source control

A sample content of .gitignore

<pre class="codeblock">
  bin/
  gen/
  ant.properties
  local.properties
  build.properties
  project.properties  
</pre>  


Don’t forget the README.txt. Even if you are working alone, it can’t hurt to write down your thoughts why you were trying to write that piece of code in the first place, put it in the README.txt

# COMMIT REGULARLY

Keep adding files to the project, keep modifying files. At the end of the day, commit your changes. Now, the frequency of the commit is usually decided as a group. There are projects where you cannot until certain number of unit tests have been performed (and passed) etc. Know your project practices and adhere to them, but the last thing you want is losing a days worth of coding/unit testing, so commit to the repo religiously

# LICENSE THE SOURCE FILE

You need to decide which license you will use. Remember, if there is no explicit license on the source file, it means its a full copyright. No one can use your code, they will have to contact you and ask for express permissions &mdash; not that everybody abides by that, but still, if you intend other people to benefit from your creation, then license it either using a permissive license (like MIT or BSD) or the GPL or what have you.

# DEBUG, OBSERVE, INSPECT, ADJUST

Learn how to type ant debug install really quickly, better yet, use a text expander so you have a fighting chance against carpal tunnel syndrome

# BETA TEST

Send the app to friends, relatives, colleagues etc, look for feedback. Go back to the app, refine. Let your thoughts germinate some more. You need to iterate a bit on the app before you release to the wild

# SIGN THE APP


ant debug install was fine for testing and development, but it cannot be consumed by other people without the developer signature. You need to [digitally sign your app]({{ post_url 2012-11-23-signing-an-android-app }}) before you release it to the public 

# GET TO GOOGLE PLAY

You can make the app available from your website as a downloadable apk (android package) or you could pay Google Play so you can sell the app at the Google Market Place (its like iTunes or the Apple App Store for Android apps)