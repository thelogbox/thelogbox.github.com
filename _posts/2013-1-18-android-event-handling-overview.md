---
layout: androidtutorial

title: Event Handling

description: There are two ways to program with event on Android. First is via the XML, the declative way. The declarative way has a limitation, a very serious limitation, you can only do the click event and nothing more. The other way, is the programmatic way --- this can handle anything. You need to be very comfortable working with interfaces and callbacks to use this.

categories:
- android-programming

---

User Interfaces usually contains views e.g. Buttons that users may activate. When these views are triggered, you will need a way to react to this event. This programming skill is called event handling.

There are two ways to handle events in Android. You can do it from within the XML file, this is called declarative event handling. The second method is programmatic which involves writing callback methods &mdash; they are called listeners &mdash; then writing codes inside the call backs. 

This chapter explores the two ways of handling event. We will go a bit deeper into each method in the succeeding chapters.

***

To follow the examples, it will be best if you create a new Android project. I hope by now you are already proficient in creating projects using the SDK tools, like we did on [Getting Started Chapter](/android-getting-started).

Once you already have a project, work on the *main.xml*. This file was generated when you created the project. Add a Button view in the main.xml file 

{% highlight xml %}
<Button
  android:layout_width="fill_parent"
  android:layout_height="fill_parent"
  android:text="Click me okay"
  android:onClick="showMe"
/>
{% endhighlight %}
<div id='lst'>/res/layout/main.xml</div>

What's new in this code is *onClick* attribute. When you add this to a view element, it adds event handling capability to your app. The value of the attribute in our example is **showMe**. This the method that the app will invoke when the user clicks on the button. It is your responsibility to implement this method.

To implement the **showMe** callback, you need to add a method inside the Activity class &mdash; the one associated with *main.xml* where the Button is defined. This method has to be *void* and must accept a *View* object as a parameter.

{% highlight java %}

class MyActivity extends Activity {
  
  public void showMe(View view) {
    // your code for the click
    // event here
  }
}

{% endhighlight %}
<div id='lst'>/src/com/thelogbox/MyActivity.java</div>

This is called *declarative* event handling in Android because you use the XML to declare the handler (the showMe method) for the button. This works well and is quite friendly for beginning Android programmers. 

This approach to event handling does have one shortcoming, it can only handle the *click* event. Other Android such as long-clicks, context-menus, touch etc, cannot be handled declaratively. To do those, you need to know how to handle events programmatically.

You will need to learn how to work with *Listeners*. 

# INPUT EVENTS

Input events from the user are triggered when he touches widgets like Buttons and TextViews. A lot of Android widgets inherits the *android.view.View* class either directly or indirectly. This is a good reason to be aware of the View's built-in listeners.

A *Listener* is a special object designated by Android. It contains callback methods which the Android runtime invokes when a specific event happens. 

To intercept the *click* event for example, you need to create a *Listener* object that was specifically designed to listen for click events. That would be the *android.view.View.OnClickListener*. 

The OnClickListener is implemented as a nested class inside android.view.View. There are many Listener interfaces that nested inside the View class, you can refer to the [android.developer/documentation](http://developer.android.com/reference/android/view/package-summary.html) for the details. 

User input like a long-click, should be handled using the **android.view.View.OnLongClickListener**, if the user pops up the keyboard and you want to intercept the keystrokes -- you use the  *OnKeyListener*; you get the idea by now. Go through the official documentation that was pointed earlier if you need to go through deeper details of the API. 

# PROGRAMMATIC EVENT HANDLING

To handle a click event, you need to create a listener object (View.OnClickListener) then register the widget of interest (a Button probably) to the listener. This is how the Android runtime will know that when a click happens to the Button, the runtime needs to invoke  the **public void onClick()** method.

{% highlight java %}

import android.view.View.OnClickListener;

class MyActivity extends Activity {

  // other setup codes here 

  @Override
  public void onCreate(Bundle sinstance) {
    
    super.onCreate(sinstance);
    button = new Button(getApplicationContext()); 
  
    OnClickListener listener = new OnClickListener(){
  
      public void(View view) {
        
        // your code for click here
  
      }
    } 
    button.setOnClickListener(listener);
  }
}

{% endhighlight %}

The example code above is not the only way to create listener. You can implement the *Listener* on the Activity as well, it may be more efficient that way because you can avoid the performance hit of the extra class loading which was caused by the inner class implementation.

The samples above should get you started on event programming, but let's take on another sample, this time, the long-click event.

{% highlight java %}

/*

HOW TO HANDLE THE LONG CLICK

*/

import android.view.View.OnLongClickListener;

class MyActivity extends Activity implements OnLongClickListener {
  public void onCreate(Bundle b) {
    super.onCreate(b);
    button = new Button(getApplicationContext());
    button.setOnLongClickListener(this);
  }

  public boolean onLongClick(View v) {
    // your code when user long clicks
    return true;
  }
}
{% endhighlight %}

The long click *Listener's* method is not identical to the void signature of the *click* event. It requires that you return a boolean value so Android runtime knows if the long click has already been handled (consumed) or not. Read and study the definitions of the events on the API documentation carefully. 
 
**Next** &raquo; [Declarative Event Handling](/android-event-handling-declarative)


