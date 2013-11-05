---
layout: javascript

title: Objects

description: How to deal with objects in JavaScript

excerpt: 

tags:
- objects
- oop
- json

author: Ted Hagos

categories:
- JavaScript

---


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