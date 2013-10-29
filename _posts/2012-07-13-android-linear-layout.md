---
layout: androidtutorial

title: Linear Layout

description: Learn to use the horizontal and vertical orientation of the LinearLayout in Android. LinearLayout is the most basic UI layout in Android

excerpt: 

tags:
- Layout
- UI

categories:
- Android

---

We will work with project you created in the [last chapter](/android-activity). The layout seems okay but a little weird. The labels are usually laid out to the left of a text field and not on top. This is happening because the LinearLayout's orientation is **vertical**. That caused the components to flow from top to bottom. 

<img class="small" src="/img/lin-sample-1.png" width="300">
<div id='lst'>Second app</div>

We can change the current  behavior so that components inside the layout will flow from left to right. Change the orientation of the layout to **horizontal**

{% highlight xml %}

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="horizontal"
    android:layout_width="fill_parent"
   	android:layout_height="fill_parent"
    >
	<TextView  
    android:layout_width="wrap_content" 
    android:layout_height="wrap_content" 
    android:text="Hello World"
    />
	<EditText
		android:layout_width="fill_parent"
		android:layout_height="wrap_content"
	/>
</LinearLayout>

{% endhighlight %}

Save the project, compile, then run. Notice any difference?

<img class="small" src="/img/lin-sample-2.png" width="300">
<div id='lst'>Second app, modified</div>

The *Name* TextView is now immediately to the left of the EditText, as compared to our first version of our layout where the *Name* TextView was on top of the editable text.  

There were two changes that made the second layout possible.

1. Change the *android:orientation* of LinearLayout from "vertical" to "horizontal", this caused TextView and the EditableText views to flow from left to right, rather than top to bottom
2. Change *android:layout_width* of the TextView from "fill_parent" to "wrap_content". Had we not made that change, the EditableText view would not have been visible. "Fill_parent" causes the view to occupy whatever space is remaining to right of the component. "Wrap_content" on the other hand, simply uses whatever space the component needs to display itself and allows the next component to occupy the next slot. 

<h2 class="section">HOW TO ADD BUTTONS</h2>

Button widgets are very common to GUI applications. They allow users to convey action. Let's learn how to add a button to our app.

You will do this by editing *main.xml* again.

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
    android:text="Hello World"
    />
	<EditText
		android:layout_width="fill_parent"
		android:layout_height="wrap_content"
	/>
	<Button
		android:layout_width="wrap_content" 
    	android:layout_height="wrap_content" 
    	android:text="Click me "			
	/>
</LinearLayout>

{% endhighlight %}


As usual, compile and run. You will do the *edit-compile-run* routine lots of times, you need to get used to it. Everytime you make a change on your code or any of the assets of the android project, you need to compile and run. 

<img class="small" src="/img/lin-sample-3.png" width="300">
<div id='lst'>The second app with a button</div>

It's not pretty. The app looks this way because the *Button, TextView and EditText views* are inside a single Layout container, which will arrange each view to flow from left to right. On top of that, the EditText's *layout_width* is set to *wrap_content*. That means in case there is a component right after EditText, it will generously give the space to the next view

To fix this, we need to place the *Button* in it's own container. It cannot share the container with EditText and Textview. After that, the *EditText* will be the last component defined in the inner *LinearLayout*. We must change its *layout_width* to *fill_parent*, so it can occupy whatever space will be left to its right

{% highlight xml %}

<!-- main.xml -->

<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    >

	<LinearLayout
		android:orientation="horizontal"
		android:layout_width="fill_parent"
		android:layout_height="wrap_content"
	>
		<TextView  
    		android:layout_width="wrap_content" 
    		android:layout_height="wrap_content" 
    		android:text="Name "
   	/>
    
		<EditText
			android:layout_width="fill_parent"
			android:layout_height="wrap_content"
			android:id="@+id/name"
		/>
		
	</LinearLayout>
	
	<Button
    	android:layout_width="wrap_content" 
    	android:layout_height="wrap_content" 
    	android:text="Click me "			
	/>
	
	</LinearLayout>

{% endhighlight %}


<img class="small" src="/img/lin-sample-4.png" width="50%">
<div id='lst'>Second app, adjusted layout</div>

