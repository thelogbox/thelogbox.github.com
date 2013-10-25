---
layout: androidtutorial

title: Declarative Event Handling

description: 

excerpt: 

categories:
- android-programming

---

Declarative event handling is one of the two ways you can react to user events. The other way of handling events is *programmatically* &mdash; which is discussed in a chapter of its own.

Handling events declaratively means you will make the event declaration inside the XML file where the UI is defined. Typically, this will an XML file inside */res/layout* folder. You will use the *onClick* attribute of a widget such as a button and assign it a string value. This string value is usually a name of method which you also need to define on Activity class that is associated with XML file.

To follow the code examples in this chapter, we will need to create a new android project. 

<pre class="codeblock">

$ android create project --path hellotoast --package com.thelogbox --activity TestToast --target 8

</pre>

Our new Android project named *hellotoast* would have created an XML file, it is located at */res/layout/main.xml*. We will add a button widget to it and use the onClick attribute to define a rudimentary event handler.

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

You will need to implement a method called "showMe()" inside the *TestToast* activity of the project. The *TestToast* activity references the *.main.xml* as the *View*. 

Next, add the *showMe()* method to the Activity class. 

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
<div id='lst'>/src/com/thelogbox/TestToast.java.</div>

To compile and run this example, use the command

<pre class="codeblock">
ant debug install
</pre>

The *showMe() method* is a programmer defined method. It is your responsibility to name it and implement it accordingly. 

The entry in the XML which is <code class="codeblock">android:onClick="showMe()"</code> is what makes the event handling possible. Upon compilation, the XML file will be expanded and translated to the necessary Java components that makes both UI display and event handling possible.

<aside>
*Toast* is a low hanging fruit for simple notifications. It is a built-in view that allows you display simple notifications to the user. These are the pop-up notifications you see on your android device. These notifications simply pops-up then disappears. 
</aside>

**Next** &raquo; [Programmatic Event Handling](/android-event-handling-programmatic)










