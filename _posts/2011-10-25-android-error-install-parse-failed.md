---
layout: androidtutorial

title: Install Parse Failed Error

description:

except:

tags:
- error
- failed

---


*Failure [INSTALL_PARSE_FAILED_INCONSISTENT_CERTIFICATES]*


This error can happen when you have used an Android device on a different development machine. There is a signature on the device that came from the old development machine, that is the one getting in the way.  

## Solution

Just delete the Android applications that are installed on the device which came from your old development machine, then try to rebuild &mdash; <span class='codeblock'> ant release install</span> or <span class='codeblock'> ant debug install </span>



