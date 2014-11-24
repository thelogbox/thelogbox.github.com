---
layout: phonegap

title: Database Programming

description: Steps on how to use the SQLite Database of HTLML5 within PhoneGap applications

excerpt: 

tags:
- Database
- SQLite
- HTML5

---


<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- 468pxby60banner -->
<ins class="adsbygoogle"
     style="display:inline-block;width:468px;height:60px"
     data-ad-client="ca-pub-4627957463175380"
     data-ad-slot="5760679882"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>

There are two ways to persist data on PhoneGap. One is to use *local storage* and the other, *WebSQL*. Local Storage involves using a data structure that is similar to a dictionary. It has two columns. First column contains the key and the other has the value.  

The other way to persist data is to use the WebSQL API. This is probably the techmique that most developers would use for providing database functionality in a PhoneGap platform because it is also the more popular. Most programmers have been taught/schooled in database programming using relational databases, that's why SQL programming is almost a baseline capability for developers.

# Websql

WebSQL essentially is about issuing SQL commands against a SQLite3 databaseprogramming. If you haven't used SQLite before, it is a lightweight desktop database. It's a desktop database because it does not require a dedicated server side process unlike MySQL, Oracle or MS SQL Server &mdash; those things are called client-server databases.
  

Databases are good for a wide variety of programming tasks, but mainly they excel for information management, specifically structured record management. An introduction to SQL is beyond the scope of this chapter, in fact, I made a very dangerous assumption that you already have a backround in basic database programming. If you feel you need an introduction to SQL or you need a refresher on it, [the SQL introduction](http://www.w3schools.com/sql/sql_intro.asp) of W3Schools.com might be a good place to start.



Most database programs involves boiler plate codes &mdash; plumbing codes, so to speak. No matter what the database program is trying to do, it will always have to cover some generic steps e.g.

1. Open a connection to the database
2. Create a database or connect to an existing one
3. Execute SQL statements in order Create, Read, Update or Delete some records
4. Close any connection that you opened

In the next sections, we will cover the syntax for these boiler plate codes and demonstrate their usage. Towards the end of the chapter, we will use the WebSQL API for a simple TODO list app.

# Create and Open a Database

We will start with some basic codes that demonstrates how to create a database. We will also take a look at some ways on how we can test and debug our database codes without running the device emulator.

Best to create a new PhoneGap project so we can try out some database coding. 

<pre class="codeblock">

phonegap create db --name "DbCodes" --id com.thelogbox

</pre>

Go to the *WWW* folder and edit *index.html* so it looks like our sample code. 


{% highlight html %}

<!DOCTYPE html>
<html>
<head>
<meta charset=utf-8 />
<script>

var out = null;

window.onload = function(){
  
	console.log("onload");
  
  var dbname = "tasks";
  var dbversion = "1.0";
  var dbdisplayname = "TasksDatabase";
  var dbsize = 1024 * 1024;
  
  var db = openDatabase(dbname, dbversion, dbdisplayname, dbsize);
  
  if(db) {
   console.log("WebSQL API use is okay"); 
  }
  else {
    console.log("WebSQL API is not supported");
  }
};

</script>

<title>theLogBox Code Sample</title>
</head>
<body>
  <h1>Database</h1>  
</body>
</html>

{% endhighlight %}
<div id='lst'>index.html</div>

The above code is a typical usage of the <code class="codeblock">openDatabase()</code> API. The openDatabase function is a member of the *window* object, hence you can write the statement as <code class="codeblock">window.openDatabase()</code> &mdash; I did not have to do that anymore because the *window* object has a global scope. 

There are 4 things you need to pass to the `openDatabase` function, the database name, version, display name and size (in bytes). 

<aside>

WebSQL is already part of PhoneGap 3.0. Access to the database feature is no longer via the plugin architecture. This is the reason why you don't have to put your codes inside the *deviceready* callback. This is also the reason why you can test your database codes using just a simple browser. There is no need to deploy it to a device or run it in an emulator.  

</aside>


If you are using the Chrome browser, you can use the **Developer Tools** to inspect the datababase. As a web developer, it is in your best interest to be familiar with debugging and profiling tools &mdash; Google Chrome comes with such tools.

![Chrome Developer Tools](/img/phonegap/chrome-dev-tools.png)

Launch a browser and open the HTML file where you wrote the sample database code. You won't see anything interesting just yet, we've just created the database, but let's take a look under the hood. I hope you used Chrome for testing, because these coding and debugging exercises were all done using Google Chrome.  

Once the page is in view, go to the *Developer Tools* of Chrome, on the *Console* tab, you should see something like this.

![Database Creation](/img/phonegap/database-creation.png)

That is the effect of the `console.log()` code.  Anything you pass to the console.log function gets echoed to the *Console* tab of the dev tools. This is quite a handy way of debugging. It is also less intrusive than the JavaScript *alert()*.

Now click the *Resources* tab. You should see something like this.

![Database Creation](/img/phonegap/database-creation-resources.png)


<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- 468pxby60banner -->
<ins class="adsbygoogle"
     style="display:inline-block;width:468px;height:60px"
     data-ad-client="ca-pub-4627957463175380"
     data-ad-slot="5760679882"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>


Under *WebSQL* you can see that there is a newly created *tasks* database. This means our code ran as expected. 

You can try to refresh the page or run the JavaScript code over and over, but it won't create another *tasks* database &mdash; if that was you were expecting. The `openDatabase` command only creates a database file (*tasks.db*, in our case) if that file does not exist yet. If the specififed database name does exist, the openDatabase function will simply return an object handle to the database so you can start using it. The `openDatabase()` function is used both to create a not yet existing database file and to open an existing one.

# Creating Tables

After creating a database, you need to create some tables inside it. The tables are the actual data structures that holds structured information. In this section, we will simply create a single table named TODO. This table will hold our todo items. 


You will notice that all of our codes are sequential. The codes to create the database is immediately followed by the table creation, which in turn is immediately followed by some commands that insert data into the table. In practice, this is rarely the case. The routine to create the database and the table will most likely be confined to a special routine that is executed only once. The routine to insert records into the table will most likely be written in a call back function that corresponds to a user-triggered action e.g. a button click. I have written the following example in a rather simplistic and unrealistic way to improve clarity of the code and so that we won't get bogged down by detailed minutiae of event-handling.

{% highlight javascript %}

window.onload = function(){
  
  out = document.getElementById('output');

	console.log("onload");
  
  var dbname = "tasks";
  var dbversion = "1.0";
  var dbdisplayname = "TasksDatabase";
  var dbsize = 1024 * 1024;
  
  var db = openDatabase(dbname, dbversion, dbdisplayname, dbsize);
  
  db.transaction(createTable,createErr,createOkay);
  
  function createTable(tx){
    tx.executeSql("CREATE TABLE IF NOT EXISTS TODO (id INTEGER PRIMARY KEY AUTOINCREMENT, item TEXT UNIQUE)");
    tx.executeSql("INSERT INTO TODO(item) VALUES(?)", ["Brush your teeth"]);
    tx.executeSql("INSERT INTO TODO(item) VALUES(?)", ["Eat Vegetables"]);
    tx.executeSql("INSERT INTO TODO(item) VALUES('Brush your teeth again')");
  }
  
  function createErr(err){
    console.log("Err # : " + err.code);
    console.log("Err : " + err.message);
  }
  
  function createOkay(){
    console.log("Creation succeeded");
  }
};

{% endhighlight %}

You will use the *transaction()* function if you want to issue commands to the database. The transaction function takes three parameters and all of them are callbacks. The first parameter is the name of a function that will be executed. This first callback usually contains the series of SQL commands you would like to execute. A database transaction context is passed along as a parameter to this function. You will use that transaction context to invoke the *executeSql()* function which in turn contains the actual SQL commands.

<script async src="//pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
<!-- 468pxby60banner -->
<ins class="adsbygoogle"
     style="display:inline-block;width:468px;height:60px"
     data-ad-client="ca-pub-4627957463175380"
     data-ad-slot="5760679882"></ins>
<script>
(adsbygoogle = window.adsbygoogle || []).push({});
</script>

The second parameter is a callback which will only be invoked if an error will be encountered while executing your SQL commands. If and when this second callback is invoked, an *error* object is passed along to the function as parameter. You can use this error object to debug and troubleshoot your code.

The third parameter is called back after all the SQL commands have been executed and no errors have been encountered.






