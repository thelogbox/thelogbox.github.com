---
layout: javascript

title: RD JS Workshop.072012

description: Journal of RD batch 1. JavaScript fundamentals

excerpt: 

tags:
- Workshop
- JavaScript

---

You will need the nodejs runtime for this workshop. You will also need the node package manager (npm) which usually comes with the installation of nodejs.

## SETUP

1. Download the installer from [nodejs site](http://nodejs.org)
2. Run the installer
3. Get to the command line *cmd.exe* in Windows, *Terminal.app* in OSX, *xterm, aterm or gnome-terminal* in Linux
4. Get the http-server module via npm **npm -g install http-server**. If you are in Linux or OSX, you will need to type **sudo npm -g install http-server**

If you are using Windows, you may need to run the *cmd.exe* using an elevated privilege (as Administator)

***

## Day One

- JavaScript is not a new language, it started during the 90's
- It's first name is LiveScript, only renamed later to JavaScript
- ECMA stands European Computer Manufacturers Association. It's a big organization, it stepped in during the browser wars to come up with an effort to standardize a scripting language. They came up with a specification, this spec is called the ECMAScript. Any scripting language that runs on the browser should strive to comply with this standard. To date, JavaScript and ActionScript (and some others more) are complying with ECMAScript 5
- JavaScript is not related to Java. They are two very different languages

JS has dynamic typing. One of its meaning is that you don't need to declare the types of your variable, ever. It is also loosely typed or weakly typed. You can use the keyword **var** to declare variables, but sometimes you can also choose not to use it (which is a bad idea).

JS has a built-in function called typeof, you can use it to do some kind of reflection on types. 

<pre class="codeblock">

var anumber = 10;	//you don't need to say int anumber = 10
anothernumber = 20;	//this will work too, but this automatically adds anothernumber 
					//to the global context, which is a bad idea

anumber = "Hello World";	//JS will allow this, even if you declared anumber to a number
							//before. Be careful with things like this

console.log(typeof(anumber)); 

</pre>

***

## Day Two

**JS objects are like hash tables,** or dictionary objects. They contain just a bunch of key-value pair type of data. The *value* part of the object's members can be anything, Booleans, Numbers, Strings, Objects, Arrays or even Functions (because functions are also objects in JS)

It is easy to create objects in JS, there is more than one way, look the following code.


{% highlight javascript %}

// 1st way
var r = {};

r.name = "Rommel";
r.id = "006";
r.dept = "Admin";

console.log(r);

// 2nd way
var rommel = {
	
	name: "Rommel",
	id: "006",
	dept: "Admin"	
}

var s = r.name;
console.log(s);


//3rd way
var r2 = new Object();
r2.name = "Rommel";
r2.id = "006";
r2.dept = "Admin";

console.log(r2);

{% endhighlight %}

The 1st and 2nd methods (above) uses object literals to create objects. The 3rd method uses the Object() constructor. 

**Functions in JS are more than just an encapsulation unit** for codes. They are malleable, flexibile and weird at first. Consider the following codes;

{% highlight javascript %}

function goo() {

   return "Hello";   
   
}

console.log(goo())); // returns "Hello";

goo = 1;

console.log(goo);    // returns 1;
console.log(goo());  // fails now, because goo is no longer a function


{% endhighlight %}

This is what I mean by malleable and flexible, function names do not have special privileges, they can be created, assigned and reassigned pretty much like regular variables. While this looks like weakness right now, it is not. It is a feauture of the language---by the way, that horrible code sample where we reassigned goo() to be a number variable, can be (should be) prevented by good programming practice (conventions etc) and is probably highly unlikely to happen. 

***

## Day Three

Back to "malleability" being a feature rather than a weakness. The flexibility of JS functions makes them more than just a semantic feature of language, more than just an encapsulation unit for logic. It makes them "first class" members of the language. There is a definition on [WikiPedia about First Class Functions](http://en.wikipedia.org/wiki/First-class_function).  

You can use JavaScript functions wherever you can use an object (which is pretty much everywhere). You can assign objects to variables, and you can also assign a function to variable&mdash;note that you are assigning the function definition to the variable, you are not assigning the result of running the function to the variable, these are two different things. 

You can return objects from a function, you can return a function from a function as well (We did touch a little bit on currying, but we won't talk about currying just yet). You can pass functions as parameters to other functions, just like you can pass objects as parameters to functions. You can define properties for an object, you can define properties for a function as well (because functions are objects).  

{% highlight javascript %}

// an example of a function return another function

var x = function() {
	
	return function() {
		return "Goo";
	}
}

var a = x();

console.log(a());

{% endhighlight %}

You can add functions as a property of an object. This is possible because properties of objects can be of any type, it can be simple types or complex types, like object or arrays. You can conjure a pretty sophisticated data structure by nesting objects within other objects. Functions, being objects themselves, means we can add a function as a property of an object.  

{% highlight javascript %}

function Employee(nameparam, deptparam) {
	
	this.empname = nameparam;
	this.dept = deptparam;
	
	this.work = function () {
		console.log(this.empname + " is working")	
	}			
}


var rommel = new Employee("Rommel", "Admin");
var ted = new Employee("Ted", "SWD");
var pepper = new Employee("Pepper", "Admin");



console.log(rommel.empname);
console.log(rommel.dept);

rommel.work();
ted.work();
pepper.work();

console.log(Employee.constructor); // results to Function
console.log(rommel.constructor); // results to Employee

{% endhighlight %}

<aside>
**NOTE** the constructor property is present on all objects. It tells us which function was used to construct the current object. **function Employee** is not an employe object, it is a function object---see the result of running the code *Employee.constructor**. While the objects rommel, ted and pepper are Employee objects.
</aside>

**SEAT WORK** - construct a car objects, such that we can make the calls

{% highlight javascript %}

var toyota = new Car();

toyota.steering.goLeft();
toyota.engine.shift();

{% endhighlight %}

This challenge involves creating 3 objects, the *Car*, an *Engine* and a *Steering* object. The engine and steering objects are members of the Car object.

**SOLUTION**

{% highlight javascript %}

//solution 1

function Car() {
	this.engine = new Engine();
	this.steering = new Steering();
}

function Engine() {
	this.shift = function(){console.log("shifting");}
}

function Steering(){
	this.goLeft = function() {console.log("go left");}
	this.goRight = function() {console.log("go right");}
}

var toyota = new Car();
toyota.engine.shift();
toyota.steering.goLeft();


//solution 2

var Car = function() {
	
	this.engine = {
		shift : function() {
			console.log("shifting");
		}
	}
	
	this.steering =  {
		
		goLeft : function() {
			console.log("going left");
		},
		goRight : function() {
			console.log("going right");
		}
		
	}
	
}

var toyota = new Car();
toyota.steering.goLeft();
toyota.engine.shift();

{% endhighlight %}

Solution no. 1 is probably the more readable version because of its verbosity, but solution no. 2 is more compact and more concise. Use object literals sparingly, choose which style is applicable in your coding situation.

***

## Day Four


Your code will always run in a *context*. In JavaScript, these are the **global** context and the context of a function.  How you declare and where you declare your variables will determine their visibility or accessibility.

{% highlight javascript %}

// this is the global context. anywhere that is not inside a function

var i = 10; //global variable
x = 10; // another global variable, but I advise against doing this, always use var

function goo() {

	var igoo = 1; // this is not visible outside function goo()
	this.goo_name = "function goo name"; // this on the other hand is visible outside goo()
										 // but it is not a global variable

	aglobalvar = "I forgot to put var"; // this automatically becomes a global variable, if you omit 
										// the var keyword. CAREFUL with this

}

{% endhighlight %}

**ARRAYS**

Arrays in JS are also objects, but don't let that distract you. Think of arrays as a sequential data structure rather than the typical objects that we have been discussing in the last couple of days. Unlike regular objects where you access the elements using a *key* (because objects are associative arrays), in an Array, you access the elements using the index number of the element. 

Here are some ways on how might declare an initialize an array

{% highlight javascript %}

var a = []; //an empty array
var b = [1,2,3,4,5,6,7]; //an array with 7 elements
var c = ["Hello", "World", 1, 2.0, 0xFF]; //an array with members of diff types
var d = [[1,1], [2,2],[3,3]]; // an array with members, which are also arrays. 


// other way to declare arrays

var a = new Array(); //equivalent to var a = []
var b = new Array(1,2,3,4,5,6,7);
var c = new Array("Hello", "World", 1, 2.0, 0xFF);
var d = new Array(new Array(1,1), new Array(2,2), new Array(3,3));

var e = new Array(5); //with 5 new elements

{% endhighlight %}

To access the elements of the array, use the bracket notation, like so

{% highlight javascript %}

var i = b[0]; // the first element of the b array, which is 1
var x = c[1]; // the second element of the c array, which is "World"

{% endhighlight %}

I did say that JS Arrays are also objects (earlier), this is what I mean by that

{% highlight javascript %}

var x = [1,2,3,4,5];

x.thisname = "John";

console.log(x.thisname)

x.doSomething = function() {
	console.log("array doing something");
}

x.doSomething();

{% endhighlight %}

Don't get too confused about the code, the fact that an Array is an object, means you can really do these things---but should you? To get started on arrays, go for the simple usage first (bracket notations). If your abstraction of the problem at hand requires that you use this kind of programming idiom (arrays with your own custom methods), you may consider its usage then. It all depends on the problem you are trying to solve and the development goals you are after.

***

## Day Five

Discussion of the code below

{% highlight javascript %}

function window() {
	this.document = new docobject();
}

function docobject() {
	this.forms = new formcollection();
}

function formcollection() {
	this.form1 = new formobject();
	this.form2 = new formobject();
}

function formobject(){
	this.elements = new elementcollection();
}

function elementcollection(){
	this.input1 = new input();
	this.input2 = new input();
	this.input3 = new input();
}

function input() {
	
	this.innerhtml = "default inner html";
	
	this.click = function() {
		console.log("Clicked");
	}
}


var w = new window();

w.document.forms["form1"].elements["input1"].innerhtml = "Hello World";
w.document.forms["form1"].elements["input1"].click();
console.log(w.document.forms["form1"].elements["input1"].innerhtml);

{% endhighlight %}

An exercise on abstraction (and writing objects)

***

## Days Six, Seven and Eight

Coding exercises

The *GCF* exercise using client-side JavaScript and HTML

{% highlight html %}
<!-- Fourth.html -->
<!DOCTYPE html>

<html>
	<head>
		<title></title>
		
		<script src="fourth.js">
		
		</script>
	</head>
	<body>
		
		<form name="objform">
			First number  :<input type=text name=text1><br/>
			Second number :<input type=text name=text2><br/>
			<input type=button name=btn1 value="Click" onclick="foo()">
		</form>
		
		<div id="gcf">
		</div>
		
	</body>
</html>

{% endhighlight %}

{% highlight javascript %}

// Fourth.js

function foo() {
	
	var form1 = document.forms[0];
	var text1 = form1.elements[0];
	
	var text2 = document.forms["objform"].elements["text2"];
	var gcf = document.getElementById("gcf");
	
	
	var firstno = parseInt(text1.value);
	var secondno = parseInt(text2.value);
	
	alert(firstno + secondno);
	
	gcf.innerHTML = "This is the GCF";
		
}

{% endhighlight %}


**Fifth.html (inlined JavaScript).** A lot of things in the DOM can be clicked, and you can attach an *onclick* event even to DIVs in the DOM. This code sample shows that


{% highlight html %}

<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN">
<html>
	<head>
		<title></title>
		<script>
		window.onload = function(){
			document.forms["objform"].elements["btn1"].onclick = function(){
				btnclick();
			}
			
			document.getElementById("section1").onclick = function(){
				sectionclick();
			}
			
		}
		
		function sectionclick(){
			alert("clicked the div");
		}
		
		function btnclick() {
			alert("Hello");
		}
		</script>
		
		<noscript>
			You have to enable JavaScript
		</noscript>
		
	</head>
	<body>
	
	<form name="objform">
		<input type=button name="btn1" value="hey"/>
	</form>
	
	<p>
	<div id="section1" style="border: 2px solid gray; width:10%;">
	You can click me
	</div>
	
	
	</body>

</html>

{% endhighlight %}

**OnChange Example**. This code sample demonstrates the use of the *onkeyup* event using a *textarea* element. 

{% highlight html %}

<!DOCTYPE html>

<html>
	<head>
		<title></title>
		
		<script src="onchange.js">
			
		</script>
	</head>
	<body>
		<form name="objform">
			<textarea name="txtarea1" rows="10" cols="100" onkeyup="changetext()">
				
			</textarea>
			<p>
			<input type="button" onclick="btnclick()" value="click me">
		</form>
		<div id="writetome">
			This text will change
		</div>
	</body>
</html>

{% endhighlight %}

The code for *onchange.js* is below

{% highlight javascript %}

// onchange.js

function btnclick() {
	
	var txtin = objform.elements["txtarea1"];
	var txtout = document.getElementById("writetome");

	txtout.innerHTML = txtin.value;
}

function changetext(){
	
	var txtin = objform.elements["txtarea1"];
	var txtout = document.getElementById("writetome");

	txtout.innerHTML = txtin.value;
	
}

{% endhighlight %}

You can experiment with the other *onkey* events like **onkeypress** and **onkeyup**

***

## Day Nine

Using the canvas element 

The canvas is some sort of a viewport to a 2D rendering platform. The canvas is an ordinary tag that is part of the DOM. However, once you get the **2D context** using the canvas reference, you can now manipulate each invidivual pixel inside the canvas&mdash;to be clear, you will be writing to the 2d context, not the canvas itself. 

The canvas uses cartesian coordinates, it starts at **0,0**, x and y coordinates respectively. Negative X and Y values are not visible in the canvas. As the value of X increases, you move farther right, as Y increases you move down. Each integer value in the canvas stands for 1 pixel point.

An example declaration of the canvas element in HTML

{% highlight html %}

<canvas id="thecanvas" width=500 height=200>
 If the browser is not capable of displaying the canvas
 this message will be seen instead of a rendered 2D platform
</canvas>

{% endhighlight %}

You can omit the height and width attribute if you wish, but the canvas will default to 150 pixels tall and 300 pixels wide. 


The canvas API is rich and offers a wide variety of drawing basic elements like rectangles, circles, lines and text. Here's a sample code on how to use the canvas


{% highlight html %}

<!DOCTYPE html>

<html>
	<head>
		<title></title>
		
		<script>
		
		function woot() {
		
			var c = document.getElementById("mycanvas");
			var ctx = c.getContext("2d");
			
			ctx.fillRect(10,10,50,50);
			ctx.strokeRect(70,10,50,50);
			
			ctx.fillStyle = "rgb(255,0,0)";
			ctx.fillRect(10,70,50,50);
			
			ctx.strokeStyle = "#ababab";
			ctx.strokeRect(70,70,50,50);
			
			// DRAW LINES
			
			//The line is gray bec the curr strokeStyle
			//is #ababab
			
			ctx.lineWidth = 1;
			ctx.beginPath();
			ctx.moveTo(130, 130);
			ctx.lineTo(0,0);
			ctx.closePath();
			ctx.stroke();
			
			// DRAW some text
			
			ctx.fillText("Hello", 130,20);
			ctx.font = "40px serif"; // you can add italics here, just like in css
			ctx.fillText("Hello", 130,60);
			ctx.strokeText("Hello", 130,100);
			
			//DRAW CIRCLE
			
			ctx.fillStyle = "green";
			ctx.beginPath();
			ctx.arc(60,180,50,0,Math.PI * 2, false);
			ctx.closePath();
			ctx.fill();
			
			ctx.fillStyle = "orange";
			ctx.beginPath();
			ctx.arc(60,280,50,0,Math.PI, false);
			ctx.closePath();
			ctx.fill();
			
			//BASIC ROTATION
			
			ctx.rotate(Math.PI/4);
			ctx.fillRect(350,250,40,40);
			
		}
		
		function clearAll(){
			var c = document.getElementById("mycanvas");
			var ctx = c.getContext("2d");
			
			ctx.clearRect(0,0,300,150);
		}
		
		function getSize(){
			var c = document.getElementById("mycanvas");
			var ctx = c.getContext("2d");
			
			alert("width = " + c.width + "\nheight = " + c.height);
		}
		
		</script>
		
	</head>
	<body onload="woot()">
		
		<canvas id="mycanvas" style="border:1px solid gray;" width=500 height=500>
			If you are seeing this, you are using a really old
			browser
		</canvas>
		
		<p>
		<input type=button value="Clear all" onclick="clearAll()">
		<input type=button value="Size of C" onclick="getSize()">
		
		
	</body>
</html>

{% endhighlight %}



1. When you set the fillStyle, every subsequent fillRect calls will follow the fillStyle. The other fillRects which were already drawn prior to the call will not be affected.
2. you can use the call [canvasname].width and [canvasname].height to determine the size of the canvas

***

## Day Ten


To get the current location of the mouse, you can use the **event.clientX** and **event.clientY** information. Here's an example code on how to use it with the canvas


{% highlight html %}

<!DOCTYPE html>
<html>
	<head>
		<title></title>
		
		<script>
		
		var c = null;
		var cx = null;
		var output = null;
		
		var shouldIPaint = null;
		
		window.onload = function(){
			c = document.getElementById("mycanvas");
			cx = c.getContext("2d");
			
			shouldIPaint = true;
			output = document.getElementById("output");
			
			c.onclick = function(){
				shouldIPaint = !shouldIPaint;
			}
			
			c.onmousemove = function(){
				
				c.style.cursor = 'crosshair';
				
				output.innerHTML = "X : " + event.clientX + " | Y : " + event.clientY;
				cx.fillStyle = "#ababab";
		
				if(shouldIPaint == true){
					cx.fillRect(event.clientX-20,event.clientY-50,5,5);
				}
			}
		}
		
		function clearall(){
			cx.clearRect(0,0,c.width,c.height);
		}
		
		</script>
		
	</head>
	<body>
		<input type=button value="clear" onclick="clearall()">
		<p>
		<canvas id="mycanvas" width=500 height=400 style="border:1px dotted gray">
		</canvas>
		
		<div id="output">
		</div>
		<p>
			
		Additional complexity:<br>
		<pre>
		1. Use circles instead of squares
		2. Use line drawings
		3. Use bezier curves	
		</pre>	
		
	</body>
</html>

{% endhighlight %}

This works because the canvas's origin (0,0) is exactly the the 0,0 also of the HTML page. If the canvas is located somewhere else on the page, you should calculate some offset (the distance of upper left corner of the page from the upper left corner of the canvas element)

Apart from knowing where the mouse position is, you should add another tool to your programming arsenal, that of knowing which key the user is pressing. This information can be acquired using the **event.keyCode** property. Here is an example on how to use it.

{% highlight html %}

<!DOCTYPE html>
<html>
	<head>
		<title></title>
		<script>
		var c = null;
		var cx = null;
		
		var lastpos; // lets keep track of where we are
		
		
		window.onload = function() {
			
			c = document.getElementById("mycanvas");
			cx = c.getContext("2d");
			
			lastpos = {x:0,y:0};
			
			output.innerHTML = "READY";
			
			// arrow keys are only detected onkeydown, not onkeypress
			
			c.onkeydown = function(){
				
				var action = event.keyCode;
				
				switch(action) {
					case 37: // <-
						moveLeft();
						break;
					case 38: // ^
						moveUp();
						break;
					case 39: // ->
						moveRight();
						break;
					case 40: // V
						moveDown();
						break;
					default:
						break;
				}
			}
		}
		
		function showStat(key){
			var temp = "ARROW key : " + key + "<br/>";
			temp = temp + "curr X : " + lastpos.x + " | curr Y : " + lastpos.y;
			output.innerHTML = temp;
		}
		
		function draw(pos){
			cx.clearRect(0,0,c.width, c.height);
			cx.fillRect(pos.x, pos.y, 10,10);
		}
				
		function moveUp() {
			lastpos.y--;
			draw(lastpos);
			showStat("Up");
		}
		
		function moveDown(){
			lastpos.y++;
			draw(lastpos);
			showStat("Down");
		}
		
		function moveLeft(){
			lastpos.x--;
			draw(lastpos);
			showStat("Left");
		}
		
		function moveRight(){
			lastpos.x++;
			draw(lastpos);
			showStat("Right");
		}
		
		</script>
		
	</head>
	<body>
		<canvas id="mycanvas" width=500 height=300 style="border: 1px dotted gray;" tabindex=1>
		</canvas>
		<p>
		<div id="output">
		</div>
	</body>
</html>

{% endhighlight %}

By attaching the onkeydown event to the canvas, we can now begin to trap some keyboard events. I used **onkeydown** and not onkeypress because onkeydown is capable of capturing the navigational arrow keys, and onkeypress is not. The keycodes for left, up, right and down arrow are 37,38,39 and 40 respectively. 

***

## Day Eleven

**Color Wheel sample** - We can get very specific pixel information from the 2d context. The *getImageData()** function returns some interesting information about specific pixels. 

The following sample code uses demonstrates the usage of getImageData().


{% highlight html %}

<!-- imagedata.html -->

<!DOCTYPE html>
<html>
	<head>
		<title></title>
		
		<style type="text/css" media="screen">
			
			#canv {border:1px solid #ababab;}
			#coloroutput {border:1px dotted orange; width:50px; height:50px;}

		
		</style>
		<script type="text/javascript" charset="utf-8" src="imagedata.js">
			
		</script>
		
	</head>
	<body>
		
		<canvas id="canv" width=400 height=400>
		</canvas>
		
		<div id="coloroutput">
		</div>
		<p>
		<div id="textoutput">
			Color value
		</div>
		
		
	</body>
</html>

{% endhighlight %}


imagedata.js

{% highlight javascript %}

var c = null;
var cx = null;
var image = null;
var mousepos = null;

var textout = null;
var colorout = null;

window.onload = function() {
	
	c = document.getElementById("canv");
	cx = c.getContext("2d");
	
	mousepos = {x:0,y:0};
	colorout = document.getElementById("coloroutput");
	textout = document.getElementById("textoutput");
	
	image = new Image();
	image.src = "colorwheel.png";
	
	cx.drawImage(image,0,0,c.width,c.height);
	
	c.onmousemove = function(){
		
		//figure out first where the mouse is
		
		mousepos.x = event.clientX;
		mousepos.y = event.clientY;
		
		var imagedata = cx.getImageData(mousepos.x,mousepos.y,1,1);
		var pixel = imagedata.data;
		
		var pred = pixel[0];
		var pgreen = pixel[1];
		var pblue = pixel[2];
		var palpha = pixel[3];
		
		var color = "rgba(" + pred + "," + pgreen + "," + pblue + "," + palpha + ")";
		
		colorout.style.backgroundColor = color;
		textout.style.color = color;
		textout.innerHTML = color;
		
		
	}
}

{% endhighlight %}

The sample code could have defined the image in the HTML using the img tag, but then, the image would have been visible in the HTML before we could draw it inside the canvas. Our code instead defined and initialized the image using JavaScript code so that it is only visible in the canvas and on the HTML page. 

***

## Day Twelve

More on animation. 

First sample code is **anim.html**

{% highlight html %}

<!DOCTYPE html>

<html>
	<head>
		<title></title>
		<style type="text/css" media="screen">
		#canv {border: 1px solid #ababab;}
		</style>
		<script type="text/javascript" charset="utf-8">
			
		var c = null;
		var cx = null;
		
		var xpos = null;
		var xpos2 = null;
		
		var stopDrawing = null;
		
		
		window.onload = function(){
		
			c = document.getElementById("canv");
			cx = c.getContext("2d");
			
			xpos = 10;
			xpos2 = 10;
			
			stopDrawing = false;
			
			c.onclick = function(){
				stopDrawing = !stopDrawing;
			}
			
			draw();
		}
			
		function draw(){
			
			if(!stopDrawing){
				cx.clearRect(0,0,c.width,c.height);
			
				if(xpos > c.width){
					xpos = 0;
				}
				else{
					xpos++;
				}
				
				if(xpos2 > c.width){
					xpos2 = 0;
				}
				else {
					xpos2 += 5
				}
				
			
				//setTimeout(draw,30);
				cx.fillRect(xpos,10,40,40);
				cx.fillRect(xpos2,40,20,20);
			}
			setTimeout(draw, 30)
		}	
			
		</script>
	</head>
	<body>
		<canvas id="canv" width=500 height=250>
		</canvas>
	</body>
</html>

{% endhighlight %}

Anim.html moves two squares across the width of the canvas. There is a little bit of collision detection at work here, as soon as the boxes collides with the right boundary of the canvas, we reset the *x-position* of each box to zero, it makes the illusion that the squares are reappearing from the right boundary of the canvas. 

While this type of coding works for a few shapes, it is not a very good way to structure our code. You will find out (pretty soon) that adding another shape into the canvas involves keeping track of another x-position---the code will turn ugly and hard-to-maintain (rather quickly too). 

Anim2.html involves 3 shapes and sports a different behavior during collision, the shape bounces back to the opposite direction.

{% highlight html %}

<!DOCTYPE html>

<html>
	<head>
		<title></title>
		<style type="text/css" media="screen">
		#canv {border: 1px solid #ababab;}
		</style>
		<script type="text/javascript" charset="utf-8">
			
		var c = null;
		var cx = null;
				
		var stopDrawing = null;
		var s1 = null;
		var s2 = null;	
			
			
		window.onload = function(){
		
			c = document.getElementById("canv");
			cx = c.getContext("2d");
				
			stopDrawing = false;
			
			c.onclick = function(){
				stopDrawing = !stopDrawing;
			}
		
			s1 = new Square(0,10,60,60);
			s2 = new Square(30,90,20,20);
			s3 = new Square(60,140,10,50);
			
			s2.setAcceleration(30);
			s1.setAcceleration(5);
			s3.setAcceleration(9);
			
			draw();
		}
			
		function draw(){
			
			cx.clearRect(0,0,c.width,c.height);
		
			s1.move2();
			s2.move2();
			s3.move2();
			
			cx.fillRect(s1.x,s1.y,s1.width,s1.height);
			cx.fillRect(s2.x,s2.y,s2.width,s2.height);
			cx.fillRect(s3.x,s3.y,s3.width,s3.height);
			
			setTimeout(draw,33);
		}	
		
		function Square(x,y,width,height){

			this.x = x;
			this.y = y;
			this.width = width;
			this.height = height;
			
			this.direction = true; // move left, false is right
			
			var acceleration = 1;
			
			this.setAcceleration = function(accel){
				acceleration = accel;
			}
			
			this.move2 = function(){
				
				if(this.direction && (this.x + this.width) > c.width){
					this.x = c.width - this.width;
					this.direction = !this.direction;
				}
				else if(this.direction == false && this.x < 0){
					this.x = 0;;
					this.direction = !this.direction;
				}
				
				if(this.direction){
					this.x += acceleration;
				}
				else {
					this.x -= acceleration;
				}
				
			}
			
			this.move = function(){
				if(this.x > c.width){
					this.x = 0;
				}
				else{
					this.x += acceleration;
				}
			}
		}
		
		</script>
	</head>
	<body>
		<canvas id="canv" width=500 height=250>
		</canvas>
	</body>
</html>

{% endhighlight %}

The code keeps track of the direction of each shape using a *direction* variable inside each Shape constructor. Abstracting each shape to be inside an object does make our code a bit more effective in taming the the complexities brought about by adding new shapes into the canvas.  

***

## Day Thirteen

Topic for today and the days to come, is SVG (Scalable Vector Graphics) in HTML5. SVG is a standard W3C specification. The ability to insert SVG inside a page without using an object (or embed) tag was added to HTML5. SVG is also a drawing API, like the canvas, but it has some differences.

SVG uses vector graphics, these are groups of math formulas to draw primitives like lines, circles, rectangles and many more. The quality of SVG graphics do not degrade as they are scaled down or up in size, unlike a bitmapped or rasterized technique (which the canvas uses). Drawings in SVG are represented using XML instead of pure code &mdash; although you can produce SVG elements purely in code because SVG elements are addressable using the DOM API (unlike elements inside the canvas) 

**CODE WORKS**

{% highlight html %}

<!DOCTYPE html>
<html>
	<head>
		<title></title>
		
		<style type="text/css" media="screen">
		
		#mysvg {border:1px solid #ababab;}
		
		</style>
		
	</head>
	<body>
		
		<svg width=500 height=400>
			<rect id="rect1" x="10" y="10" width="50" height="50" />
			<rect id="rect2" x="70" y="70" width="50" height="50" />
		</svg>
		
		<div id="watch">
	
		</div>
	</body>
</html>

{% endhighlight %}

To insert an SVG drawing, create an SVG tag, specify the width and height using the attributes. To draw a rectangle, create a **rect** tag, specify the *x, y, width and height* attributes. 


{% highlight html %}

<!DOCTYPE html>
<html>
	<head>
		<title></title>
		<style type="text/css" media="screen">
		
		#mycanvas {border:1px solid #ababab;}
		
		</style>

		<script type="text/javascript" charset="utf-8">
		
		var r = null;
		
		
		window.onload = function(){
			
			r = document.getElementById("therect");
			
			r.onclick = function(){
				r.setAttribute("width", 200);
			}
						
		}
			
		</script>
		
	</head>
	<body>
		
		<svg width=500 height=200>
			<rect id="therect" x=10 y=20 width=50 height=100
			style="fill: #ababab; stroke:#000;"
			>

		</svg>
		<div id="watch">
	
		</div>
	</body>
</html>

{% endhighlight %}


The second example shows how attach an **onclick** event to the SVG drawing. As previously mentioned, SVG drawing elements are DOM addressable, they are part of the DOM, which means you can attach events to it just like you would say, a button, text or a DIV element. 


{% highlight html %}

<!DOCTYPE html>
<html>
	<head>
		<title></title>
		<style type="text/css" media="screen">
		
		#mysvg {border:1px solid #ababab;}
		
		</style>

		<script type="text/javascript" charset="utf-8">
		
		var rect = null;
		//var rectx = 0;
		
		window.onload = function(){
			rect = document.getElementById("therect");
			anim();
		};
		
		function anim(){
		
		
			var rectedge = parseInt(rect.getAttribute("x")) + parseInt(rect.getAttribute("width"));
			var svgedge = parseInt(document.getElementById("mysvg").getAttribute("width"));
			var rectx = parseInt(rect.getAttribute("x"));
			
			if(rectedge < svgedge){
				rect.setAttribute("x", rectx += 5);
			}
			else {
				rect.setAttribute("x", 0);
			}
			document.getElementById("watch").innerHTML = "rect " + rectedge + " | svg edge : " + svgedge;
			setTimeout(anim, 10);
			
		}
		
			
		</script>
		
	</head>
	<body>
		
		<svg id="mysvg" width=800 height=200>
			<rect id="therect" x=10 y=20 width=50 height=100
			style="stroke:gray;fill=gray;"
			>

		</svg>
		<div id="watch">
	
		</div>
	</body>
</html>

{% endhighlight %}

The third example demonstrates the use of *getAttribute* and *setAttribute* methods. This example animates the location of the rectangle by altering the **X** attribute of the rectangle drawing. 

***

## Day Fourteen

How to create SVG elements programmatically.

1. Create the outer SVG element using the *createElementNS* method of the **document** object
2. Attach the created SVG element to the page body using **document.body.appendChild()** method
3. Create SVG elements (such as rect) using the createElementNS as well
4. Attach the newly created SVG elements (rect in this case) to the SVG element using the appendChild method

{% highlight html %}

<!DOCTYPE html>
<html>
	<head>
		<title></title>
		<style type="text/css" media="screen">
		
		</style>

		<script type="text/javascript" charset="utf-8">
			
		var NS="http://www.w3.org/2000/svg";
		var svg = null;
		var rect = null;
		var watch = null;
			
		window.onload = function(){
		
			watch = document.getElementById("watch");
		
			svg = document.createElementNS(NS, "svg");
			svg.setAttributeNS(NS, "width", '700px');
			svg.setAttributeNS(NS, "height", '400px');
			
			//svg.width = 800;
			//svg.height = 400;
			
			rect = document.createElementNS(NS,"rect");
			rect.setAttribute("x", 10);
			rect.setAttribute("y", 10);
			
			rect.setAttribute("rx", 10);
			rect.setAttribute("ry", 10);
			
			rect.setAttribute("width", 50);
			rect.setAttribute("height", 50);
			
			document.body.appendChild(svg);
			svg.appendChild(rect)
						
			rect.onclick = function(){
				
				var svgheight = parseInt(svg.getAttributeNS(NS, "height"));
				var svgwidth = parseInt(svg.getAttributeNS(NS, "width"));
				
				var newx = Math.round(Math.random() * svgwidth);
				var newy = Math.round(Math.random() * svgheight);
				
				var message = "X : " + newx + " | Y : " + newy;
				rect.setAttribute("x", newx);
				rect.setAttribute("y", newy);
				watch.innerHTML = message;				

			}
			
		}
	
			
		</script>
		
	</head>
	<body>

		<div id="watch">
	
		</div>
	</body>
</html>

{% endhighlight %}

***

# RaphaelJS

[RaphaelJS is a small JavaScript library that simplifies working with SVG using JavaScript](http://raphaeljs.com). 

1. Download the RaphaelJS code from the [RaphaelJS site](http://github.com/DmitryBaranovskiy/raphael/raw/master/raphael-min.js)
2. Include the library as external JS file

{% highlight html %}

<script type="text/javascript" charset="utf-8" src="raphael-min.js">
</script>

{% endhighlight %}

3. Follow the vanilla sample on the RaphaelJS site to make sure everything is working

{% highlight html %}

<!DOCTYPE html>
<html>
	<head>
		<title></title>


		<script charset="utf-8" src="raphael-min.js"></script>
		<script charset="utf-8">
			
		var paper = null;
		
		window.onload = function(){
		
			paper = Raphael(0,0,500,300);
		
			var circle = paper.circle(200,150,100);
			
			circle.attr("fill", "#ffffff");
			circle.attr("stroke", "#000000");
			
			circle.click(circleclick);
						
		}
		
		function circleclick(){
			alert("Hello");
		}

			
		</script>
		
	</head>
	<body>
		
	</body>
</html>

{% endhighlight %}

The constructor call **Raphael(0,0,500,300)** is equivalent to writing

{% highlight html %}

<body>
	<svg width="500" height="300">
	</svg>
</body>

{% endhighlight %}

Another sample of using the RaphaelJS functions featuring some simple drag-and-drop capabilities

{% highlight html %}

<!DOCTYPE html>
<html>
	<head>
		<title></title>


		<script type="text/javascript" charset="utf-8" src="raphael-min.js"></script>
		<script type="text/javascript" charset="utf-8">
			
		var paper = null;
		var circle = null;	
			
		window.onload = function(){
				
			paper = Raphael(0,0,750,400);
			circle = paper.circle(150,150,70);
			
			circle.attr("fill", "#ababab");
			circle.attr("stroke", "#000000");
			
			var move = function(){
				circle.attr({cx: event.clientX, cy: event.clientY});
				circle.animate({r: 100, opacity: .25},100);
			}
			
			var start = function(){
				circle.attr({cx: event.clientX, cy: event.clientY});
			}
			
			var up = function(){
				//circle.attr({cx: event.clientX, cy: event.clientY});
				circle.animate({r:70, opacity: .5},100);
			}
			
			circle.drag(move,start,up);
			
				
		}
					
		</script>
	</head>
	<body>

		<div id="watch">
			X Y
		</div>
	</body>
</html>

{% endhighlight %}

The **drag** method attached to the circle object takes three **callbacks** parameters. On the first callback, write what you would like to happen during the initial mousedown event. On the second callback, write what you would like to happen during the mousemove and the final callback, write what you would like to happen when the user releases the mouse (mouseup).

 


