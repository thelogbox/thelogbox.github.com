---
layout: androidtutorial

title: Declarative Event Handling

description: 

excerpt: 

categories:
- android-programming

---


One of the two ways to handle events in Android programming is declaratively---which means we will declare the event using the appropriate *xml* file in the **res** folder. If you create a default android project (like how we have been [creating android projects ](/android-getting-started/), there will be a *main.xml* inside the **res folder**. When you add views or widgets using that xml, you can declare the name of the function that will be called when an event is triggered, such as *onClick*. 

# Steps

1. Create an android project named hellotoast (*--path hellotoast*)

	$ android create project --path hellotoast --package com.thelogbox --activity TestToast --target 8

2. Add a *Button* view to the *main.xml* and set the method to call if the Button widget is clicked.

{% highlight xml %}

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    >
<TextView
    android:layout_width="fill_parent" 
    android:layout_height="wrap_content" 
    android:text="Hello World, TestToast"
    />
    
<Button
	android:layout_width="fill_parent"
	android:layout_height="fill_parent"
	android:text="Click me okay"
	android:onClick="showMe"
/>

</LinearLayout>

{% endhighlight %}

3. The **android:onClick="showMe** declaration of the Button widget means that when main.xml is expanded, it will create the necessary hooks for the proper handling of event. You will need to define a method called "showMe()" inside the *TestToast* activity of the project. The *TestToast* activity references the *.main.xml* as the *View*. 

4. Add the *showMe()* method inside /src/com/thelogbox/TestToast.java.

{% highlight java %}

package com.thelogbox;

import android.app.Activity;
import android.os.Bundle;
import android.widget.Toast;
import android.content.Context;
import android.view.View;

public class TestToast extends Activity {

/** Called when the activity is first created. */

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.main);
    }

	public void showMe(View v) {
		Context ctx = getApplicationContext();
		String msg = "Hello World";
		int duration = Toast.LENGTH_SHORT;
		Toast notification = Toast.makeText(ctx,msg,duration);
		notification.show();
	}

}
{% endhighlight %}

Compile and Run using <code class="codeblock">and debug install</code>

The *showMe() method* - this is a programmer defined method. It could be any other name, as long as it is a valid Java identifier and a valid method. 

When you declare an event inside the res/xml  file, you need to ensure that a method with the same signature is found on the class that references the xml file as its ContentView---in this case, the TestToast class references main.xml as its content view, that is why the *showMe()* method is defined inside the TestToast class.

***

*Toast* is a low hanging fruit for simple notifications. It is a built-in view that allows you display simple notifications to the user. These are the pop-up notifications you see on your android device. These notifications simply pops-up then disappears. 

**Next** &raquo; [Programmatic Event Handling](/android-event-handling-programmatic)










