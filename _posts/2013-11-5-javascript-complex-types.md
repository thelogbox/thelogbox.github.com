---
layout: javascript

title: Complex Types

description: JavaScript is object oriented. You can define complex data types in it

excerpt: 

tags:
- types
- reference
- complex
- objects

author: Ted Hagos

categories:
- JavaScript

---



JavaScript has some containers (stuff that can contain other stuff, that can contain other stuff … ). We will take a look at two of them right now &mdash; Arrays and Objects. These are not simple types like Numbers or Strings or Boolean. Instead of representing single values, Objects and Arrays can represent a collection of values. 


*** 

*OBJECTS*. Lots of things are considered objects in JavaScript, even arrays and functions are objects, but let's not get distracted by that right now. Think of an object like a dictionary or the telephone yellow pages. It is just a collection of stuff. This stuff though has a format, it comes in pairs. The first part of the pair is a key, the other part of the pair is a value. Using the yellow pages analogy, the key is probably a person's name or name of a business. The value is the address or the phone number. The key has to be unique, you cannot have more than one key with exactly the same name. 

The value part of each pair could be anything. It could be simple data (Numbers, Booleans, Strings) or it could be complex data (Arrays, Objects or functions).

There are a couple of ways to create objects in JS.

1. Using object literals
2. Using the new keyword against the Object type
3. Constructor functions

Try your best to ignore number 3 above (at least for now). We will circle around that later when we get to JavaScript OOP.

## OBJECT LITERALS

Object literals have very simple construction. The code sample below illustrates how to use *object literals* in your code. Object literals are also known as JSON &mdash; short for JavaScript Object Notation.

{% highlight javascript %}

var obj = {} // this one constructs an empty object
var pt 	= {x:0, y:0} // an object with simple data types as members
var person = {

	name: "John Doe",
	email: "johndoe@somewhere.com",

} // an object that has two members, both of which are Strings

{% endhighlight %}

When you use object literals to initialize objects, don't forget to separate the pairs using comma. You can add properties (the key-value pair) to objects by simply declaring the member--using the dot notation--and assigning them values

<pre class="codeblock">
person.date_hired = "some date value";
person.address = "some address";
</pre>

Similarly, you can access values of the object properties using the dot notation as well, although this is not the only way.

<pre class="codeblock"></code>
console.log(person.name);
console.log(person.address);
</pre>

JavaScript's use of dot notation to access object properties and method will feel very familiar with programmers because a lot of other languages use this notation too. What might not feel familiar will be the fact that JS can also access object properties using square brackets. Like this

<pre class="codeblock">
person["name"];
person["address"];
</pre>

JS objects are actually associative arrays---I need to clarify one point, when I write **Array** (capitalized) I am referring to the JavaScript complex type. When I write **array** (lowercase) I am referring to the array data structure in general, what I mean by this is a collection of rows (and sometimes columns). An object looks like an array because it a collection of **named** values, this is the reason you can use the square braces approach to reference a member of a specific object. 

## ARRAYS

An Array is also a collection of values. Unlike an object, an Array is a collection of *ordered values*, not *named values*. Each member of an Array is called an element. Each element is denoted by a numeric position in the array--the position is called an index. Like objects, Arrays can be created using a variety of ways;

<pre class="codeblock">

var a = []; //an empty array
var b = [1,2,3,4,5,6,7]; //an array with 7 elements
var c = ["Hello", "World", 1, 2.0, 0xFF]; //an array with members of diff types
var d = [[1,1], [2,2],[3,3]]; // an array with members, which are also arrays. 

</pre>

The other way to create an Array is to use the **Array()** constructor

<pre class='codeblock'>

var a = new Array(); //equivalent to var a = []
var b = new Array(1,2,3,4,5,6,7);
var c = new Array("Hello", "World", 1, 2.0, 0xFF);
var d = new Array(new Array(1,1), new Array(2,2), new Array(3,3));

var e = new Array(5); //with 5 new elements

</pre>

If you call the Array constructor with a single integer as parameter, it means you are specifying the length of the Array--you are not declaring an array with a single element, and the number you passed is the value of the first element.

Array members can be retrieved by accessing the individual elements. Arrays are zero-based, hence the first element is index 0.


<pre class="codeblock">

b[0] =  8; //assigns the value 8 to the first element of the Array
console.log(b[2]); //prints the value of the third element (remember, zero based)

</pre>

The characteristic of arrays having index positions makes them ideal for iterating using a for-loop. You cannot access members of an array using the dot notation--like you did when you accessed members of an object.