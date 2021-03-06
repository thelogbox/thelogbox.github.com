---
layout: androidtutorial

title: Database Programming 

description: Understand the basics of how to use SQLite in your mobile apps

excerpt: Database programming is probably the one of the most common programming task. Even entertainment oriented applications has a need for a database backend. The Android platform has a database library and runtime. That's SQLite3. This database is baked right into Android. There is no need for a separate installation activity.

author: Ted Hagos

tags:
- Database
- Introduction

---

While there exist a class of applications that do not use databases, they are few. It's almost an automatic expectation that a programmer knows how to deal with databases. 

We will use the built-in database of Android, **SQLite**. To use this database, we simply need to declare it in our *import* statements. This db is baked right into Android. There are no third party installs necessary.

If your background in Java database programming is JDBC or Hibernate or something else, there is a slight adjustment you need to make. You won't be able to use JDBC in Android. There is no JDBC in here. Don't worry too much. The SQLite API is not terribly difficult. It won't take you an afternoon to learn the basics.

## 1. Goals

To Display a simple form to the user. Let him type anything he wants on a free-form editable UI widget, an EditText View. 

To Get the runtime value of the EditText and insert it as a record in the database. Afterwhich, read the whole table and display the contents in scrollable, non-editable widget, a **TextView**

## 2. Basic Concepts

The class **SQLiteOpenHelper** is the middle-man that stands between your application logic and the database. You will use this to create and upgrade a database. You will also use it to get a handle on a readable and writable database. Think of it as a replacement of the Connection object in JDBC. 

Another class used in this example is the **SQLiteDatabase**. Think of it as the equivalent of the Statement object in JDBC. When you need to perform raw SQL statements, this is the class to use. 

Once we have created the database using **SQLiteOpenHelper** and captured some info from the UI, we need to deal with data retrieval. We need to find a way to get a handle on a readable database, pass a query to it, get the result of the query and save it somewhere else. The **Cursor** object is what we will use to store the results of the query. In JDBC you might remember this as the **ResultSet** object. 

Once we have a Cursor, we can simply iterate through it to process the contents of the database. 

## 3. How to

Create a new android project for this exercise. Add the appropriate View elements like TextView, EditText and Button.

~~~
$ android create project --target 15 --activity DbSample --path dbsample  --package com.thelogbox
~~~

To build a basic UI for our project, we can use the following code inside our **project_folder/res/layout/main.xml**

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

The **TextView** component is embedded in a **ScrollView** component so we can scroll through the contents of the TextView. The ScrollView acts like a viewport. We also used the **weight** property of the layout so our viewport is given the biggest portion of the screen. See the note on [how to use weights to maximize screen space](/android-layout-weights)

The **Button's** onClick property is a method called **recAdd()** which we need to implement inside on the Activity class. 

### 3.1 The SQLLiteOpenHelper Class

Create a class that extends SQLiteOpenHelper

~~~
// SQLiteOpenHelper .java

package com.thelogbox;

import static android.provider.BaseColumns._ID;
import android.content.Context;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;


public class DbHelper extends SQLiteOpenHelper {

  String sqlcreate = "CREATE TABLE todo( " + _ID  + " INTEGER PRIMARY KEY AUTOINCREMENT, item TEXT);";


  public DbHelper(Context ctx) {
    super(ctx,"tododb.db",null, 1);
  }
  
  @Override
  public void onCreate(SQLiteDatabase db) {
    db.execSQL(sqlcreate);
  }
  
  @Override
  public void onUpgrade(SQLiteDatabase db, int oldversion, int newversion) {
    db.execSQL("DROP TABLE IF EXISTS tododb.db");
    onCreate(db);
  }
  
}
~~~

You need to do **3 things** at a minimum when defining a SQLiteOpenHelper.

**1. Define a public constructor** that accepts a Context object.  This context is the context of the *Activity* class where you will instantiate the Helper class. Call the super constructor so that you don't break the chain. The first parameter to super constructor is the *context object* &mdash; you know this already, next parameter is the name of database you want to create; third parameter is a cursor factory, you can ignore this for now, that is why I passed *null* to it. 

The last parameter is an integer value which stands for the database version. I placed one (1) because it is my first version of this database. When you revise the schema of the database, increase this value by one so that the *onUpgrade()* method kicks in---it will perform some sort of an ALTER database command in your behalf.

**2. Override the onCreate()** method. This is where you can execute DDL (SQL Data Definition) commands against the database. 

**3. Override the onUpgrade()** method, even if you won't need it yet. You won't be able to compile unless you override this method

### 3.2 The Activity Class

We will use an instance of SQLiteOpenHelper class for reading and writing to the database


~~~
// Activity .java}

package com.thelogbox;

import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.content.Context; 
import com.thelogbox.DbHelper;
import android.content.ContentValues;
import android.database.sqlite.SQLiteDatabase;
import android.database.Cursor;
import android.widget.TextView;
import android.widget.EditText;


public class DbSample extends Activity {


  DbHelper dh;
  SQLiteDatabase dbwrite;
  SQLiteDatabase dbread;
  
  EditText input;
  TextView output;
  

   /** Called when the activity is first created. */
   @Override
   public void onCreate(Bundle savedInstanceState) {
        
      dh = new DbHelper(getApplicationContext());
      dbwrite = dh.getWritableDatabase();
      dbread = dh.getReadableDatabase();
      
    // you cannot put the findViewById here, it causes errors
      
    super.onCreate(savedInstanceState);
      setContentView(R.layout.main);
    }
    
    
    public void recAdd(View v) {

      input = (EditText) findViewById(R.id.todoedit);
      output = (TextView) findViewById(R.id.tododisplay);
    
    String itemtoadd = input.getText().toString();    
    
    ContentValues cv = new ContentValues();
    cv.put("item", itemtoadd);
    dbwrite.insertOrThrow("todo",null,cv);
    
    String temptext = (String) output.getText();
    
    //Write the dbExtraction routine here
    
    //temptext = temptext + "\n";
    output.setText(getTodos());
    
    }
    
    private String getTodos() {
      
      String cols[] = {"item"};
      StringBuilder sb = new StringBuilder("");
      Cursor cursor = dbread.query("todo",cols,null,null,null,null,"item");
      startManagingCursor(cursor);
      
      while(cursor.moveToNext()) {
        sb.append(cursor.getString(0));
        sb.append("\n");
      }
      return sb.toString();
    }
}

~~~

**DBSample** is a regular Activity class. It's bad coding practice to embed the database logic in the UI, but were just starting out to learn about databases in Android, we will let it pass for now. If we partition this app properly and use the nice design patterns, we will have more code to deal with (and to understand).

We instantiated the DbHelper class so that we can create the database during our first run of this app. We also used the DbHelper to create 2 SQLiteDatabase objects, one for reading (dbread) and another for writing (dbwrite). 

The **recAdd()** method starts out by getting the object references to the EditText and TextView components, todoedit and tododisplay respectively. 

Once we extracted whatever the user typed inside the EditText via **getText()** method, we stored it inside the **itemtoadd** String variable. 

The **ContentValues** object is some sort of a Dictionary data structure (key value pair), this data structure is required by the **insert()** method of the SQLiteDatabase object, that is why we used it to wrap the string data we got from the EditText. You don't have to use the **insertOrThrow()**< method if you don't want to, you can insert a record to the database using raw SQL. If you pass an INSERT SQL command inside the **execSQL()** method, that will do the job just as well.


Compile and Test the project

~~~
ant debug install
~~~

The **codeonCreate()*** method of DbHelper should kick in the first time your app issues a db related command. 

