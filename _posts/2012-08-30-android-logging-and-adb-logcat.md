---
layout: androidtutorial

title: Logging and adb logcat

description:

except:

categories:
- android-programming

---



# LEARNING OBJECTIVES

1. Validate the *Activity* life cycle. See for ourselves when the Activity *call-backs* are fired
2. Use the android.util.Log for logging messages
3. View the logged messages using *adb logcat*  



# STEPS 

Choose a suitable working directory then create a project.  <span class='codeblock'>$ android create project --path lifecycle target --8 --package com.thelogbox --activity LifeCycle </span>

A Froyo target (API level 8) is what I used. Use whatever API level you need or works for you. I used Froyo because this is what is installed on my physical testing device. If you need to find out which API levels are installed on your machine, type <code class="codeblock">android list targets</code>

Next, add some UI elements and some event methods. Edit the */res/layout/main.xml* and follow the code sample

{% highlight xml %}

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
  android:orientation="vertical"
  android:layout_width="fill_parent"
  android:layout_height="fill_parent"
  >

<ScrollView
	android:layout_width="fill_parent"
	android:layout_height="wrap_content"
	android:layout_weight="9">
			
	<TextView  
    android:layout_width="fill_parent" 
    android:layout_height="wrap_content"
		android:id="@+id/displaytext" 
    android:text="Hello World, LifeCycle"
  />
</ScrollView>

<Button
	android:layout_width="fill_parent"
	android:layout_height="wrap_content"
	android:layout_weight="0"
	
	android:text="Click me"
	android:onClick="btnClick"	
	/>
</LinearLayout>

{% endhighlight %}

The TextView will be used to provide some sort of proxy to STDOUT of our little app. While we will use logcat to view the call-backs, we will also print it out on the screen of the device. The TextView is wrapped inside a *ScrollView* because we will append  new messages on top of older messages, it will spill over the height of the viewport. 

A Button is also included in the UI. After the application hits the *onResume()* callback, our app now has focus, it is ready to accept input and respond to the user, the Button is a simple mechanism to demonstrate the *actual life* of the application &mdash; when it is interacting with the user. 

***

You will need to override some call back functions in the main Activity class. Go the file *src/com/thelogbox/LifeCycle.java* and follow the sample code

{% highlight java %}

package com.thelogbox;

import android.app.Activity;
import android.os.Bundle;
import android.util.Log;
import android.widget.TextView;
import android.view.View;

public class LifeCycle extends Activity {
	
	private final String TAG = getClass().getName();
	
	TextView tview;
	
	
    /** Called when the activity is first created. */
    @Override
    public void onCreate(Bundle savedInstanceState) {
				
		System.out.println("HELLO THERE");
		Log.v(TAG, "inside onCreate");
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);
    }
	
	@Override
	public void onStart() {
		tview = (TextView) findViewById(R.id.displaytext);
		super.onStart();
		log("inside onStart");
	}
	
	@Override
	protected void onResume() {
		super.onResume();
		log("inside onResume");
	}
	
	@Override
	protected void onPause() {
		super.onPause();
		log("inside onPause");
	}
	
	@Override
	protected void onStop() {
		super.onStop();
		log("inside onStop");
	}

	@Override
	protected void onDestroy() {
		super.onDestroy();
		log("inside onDestroy");
	}
	
	private void log(String message) {		
		String temp = (String) tview.getText();
		Log.v(TAG, message);
		tview.setText(temp +  "\n" + message);
	}
	
	public void btnClick(View v){
		log("Button was clicked");
	}
}

{% endhighlight %}

# TEST & RUN

Inspect the logged activity using the built-in android debugger <span class='codeblock'>adb logcat com.thelogbox.LifeCycle *:S </span> &mdash;  If I don't do this, I would have been inundated with a lot of android messages. 

Where is the *System.out.println*?  Well, this was re-routed to logcat, because there is no *STDOUT* in android. If you really want to see it, you need to run <span class='codeblock'>adb logcat System.out *:S </span>













