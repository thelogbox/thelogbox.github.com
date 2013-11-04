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


Variables can be declared using the word **var** (or without). I would rather that you always declare your variables using *var* because it has some effects on the *global context*. Don't worry about that context for now, they will be discussed shortly.

