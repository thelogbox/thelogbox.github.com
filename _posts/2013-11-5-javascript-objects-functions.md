---
layout: javascript

title: Objects and Functions

description: Functions are first class citizens in JavaScript. When you write functions inside Object definitions, that is the first step in JS OOP

excerpt: 

tags:
- oop
- functions
- objects

author: Ted Hagos

categories:
- JavaScript

---

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