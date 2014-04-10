---
layout: javascript

title: Guessing Game coding practice

description: 

excerpt: 

author: Ted Hagos

lastupdate: April 10, 2014


tags: 
- javascript
- jquery


categories: JavaScript

---


## Use case

When the page loads up, a picture will be shown. The user will guess who or what the picture is by typing his answer on the provided text field and clicking the submit button. 

If the user guesses correctly, proceed to the next picture and let the user guess again. If the guess is incorrect, display a "Try again message", clear the text field and await for the response.

## Solution approach 

Will make the html portion quite spartan. We won't use any fancy divs or nested tables so that we won't get distracted by styling clutter.  We will handle the image using the *img* tag. We will use the old school *input* element for the text field and we will use the *button* element for, well, the button.  

The JavaScript part of our solution will be in an external file named *script.js*, so our JS and HTML codes don't mingle up. We will use JQuery for DOM manipulation, surely by now you must be tired of typing *document.getElementById*. We can do this by embedding two *script* elements in the *head* region of the html code.


{% highlight html %}

<script charset="utf-8" src="jquery-1.11.0.js"></script>
<script charset="utf-8" src="script.js"></script>

{% endhighlight %}

The script tag above assumes that you have downloaded the JQuery library into your work area. It also assumes that the JQuery file and *script.js* is located on the same directory where the html file is.

The full code listing for the html part is below.

{% highlight html %}
<!DOCTYPE html>
<html>

<!--  index.html -->

<head>
  <script charset="utf-8" src="jquery-1.11.0.js"></script>
  <script charset="utf-8" src="script.js"></script>
  
  <style type="text/css" media="screen">
  
    #status {
      color: #CACACA;
      font-weight: normal;
    }
  
    * {
      font-family: Helvetica, Arial, serif;
    }
    
    img {
      display: block;
      margin-top: 30px;
      margin-bottom: 30px;
      height: 300px;
    }
    body {
      margin: 0 auto;
      width: 80%;
    }
  </style>
</head>
<body>
  <h4 id="status">The Status</h4>

  <img id="a"/>

  <input type=text id="answer">
  <button id="clickme">Submit</button>

</body>
</html>
{% endhighlight %}


### The JavaScript part

Create a file named *script.js* on the same folder where you created *index.html*. It is not necessary, neither it is always desirable to put the JS files on same folder as other files such as html or images, but we chose to do it that way to keep the codes and directory structure simple.

First thing we need to write is the block of code where we will put all of our subsequent JavaScript codes. Many other programs require such an entry point. If you have experience coding in other languages, you might remember that there is a function **main** which serves as the program entry point. In JavaScript however, you cannot simply write a function called **main** and proceed from there. Well, actually you can write a function and name it *main*, but that won't do anything. It will simply be a regular function. It won't have magical powers that makes it a program entry point. 

JavaScript is event aware. You can listen for events and then write code when that event is raised. There are two sources of events in our use case. The user will raise an event when he types his answer on the text field and when he clicks the button to submit his answer. The browser also raises events. When a page is pulled from a web server, it goes through some stages

1. It scans all the html tags and renders them
2. If you have some directives to pull files, e.g. a CDN hosted JQuery library, it will pull that from the server. When it is done processing the directives on the *head* region, it goes to the *body* region. At this point, it raises an event that the *body* part of the html document is being loaded. 
3. When it encounters a *script* tag, it momentarily stops rendering any html element. It needs to stop because JavaScript is capable of writing and changing the DOM (Document Object Model), the browser will wait for all the script tag to be processed before it can continue rendering html elements. When all the DOM elements have been processed, the browser raises an event saying that the "document is ready". 
4. If you have image tags, the browser will make another request to the server to download the image files
5. Once all the resources have been completely downloaded and rendered, the browser raises an event that says it the "window is ready". Ideally, this is the point where it is safe to do anything with JavaScript because all the DOM resources that your code anticipates, are already available. In some occasions, you might want to start doing things before the document is ready, say during *body onLoad* but for this example, we will wait for the document to finish loading. 


In order to write our program entry point, we will choose an event that the browser will raise, and use it as the entry point. 

{% highlight javascript %}

$(document).ready(function(){
  // this is our entry point
});

{% endhighlight %}

The above snippet is a JQuery code. It binds our code into *document.onload* event of the browser. When the browser has finished processing all the DOM elements in the html, it will raise the document.onload event. We are simply latching on to that event. Think of this code block as some sort of initialization routine. If you need to define arrays, variables or bind buttons to events, this is the place to do it.


### Make sure the simplest scenario is working

The best advice I have ever given to beginning programmers is to *make sure the simplest scenario is working*&mdash; next only to "don't forget the semi colon". A complex system does not start out to be complex, they start out as simple systems. They get complex in time. Make sure that the building blocks of your code are sound and that they are working.  

We need to make sure that our program entry point actually does something. A small noticeable change in the UI will do. Let's change the text of the heading element. 

{% highlight javascript %}

$(document).ready(function(){
  $("#status").val("hello there");
});

{% endhighlight %}

Open *index.html* using the browser. You should see the "Hello there" message when it loads. It will confirm that our code is actually running when the page loads. If you don't see the message, you need to check your code for spelling and other typing errors. If you know how to use the debugging tools in the browser such as *FireBug* in FireFox and the developer tools of *Chrome/Safari*, they will help you find the errors faster.

Next step is to display just a single image when the page loads. That can be managed using the following code

{% highlight javascript %}

$(document).ready(function(){
  $("#status").val("hello there");
  $("#a").attr("src", "bugsbunny.jpg");
});

{% endhighlight %}

The code above assumes the file *bugsbunny.jpg* is on the same folder where *index.html* and *script.js* are. Right after we get the IMG element using the #a selector, we changed the *SRC* attribute programmatically using the JQuery *attr* function. That code should display the contents of the image. 

Next thing to manage is accept user input via the text element and do something with when he clicks the button. For that, we need to bind the click event of the button to our code. 


{% highlight javascript %}

$(document).ready(function(){
  
  $("#status").val("hello there");
  $("#a").attr("src", "bugsbunny.jpg");
  
  $("#clickme").click(function() {    
    var useranswer = $("#answer").val();
    $("#status").html(useranswer);    
  });  
  
  
});

{% endhighlight %}

To bind the button to our code, we selected it via JQuery and invoked the the *click* function. The JQuery click function takes a single argument. You can put a named function inside it or an anonymous function. Either way, JQuery will call whatever you put inside the *click* function when the user clicks the button.
 
Our click handler is quite simple. It extracts the value of the text field and changes the message of the heading element to whatever the user has typed in the text field.

We will add some more codes so we can check the user's input against the correct answer.


{% highlight javascript %}

$(document).ready(function(){
  
  $("#status").val("hello there");
  $("#a").attr("src", "bugsbunny.jpg");
  
  $("#clickme").click(function() {    
    var useranswer = $("#answer").val();
    $("#status").html(useranswer);
    
    if (useranswer == "Bugs Bunny") {
      alert("correct");
    }
    else {
      alert("try again");
    }
  });    
});

{% endhighlight %}

An *if-else* statement provides a simple validation for our code. Note that the *if* branch is inside the click handler block. We will perform this check only when the button is clicked. If you place it outside the click handler block, it will be evaluated during *page load*&mdash;which does not make sense. 

The answer key in our example code is hard coded, in a real life application this should be pulled from a data structure like a database or a file.

At this point, we know we can display a picture, wait for a user's input and validate whether it is correct or otherwise. We can now use this as a building block for the more complex portion of the solution.

### Complexity




<img class=default src="/img/javascript/guessing-game.png"/>



{% highlight javascript %}
$(document).ready(function() {
  
  var gamedb = new Array();
  var currentround = null;
  
  Init();
  Draw();

  // EVENT HANDLER
  $("#clickme").click(function() {
    
    var useranswer = $("#answer").val();
    $("#status").html(useranswer);
    
    if (currentround.answertext == useranswer) {
      alert("correct");
      ClearText();
      Draw(); // Move on to the next round
    }
    else {
      alert("try again");
      ClearText();
    }    
  });
  
  function ClearText() {
    $("#answer").val("");
    $("#status").html("X");
  }
  
  
  function Init() {
    
    var round1 = {
      round: 1,
      picture : "bugsbunny.jpg",
      answertext : "Bugs Bunny"
    };
    
    var round2 = {
      round: 2,
      picture : "bart.jpg",
      answertext : "Bart"
    };
    
    gamedb.push(round1);
    gamedb.push(round2);
    
  }
  
  function Draw() {
    currentround  =  gamedb.shift();
    $("#a").attr("src", currentround.picture);
  }
  
});
{% endhighlight %}