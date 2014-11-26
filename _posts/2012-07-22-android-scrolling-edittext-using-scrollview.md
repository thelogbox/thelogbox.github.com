---
layout: androidtutorial

title: Scrollable Text

description: Really simple steps on how to do scrollable texts in Android

except:

tags:
- UI
- View

---

There will be times when you will need to display multiple lines of text that will exceed the height of visible display. You will need to scroll to view the rest of the text. For example, if you read something from a datasource, a file or a database and display its contents, chances are the number of lines of the datasource will be greater than the height of View component.

To deal with this challenge, you can wrap an *EditText* inside a *ScrollView* component. The ScrollView will act as a viewport to textual content of the EditText. 


~~~
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

	<ScrollView
		android:layout_width="fill_parent"
		android:layout_height="wrap_content"
		android:layout_weight="10"
	>

		<TextView  
    		android:layout_width="fill_parent" 
    		android:layout_height="wrap_content" 
    		android:text="I have nothing"
			android:id="@+id/tododisplay"
    	/>
	</ScrollView>
	<Button
		android:layout_width="fill_parent"
		android:layout_height="wrap_content"
		android:text="Add item"
		android:id="@+id/btnadd"
		android:onClick="recAdd"
		android:layout_weight="0"
/>
</LinearLayout>
~~~

There is no need to mess around with the Activity class. The scrolling functionality is accomplished on main.xml file
