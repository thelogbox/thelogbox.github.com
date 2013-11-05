---
layout: javascript

title: Anonymous Functions

description: Understanding anonymous functions in JavaScript

excerpt: 

tags:
- anonymous
- function
- callback

author: Ted Hagos

categories:
- JavaScript

---

We have already taken a look at functions earlier. At first glance, functions in Javascript does not seem too special. Like in any other language, we used it to contain a bunch of statements and gave it a name. This name, when we call them at a later time, will execute the set of commands inside its block. We use the function simply as an encapsulation unit for a sequence of statements.

Functions in JavaScript has some twists that may seem weird at first (depending on where you are coming from). The dynamic characteristic of the language presents a lot of possibilites&mdash;and some suprises too. Take a look at the following code

{% highlight javascript %}

function foo() {
	return 10;
}

console.log(foo()); 	//nothing surprising here, it will return 10

foo = "Hello World"; 	//This is allowed in JS, because it is not strongly typed
console.log(foo); 		//This will now output "Hello World". It has already forgotten that it was a function
						//before

console.log(foo());		//this one will throw an error, because foo is no longer a function

{% endhighlight %}

JavaScript function names are not that different from ordinary variables. You can assign them values, just like how you would an ordinary variable. Similarly, you can assign functions to variables; like this

<pre class="codeblock">

var foo = function() {
	return 10;
}

console.log(foo()); //returns 10

</pre>

It may seem that you don't have a need for anymous functions at the moment. Admittedly, the code example above does a poor job hinting at it's utility value. Anonymous functions will become increasingly important when you start using them for call backs e.g. during event driven programming on the browser, using third party libraries like JQuery or server side programming with NodeJS

***

This is another way to create a function. Notice that the function on the right hand side of the equal sign does not have a name. Notice also that we can assign it to a regular variable named "foo" then invoked **foo()**. What we have just done was create an anonymous function and assigned it to variable *foo*. It is called an anonymous function, for obvious reasons, it does not have a name. There are other ways to create functions in JS, but we will stop here because we don't have any further use for another way to create a function, what we have is quite enough for now.