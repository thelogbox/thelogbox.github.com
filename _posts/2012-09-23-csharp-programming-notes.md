---
layout: post

title: C# Programming Notes

description: C# Language Fundamentals. Data types, Reference types, Loops and Branch

except:

tags:
- Introduction
- Language
- Fundamentals

categories:
- CSharp

---




# 0. Who should read this

I wrote this note for Steph. Hopefully, she will have a genuine interest in programming and that she may find this note as a useful learning resource as she goes through her college programming subjects---I know that this term, it is C#, hence, this guide. If you happen to find this note on the world wild web, you are probably one of my daughter's classmate, groupmate or one of my former students&mdash;whoever you maybe, I hope you find this note useful. I wrote it to guide beginning programmers on their first few steps towards a very long journey in software development.

# 1. Of programs and programming languages

Programs are the stuff that you run on your computer; or tablets or phones---you probably know them better as **apps**. There are lots of things that you need in order to build an app, but the biggest and probably the most important thing you need is knowledge of a programming language.

A program is just a bunch of executable statements arranged in a specific order. Some statements execute right after another statement; some execute repeatedly while some conditions are true (or not), and then some statements are executed only when conditions are true. 

The subject of this field guide is C# (pronounced see sharp) It is intended to be a simple, modern, general-purpose, object-oriented programming language.[6] Its development team is led by Anders Hejlsberg. The most recent version is C# 5.0, which was released on August 15, 2012. [^1].

There are other things to say about this language, such as it is statically typed, supports class-based OOP, strongly typed and has support for both functional style and imperative type programming, but they won't make sense right now. You need to know some basics about the language before any of these fancy vocabulary will make sense to you, so I will try to explain what they mean along the way. What maybe important to realize right now are the facts that C# is a high-level language and that it is compiled.

To speak loosely, computers can only run low-level instructions (sometimes they are also called machine instructions or assembly instructions). Low level languages are more difficult to write, that is why they are also more difficult to change. A high-level program on the other hand is written in an almost-English-like language. They are easier to learn and write (re-write).   

A program written in a high level language will not be readily understood by a machine though, they need to be translated. There are two ways to translate high level languages. One is by *compilation* and the other is by *interpretation*. An interpreter is also computer program, it does what it says---it interprets a high-level program to machine language. It does so by reading a the high-level source file one line at the time, and executes them also one line at a time.

A compiler (which is also another computer program) reads a high level source code in its entirety and translates it in one fell swoop, then you can run the program. 


## Things you need before you can start programming 

1. modern PC running a Windows OS
2. a recent version of the .NET Framework SDK (Software Development Kit). This will suffice for learning purposes, but when actual .NET programmers rarely (actually, never) use just the SDK alone. They use a proper development tool like Visual Studio
3. a good and proper program editor. If you went the Visual Studio route, then it already includes a program editor

.NET is not exclusive for Windows, it runs on Linuxes, UNIXes and OSXes too. That is why alternatively, you can also write C# programs those other platforms I mentioned, you just need to install [mono framework and SDK](http://www.go-mono.com/mono-downloads/download.html)


## First program

Get a feel of how C# programs are written by writing the age-old "Hello World". There are some things--lots actually--that you won't understand at first. That's ok. The goal of the exercise is just to get a feel on writing, compiling and running a C# program.  

You won't be using Visual Studio for this one. In fact, you won't be using Visual Studio for the rest of this guide. Learn the language first, not the tool. When you are good with the language, the tool will not be able to distract you anymore. 

Create a folder where you will store all your practice source files. Create a file and name it "Hello.cs". In OSX you can do this on the Terminal.app

<pre class='codeblock'>

$ cd ~/
$ mkdir csharp
$ cd csharp
$ touch Hello.cs
$ mate Hello.cs

</pre>

The last command is not a standard OSX command, it invokes the TextMate editor (if you have it). If you don't have the TextMate editor, you can use any other programming editor (vim perhaps or smultron)

Type the following code inside the editor

{% highlight c# %}

/*

filename: Hello.cs
author: Ted
date: 

*/

using System;

class Hello {
	
	public static int Main(){
		Console.WriteLine("Hello World");
		
		return 0;
	}	
}

{% endhighlight %}

You need the C Sharp Compiler (csc) to build this. If the Framework SDK has been properly setup on your Windows machine, you will have a short-cut to a batch file called **VCVARS32.BAT** somewhere on the windows menu-->Microsoft Visual Studio…

On other platforms using **mono**, you will the **mcs** command to compile our example.


<pre class='codeblock'>

# On UNIXes, Linuxes and OSXes

$ cd /path/to/your/project/folder
$ mcs Hello.cs
$ mono Hello.exe

</pre>

You cannot simply type "Hello.exe", .NET programs needs a runtime environment to execute, that is why you need to run mono first before you can run Hello.exe. This runtime is called the CLR (Common Language Runtime). I will tackle this subject, but not now.

<pre class='codeblock'>

# On Windows

C:\> cd \path\to\your\project\folder
C:\> csc Hello.cs
C:\> Hello.exe 

</pre>

On a windows machine, you did not need to invoke the .NET runtime, you simply typed Hello.exe and it runs just fine.Why?--because recent versions of Windows actually includes the .NET runtime already, and if it is intelligent enough to invoke the .NET runtime when it needs to. 


## Walk through of the Hello program 

**using System;** - The *using** keyword allows you to use the Types defined in the *System* namespace. When .NET was released, it came not only with the languages, it also came with lots of built-in Types that you can use immediately. There will be a discussion of Types way down the road, but for now, just settle for the explanation that if we did not use the System namespace, instead of writing **Console.WriteLine()** we needed to write **System.Console.WriteLine()**.  

**class Hello {}** - CSharp is very object oriented, you cannot write anything meaningful outside of a class construct. Unlike C++, where you can still program in a procedural way and only optionally use the OOP constructs, CSharp forces you to use the class constructs---even for a trivial program like the Hello program; **class** is a keyword (reserved word) which denotes that what follows is a name of class you are trying to define.  The pair of curly braces is the body of the class. You can write lots of things inside the class' body, although for now, we just wrote *main()*.

**public static int Main()** - this is called a method, some people may refer to it as a function, they will be right also but in OO languages, generally functions are referred to as methods--I will tell you why later, but not now. Main() is a very special method, all console applications (like our Hello program) is expected to have the Main() method because this is the entry point of the program. When you invoke the program, the .NET runtime will look for method, and if you did not define it---I mean exactly as it is written in the sample code, nothing will happen when you run your program. So make sure you type it exactly as it appeared in the sample code

**Console.WriteLine()** - Console is a built-in type under the System namespace, it does lots of things and it has lots of methods. One of the method is WriteLine(). What WriteLine does is to send a string data straight to the stdout (standard out, which means your screen). 

**Semi colon** - You will notice that all statements in CSharp are terminated using a semi colon, this is important because the semi colon will tell the compiler that you are finished with a statement. It signals the end of a programming statement pretty much as a period signals the end of a sentence in the English language. 

CSharp is a case-sensitive language, **main()** is not the same as **Main()**, so type carefully.


## Word power

1. **Source code** - sometimes called source file. It is a text file where you write CSharp statements.
2. **High level language** - a computer programming language undertandable by mere mortals, it looks a lot like the English language, but a computer programming language, unlike English does not contain ambiguities. Each statement you write in a programming language has very precise meaning---strive to know them well
3. **Compiler** - a computer program that takes in a source file as an input, processes it (parsing) then translates it to a format understandable by machines (machine code). CSharp comes with **csc** on Windows and **msc** on mono platform (which can run on platforms other than Windows)
4. **Main()** - a special function in CSharp, if you will write console applications, you need to be very acquainted with the format of Main(). Whenever you invoke a compiled .NET CLI (command line interface) program, .NET will always look for **public static int Main()**. This is the entry point of your app
5. **CLR** - The common language runtime is a rich environment which abstracts a lot of what the Operating System can do for your programs. The CLR can open files, network connections, database connections etc. There are things also that a CLR can do for you that the Operating System cannot---the OS cannot do automatic garbage collection for your app, the CLR can; but let's leave GC (garbage collection) for another discussion.  

# 2. Variables and Data types 

Think of a variable as a shoebox or a desk drawer--actually, just a shoebox, it is easier to explain the concept that way. You can put things inside a shoe box like a ball, paper, etc. The box is used basically as a storage. Program variables work that way too, they function as a storage. One time you can put a red-colored ball into the shoebox, then another time you can take the red ball out and replace it with say, a green ball. 


{% highlight c# %}

using System;

class Vars {
	
	public static int Main(){
		
		int a = 1;
		Console.WriteLine(a); // prints 1
		
		a = 2;
		Console.WriteLine(a); // prints 2
		
		return 0;
	}
}

{% endhighlight %}

In the above sample code, we defined a variable called **"a"**, then we assigned the whole number 1 into it. At a later time, we assigned a different value to **a**, then printed it again. This is a typical programming use of variables. You may assign them intially some value, then change that value later on. 

Let's mess around with the sample code a little bit and try to break it deliberately. See if you can spot the difference.

{% highlight c# %}

using System;

class Vars {
	
	public static int Main(){
		
		int a = 1;
		Console.WriteLine(a); // 
		
		a = "2";
		Console.WriteLine(a);
		
		return 0;
	}
}

{% endhighlight %}

If you try to compile this source, you would have encountered your first **compiler error**. You probably got a message like this;

<pre clas='codeblock'>

Vars.cs(10,19): error CS0029: Cannot implicitly convert type `string' to `int'
Compilation failed: 1 error(s), 0 warnings

</pre>

The reason you are getting this error is because of the statement **a = "2";** You are no longer assigning the integer 2 to the variable "a". You are trying to assign a String to "a"---and that is not allowed in CSharp. Going back to shoebox example, when you put a red ball into the box, you can change the contents of the box at a later time provided that you put a ball, it could be a green ball or black ball, a tennis ball or pingpong ball---as long as it is ball. When variable **a** was defined in the program, it was defined to be an **int**, it is meant to store integers (numbers that you use for counting things, they don't have decimal parts). You can replace the contents of variable **a** as long as you replace it with another integer. 

This characterisc of CSharp is called **strong typing**, it means that when you declare a variable using a specific type, you cannot change the type of the variable anymore. The fact that you need to tell the compiler what kind or type a variable should be is because CSharp is **statically typed** also. Static typing is a pretty deep subject, and you might not be ready for it (just yet). You need to attend a couple more subjects and read a lot more books, but basically here is what it looks like;

<pre class='codeblock'>

# Static and Strong typing

int a = 1; 	// Strongly typed languages like C, C++, C# and Java 
a = 1024;  	// not a problem, 1024 is still an int
a = 1.0;   	// problem, 1.0 is not an integer, strong typing kicks in
a = "1";   	// problem, "1" is not an integer, its a String


# Weak and dynamic typing 

a = 1		// Languages like ruby, python and JavaScript are weakly and dynamically typed
a = "1"		// not a problem 

a = function() {return "Hello"}; // a little too weird for now, but this is possible in JavaScript

</pre>

Okay, now you know CSharp is strongly typed and statically typed. The Typing system of CSharp (or any programming language for that matter) is just a clever way of classifying the stuff that programs can work on (that means create and manipulate, variables, remember?). It begs the question now, how many kinds of stuff are there? Here they are;


1. **bool** - true or false values
2. **byte** - whole numbers or counting numbers like the **int** you saw before, but these are way smaller. This is an 8 bit value. The smallest value is zero and highest value is 255
3. **char**  
4. **decimal** - It's quite self-explanatory and obvious what this type is for. Use it for numbers that have decimal parts. There are other types like this, namely the float and the double. Decimal is a 128-bit type, they are far more accurate than a float but it can contain smaller values than a double. Programmers dealing with financial and monetary calculations use this because of its accuracy
5. **double** - numbers with decimal parts, its accuracy is limited compared to the **decimal type** but it can contain a larger number
6. **enum**
7. **float** - like a double, only it can contain a smaller number and it is less precise (7 digit precision only, compared to the double which is 16 digits accurage, or the decimal which is 29 digits accurate)
8. **int** - whole numbers, values range is -2,147,483,648 to 2,147,483,647. Its a 32 bit type
9. **long** - whole numbers also, this is a 64 bit value. Can contain –9,223,372,036,854,775,808 to 9,223,372,036,854,775,807
10. **sbyte** - like the byte, but this is signed, which means it does not start from zero, it starts from -128 and goes up to 127
11. **short** - bigger than an int, contains -32,768 to 32,767. Its a 16 bit type
12. **struct**
13. **uint** - like an int, but this is unsigned, which means it starts from 0 and goes up to 4,294,967,295
14. **ulong** - like a long, but unsigned. It starts from 0 and goes up to 18,446,744,073,709,551,615
15. **ushort** - like a short, but unsigned. It start from 0 and goes up to 0 to 65,535


The number of bits assigned to a data type is what determines the higher-bound and lower-bound values (at least for integral types like short, byte, int, long etc). The general idea is this;

1. Lower range is = 2^(n-1) where n is equal to the number of bits
2. Higher range is = 2^(n-1) - 1 where n is equal to the number of bits

There are types I did not define, that's because it will mess up your learning for now, you will not need them in the near future, so a discussion of what they mean right now will be of very little value, but very high in clutter (mind clutter, that is)

Also, the 15 types listed above, is not complete. These are called **Value Types** in CSharp---there is another kind called **Reference Types** but we will hold off on that, you are not yet ready for that until the discussion on OOP (Object Oriented Programming)---however, we cannot put off even a small discussion of the **String** data type. String is not a value type like ints, shorts, or bytes. String is a Reference Type. Without going too deep on Reference vs Value Type discussion, here are some basic things you need to use the String type.


# 3. Flow of control 

By far, we have only written programs that are executed one statement or one instruction after another. Non trivial applications usually require program flows that are more sophisticated than merely sequencing (executing commands one after another). CSharp provides quite a few mechanisms that will allow you to control program flow. 

## What the {} means -- compound statements

Whenever you see a pair of curly braces, you will usually find a group of statements inside them. That is precisely their purpose, to group statements.

{% highlight c# %}

{
   /*
   
   Statements inside a block are executed in a linear fashion, top to bottom.
   
   */
   
}

{% endhighlight %}

A compound statement is a statement itself, you can use it whenever you can use a statement. Although you will usually see compound statements alongside flow-control keywords such as **if, while, for etc**.  


## If 

This is used if you need to branch or you want to decide whether a statement (or a group of statements) should be executed, based on some condition

{% highlight c# %}

if(condition is true){
   // execute these statements
   // ...   
}

{% endhighlight %}

The **if** statement actually includes some optional forms, like the **else if and else** branches. The complete form of the **if** statement is as follows;

{% highlight c# %}

if(condition is true){
   
}

else if(another condition){
   
}

else if(yet another condition){
   

   
}

else if(condition_n…){
   
}

else {
   
}

{% endhighlight %}

You can write as many **else ifs** as you need. The way this works is that, the first condition will be tested (the first if condition), if that is true, the statements inside the first **if** block will be performed and then the if block is exited. The other conditions stated on **else ifs and else** will not be executed.

On the other hand, if the condition stated on the first **if** is not true, the program flow will trickle down to the else ifs and will test each condition specified in them. If one of the conditions evaluates to true, then that else if block will be executed. 

If none of the conditions on the **if and else ifs** return true, then the group of statements inside the **else** branch will be executed. If you did not have an else block, then none of the statements will be executed if none of the specified conditions evaluates to true. 

{% highlight c# %}

using System;

class If {
	
	public static void Main(){
		
		int a = 101;
		
		if(a == 1){
			Console.WriteLine("One");
		}
		else if(a == 2){
			Console.WriteLine("Two");
		}
		else if(a == 101){
			Console.WriteLine("One Hundred and One");
		}
		else {
			Console.WriteLine("Clueless");
		}
	}
}


{% endhighlight %}

In this example, "One hundred and One" will be printed.

{% highlight c# %}

using System;

class If {
	
	public static void Main(){
		
		int a = 101;
		
		if(a == 1){
			Console.WriteLine("One");
		}
		else if(a == 2){
			Console.WriteLine("Two");
		}
		else {
			Console.WriteLine("Clueless");
		}
	}
}

{% endhighlight %}

In this example, "Clueless" will be printed because there are no conditions that evaluates to true

{% highlight c# %}

using System;

class If {
	
	public static void Main(){
		
		int a = 101;
		
		if(a == 1){
			Console.WriteLine("One");
		}
		else if(a == 2){
			Console.WriteLine("Two");
		}
	}
}

{% endhighlight %}

In this example, the program will not do anything. It will not print anything because none of the conditions evaluated to true, and there is no **else** branch


## Switch 

The **switch** statement is another branching mechanism. It passes control though each *case* statement inside the switch block. The **case** statement expects a constant value, so you cannot do something like **case == 1**. See the example code for more info.


{% highlight c# %}

using System;

class Switch {
	
	public static void Main(){
		
		int a = 3;
		
		switch(a){
			case 1:
				Console.WriteLine("One");
				break;
			case 2:
				Console.WriteLine("Two");
				break;
			case 3:
				Console.WriteLine("Three");
				break;
			default:
				Console.WriteLine("Default");
				break;
		}	
	}
}

{% endhighlight %}

Why is there a **break** statement inside each **case**--because withou the break statement, the flow of control will cascade to the next **case** or **default** statement--that is not what you want. As a matter of exercise, try removing the **break** on the case statements and see what happens. 

The **switch** can also handle string arguments, not only integers.

{% highlight c# %}

using System;

class Switch {
	
	public static void Main(){
		
		string a = "1";
		
		switch(a){
			case "1":
				Console.WriteLine("One");
				break;
			case "2":
				Console.WriteLine("Two");
				break;
			case "3":
				Console.WriteLine("Three");
				break;
			default:
				Console.WriteLine("Default");
				break;
		}	
	}
}

{% endhighlight %}


## While

A looping mechanism. Use this if you would like to perform a group of statements repeatedly. General format is **while(expression) statement** -- if you need to execute more than one statmeent, use the curly braces to group the statements. Example;

{% highlight c# %}

using System;

class While {
	
	public static void Main(){
		
		int a = 0;
		
		while(a < 10){
			Console.WriteLine("Value of a = " + a++);
		}
		
	}
}

{% endhighlight %}

The expression **a++** is syntactically equivalent to **a = a + 1**, it simply adds one to current value of a;


## For

The **for** loop is doing what the **while** loop is doing as well, it executes a group of statement repeatedly. The format of the for loop is a bit more involved though. The for loop has three (optional) arguments inside it. The arguments, if you provide it, changes the behavior of the for loop. 

Let's rewrite the **while loop** example using the for loop.

{% highlight c# %}

using System;

class ForLoop {

	public static void Main(){

		for(int a = 0; a < 10 ; a++){
			
			Console.WriteLine("Value of a = " + a);
		
		}		
	}
}

{% endhighlight %}

Take a closer look at the form of the *for-loop*, it is actually like this; **for(initializer ; condition ; iterator) statement**.

1. **initializer** - sets the initial value of a counter, in our sample, this counter is the variable **a**
2. **condition** - you have to stop somewhere, other wise you will have a loop that doesn't terminate. This is an expresion that evaluates to a boolean value. While this expression evaluates to true, the statement inside the body for-loop will keep on executing. When this expression evaluates to false, the loop terminates.
3. **iterator** - this expression defines what happens after each iteration of the loop, this is typically used to either increment or decrement a counter variable, but you can get creative with it

The *initializer and iterator** arguments of the for-loop takes more than one value, you just need to separate them with commas. As a beginning programmer though, you probably would have a less easy time making sense of convoluted codes like that, but just to show what else you can do with for-loops, take a look at the following code.

{% highlight c# %}

using System;

class ForLoop {

	public static void Main(){

		for(int a = 0, b = 10; a < 10 ; a++, b--, foo()){
			
			Console.WriteLine("Value of a, b = " + a + " , " + b);
		
		}		
	}
	
	static void foo(){
		Console.WriteLine("Foo");
	}
}

{% endhighlight %}

In this sample code, two variables (a and b) were initialized. Variable **a** was set to 0 and variable **b** was set to 10, they are just separated by commas (not semi colon). In the iterator part of the loop, variable **a** is incremented by 1 and variable **b** is decremented by 1---not only that, you can also insert function calls in the iterator section, just like what we did in this sample code. Each time the for-loop iterates, function foo() is called.  

## Nesting control structures

You can write loops inside other loops, ifs inside other ifs, switches inside ifs or whatever combination you can imagine (or need). Here is an example of a for-loop nested inside a for-loop.

{% highlight c# %}

using System;

class ForLoop {

	public static void Main(){

		for(int i = 1; i <= 5; i++){
			for(int j = 1; j <= 5; j++){
				Console.WriteLine("values of i and j are {0} {1}", i,j);
			}
		}		
	}
		
}

/*

the above code produces the output

values of i and j are 1 1
values of i and j are 1 2
values of i and j are 1 3
values of i and j are 1 4
values of i and j are 1 5
values of i and j are 2 1
values of i and j are 2 2
values of i and j are 2 3
values of i and j are 2 4
values of i and j are 2 5
values of i and j are 3 1
values of i and j are 3 2
values of i and j are 3 3
values of i and j are 3 4
values of i and j are 3 5
values of i and j are 4 1
values of i and j are 4 2
values of i and j are 4 3
values of i and j are 4 4
values of i and j are 4 5
values of i and j are 5 1
values of i and j are 5 2
values of i and j are 5 3
values of i and j are 5 4
values of i and j are 5 5

*/

{% endhighlight %}

The outer loop counts from 1 to 5 using the iterator (variable) **i**, the inner loop counts from 1 to 5 also. This kind of program produces what you might call a **cartesian product**. Notice how the variable **i** is printed 5 times--i is printed for each iteration of **j**. That is the reason why you have 25 rows of output; i iterates up to 5 and j iterates up to 5 also (5 * 5 = 25).  

**NOTE :** - The curly braces inside the string is called a formatter, it is somewhat similar to the **sprintf** of the C language---but you haven't coded in C, which means you will need some more explanation and examples;

{% highlight c# %}

int a = 10;
int b = 20;

Console.WriteLine("The value of a is {0}", a);
// the actual value of the variable a will be substituted to {0}

Console.WriteLine("a is {0} and b is {1}",a,b);
//value of a will be substituted to {0}, and value of b will be subsituted to {1}
//0 corresponds to the first actual number right after the string, and 1 to next, so on
// and so forth. 0 and 1 are actually positional values of the arguments that follow
// string


{% endhighlight %}

You can genearate the multiplication table using nested loops, like this;

{% highlight c# %}

using System;

class ForLoop {

	public static void Main(){

		for(int i = 1; i <= 5; i++){
			for(int j = 1; j <= 5; j++){
				Console.Write(i * j + "\t");
			}
			Console.WriteLine();
		}		
	}
		
}

/*

1	2	3	4	5	
2	4	6	8	10	
3	6	9	12	15	
4	8	12	16	20	
5	10	15	20	25

*/


{% endhighlight %}

The **\\t** is to simply add a tab in between the numbers. I used *Console.Write* so that the line won't add a carriage return/line feed after every number. I need the CRLF at the end of the row (that is the reason why there is an empty WriteLine outside the inner loop)


<!--

# 2. Program structure
# 3. Variables and Data types
# 4. Looping
# 5. Branching
# 6. Basic input output

-->


# Bibliography

1. Title: Inside C#. Author: Tom Archer, Publisher: Microsoft Press 2001
2. Title: Real World Functional Programming with examples in F# and C#. Authors: Thomas Petricek with John Skeet, Publisher: Manning Publications 2010

## Footnotes

[^1]: http://en.wikipedia.org/wiki/C_Sharp_(programming_language)



