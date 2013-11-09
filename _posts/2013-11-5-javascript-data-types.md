---
layout: javascript

title: Typing

description:  Getting to grips with JavaScript data types

excerpt: 

tags:
- types
- javascript

author: Ted Hagos

categories:
- JavaScript


---


Programmers create things (data). We manipulate them by adding, substract- ing, dividing or multiplying. Sometimes we mash them up together (concatenation). Then we create more things. Sometimes, we store these things for later use, and other times we don’t, we simply discard them. Sometimes we dig up things that we have stored in the past (retrieval) and other times we show the things we’ve tucked away to other people (reports).

This is an oversimplification of what programmers do, but it is very common. In order to create things, we need to know what kinds of things you can create. Are we going to count these things (whole numbers) or are we suppose to measure them (real numbers). If we need to compare one thing to another thing, how will I remember the result of that comparisson, can I store the result in another kind of thing that is aware of truth and falsity?

If we were using a language that is pretty close to the metal, like assembly or C, you may need to know quite a bit about how things are stored and organized in a very low-level fashion before you can get very far.

Thankfully, we are using JavaScript and it will not require us to work close to the metal. You will work with Types rather than bits (zeroes and ones). JS has defined some useful abstractions for us already. These abstractions allow us to work with ease because we can represent business concepts with ready-made Types.

For example, if you need to work with real numbers, Java has defined the float and double data types. If you need to work with words and letters, JavaScript can work String

These abstractions are high enough that we don’t get bogged down by the de- tails of how they are stored and structured on the disk, we can worry about other things like the logic of our application.

# Data Types

You need to know what kinds of stuff you can create, define and manipulate in JS. 

JavaScript have simple data types. These are *Number, Boolean* and *String*. It also have other data types which are not so simple anymore. Their complexity is primarily because they are no longer scalar values. These are *Array, Object* and *Function*. There are two more types right after the complex types. The last two are *null* and *undefined*

*Number* - 10, 2, 100 (integers), 2.3, 1.2 (floats) are numbers. JS does not discriminate whether it is of integral or float type. There's more; 0xFF, 0xCAFEBABE (hex or octal) are also considered numbers, and so are base 8 numbers (i.e. 0377)

When you try to store a value that is more than what a Number can hold, it can result to either *Infinity* or *-Infinity*. You can also get some weird results like *NaN* (not a number). The NaN can result if you try to do some illegal operations, i.e. divide something by zero. 

*Boolean* - either *true* or *false* 

*String* - A sequence of UNICODE characters, although, there is no concept of character arrays in JS. You can define Strings using either the single quote or double quote technique. i.e. "Hello World" is as good as 'Hello World'. You may insert escape characters in Strings like "Hello\n World".

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
<div id='lst'>VAR types</div>

Variables can be declared using the word **var** (or without). I would rather that you always declare your variables using *var* because it has some effects on the *global context*. Don't worry about that context for now, they will be discussed shortly.

