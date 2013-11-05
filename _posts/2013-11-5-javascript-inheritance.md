---
layout: javascript

title: Inheritance

description: Learn the mechanisms of prototypal inheritance in JavaScript

excerpt: 

tags:
- prototype
- inheritance
- oop
- javascript

author: Ted Hagos

categories:
- JavaScript

---



You can use JavaScript pretty much in a procedural way. What I mean by that is, without using coarse grained abstractions for interesting objects of your problem domain. But as soon as you find yourself coding way past 300 lines of code (give or take a 100 lines), you might find yourself in a (pretty) mess. The code becomes incresingly complex and increasingly difficult to change or introduce new features. Soon you need to find a way to compartmentalize the mess, you will still deal with the mess, but with OO abstractions, the messes are in bigger boxes. Inheritance is one of the bigger concepts in OO programming, here's one way to do them in JS.

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

When you create a constructor function (like Manager and Person, in the examples above), they will have a property called *prototype*. A prototype is an object whose properties are shared by all the objects that have that prototype . In the example above, Manager inherits from Person via the code <code class="codeblock">Manager.prototype = new Person</code>. Whatever Person have, Manager will also have.  

To override an inherited method, simply redefine (reimplement) the method in inheriting class (the child class), that makes the method polymorphic. When you invoke a method against an object, the method will be searched (first) on the child class, if the method is not found, the search will go up the prototype chain until the method definition is found. 