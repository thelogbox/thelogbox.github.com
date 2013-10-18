---
layout: androidtutorial

title: Using Layout Weights

description:

except:

categories:
- android-programming

---



Learning to layout vertically and horizontally are basic skills in UI programming. They are effective and good enough, but that's just the thing, they are just good enough. If you want to show a bit of finesse, you need to do something beyond the basics.  

Linear layouts will do exactly what the name implies. It will layout the Views linearly. What it will not do is resize the Views to take advantage of free space.  If you do not manage free space in your layout, the design will not appear tight, and a bit, well, amateurish. 

There is one easy thing that if you do, will add a bit of finesse to the UI design. That one thing is to add *layout weights* to the Views.

<h2 class="section">START WITH A BASIC UI WITHOUT LAYOUT</h2>

Create an *Activity based* project for this example. Use the default vertical linear layout and add an *EditText, TextView and Button* components


{% highlight xml %}

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    >

	<EditText
		android:layout_width="fill_parent"
		android:layout_height="wrap_content"
		android:id="@+id/todoedit"

	/>

	<TextView  
    	android:layout_width="fill_parent" 
    	android:layout_height="wrap_content" 
    	android:text="I have nothing"
		android:id="@+id/tododisplay"

    />

	<Button
		android:layout_width="fill_parent"
		android:layout_height="wrap_content"
		android:text="Add item"
		android:id="@+id/btnadd"
		android:onClick="recAdd"

/>
</LinearLayout>


{% endhighlight %}


<img class="small" src="/img/layout-no-weight.png" width="50%"/>
<div id='lst'>The UI as it current looks</div>

This design suffers from a couple of problems. The vertical space for the *TextView* is lacking. If the application intends to display multiple lines on the *TextView* to let users type up inputs and append the results to TextView, then the TextView should have more vertical space than either the *Button* or the *EditText*. 

We can increase the space occupied by the *TextView* by increasing the number of lines it will occupy. It can be done by adding  a statement like *android:lines="10"* or any number of lines to the TextView declaration. That approach however, have some setbacks, it might work for a 5" screen device but you might need to tweak the number of lines if the app is deployed on another device with a different screen size. Specifying absolute values is a dangerous thing to do in UI design. You just don't know the form factor of the device where you will app will run. 

# USING A WEIGHTED LAYOUT

Each *View* component can be assigned a *weight property*. You can specify the amount of remaining space that the component can occupy  relative to the amount of space that the other components are occupying. 

Think of the weight approach as pie chart. If there 3 components in the UI, I can try to allocate percentages to each component. The percentages represents the amount of screen real-estate to be allocated. 

{% highlight xml %}

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    >

	<EditText
		android:layout_width="fill_parent"
		android:layout_height="wrap_content"
		android:id="@+id/todoedit"
		android:layout_weight="0"
	/>

	<TextView  
    	android:layout_width="fill_parent" 
    	android:layout_height="wrap_content" 
    	android:text="I have nothing"
		android:id="@+id/tododisplay"
		android:layout_weight="10"
    />

	<Button
		android:layout_width="fill_parent"
		android:layout_height="wrap_content"
		android:text="Add item"
		android:id="@+id/btnadd"
		android:onClick="recAdd"
		android:layout_weight="0"
/>
</LinearLayout>


{% endhighlight %}

<div id='lst'>LinearLayout with weights</div>

<img class="small" src="/img/layout-weight.png" width="50%"/>

<div id='lst'>How it looks with layout weights</div>

**REMEMBER**

Use the weight property of the view to allocate the amount of screen real estate for it.

The weight of all the views will be summed up. If you have 3 views and you gave them all equal weights of 10, it is as good as assigning them equal weights of 1 or 0. The integer value does not matter, it is the proportion of each view relative to its sibling views. 

You can only use the *weight property* on a **LinearLayout**. The other layouts will have their own acrobatics to position views in relation to its sibling views and the frame


