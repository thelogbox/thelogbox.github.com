---
layout: androidtutorial

title: Signing an App

description: Details steps on how to generate a key, digitally sign and align your android project apk

categories:
- android-programming

---

You have to sign the app before other people can install it on their devices.

## 1. keytool
Check if you have *keytool* in your SYSTEM PATH. Just invoke **keytool** on a terminal window and you will soon find out if you have it or not. If you don't have it, review your JDK installation

## 2. Generate your key

*$ keytool -genkey -v -keystore thelogbox_key.keystore -alias thelogbox_key_alias -keyalg RSA -keysize 2048 -validity 10000*


If you get the exception *Keytool-error: java.io.IOException : Incorrect AVA format*, check if you mistyped the command, or if  you have inadvertently added *dname** somewhere in there. Next, use the **jarsigner**


*$ jarsigner -verbose -sigalg MD5withRSA -digestalg SHA1 -keystore my-release-key.keystore my_application.apk 
alias_name*

**my_application** should be the actual name of your application, as you created it in the **android create project…** command

The *jarsigner* prompts you to provide passwords for the keystore and key. It then modifies the APK in-place, meaning the APK is now signed. Note that you can sign an APK multiple times with different keys.

GOOD TO KNOW: As of JDK 7, the default signing algorithim has changed, requiring you to specify the signature and digest algorithims (-sigalg and -digestalg) when you sign an APK.

## 3. Verify

Verify that your APK is signed &mdash; run **$ jarsigner -verify my_signed.apk** on the terminal window. You can also use the commands **$ jarsigner -verify -verbose my_application.apk** or **$ jarsigner -verify -verbose -certs my_application.apk**

## 4. Align the package

Run zipalign on your apk file after you have signed the apk with your private key. Zipalign ensures that all uncompressed data starts with a particular byte alignment relative to the start of the file. The *zipalign* tool is part of Android SDK, so you should have it on your SYSTEM PATH.

Ensuring the alignment at 4 byte boundaries has a positive effect on application performance when installed on a device.


*$ zipalign -v 4 your_project_name-unaligned.apk your_project_name.apk*

When aligned, the Android system is able to read files with mmap(), even if they contain binary data with alignment restrictions, rather than copying all of the data from the package. The benefit is a reduction in the amount of RAM consumed by the running application.

## Reference:

[developer.android.com](http://developer.android.com/tools/publishing/app-signing.html) - Web Reference (Nov 2012)

