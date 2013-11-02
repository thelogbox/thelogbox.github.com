---
layout: post

title: JavaScript Tutorial

description: A quick tour of the JavaScript language

excerpt: 

tags:
- Tutorial
- Language
- Basics

categories:
- JavaScript

---



<div id="update-history">
<strong>Doc History</strong><br/>
7.August.2012 &mdash; created<br/>
30.14.October.2012 &mdash; Added sections on Inheritance, DOM and event programming <br/>
</div>

<div id="minitoc">
<h3>Contents</h3>

0. Audience
1. Development environment setup
2. Code structure
3. Data Types and variable declarations
4. Functions
5. Keywords
6. Arithmetic
7. Boolean
8. Control of program flow
9. Complex data types
10. Anonymous functions
11. Objects (again)
12. Objects with Functions
13. Inheritance
14. Modularization
15. JavaScript in the browser
	- 15.1 Event programming
16. JQuery
17. TypeScript
18. CoffeeScript
19. Other stuff that compile to JavaScript
20. JavaScript on the Server
21. Asynchronous JavaScript
22. JavaScript, Android, IOS (mobile platforms)

<h3>Related tutorials/blog entries</h3>
- [HTML5 Canvas Programming](/html5-canvas-programming/)
- [TypeScript and HTML5 Canvas](/typescript-html5-canvas-cartersian/)
</div>


JS (JavaScript) is a loose, dynamically typed and interpreted  scripting language. It began life as LiveScript (1995); when it was a project at Netscape Communications. At some point in time, it was renamed JavaScript (roughly around the time when plugin support for the Java language was added to Netscape Navigator).

Java and JavaScript are not related to each other, not even remotely, they simply share a commonality in their names.

JavaScript's popularity maybe attributed to it's ubiquity amongst web pages (client side JavaScript), but it is actually being used in lots of places other than web pages. JS can be ran on the server (Node.JS), it can be used to do MVC type development of web apps (Backbone.JS) and it can also be used to stitch together a bunch of Java apps together (Rhino); these are just some of the other uses of JavaScript. 

JavaScript as we know it today, is the scripting language consistent with ECMAScript. ECMAScript is a standardized scripting language according to ECMA specification 262 and ISO/IEC 16262. ECMAScript exist in the form of JavaScript, ActionScript and JScript. If you are looking for language specification of JavaScript, you can look at the ECMAScript 262 specification---it is included in the Bibliography.

# About this tutorial

The tutorial has evolved overtime. When this was started, it aimed only to introduce the bare-boned JavaScript core language&mdash;without the attendant technologies e.g. DOM, JQuery, AJAX, node  etc. As it turns out, JavaScript is right in the middle of a lot of important and emerging technologies right now, hence, it is difficult not to mention the eco system of JavaScript technologies.

# Who is the intended audience 

I wrote this for an internal (company) programming workshop. It is **Part 2** of a 3-part programme for HTML5 programming. The participants had little (or no) prior programming background. Prior to JavaScript, the participants took up programming concepts using the Java language. 

This tutorial does not cover the fundamental concepts of programming. Neither does it cover the more advanced techniques of JavaScript. It aims to cover Core JavaScript (ECMAScript 5) language fundamentals. 


# 1. Environment setup

Chances are you already got most of the things you need. The JavaScript engine is found on modern browsers, so already got the runtime covered. The only thing you need to start is a decent programmer's editor. You can get by using the Notepad in Windows or TextWrangler (perhaps TextEdit) in OSX, I urge you however to invest a little bit on a programmer's editor--there are plenty to choose from, commercial software or opensource. 

I would urge you to download NodeJS environment because it comes in handy when you are trying to learn the core JavaScript language. The ability to whip up a quick JS source and run it on top of a JavaScript interpreter is surely quicker than setting an HTML container to run the JS code. You can download Node.JS from [NodeJS.org](http://nodejs.org)

On Linux and OSX, the *node* command did not need any setting up (I used brew install node on OSX and the apt-get on Debian Linux). If you install on another platform, you may need to configure *node* to be included in the SYSTEM PATH. To test if you can run the node, just invoke **node** from the command line. You should be greeted with a **>** prompt; then you know node is working.

  
# 2. Code structure

1. **Variable** - a temporary storage for something. It can hold any type of data 
2. **Literals** - e.g. 10 is Number literal, "Hello" is a string literal
3. **Expression** - involves operand(s) and operators. e.g. *a + b or 1 + a or 15 % 12*
4. **Statement** - similar to expressions. They are (optionally) terminated by semicolon. They can be written either inside a function or outside a function
5. **Function (method)** - a programming block that (usually) have a name. A programming block is a bunch of statements grouped together and enclosed inside a pair of curly braces
6. **Source file** - contains JS functions and statements. Usually has a *.js* extension


# 3. Data Types and Variable declarations

You need to know what kinds of stuff you can create, define and manipulate in JS. 

1. Number
2. Boolean
3. String
4. Array
5. Object
6. Function
7. undefined
8. null
9. Object

The first three are simple data types in JS, the rest are not so simple (don't worry, we will try to define the *not so simple* types a bit down the road)

**Number** - 10, 2, 100 (integers), 2.3, 1.2 (floats) are numbers. JS does not discriminate whether it is of integral or float type. There's more; 0xFF, 0xCAFEBABE (hex or octal) are also considered numbers, and so are base 8 numbers (i.e. 0377)

When you try to store a value that is more than what a Number can hold, it can result to either *Infinity* or *-Infinity*. You can also get some weird results is *NaN* (not a number). The NaN can result if you try to do some illegal operations, i.e. divide something by zero. 

**Boolean** - either *true* or *false* 

**String** - A sequence of UNICODE characters, although, there is no concept of character arrays in JS. You can define Strings using either the single quote or double quote technique. i.e. "Hello World" is as good as 'Hello World'. You may insert escape characters in Strings like "Hello\n World".

We will deal with the other data types a little bit later, these three are actually enough to keep us busy for now. 

You will usually bother with data types when you are either declaring variables or returning something from functions. If you need to see for your eyes how the JS runtime really treats this variable, this small code snippet should help


{% highlight javascript %}

/*

A small test on how JS treats types

*/

var s = "hello";
var int = 1;
var float = 1.0;
var boolean = true;
var vnull = null;
var vundefined = undefined;
var obj = new Object();
var arr = new Array();

function x() {
	return 1;
}

function y() {
	return
}

function z() {
	
}

// Let's see the typeof results

console.log("s " + typeof(s));
console.log("int " + typeof(int));
console.log("float " + typeof(float));
console.log("boolean " + typeof(boolean));
console.log("vnull " + typeof(vnull));
console.log("vundefined " + typeof(vundefined));
console.log("obj " + typeof(obj));
console.log("arr " + typeof(arr));
console.log("function x " + typeof(x()));
console.log("function y " + typeof(y()));
console.log("function z " + typeof(z()));
console.log("wildcard " + typeof(wildcard));

/*

RETURNS:

s string
int number
float number
boolean boolean
vnull object
vundefined undefined
obj object
arr object
function x number
function y undefined
function z undefined
wildcard undefined

*/

{% endhighlight %}


Variables can be declared using the word **var** (or without). I would rather that you always declare your variables using *var* because it has some effects on the *global context*--which we will discuss in a bit.


# 4. Functions

A JS function is named code-block. A code block is a group of statements tucked inside a pair of opening and ending curly brace. 


{% highlight javascript %}

/*
File name: hello.js
The hello world program in JavaScript
*/

foo();

function foo() {
	var s = "Hello World\n";
	console.log(s);
}

{% endhighlight %}

If you installed node.js (and I hope you did) you can run try this out on the command line using **$ node hello.js** 

The hello.js program is actually more verbose than it has to be,  it could have been written as <code class="codeblock">console.log("Hello World");</code>


I wrote it that way to demonstrate a few more JS characteristics. /*    */ are comments. Comments are non-executable codes, the interpreter will ignore them, but they are useful in putting reminders or markers in your code. It can help others read your code as well. 

Functions are defined in JavaScript by using the word **function** then give it a name (hopefully a descriptive one), put open and close parentheses immediately after the function name, then put the pair of curly braces. 

The *console.log()* command is the STDIO library of Node.JS (although some browsers include this as part of their JavaScript runtime). This command routes the output to stderr and stdout (the command line screen) 

<pre class="codeblock">

CANONICAL FORM OF THE FUNCTION

function <name> (<parameters) {
  // statements
  [return <value>]
}  
  
</pre>

Functions can contain a *return* statement, take note of the following though;

1. Calling a function without a return statement - returns undefined
2. Calling a function with return statement, but does actually return anything - returns undefined
3. Calling a function with a return statement and a proper return value - returns the value

<span class="stress">CAUTION:</span> careful how you write your curly braces, JavaScript's defaults might produce unexpected results, see the following code

{% highlight javascript %}

function goo() 
{

	return
	{									// this line is unreachable
		objprop: "Some obj property";
	}

}

{% endhighlight %}

The statement will be unreachable because JavaScript would have inserted a semi-colon right after the **return** statement. The object literal is unreachable as a return value.


Functions are different from JS statements. Statements are executed at once as soon as it is encountered by interpreter. Functions on the other hand are *compiled* first, they are not executed when first encountered, intead, it will be parsed and stored for later use. 

Theres a lot more to JavaScript functions but we will stop here for now. The other characteristics of functions are better explained when we are the context of Object Oriented JavaScript and some more advanced concepts.


# 5. Keywords

When you create identifiers, e.g. variable names, function names and class names, you need to stay away from certain words--the JavaScript reserved words. Here they are;


- break case catch continue debugger default
- delete do else finally for function if in
- instanceof new return switch this throw try
- typeof var void while with implements
- interface let package private protected
- public static yield class enum export 
- extends import super


Read the ECMA specification for keywords, I just listed them here for convenience. 

# 6. Arithmetic Operators

These operators behave exactly as they behave in your calculator. + for adding, - subtracting, * multiplying and / for performing division. The only other operator in the arithmetic arsenal is the modulo (%) operator. It also performs divsion, but instead of giving you the quotient, it gives you the remainder. e.g. *156 % 12* gives you 3

# 7. Boolean operators 

These operators allows you to compare things logically and do some equivalence tests. Boolean expresssions yields either true or false. 

The *&&* (logical AND), *||* (logical OR) and the *unary NOT !* operator allows you to perform logical comparissons. 


The **&&** operator yields true only if both operands are result to true. If you are coming from another language where this symbol has a short-circuit behavior, be careful. This operator evaluates both operands before yielding the truth value.

{% highlight javascript %}

/*
	Simple test for && operator
*/


console.log(a() && b());

function a() {
	console.log("inside a");
	return true;
}

function b() {
	console.log("inside b");
	return false;
}

RESULT:

inside a
inside b
false

{% endhighlight %}

the **||** operator on the other hand requires that only one of the operands is true for the expression to return true. 

{% highlight javascript %}

/*
	Simple test for || operator
*/


console.log(a() || b());

function a() {
	console.log("inside a");
	return true;
}

function b() {
	console.log("inside b");
	return false;
}

// RESULT:

// inside a
// true

{% endhighlight %}

The || operator did not even evaluate function b() before returning the truth value. 


The other boolean operators **== != > < <= >=** and **!** are straight forward, you can read them in the ECMAScript specification if you prefer. 




# 8. Control of program flow

You will need to know how to direct program flow. There are 3 ways; execute statements one after another (sequencing), execute some statements when some condition is true (branching) and performing some statements repeatedly while some conditions are true (looping or iteration). 


<span class="stress">if-else statement</span> is way to branch. When the expression inside the **if()** construct yields true, the statement inside the if block is executed. 


{% highlight java %}


var i = 10;

if (i == 20) {
	console.log("true");
}
else {
	console.log("nah!");
} 

// RETURNS nah!

{% endhighlight %}

Be careful when writing your comparisson operator. Here's a slightly modified version of the code above

{% highlight javascript %}

var i = 10;

if (i = 20) {
	console.log("true");
}
else {
	console.log("nah!");
} 

// RETURNS true

{% endhighlight %}

Can you spot the difference? The expression inside the if() construct is improperly written as an assignment rather than a test for equality--but JavaScript went to evaluate it anyway. Be careful with this one because this mistake is so easy to make. The reason this returned **true** is because an arithmetic assignment operation returns the zero value, and if you use a number where a boolean expression is expected, the number is convered to the *true* value. 


<span class="stress">Switch statement</span> is another way of branching. It is a bit more concise than the if-else statement, it allows for a different kind of construction. 

{% highlight javascript %}

var s = "hello";
var ret;

switch (s) {

	case "he":
		ret = "he";
		break;
	case 1:
		ret = 1;
		break;
	case true:
		ret = "true";
		break;
	case "Hello".toLowerCase():
		ret = "Hello";
		break;
	default:
		ret = "nothing";
}

console.log(ret);

/*

RETURNS "Hello"

*/

{% endhighlight %}

The values listed in *case* statements can be Strings, booleans or numbers (a bit of a relief if you are coming the Java language where the case is restricted to integer values). Always add the *break* keyword inside the case statement lest you will have unintended consequences--without the break keyword, the program will overflow to the remaining statements of the *switch construct* even if a match has already been found. 


<span class="stress">While statement</span> is a looping mechanism. It requires a boolean value (or an expression that yields a boolean value) inside the **while()** construct. The statements inside the while block will be executed repeatedly as long as the expression inside while() is true. When the expression is no longer true, the loop terminates. 

{% highlight javascript %}

var timetoexit = false;
var counter = 0;

while (!timetoexit) {
	console.log("counter = " + counter);
	if (counter++ == 10) timetoexit = true;
}

{% endhighlight %}

You can use the **break** keyword to break out of loops, like this


{% highlight java %}

var timetoexit = false;
var counter = 0;

while (!timetoexit) {
	console.log("counter = " + counter);
	if (counter++ == 10) break;
}

{% endhighlight %}

The break keyword causes the program flow to ignore all the statements (if there are any) immediately following the *break* keyword and fall right outside the end of the while block where the program flow will resume.  

Another keyword related to loop structures is the **continue** keyword. It causes program flow to jump also

{% highlight java %}

var timetoexit = false;
var counter = 0;

while (!timetoexit) {

	console.log("counter = " + counter);
	if (++counter == 10) {
		timetoexit = true;
		continue;	
	}
	console.log("*");
}

{% endhighlight %}

Unlike *break* though, **continue** causes program flow to ignore all the remaining statements until the end of the while block and jump right away to the beginning of the while loop---forcing the condition to get re-evaluated; this is the reason why our last asterisk never got printed. 


<span class="stress">For statement</span> is another looping mechanism. The for loop like the while loop allows you to iterate and perform a group of statements over and over again. 


<pre class="codeblock">

  CANONICAL FORM

  for ([where to begin] ; [where to stop] ; [step]) {

  }
  
  
</pre>


A key concept in using the for loop is the counter (the step). Loop will perform all the statements inside the block for a finite and determined number of times. Each time that the whole block is evaluated, the step value is incremented. The incremented step value is then compared to the ending value, and when the ending value is reached, the for loop will then terminate. The program control will fall over to first statement immediately after the for loop block.

{% highlight javascript %}

for (i = 1 ; i < 10 ; i++) {

	console.log(i);

}

{% endhighlight %}

The code sample above defines the starting point at 1 (i = 1), it will stop the loop execution when *i < 10*.  Each time the *for* loop is evaluated, the i variable will be incremented by 1 (i++).

Here is a another sample of the for loop.

{% highlight javascript %}

var util = require('util')

var i = 1;
var j = 1;

for (i = 1 ; i < 10; i++) {

    for (j =1 ; j < 10; j++) {

        util.print(i * j + "\t");

    }

    util.print("\n");
}


/*

RESULT

1   2   3   4   5   6   7   8   9   
2   4   6   8   10  12  14  16  18  
3   6   9   12  15  18  21  24  27  
4   8   12  16  20  24  28  32  36  
5   10  15  20  25  30  35  40  45  
6   12  18  24  30  36  42  48  54  
7   14  21  28  35  42  49  56  63  
8   16  24  32  40  48  56  64  72  
9   18  27  36  45  54  63  72  81

*/

{% endhighlight %}


This code requires the node.js library *util*. We can't use the STDIO (console.log) here because it automatically adds a CRLF (carriage return-line feed) while *util.print()* library does not. Node.JS has many libraries for convenient use, you just need to do the *require(libname)* statement if you want to use it. 


# 9. Complex data types 

JS has some containers (stuff that can contain other stuff, that can contain other stuff … ). We will take a look at two of them right now &mdash; Arrays and Objects. These are not simple types like Numbers or Strings or Boolean. Instead of representing single values, Objects and Arrays can represent a collection of values. 


*** 

*OBJECTS*. Lots of things are considered objects in JavaScript, even arrays and functions are objects, but let's not get distracted by that right now. Think of an object like a dictionary or the telephone yellow pages. It is just a collection of stuff. This stuff though has a format, it comes in pairs. The first part of the pair is a key, the other part of the pair is a value. Using the yellow pages analogy, the key is probably a person's name or name of a business. The value is the address or the phone number. The key has to be unique, you cannot have more than one key with exactly the same name. 

The value part of each pair could be anything. It could be simple data (Numbers, Booleans, Strings) or it could be complex data (Arrays, Objects or functions).

There are a couple of ways to create objects in JS.

1. Using object literals
2. Using the new keyword against the Object type
3. Constructor functions

Try your best to ignore number 3 above (at least for now) -- we will circle around that later when we get to JavaScript OOP.

<span class="stress">Using Object literals</span>

{% highlight java %}

var obj = {} // this one constructs an empty object
var pt 	= {x:0, y:0} // an object with simple data types as members
var person = {

	name: "John Doe",
	email: "johndoe@somewhere.com",

} // an object that has two members, both of which are Strings

{% endhighlight %}

When you use object literals to initialize objects, don't forget to separate the pairs using comma. You can add properties (the key-value pair) to objects by simply declaring the member--using the dot notation--and assigning them values


~~~

person.date_hired = "some date value";
person.address = "some address";

~~~

Similarly, you can access values of the object properties using the dot notation as well, although this is not the only way.

~~~

console.log(person.name);
console.log(person.address);

~~~

JavaScript's use of dot notation to access object properties and method will feel very familiar with devs because a lot of programming languages utilizes this notation too. What might not feel familiar will be the fact that JS can also access object properties using square brackets. Like this

~~~

person["name"];
person["address"];

~~~

JS objects are actually associative arrays---I need to clarify one point, when I write **Array** (capitalized) I am referring to the JavaScript complex type. When I write **array** (lowercase) I am referring to the array data structure in general, what I mean by this is a collection of rows (and sometimes columns). An object looks like an array because it a collection of **named** values, this is the reason you can use the square braces approach to reference a member of a specific object. 

***

*ARRAYS*. An Array is also a collection of values. Unlike an object, an Array is a collection of *ordered values*, not *named values*. Each member of an Array is called an element. Each element is denoted by a numeric position in the array--the position is called an index. Like objects, Arrays can be created using a variety of ways;

~~~

var a = []; //an empty array
var b = [1,2,3,4,5,6,7]; //an array with 7 elements
var c = ["Hello", "World", 1, 2.0, 0xFF]; //an array with members of diff types
var d = [[1,1], [2,2],[3,3]]; // an array with members, which are also arrays. 

~~~

The other way to create an Array is to use the **Array()** constructor

~~~

var a = new Array(); //equivalent to var a = []
var b = new Array(1,2,3,4,5,6,7);
var c = new Array("Hello", "World", 1, 2.0, 0xFF);
var d = new Array(new Array(1,1), new Array(2,2), new Array(3,3));

var e = new Array(5); //with 5 new elements

~~~

If you call the Array constructor with a single integer as parameter, it means you are specifying the length of the Array--you are not declaring an array with a single element, and the number you passed is the value of the first element.

Array members can be retrieved by accessing the individual elements. Arrays are zero-based, hence the first element is index 0.


~~~

b[0] =  8; //assigns the value 8 to the first element of the Array
console.log(b[2]); //prints the value of the third element (remember, zero based)

~~~

The characteristic of arrays having index positions makes them ideal for iterating using a for-loop. You cannot access members of an array using the dot notation--like you did when you accessed members of an object.


# 10. Anonymous Functions

We have already taken a look at functions earlier. At first glance, functions in Javascript does not seem too special. Like in any other language, we used it to contain a bunch of statements and gave it a name. This name, when we call them at a later time, will execute the set of commands inside its block. We use the function simply as an encapsulation unit for a sequence of statements.

Functions in JavaScript has some twists that may seem weird at first (depending on where you are coming from). The dynamic characteristic of the language presents a lot of possibilites&mdash;and some suprises too. Take a look at the following code

{% highlight java %}

function foo() {
	return 10;
}

console.log(foo()); 	//nothing surprising here, it will return 10

foo = "Hello World"; 	//This is allowed in JS, because it is not strongly typed
console.log(foo); 		//This will now output "Hello World". It has already forgotten that it was a function
						//befor

console.log(foo());		//this one will throw an error, because foo is no longer a function

{% endhighlight %}

JavaScript function names are not that different from ordinary variables. You can assign them values, just like how you would an ordinary variable. Similarly, you can assign functions to variables; like this

~~~

var foo = function() {
	return 10;
}

console.log(foo()); //returns 10

~~~

This is another way to create a function. Notice that the function on the right hand side of the equal sign does not have a name. Notice also that we can assign it to a regular variable named "foo" then invoked **foo()**. What we have just done was create an anonymous function and assigned it to variable *foo*. It is called an anonymous function, for obvious reasons, it does not have a name. There are other ways to create functions in JS, but we will stop here because we don't have any further use for another way to create a function, what we have is quite enough for now.

# 11. Objects, again


A few things we need to remember (or know for the first time) about objects. *Objects in JS are reference types*, they are not value types, you can declare as many reference variables pointing to the exact same object

{% highlight javascript %}

//filename: multiref.js

var obj1 = {
	name: "firstobject"
}

var obj2 = obj1; // both obj1 and obj2 reference var is pointing to the same object
console.log(obj2.name); //exact same property as obj1

obj2.anothername = "still first object";
console.log(obj1.anothername); //obj1 should have "anothername" as well, because 
							   //object 2 is pointing to the same object 
							   //being referenced by obj1

{% endhighlight %}

*2. Some object's structure can be modified (mutable)*.  An array is actually an object, it is a good example of an object that is mutable. Mutability means that as you modify the content or structure of the object, it does not spawn or create newer objects. It modifies the original object that was created. 

*3. And then, some objects cannot be modified (immutable)*.  The String objects that you create are such examples of immutable objects in JS. To add this list, Numbers and Booleans (when wrapped) are also immutable. What this means is that if you apply transformations to immutable objects, they will not modify the original object that was created. The transformation will cause the object to create a new object. 

{% highlight javascript %}

var assert = require('assert');

var s = "A String";
var stemp = s;	//s and stemp points to "A String"

assert(stemp == s, "checking is s is equal to stemp"); // result is ok

s = s + "Hello World";

assert(stemp == s, "checking is s is equal to stemp"); // result not ok

{% endhighlight %}
	
If Strings are mutable, then the second assert would not have failed. The references "s" and "stemp" are simply no longer pointing to the same object. Any transformation that you apply on an immutable object will cause the creation of a new object, the original content plus any transformation you applied will now be contained inside the new object. By the way, **assert** works pretty much like a test for truth or falsity, but it behaves violently. When the expression inside the assert (the asserted value) does not evaluate to true, your code will fail with a pretty ugly run-time error. Defensive programmers use this to test their codes mercilessly, better that the code fails during development time, rather than the code failing in front of hte users. 

*4. Pass by Reference*

{% highlight javascript %}


function Base() {

	this.prop1 = "Property 1"

}

var a = new Base();		// Property 1
console.log(a.prop1);

paramPass(a);
console.log(a.prop1);	// Altered prop1


function paramPass(arg) {
	arg.prop1 = "Altered prop1";
	console.log("While inside ParamPass : Base.prop1 = " + arg.prop1 );
	// this outputs Altered prop1
	return 0;
}

{% endhighlight %}

When you pass object references to functions as parameters, whatever changes you make to the object (that was passed) will endure even after the function goes out of execution scope.

# 12. Objects with Functions


Objects are easy to create, construct and modify in JS. Adding a property to an object takes nothing more than declarating the name of the property (attached to the object using the dot notation), then simply assigning a value to to it. Just don't forget that objects in JS are like hash tables, each member of the object is a pair of data, the first one is the key and the second one is the value. 

You can put any type of member inside an object. A member could be any data type in JS, simple data or complex data&mdash;which means you can put another object inside another object. This is the part we need to make a leap on our JS knowledge. **Functions** in JS are objects as well, that's right. Which means, we can put functions inside objects, and when functions are inside objects, they become methods of the objects. 

{% highlight javascript %}

// file: obj3.js

var employee =  {
	
	name: "Ted", 
	work: function() {
		console.log(this.name + " is working")
	}
}

employee.work();

{% endhighlight %}

The preceding code sample is straightforward, it is a simple creation of an object using object literals. The second property though, used an anonymous function which was assigned to the property named "work". When we invoked the *work()* property as function&mdash;as we should, because it is a function, it then executed whatever was defined inside the function block.  

If we need another object, we need to repeat whatever we did on the first employee object, like so;


{% highlight javascript %}

var employee =  {
	
	name: "Ted", 
	work: function() {
		console.log(this.name + " is working")
	}
}

employee.work();

var rommel = {};
rommel.name = "Rommel";
rommel.work = function() {
	console.log(this.name + " is working");
}

rommel.work();

{% endhighlight %}

While this is perfectly legal to do, the idiom used in creating the *rommel* object is bit bitter to the taste, surely, there has to be a way to achieve some sort *Object factory* idiom in JS. The code is too malleable (it could be a good thing though). It seems that following this idiom, one can pretty much add properties as you go along. I am sure there is a class of problems where this kind of flexibility and malleability is desired, probably necessary even. Coming from a language that supported classical OOP (like Java), it can send some chill on the spine knowing that I could easily change properties of my object anywhere in the code. Fortunately, JS is very orthogonal language&mdash;there are lots of ways of achieving same results, so let's look for something more palatable for classical OO programmers.

{% highlight javascript %}

// Employee object: Template

function Employee(name,id, dept) {
	this.name = name;
	this.id = id;
	this.dept = dept;	

	this.work = function () {
		console.log(this.name + " is working")
	}

}

// Company object: Template

function Company() {
	this.employees = [];
	
	this.recruit = function(employee) {
		this.employees.push(employee);
	}
	
	this.listEmployees = function() {
		arrlength = this.employees.length;
		for (i = 0; i < arrlength; i++) {
			console.log(this.employees[i]);
		}
	}	
}


var ted = new Employee("Ted H", 39, "swd" );
var kit = new Employee("Kit A", 31, "swd");
var pepper = new Employee("Pepper F", 2, "admin");

var rd = new Company();


rd.recruit(ted);
rd.recruit(kit);
rd.recruit(pepper);

rd.listEmployees();

{% endhighlight %}

The preceding code feels a bit firmer than the one before it. This code used the function as some sort of constructor (actually, it is called exactly that, a function constructor). JavaScript does not have class mechanisms like Java or C++. Code reuse is not achieved by class extensions, but rather by Object extensions. By the way, this last code we just did sure looks a lot like the class mechanism, if you could just get over the fact that it said **function** rather than *class*. 

There a couple of things we need to talk about in this code, specifically they keyword **this**, but before we go there, let's look at another code, it is exactly the *Employee* and *Company* constructor code also, but with a bit of modification. 

{% highlight javascript %}

// Company.js

// Employee object: Template

function Employee(name,id, dept) {
	this.name = name;
	this.id = id;
	this.dept = dept;	
}

Employee.prototype.work = function () {
	console.log(this.name + " is working")
}


// Company object: Template

function Company() {
	this.employees = [];
}

Company.prototype.recruit = function(employee) {
	this.employees.push(employee);
}

Company.prototype.listEmployees = function() {
	arrlength = this.employees.length;
	for (i = 0; i < arrlength; i++) {
		console.log(this.employees[i]);
	}
}

var ted = new Employee("Ted H", 39, "swd" );
var kit = new Employee("Kit A", 31, "swd");
var pepper = new Employee("Pepper F", 2, "admin");

var rd = new Company();


rd.recruit(ted);
rd.recruit(kit);
rd.recruit(pepper);

rd.listEmployees();

{% endhighlight %}


# 13. Inheritance 

You can use JavaScript pretty much in a procedural way--what I mean by that is, without using coarse grained abstractions for interesting objects of your problem domain--but as soon as you find yourself coding way past 300 lines of code (give or take a 100 lines), you might find yourself in a (pretty) mess. The code becomes incresingly complex and increasingly difficult to change or introduce new features. Soon you need to find a way to compartmentalize the mess, you will still deal with the mess, but with OO abstractions, the messes are in bigger boxes. Inheritance is one of the bigger concepts in OO programming, here's one way to do them in JS.

[TO DO: Finish the section above with a really simplified explanation of OO abstractions and how to use them in JavaScript]

{% highlight java %}

var Person = function() {
	this.work = function() {
		console.log("Person working");
	}
	this.managing = function() {
		console.log("should not be implemented here");
	}
}

var Manager = function() {
	this.managing = function() {
		console.log("am managing");
	}
}

Manager.prototype = new Person;

var m = new Manager();
m.work();		// Person working
m.managing(); 	// am managing

console.log("Keys : " + Object.keys(m));
console.log("isPrototypeOf manager : " + Person.prototype.isPrototypeOf(m)); 
console.log("getPrototypeOf m : " + Object.getPrototypeOf(m));


console.log("m instanceof Manager  :" + (m instanceof Manager)); //true
console.log("m instanceof Person   :" + (m instanceof Person)); //true
console.log("m instance of Object  :" + (m instanceof Object)); //true
console.log("m instanceof Function :" + (m instanceof Function)); //false

{% endhighlight %}

JavaScript is an OO language but it is not class-based. There are no templates (classes) you can use to create objects. Objects, in JavaScript are created using other objects; more specifically, they are created using the function object. There is a way to create an object in JS using a literal, but we are not interested in those, we are interested in objects created using constructor functions. 

When you create a constructor function (like Manager and Person, in the examples above), they will have a property called *prototype*. A prototype is an object whose properties are shared by all the objects that have that prototype . In the example above, Manager inherits from Person via the code **Manager.prototype = new Person**. Whatever Person have, Manager will also have.  

To override an inherited method, simply redefine (reimplement) the method in inheriting class (the child class), that makes the method polymorphic. When you invoke a method against an object, the method will be searched (first) on the child class, if the method is not found, the search will go up the prototype chain until the method definition is found. 

# 14. Modularization

[TODO: finish this section]


# 15. JavaScript in the browser

So far, by far, the JavaScript we have been doing lives on the CLI (Command Line Interface), it actually lives on the Node.JS runtime, to be specific. JavaScript also lives in the browser. 

{% highlight html %}

<!DOCTYPE html> 

<html>
<body>

<script>
	document.write("Hello JavaScript");
</script>

</body>
</html>

{% endhighlight %}

JavaScript lives inside the *script* tag of an HTML page, in this example, the JavaScript code is inline, meaning it is written on the same source file where the HTML codes are also written in. 


{% highlight html %}

<!DOCTYPE html>

<html>
<body>

<script src="hellojavascript.js"></script>

</body>
</html>

{% endhighlight %}

In this example, the script element has an src attribute which is given a value "hellojavascript.js"---this is a JavaScript source file. You can write whatever legal JavaScript statements in that source file.

The code document.write() , when executed, will erase the whole content of the HTML page (specifically the whole of the body element) and then replace it with whatever you supplied as parameter to the write() method—that's probably not what you would like to do, so be careful using that command, you normally see that code on introductory codes of JavaScript on the browser so that you can quickly get a tactile feel of JS coding. In order to produce dynamic HTML with JavaScript you will need to know a little bit about the DOM (Document Object Model).

An HTML page is composed tags (elements) which in turn can contain other elements. If element1 contains element2 and element3, the relationship between these elements is that; element2 and element3 are child nodes of element1, another way of saying it is that, element1 is the parent node of element2 and element3. If you try to picture the relationship of HTML elements to one another, it might resemble something like a tree structure. The trunk, the main node is the <html> element, and then it will have branches (the <head> and <body>) elements. The head and body elements can in turn contain other elements like script, style, input, textarea, options, canvas etc.

The document object model allows you programmatic access to these elements and their attributes. Navigating the DOM is an essential skill of a JavaScript programmer. Below is a rough pictorial representation of DOM (Level 0)

<img class="default" src="/res/article-pix/notes-javascript/dom-level-0.png" width="550">

Each node in the DOM is an object, so you can use the dot notation to reference each element. The root element of the DOM is the window object, this is the most global space in client-side JavaScript. It has many child nodes, you have already seen one of them in action a while back, the document object. When we wrote document.write(), we actually meant window.document.write(), but we don't have the write the window object explicitly.

I already mentioned that each node in the DOM is an object, which means if you want to do something to one of elements, you need to know their methods so you can do something meaningful to them.

{% highlight html %}

<!DOCTYPE html>
<html>
    <head>
        <title></title>     
    </head>
    <body>
        <div id="watch">
    
        </div>

        <script>

        var out = document.getElementById("watch");
        out.innerHTML = "Hello JavaScript";

        </script>

    </body>
</html>

{% endhighlight %}

The document object has a method---which you will use quite a lot---the getElementById(). It is used to locate an HTML element that has a specific ID. When the element is found, a programmatic reference to that object is returned. After that, you can call the methods of the HTML element. In the example above, a div named "watch" was defined in the HTML. You can use document.getElementById("watch") to obtain an object reference to that div just like what we did on the sample code. The innerHTML is a property of any div element, this is a read-write property so you can pretty much use it like this


{% highlight javascript %}

var x = document.getElementById("watch");
x.innerHTML = "Writing to the div";  // writes to the div

var y = x.innerHTML; // reading the runtime content of the div

{% endhighlight %}

Let's re-arrange the codes in our sample


{% highlight html %}

<!DOCTYPE html>
<html>
    <head>
        <title></title>     
    </head>
    <body>

        <script>

        var out = document.getElementById("watch");
        out.innerHTML = "Hello JavaScript";

        </script>

        <div id="watch">
    
        </div>



    </body>
</html>

{% endhighlight %}




In this version, the script comes before the div definition, if you run this code, you will see nothing---because there will be an error. The variable out will contain null. The reason for this is because we tried to obtain an object reference to a div element which does not exist yet. The div "watch" must be defined and loaded in the DOM before we can obtain a programming reference to it. It is time to step back a little bit and try to get some more understanding of how the browser, DOM, and JavaScript works.

<img class="shadow" src="/img/dom-javascript-rendering.png"/>

When a web page is received by browser, it will go to work by scanning through all the HTML elements in the page. It will be interrupted shortly when it encounters elements that have an src attribute, because that attribute means that whatever information follows the src, it is not part of the current document being rendered &mdash; the browser will make another roundtrip requesting the resource from the server, then coming back again. This is the reason why sometimes, the browser seems to load for a very long time, because it is trying to complete all the elements in the web page. If the element has an src attribute, it will be fetched before the browser can complete rendering the complete DOM.

The other occassion when the browser will stop rendering the DOM is when it encounters the *script* element. JavaScript has the ability to alter the DOM, that is why the browser needs to suspend operation when a JavaScript code is running. When the script is done, the DOM rendering can resume.

You need to keep this interplay between the DOM, JavaScript and the browser in mind so that you always know the state of the browser and the DOM before you accessing any element of the DOM.

This does not mean though that you have to position your scripts on very select places of the HTML page just to ensure that your code is synchronized with the HTML elements. Not only is that an ardous task, it is also bad form. What we need right now is to use a little bit of callbacks.

Callbacks are simply functions in JavaScripts, you probably know them better as events. Each element of the DOM have built-in events that you can already use. Let's start with the **window** object, we'll rewrite the previous code sample using some events of the window object.

{% highlight html %}

<!DOCTYPE html>
<html>
  <head>
    <title></title> 
    <script>

      window.onload = function(){
        var x = document.getElementById("watch");
        x.innerHTML = "Writing to the DIV watch";
      }

    </script>   
  </head>
  <body>
    <div id="watch">
      
    </div>
  </body>
</html>

{% endhighlight %}

This is a lot different now, the script element is on the head portion of the HTML page, obviously none of the HTML elements have been rendered at this point, but code works just fine. This is because we have overriden the onload event of the window* object. By assigning a callback function to the onload member of window, we are in fact telling it which function to execute when all the elements of DOM have already been loaded, because at that point, the DOM is pretty stable, all of the elements would have been rendered.

## 15.1 Event Programming

The basic idea is when a user does something, e.g. click, right-click, types something, hovers the mouse over an area, your code will do something meaningful, useful or cool (or all of the above). These useful codes reside on your JavaScript functions. Hence, the trick is to bind a function (a function that you define) to an established event of an HTML element.

Events can be bound to JavaScript functions in a couple of ways.

### 15.1.1 By binding the event using the attribute of an HTML element


{% highlight html %}


<!DOCTYPE html>

<html>
    <head>
        <title></title>
        <script>

        function btnClick() {
            var x = document.getElementById("writetome");
            x.innerHTML = "Hi World";
        }

        </script>

    </head>
    <body>
        <form>
        <input type="button" value="Click me to see" onclick="btnClick()">
        </form>

        <div id="writetome"></div>
    </body>
</html>

{% endhighlight %}

The onClick attribute of the input element is assigned a name of the JavaScript function. When the user clicks the button, btnClick() will be called. This is fine if you are experimenting on JavaScript, but this style of coding is obstrusive, it sullies the HTML code.


### 15.1.2 using callbacks programmatically

{% highlight html %}

<!DOCTYPE html>

<html>
<head>
    <title></title>
    <script>

    window.onload = function(){
        var btn = document.getElementById("btn");
        btn.onclick = function(){
            document.getElementById("writetome").innerHTML = "Hi World";
        }
    }


    </script>
</head>
<body>
    <form>
    <input type="button" value="Click me to see" id="btn"/>
    </form>

    <div id="writetome"></div>
</body>
</html>

{% endhighlight %}

The second version of our code is a bit cleaner. There are no programming instructions on the input element, just styling and bare instructions. The onclick event was bound to the button entirely inside the *script* element. All of our logic are wrapped inside the window.onload callback because we need the DOM to have completely rendered before we get a reference to both the div and the button input element.

Most input elements of the DOM have the onclick event, you can even use it on document object itself, if you want to.

I really did not intend to list down all of the input elements and their events in this page because you can easily access that information elsewhere (a book perhaps, although I think will try to google it first, before reading a JavaScript book), however, to get started quickly without being constantly being stopped by syntax issues, here are some of the most common events that you might need.

1. *onclick* - works on lots of HTML elements, there is no ondoubleclick or onrightclick, that is handled using some other trickeries of the event object. I will get to that, but not now
2. *onmousedown, onmousemove, onmouseover, onmouseup* - the events are pretty self explanatory, you can probably guess already when these events are triggered, no need to spell it out. This event works on lots of elements too, like the onClick
3. *onchange* -- usually found on input, select and textarea elements. This event is triggered when the value of the element has changed and it has lost the focus
4. *onkeyup, onkeydown, onkeypress* -- if you want to handle keyboard events

### Sample code, onkeyup


{% highlight html %}

<!DOCTYPE html>

<html>
<head>
    <title></title>
    <script>

    window.onload = function(){

        var txtobj = document.forms[0].elements["txtarea1"];

        txtobj.onkeyup = function(){
            document.getElementById("writetome").innerHTML = txtobj.value;
        }
    }
    </script>
</head>
<body>

<form name="objform">
    <textarea name="txtarea1" rows="10" cols="100">

    </textarea>

    <p>
</form>
<div id="writetome">
    This text will change
</div>
</body>
</html>

{% endhighlight %}

Everytime the text inside the textarea element changes, we get the value of textarea (txtobj.value) then we assign that to the innerHTML property of the div

### Handling the right click

{% highlight java %}

<!DOCTYPE html>

<html>
<head>
    <title></title>

    <style>
        #thearea {
            border:4px solid gray;
            width: 500px;
            height: 200px;
        }
        #watch {
            border:5px solid green;
            padding-top: 50px;
            width:500px;
        }
    </style>

    <script>

    window.onload = function(){

        var objarea = document.getElementById("thearea");

        objarea.oncontextmenu = function(){
            return false;
        }

        objarea.onmousedown = function(){

            var watch = document.getElementById("watch");
            var x = event.clientX;
            var y = event.clientY;
            var msg = "X : " + x + " | Y: " + y;

            switch(event.which){
                case 1: // left click
                    watch.innerHTML = "Left " + msg;
                    break; 
                case 2: // middle click
                    watch.innerHTML = "Midle " + msg;
                    break;
                case 3: // right click
                    watch.innerHTML = "Right " + msg;
                    break;
            }
        }

    }

    </script>
</head>
<body>

<div id="thearea">Right click inside the box. Then right click outside 
the box. The context menu will not be triggered inside this div
</div>
<p>
<div id="watch"></div>
</body>
</html>

{% endhighlight %}

We need to override the **oncontextmenu** function so that the default context menu will not kick in. The key to detecting which mouse button was used to click is the **which** property of the event object---note though that there have been inconsistencies on the values of which, sometime in the past, I remember 0 = left click, 1 = middle and 2 = right; Do your proper testing, you have been warned.

### Tracking the mouse position

The X and Y position of the mouse is always reported by the event object, in the following code sample, the mouse position is captured during the **onmousemove** of a div element.


{% highlight html %}

<!DOCTYPE html>

<html>
<head>
    <title></title>

    <style>
        #thearea {
            border:4px solid gray;
            width: 500px;
            height: 200px;
        }
        #watch {
            border:5px solid green;
            padding-top: 50px;
            width:500px;
        }
    </style>

    <script>

    window.onload = function(){

        var objarea = document.getElementById("thearea");

        objarea.onmousemove = function(){

            var xpos = event.clientX;
            var ypos = event.clientY;
            var msg = "X : " + xpos + " | Y : " + ypos;

            document.getElementById("watch").innerHTML = msg; 
        }
    }

    </script>
</head>
<body>

<div id="thearea">Just hover your mouse inside box</div>
<p>
<div id="watch"></div>
</body>
</html>

{% endhighlight %}

The event object has two members, clientX and clientY which corresponds to exact position of mousepointer at the time of capture. You need to be careful when using event.clientX and event.clientY*, these may not be the same from one browser to another--which is why its worthwhile using JavaScript libraries that takes away our worries of cross-browser coding, like JQuery; which is coming up next.

# 16. JQuery
[TO DO: finish this section]

# 17. TypeScript
[TO DO: finish this section]

# 18. CoffeeScript
[TO DO: finish this section]

# 19. Other stuff that compile to JavaScript
[TO DO: finish this section]

# 20. JavaScript on the server
[TO DO: finish this section]

# 21. Asynchronous JavaScript (AJAX)
[TO DO: finish this section]

# 22. JavaScript, Android, IOS and other mobile platforms
[TO DO: finish this section]


<!-- 

# 13. Inheritance and polymorphism [done]
# 14. Modularization
# 15. In the browser
# 16. DOM
# 17. JQuery
# 18. TypeScript
# 19. CoffeeScript
# 20. Other stuff that compile to JavaScript
# 21. JavaScript and Mobile applications

Assert keyword
Abstractions
ECMA 6 

-->


# Bibliography

1. <a href="http://www.amazon.com/gp/product/0596805527/ref=as_li_tf_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0596805527&linkCode=as2&tag=javafornoob-20">JavaScript: The Definitive Guide: Activate Your Web Pages (Definitive Guides)</a><img src="http://www.assoc-amazon.com/e/ir?t=javafornoob-20&l=as2&o=1&a=0596805527" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />
2. [W3C Schools](http://www.w3schools.com/js/js_intro.asp)
3. [NodeJS.org](http://nodejs.org/api/index.html)
4. [Google JavaScript Style Guide](http://google-styleguide.googlecode.com/svn/trunk/javascriptguide.xml)
5. [O'Reilly Web Dev Center](http://www.oreillynet.com/pub/a/javascript/2001/04/06/js_history.html)
6. [ECMA publications](http://www.ecma-international.org/publications/standards/Ecma-262.htm)
7. [JavaScript history: Wikipedia](http://en.wikipedia.org/wiki/ECMAScript)
8. [Mozilla Developer Reference](https://developer.mozilla.org/en-US/docs/JavaScript/Reference/Reserved_Words)
9. Pro JavaScript Techniques, John Resig, Apress 2006






