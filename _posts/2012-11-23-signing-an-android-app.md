---
layout: androidtutorial

title: Signing an App

description: Detailed steps on how to generate a key, digitally sign and align your android project apk

tags:
- Release
- Signing
- Google
- Play

categories:
- Android

---

You have to sign your app before you can sell them and before other people can install them on their devices. Follow the steps below to sign your app.

**KEYTOOL** 
Check if you have keytool in your system path. Run the <code class="codeblock">keytool</code> command on a terminal window and you will soon find out if you have it or not. If you don't have it, troubleshoot your JDK installation. Most likely, the bin folder of JDK is not included in your system path

**GENERATE THE KEY**

<pre class="codeblock">

$ keytool -genkey -v -keystore thelogbox_key.keystore -alias thelogbox_key_alias -keyalg RSA -keysize 2048 -validity 10000

</pre>

If you get the exception *Keytool-error: java.io.IOException : Incorrect AVA format*, check if you have mistyped the command, or if  you have inadvertently added *dname** somewhere in there. Then, use the jarsigner

**JARSIGNER**

<code class="codeblock">

jarsigner -verbose -sigalg MD5withRSA -digestalg SHA1 -keystore my-release-key.keystore my_application.apk 
alias_name*

</code>

*my_application* should be the actual name of your application, as you created it during the  <code class="codeblock">android create project</code> command

The **jarsigner** prompts you to provide passwords for the keystore and key. It then modifies the APK in-place, meaning the APK is now signed. Note that you can sign an APK multiple times with different keys.

*Note:* As of JDK 7, the default signing algorithim has changed, requiring you to specify the signature and digest algorithims (-sigalg and -digestalg) when you sign an APK.

**VERIFY**

Verify that your APK is signed &mdash; run <code class="codeblock">jarsigner -verify my_signed.apk </code> on the terminal window. 

You can also use the commands <code class="codeblock"> jarsigner -verify -verbose my_application.apk </code> or <code class="codeblock"> jarsigner -verify -verbose -certs my_application.apk </code>

**ALIGN THE PACKAGE**

Run <code class="codeblock">zipalign</code> on your apk file after you have signed the apk with your private key. This command ensures that all uncompressed data starts with a particular byte alignment relative to the start of the file.

zipalign is part of Android SDK, so you should have it on your SYSTEM PATH.

Ensuring the alignment at 4 byte boundaries has a positive effect on application performance when installed on a device.

<code class="codeblock">zipalign -v 4 your_project_name-unaligned.apk your_project_name.apk
</code>

When aligned, the Android system is able to read files with mmap(), even if they contain binary data with alignment restrictions, rather than copying all of the data from the package. The benefit is a reduction in the amount of RAM consumed by the running application.

