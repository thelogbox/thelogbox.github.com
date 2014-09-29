---
layout: javascript

title: JavaScript Conditions

description: 

excerpt: 

author: Ted Hagos

lastupdate: 

tags: Conditions, if, else, switch, JavaScript

categories:

---

As you progress in your practice of writing JavaScript codes, you will
begin to write codes that increases in complexity. After writing basic
Math expressions, alerting some string and other various one-liner
codes, you will need to exert control over program flow.

When JavaScript encounters your first line of code, it will execute that
immediately, then it will look for the next line of code and the next
one after that and the next one after that. Until it runs of out of code
to execute. This is a very sequential way of executing statements. And
this is the default.

As you begin writing codes with increasing complexity and
sophistication, you will need a way to write code that only runs only
when certain conditions are true and skip some codes when conditions are
not right. This program flow is known as branching. We will look at two
constructions in this section that will help us deal with branching.

1 Symbols and Syntax
--------------------

Before we begin any further, we need to cover some basic symbology when
writing codes. Especially when writing codes in a language that is a C
derivative. JavaScript is such as language. Quite often, you will see
symbols such as the parens **()**, brackets **[]** and braces **{}**.
They do quite different things hence they are not intechangeable. You
cannot substitute one symbol for another. But they have similarities.
All of them are used to group or enclose either statements or
expressions. And all of them come in pairs. When you write an opening
paren, brace or bracket, you will sure have to close it up somewhere in
your code. Maybe not immediately but you need to make sure they all pair
up. Unpaired symbols is one of the most common sources of errors and
developer grief. It is not a simple activity to hunt down a missing
curly brace.

### 1.1 Parens

Parens or parentheses are commonly found on branching and looping
expressions. You will also use them when defining or calling functions.
The sample code below shows situations where you might use or see the
parens

{% highlight java %}
// CONDITIONS

if (a > b) {
  console.log("a is greater than b");
} 

// LOOPS

while (a > b) {
  console.log(a);
}

// FUNCTIONS

function foo() {
  console.log("I am fooing");
}

foo();


var colors = ["red","gold","green"];
var x = colors[1];
consoloe.log(x);
{% endhighlight %}

There are times when some expressions are written inside the parens and
other times there aren't any. It depends on what you are trying to do.
We will get to those details when we discusss JavaScript functions.

### 1.2 Braces

Programmers often refer to this symbol as curly braces, but calling them
braces is acceptable too. Programmers would know what you mean. You will
use brackets to group together a bunch of statements. This is done so
you can refer to the statements as one unit. The grouped statements is
called a **block**. A block is executed as if it is a single statement.

There is another reason why a block is beneficial. It defines a boundary
or a limit to the scope of your variables. Although we will not go to
the details of lexical scope just yet, it is helpful to know that blocks
are basically namespaces. It allows you to define data within a space,
limit the accessibility of this data and protect the data from potential
conflict which may exist outside the block. The block acts as a basic
unit of encapsulation. This is foundational knowledge in structured
programming.

A block defines a single point of entry and exit. The program flow
enters the block thrugh the opening curly brace and it exits on the
closing curly brace. It is important to realize and internalize this
concept because it goes a long way in code analysis.

#### 1.2.1 One point of entry, One point of exit

Program flow can only enter the block one way. That is through the
beginning curly brace. There are no conditions or instructions
whatsoever in which you can selectively jump to an instruction in the
middle of the block. When you enter it, you start at the very first
instruction within it, then to the next line of code, then to the next.
You will execute it in sequence and in the order which they were
defined. Guaranteed.

There is only one exit point in the block and that is through the
closing curly brace. Only the last instruction within the block can
cause the program flow to exit. I need to tell you though that this
exiting behavior is not always strictly followed. There are some
programming elements that can bend this behavior. The **return** and
**throw** keywords will introduce some subtleties to the exiting
behavior of blocks. We will not go to those details in this section
though.

A very common use of blocks for grouping statements is shown below:

{% highlight java %}
if (actual_hrs_worked > 80) {
  var overtime = actual_hrs_worked - 80;
  var overtime_pay = overtime * hourly_rate * 1.3;
  var base_pay = hourly_rate * 80; 
  var gross_pay = base_pay + overtime_pay;
}
{% endhighlight %}

Even if the example code is contrived, it is easy to see and discover
the intent of the programmer. When the number of actual hours worked is
more than 80 hours, a series of instruction will be carried out. From
start to finish.

#### 1.2.2 Block syntax

The block syntax of JavaScript is achieved using a pair of curly braces.
Not all programming languages are like this. Other languages mark their
blocks using specific keywords such as **begin** and **end**, or some
variations of it. Ruby and Algol are some examples of such languages.
Other languages use indentations to define a block. Python is famous for
this. Most languages derived or inspired by the C language use the curly
brace to define blocks. JavaScript is such a language.

The placement of curly braces has become a contentious subject over the
years. It continues to do so these days. We will not discuss the merits
or pros and cons of these arguments.

{% highlight java %}
// C Style braces
// Known also as Kernighan and Ritchie or K & R

if (a > b) {
  // statements
}

// C++ style

if (a > b) 
{
  // statements
}
{% endhighlight %}

K & R places the opening brace on the same line as the header and the
closing brace is flushed to left. When using the C++ style, the opening
and closing brace aligns with each other.

JavaScript doesn't care whichever of these styles you used. But other
people you will be working with might. These coding styles are usually
dictated as part of a convention for a team of programmers. A tech lead,
project lead or whoever is in charge with the project places certain
impositions on how code will be written. The placement of the curly
brace is a matter of style and convention. It is not a technical
imposition.

While you are still a beginner, no one is probably in charge of your
coding style but yourself. Just pick any one style and stick with it. Be
consistent. If you choose K & R, use it all through out. It improves
readability of the codes.

### 1.3 Brackets

Brackets are often found in Array definitions. Other languages such as
Objective C use them for other purposes such as message sending. But in
JavaScript, we will almost exclusively use the bracket when working with
arrays.

We will discuss arrays in future sections, so we will not go to the
details and mechanics of array creation and management here. But let us
look at some short code samples that shows how brackets might look like
in our program

{% highlight java %}
var colors = ["red","gold","green"];
var x = colors[1];
colors[2] = "black";
console.log(x);
{% endhighlight %}

The first line of code used the brackets to define an array of colors.
You might have noticed that the brackets on that line were at right hand
side (RHS) of the equal sign. When we want to assign a certain value to
a variable, that value will be on the RHS.

Notice the third line of code which changed the value of the third
element of the colors array. The brackets appeared on the left hand side
(LHS) of the equal sign. That is because we wanted to assign a certain
value to the third element of the array. When we are storing something
to an array or to whatever variable, we place them on LHS. When we want
to get something from the array or whatever variable, we place them on
the RHS.

We can now go back to discussing JavaScript conditions.

2 Condition
-----------

Beyond the most basic of codes, you will need a way to route program
logic or program flow. There will be times when we need to execute a
block when some some criteria is met and on other times we simpy ignore
the block. Like in other languages, JavaScript uses the **if statement**
to route program logic.

The basic form of the if statement is as follows:

{% highlight java %}
if (condition) {
 // statement to execute
}
{% endhighlight %}

The statement requires an expression that resolves to either true or
false. We need to write this boolean expression inside the parens.
JavaScript will only look inside the parens for a conditional
expression. It won't look elsewhere. This is the reason why you need to
develop a keen eye for paired symbols. Some conditional expressions
could be short, and in those cases it is not visually challenging to
keep the symbol pairs straight. But there could be times when the
expression is a mouthful.

When the expression resolves to true, whatever statements contained in
block will be executed. If it isn't true, we simply scoot over to end of
the block and continue our program.

### 2.1 We only care if it is truthy or falsy

When write conditions for the if statement, we only care about truthness
or falseness of the expression. Nothing more. Were not checking for any
values whatsoever.

{% highlight java %}
if ( x > 50) {

}

if ( y < 100) {

}

if ( foo == "Hello" ) {

}
{% endhighlight %}

In the above code samples, we only want to know if the value currently held by the variable x is more than 50. We are not concerned about the actual value of x, it may be a really large number, it could be 51 or it could even be 50. Is x greater than 50 or is it not. Is y less than 100
or is it not. Those are the only things we care about.

### 2.2 else and else if

Now that we know how to execute a block when a condition is true. What happens when it isn't true? Well, we know that program control will skip the block and continue on.

If you want something else to happen when the condition evaluates to
true, you can specify that also by using the optional **else** clause.

#### 2.2.1 TODO Samples and usage of else


### 2.3 Comparisson operators

1.  TODO Samples and usage of operators\
    -   double equal: ==
    -   tripe equal: `=`
    -   not equal : !=
    -   not double equal : !==
    -   greater than : \>
    -   greater than or equal to: \>=
    -   less than : \<
    -   less than or equal to : \<=

### 2.4 Complex decisions

3 Switch statement
------------------

4 Nesting
---------

don't nest too deep



