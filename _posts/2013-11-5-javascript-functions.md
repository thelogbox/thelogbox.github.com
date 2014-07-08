---
layout: javascript

title: Functions

description: The basics of writing JavaScript functions

excerpt: 

tags:
- functions
- javascript

author: Ted Hagos

---


A JavaScript function is named code-block. A code block is a group of statements tucked inside a pair of opening and ending curly brace. 


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

{% highlight javascript %}

function <name> (<parameters) {
  // statements
  [return <value>]
}  
  
{% endhighlight %}
<div id='lst'>Canonical Form</div>


Functions can contain a *return* statement, take note of the following though;

1. Calling a function without a return statement - returns undefined
2. Calling a function with return statement, but does actually return anything - returns undefined
3. Calling a function with a return statement and a proper return value - returns the value

<aside>
**CAREFUL** how you write your curly braces, JavaScript's defaults might produce unexpected results, see the following code
</aside>

{% highlight javascript %}

function goo() {

	return
  {			// this line is unreachable
		objprop: "Some obj property";
	}

}

{% endhighlight %}

The statement will be unreachable because JavaScript would have inserted a semi-colon right after the **return** statement. The object literal is unreachable as a return value.


Functions are different from JS statements. Statements are executed at once as soon as it is encountered by interpreter. Functions on the other hand are *compiled* first, they are not executed when first encountered, intead, it will be parsed and stored for later use. 

Theres a lot more to JavaScript functions but we will stop here for now. The other characteristics of functions are better explained when we are the context of Object Oriented JavaScript and some more advanced concepts.