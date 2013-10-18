---
layout: androidtutorial
title: Check for Network Connectivity

description: Detailed steps on how to check what kind of network connectivity an android device has. This code is useful to execute before you push out a significant amount of data using the network.

categories: 
- android-programming
---

Finding out the state of connectivity of an Android device is a fundamental technique. You need to know which type of connectivity the device has before you perform any activity that requires data transfer. You may encounter situations where you want to send data e.g. picture files,  maps or any other sizeable data through the wire, only when WIFI connectivity is up.

There are two classes in android.net package that can be used to determine connectivity; The ConnectivityManager and NetworkInfo

1. Use a ConnectivityManager object, get the System Service information — getSystemService(Context.CONNECTIVITY_SERVICE)
2. Get the network information from the ConnectivityManager object, the getActiveNetworkInfo() returns an android.net.NetworkInfo object, this contains some detailed information about connectivity
3. Call the getType() method against the NetworkInfo object, it will return an int value, check it against the CONSTANTS defined in the ConnectivityManager class

Before you compile and install on the device, you need to set additional permissions on the Manifest file

### The Manifest file

<img src='../img/android-manifest-conntest.png'/>

### Code

{% highlight java %}
/*

BSD License: Copyright (c) 2009-2012 Ted Hagos
All rights reserved.

License text: http://thelogbox.com/source-docs/software-license.txt

filename: ConnTest.java

*/

package com.thelogbox;

import android.app.Activity;
import android.os.Bundle;
import android.content.Context;
import android.widget.LinearLayout;
import android.widget.TextView;
import android.view.View;
import android.view.View.OnClickListener;
import android.net.ConnectivityManager;
import android.net.NetworkInfo;

class ViewConnnTest extends LinearLayout implements OnClickListener {

  Context context = null;
  TextView tv = null;
  ConnectivityManager connman = null;
  NetworkInfo netinfo = null;

  public ViewConnnTest(Context context) {

    super(context);
    this.context = context;
    tv = new TextView(context);
    addView(tv);
    setOnClickListener(this);

  }

  public void onClick(View v){

    StringBuilder sb = new StringBuilder();
    connman = (ConnectivityManager) context.getSystemService(Context.CONNECTIVITY_SERVICE);
    netinfo = connman.getActiveNetworkInfo(); 

    switch(netinfo.getType()) {
      case ConnectivityManager.TYPE_MOBILE:
        sb.append("\nMobile data OK.");
        break;
      case ConnectivityManager.TYPE_WIFI:
        sb.append("\nWIFI OK.");
        break;
      case ConnectivityManager.TYPE_WIMAX:
        sb.append("\nWIMAX OK.");
        break;
      case ConnectivityManager.TYPE_ETHERNET:
        sb.append("\nOn Ethernet.");
        break;
      case ConnectivityManager.TYPE_BLUETOOTH:
        sb.append("\nBluetooth OK.");
        break;
      default:
        sb.append("\nNot connected. Not OK.");
    }
    sb.append("\nState= "); 
    sb.append(netinfo.getState().toString());

    tv.setText(sb.toString());
  }
}

public class ConnTest extends Activity {
    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(new ViewConnnTest(this));
    }
}
{% endhighlight %}