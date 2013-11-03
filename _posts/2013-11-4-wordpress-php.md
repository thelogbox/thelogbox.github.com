---
layout: wordpress

title: Introduction to PHP

description: A simple introduction to the PHP language. Just about enough so you can build WordPress applications

excerpt: 

tags:
- php

author: Ted Hagos

categories:
- WordPress

---

[Getting started, like hello world in PHP]


Think of programming as if you are writing a recipe for a friend. To write a recipe, you need to tell him two things. Firstly, the ingredients, what kinds of things he needs to work with. Secondly, how to work on those things. Some things you slice or dice. Some things you put in the pan first before you put the others. Some things you keep on doing until the food is of a certain color or temperature or consistency.

Programming is a lot like that. It might be oversimplication but oversimplification is what we need in order to begin understanding a complex subject. Before you can begin writing codes, you need to decide on a lot of things e.g. which language are we going to use, should we learn desktop, web or mobile programming etc. In our case, a lot of these decisions have already been made. We are building skills so that we can write a Wordpress app. That narrows things down for us.

A Wordpress app requires knowledge HTML, JavaScript, CSS and PHP. I did not include MySQL anymore because the Wordpress platform insulates you from dealing with the database. You will only need to deal with the database if you are working on a really unusual problem.

We will start building our programming competencies in PHP, this is what this chapter is all about.

## STATEMENTS

Remember the recipe analogy? First we need to know what kinds of things we can work with. In programming that means data. What kinds of data you can work with. You can work with numbers, both whole and real. You can use strings (words). You can work with boolean values (true or false). There are other things you can also work with but they are bit advanced, these are objects and arrays. We will circle back to these two when you have a bit more programming muscles.

A statement in PHP is a declaration of an operation, something that you would like to do. For example, if you want define a variable and store a number in it, you need to tell PHP exactly that.

{% highlight php %}
<?php

$anumber=10; 4

?>
{% endhighlight %}

The variable name is *anumber* but I did put a dollar sign before it. That is required. 

When you define a variable in PHP, you need to prepend it with the dollar sign so that PHP knows you are declaring a variable. The equal sign is used for assignment. In this statement, we defined a variable named *anumber* and assigned an an integer to it.

You will notice that there is a semicolon right after the number 10. That is a big deal. The semicolon tells PHP that you are already done with the statement. Just like when you want to end a sentence, you would punctuate it with a period to signal that it is already a complete thought, you need to punctuate your PHP statements with a semicolon.

*$anumber* is called a variable because we can change it’s value later on. You can add, subtract, divide and multiply it with some other value then store the new results on $anumber thereby changing its original value, like this


{% highlight php %}

<?php

$i = 10;
$j = 20;
$k = "Hello";
$i = $j;
$i = $i + 1;

?>

{% endhighlight %}

## CO MINGLED WITH HTML

You need to write your PHP statements inside this tag *&lt;?php  ?&gt;*. PHP is a server side scripting language, the php tag tells the server that what's inside is not HTML. It contains PHP instructions that needs to be *parsed and evaluated*. When these instructions are evaluated, sometimes they produce HTML and other times they don't. Through your practice, you will learn which statements produce HTML and which parts do something else. You don't always need to output something, sometimes you just need to do some stuff that don't necessary need to be seen by the user. 

PHP statements are often found co-mingled with HTML, like this;

{% highlight php %}
<!doctype html>
<html lang=en>
<body>
  <h1>My Spanking Web App</h1>
  <span>Today is </span> <?php echo date(DATE_RFC822); ?>
</body>
</html>
{% endhighlight %}

See that. Most of the codes are in HTML except for that tiny *&lt;?php echo date(DATE_RFC822); ?&gt;* which basically just outputs the current date. When the server sees that instruction, it will get the  system date then *echo* the return value as HTML. By this time you must have figured out that whatever you *echo* it will be part of the HTML output.

Many developers frown upon the practice of peppering your HTML codes with PHP expressions and statements, I don't necessarily agree with this approach as well, but were just starting out to learn PHP, so don't sweat about it just yet. Get some grips with the language first then worry about separation of concerns, MVC and other artsy fartsy architectural buzzwords. 

Before you can write elegant prose, you need to know vocabulary first, then grammar and rhetoric structures. Prose will come later, not before. 


## THREE THINGS YOU CAN DO WITH STATEMENTS

First. You can write one statement after another, like this

{% highlight php %}

$in = 5;
$cm = 10;
$factor = 2.54;

echo $in . " inches = " . $in / $factor;
echo $cm . " cm = " . $cm * $factor;

{% endhighlight %}

That is called *sequencing*. Your code starts executing the first statement until it runs out of things to do. 

***

Second. You can execute some statements when some condition is true, if it is not true, do something else; like this

{% highlight php %}

$a = 10;
$b = 20;

if($a > $b) {
  echo "a is > b";
}
else {
  echo "a < b";
}

{% endhighlight %}

*if* is a special word in PHP, programers call it a reserved word. Like *echo* it has a specific action when used. The *if* keyword is what you use for branching. You need to give it an expression, a boolean expression to be exact and it needs to result to either true or false. When the condition is true, all of the statements inside the *if block* is ran. 

The pair of curly braces is called a *block*. When statements are inside a block, they are executed as a group, start with the first one and all go all the way til the last. When you reach the last curly brace, execution resumes &mdash; unless you encounter another branching command or any command that alters the sequential flow of instruction. You will usually find blocks in control structures that either branch or loop.  

The *else block* gets executed when the condition given on the if block results to false. Mind you that the else block is not always necessary. Some programs only writes the if block and nothing else, like this

{% highlight php %}

$a = 10;
$b = 20;

if($a > $b) {
  echo "a is > b";
}

{% endhighlight %}

The code is still valid, although incomplete. So when do you use the else? That is left to your discretion, the programmer. Use it when it makes sense. 


***

We come to the last thing you can do with statements. If branching allows you sidestep some statements depending on some conditions, looping will let you perform some statements repeatedly until some conditions hold true.

There are a two ways to perform looping in PHP. They use very different keywords and have very characteristic semantics. 

