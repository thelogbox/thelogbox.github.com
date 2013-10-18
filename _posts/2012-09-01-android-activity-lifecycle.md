---
layout: androidtutorial

title: Android Activity Life Cycle

description:

except:

categories:
- android-programming

---



As an (Activity-based) application is started up until it is discarded, it will go through several states; namely, created, started, paused, resumed then eventually destroyed. 

1. onCreate() - When an Activity is first created. Typically this is place for setup of data sources, UI and other layouts. You cannot display anything during this period though. This is not a place for initializing widgets
2. onStart() - It is only during this time that you can really draw something on the screen. This is why I initialized the TextView on this callback. It doesn't make sense to initialize it during *onCreate()*, in fact you cannot, you will encounter a runtime error if you do so.
3. onResume() - This method will be called the first time the Activity is about to run. It will be subsequently called if the application loses focus, say when a call came in and your application got interrupted, then the application got the focus back again
4. on Pause() - If another application grabs the focus away from your application, but the application is still visible, it will be paused
4. onDestroy() - When the application exits, or forcibly shutdown by the Android runtime (for some reason)



<img class="default" src="/img/activity_lifecycle.png">

