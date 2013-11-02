---
layout: post

title: RD Skill Building. Programming Concepts

description: Journal of RD batch 1. Programming concepts using Core Java

except:

tags:
- Concepts
- Programming
- Introduction

categories:
- Training

---


# Overview

**Programming Concepts** is 1 of 3 training modules to prepare non-programming folks for HTML5 programming. 

The route we will take is rather a traditional one. We will build skills fundamental to programming, progress to JavaScript and finally, take HTML5 programming head on. The reason we need the programming skills is because we intend do lots of things in HTML5, things other than markup. 

## Why are we using Java

There were a couple of choices on what programming to use for the programming concepts part. These were Python, Ruby, JavaScript, C and C++.

We ruled out JavaScript---even if at first it would seem that we should start using it early on---because of the inherent complexity of its eco-system. It needs to be run inside the browser, the interpreters is inside the browser and the basic I/O or networking capabilities needs to be done within the confines of the browser. Surely we could have considered other acrobatics in JavaScript to overcome these issues, such as using the V8 engine, Rhino or even Node.JS, but it might add unecessary complexity and get in the way of learning how to program---quickly.

Python and Ruby are probably the easiest language to learn for a beginner. I did not choose them because of their syntactical characteristics, they are too far from JavaScript.

The options were then limited to C, C++ and Java. C has been discarded because it is too difficult to demonstate object oriented technqiues in it, it does not have native facility for OOP idioms.

C++ and Java shares quite a lot of the syntactical characteristics of JavaScript, either one of these two would have sufficed. I chose Java finally because of the richness of built-in libraries. It is easier and faster to get ramped up on Java than in C++ because Java has a more complete eco-system for development.

## Why are we keeping a journal

The basic idea is that each day, we will tackle something new on concepts and we will add some words to our vocabulary. 

Vocabulary is important because it allows the learner to have some handle on concepts being learned. The learners can talk about the concepts and start extrapolating ideas behind those concepts. This is a very simple approach in pedagogy. 

## Resources

1. The Java Language Specification (reference material)
2. Java Shooters (reference material) -- this is free and can be [downloaded here](free-resource-java-shooters-pdf/)
3. The Java Programming Language 3rd Edition (Reference material)
4. [Programming concepts workbook](/java-programming-concepts-workbook/)(workbook and practice questions)
5. GitHub Repo - All the code samples and exercises are stored on [this GitHub Repo](https://github.com/tedhagos/rd-prog-con-batch1.git). You need to have a Git client setup on your machine. If you do have Git, you can pull this repo by cloning it in your machine **https://github.com/tedhagos/rd-prog-con-batch1.git** 

## A note to the reader

These notes will make sense to you if you attended the workshop because they are essentially a bullet point of what have been discussed each day of the workshop. If you are (were) not part of the workshop, some concepts might make sense and others might not. Reading the [Java Shooters PDF material](free-resource-java-shooters-pdf/) could help because these lessons were based on that book.


# Day 1

## Concepts

1. An executable file is something that an Operating System (Win, OSX, Linux or UNIX) knows how to run. This is often called machine readable code. These are not readable by mere mortals
2. There was a time that programmers had to code in a very low level way (as low level as zeroes and ones). This wasn't fun and caused lots of nosebleeds, so they (programmers and computer scientist way before our time) deviced some abstractions, some sort of short-hand to these low level programming language (assembly language etc) 
3. As time went on, other programming languages sprouted. Some languages did build on top of other programming languages, providing a much higher abstraction (short hand)
4. These higher level languages became increasingly powerful because they were easier to understand. They can be read by mere mortals. The files where we write programs using higher level languages are known as source files or source code. Source files are not machine-readable codes, we will need some tools to make our source code palatable or runnable by the OS
5. Now comes the compiler and linker. Compilers and linkers gobbles up source codes and spits out machine readable codes. The machine readable code is what you double-click and launch as applications

## Setup of development environment 

1. Install the JDK (Java Development Kit)
2. Configure the PATH and CLASSPATH variables. There are some resources you can look at on how to do this. One from [Oracle](http://docs.oracle.com/javase/7/docs/webnotes/install/windows/jdk-installation-windows.html) and [another one](http://www3.ntu.edu.sg/home/ehchua/programming/howto/JDK_Howto.html), somewhere on the net.
3. Test the configuration. Get a terminal (Termina.app, cmd or gnome-terminal) 

<pre class='codeblock'> 
  
  java -version  		//for OSX and Linux
  c:\>java -version	//if you are on windows

</pre>

This should return something like this


<pre class='codeblock'>

  java version "1.6.0_33"
  Java(TM) SE Runtime Environment (build 1.6.0_33-b03-424-11M3720)
  Java HotSpot(TM) 64-Bit Server VM (build 20.8-b03-424, mixed mode)
_$
 
</pre>


## Vocabulary 

1. **Source code** - Computer program that contains instructions using a high level language. There are lots of programming languages, each language will have its own sets of programming instructions
2. **Compiler** - source codes, while easier to read and write, are not machine-readable. A compiler is used to gobble up source code(s) and transform them. The resulting files can now be read by the machine (can be ran by the OS)
3. **Interpreter** - does exactly what a compiler would do, but it does a little bit differently. A compiler will read and process each entry in the source file before it executes all the instructions, one after the other until there is no more instruction to execute. An interpreter on the other hand, reads the first instruction, executes it immediately, then proceeds to the next instruction
4. **High level language** - A programming language that humans can read. Some of them are even close to the language we use in everyday conversations---well, not really, programming languages are usually terse, dry and cryptic, the point is that they are more intuitive than instructions like *MOV, JMP or 010101111 100111* so on and so forth. Java, Python, Ruby, JavaScript are examples of high level languages; there are many more, but you get the idea 
5. **Java is different from JavaScript** - They are two different programming languages. One came from Sun Microsystems (now Oracle) and the other came from NetScape. One is a compiled language that runs inside a Virtual Machine and the other is a scripting language that runs inside a browser. There are some similarities on the syntactical aspect but they are like apples and oranges, they are not related even


### Code works

Learn how to write the simplest program in Java. The purpose is not to gobble up a lot of Java---just get a feel of how to write a (valid) code, compile it and run it.

<script src="https://gist.github.com/3192789.js?file=HelloWorld.java"></script>


# Day 2

- [Little bit of history about Java](http://www.oracle.com/technetwork/java/javase/overview/javahistory-index-198355.html)
- Java's first name was Oak. Java's rise to fame wasn't all because of Java's technical merits. The rising popularity of HTML and Internet technologies (HTTP) contributed to Java's claim to fame

## Concepts

1. **Java native data types** - There are eight (8). You can use *byte, short, int & long* for counting things. You can use *float & double* for measuring things. Use *boolean* to represent truth or falsity. Use *char* to do stuff in unicode
2. Each programming language have their own set of keywords or reserved words. These reserved words have special meaning to the language's compiler. Learning the actions of the reserved words is an important activity in programming. Do not use reserved words as identifiers (variables, class names or method names) in your own code
3. White space is used by the Java compiler to separate the parts of the code. Whether you use a single white space or a 100 white spaces does not matter at all. Use whitespaces intelligently to improve readability of your code 
4. A program code, like a regular English sentence, can be broken down into components. The process of tokenizing (segregating) the source code and performing analysis/evaluation on it, is known as lexical analysis---this is a function of the compiler
5. Java has some rules when performing addition between types. When one of operands in a an addition expression is a *double*, the result of the expression is a double type; when one of the operands is a *float*, the result of the expression is a float type; when one of the operands is of type *long*, the result is of type long; any other case, the result of a math addition is of type *int*

## Vocabulary 

- **Reserved words or keywords** - special words in a programming language. They have designated actions. You cannot use these as names of either class, variable or function
- **Identifiers** - a collective term used to refer to either program variables, name of classes or name of functions (methods)
- **Data types** - The kinds of data you can define and use. Java has 8 native data types. byte, short, int, long, float, double, char and boolean
- **Syntax error** - When you don't follow the rules of the language or don't write the program source code in accordance to the rules of usage, this is what you get. You cannot proceed to compilation until you have corrected all syntactical errors
- **Compiler error** - Error that happens during compile time. Syntax errors could be one of the causes of a compilation error---there are other reasons

# Day 3

## Concepts

- You can organize your code by breaking it down into little, more manageable pieces and tuck them away into functions. Using functions as a unit of abstraction is a characteristic of modular or procedural programming
- While Java can use functions a unit of abstraction, it has language support to use a wider unit of abstraction---the class mechanism. 
- **Control structures** - There are 3 ways a program can flow, at the method *block level*. It can proceed sequentially by executing statements one after another until it runs out of code to execute. It can fork or branch, going one direction when some condition is true, then going another direction when the condition is not true. The code can also flow in a circular and repetitive fashion---it can go on in this loop while certain conditions are true. 


## Vocabulary

- **RHS** and **LHS** - left hand side (LHS) refers to stuff that you write to the left of the equal sign (=), Java's assignment operator. Corollarily, right hand side (RHS) refers to what you write on the right side of the equal sign. LHS is concerned about the *location* of a variable, not it's content. The RHS is concerned about the content (value) of the variable, not its location or address. Hence, the expression *a = a + 1*, means; a (LHS) will resolve to where *a* is located, say address 1001; and *a* (RHS) refers to the current value of *a*.
- **Abstraction** - Its a mental process of thinking a dozen (or so) characteristics about a specific something. List down its traits, behavior, characteristics, properties etc. Then try remove items from this list or reduce this list. Each time you remove an item, ask yourself---"If I remove this stuff, will this object still be the same object, or will it become something else". You will stop the reduction when what remains is the absolute essential characteristics of the object


### Code works 

<script src="https://gist.github.com/3192789.js?file=Multiply.java"></script>


# Day 4

Not much concepts during day 4, this was spent clarifying solutions to previous home works and machine problems.


- **Data structure** - constituent components or parts of a data type. e.g. the data structure of a calling card or a business card is; name, email address, phone number. If we were to write this data structure in Java, it would look like;

~~~
class BusinessCard {
	String name;
	String phoneno;
	String emailaddress;
}
~~~

- **Objects** - it is quite convenient (for now) to think of Java Objects as some sort of data structure, since it is, after all, a complex data type. Its difference with a traditional data structure (like the BusinessCard example above) is that, a Java object has *behavior* (because there are functions in it), while a traditional data structure cannot exhibit behavior

- **Runtime error** - a kind of error that happens when your application is running. The code may have compiled, which means syntactically it is okay, however, your code has not satisfied some runtime requirement or may have violated some rules (which cannot be checked during compile time). e.g. If you compile a class that does not have *public static void main*, and tried to run that class, you will get a **NoSuchMethod** exception. Having a valid public static void main is a requirement for an application to run (CLI applications)

### Code works

<script src="https://gist.github.com/3192789.js?file=KeyboardInput.java"></script>
<script src="https://gist.github.com/3192789.js?file=FindGCF.java"></script>


# Day 5

- **On Object Oriented approaches** - There is *class-based* OOP and *Prototypal* OOP. Java uses class-based OOP---lets start with this one because this seems to be the classical approach

- **On Objects and Classes** - We already discussed objects in the last couple of days. We will use objects to model real-world (business) objects. In order to do this, we need to go through an *Abstraction* process. Once you've got an idea about what the object should do and what it must know about itself, these can be codified into **Classes**. 

Classes are the stuff where objects comes from. An object is an instance of class. Just like when you have a blue print of the house, the blue print is the not the house, it only contains instructions on how to build the house. Classes are to blueprints, as objects are to houses. 

- **Methods** - methods or functions can accept arguments or parameters. Whatever data you pass as a parameter to the method you are calling will become available to the method. The method can do with the data as it pleases. When a method makes changes to the parameters, sometimes the original data is not affected (pass by value) and sometimes the original data can be affected (pass by reference) --- but we will get to that on later sessions


### Code works

Java accepts parameters from the command line. Everything you pass as a command line argument is stored inside *main(String []args)*. The very first command line param is stored in args[0], the next one in args[1] ...

<script src="https://gist.github.com/3192789.js?file=MainParams.java"></script>

# Day 6

- **Member variable** - declared on the same level where methods are declared (at the top level). These variables becomes the states of the object. They are reachable and addressable as long as the object is in scope--meaning, it hasn't been garbage collected yet
- **Local variable** - declared inside methods. They are only usable from within the method where they were created--they cannot be used by other methods. Parameters to the methods become local variables as well.
- **Inheritance** - A major characteristic of an OO language. A form of re-use (by extension), in Java , the keyword for class inheritance is *extends*
- **Base class** - sometimes also called *Parent class or Super class*. A target of the *extends* keyword. When a Parent class is extended, whatever behaviors or states the Parent class have, the extending class will automatically have.
- **Derived class** - sometimes also called *Child class*. In an inheritance relationship, the Child class is the one doing the extending. It is the recipient of the behaviors and states of the class being extended (Parent class) 

### Code works

The MobilePhone class defines, for itself, only the *void sms()* method, however, because it extended the Phone class, it can also exhibit behaviors of the Phone. The methods setNumber, call and answer are available for the MobilePhone even if MobilePhone does not contain code definitions for these methods--they are available because these methods were inherited from class Phone

<script src="https://gist.github.com/3192789.js?file=Phone.java"></script>

# Day 7

- **Type** - A type is synonymous to a set of behaviors that an object exhibits. A set of behavior (or promised behavior) usually constitutes a Type---usually because there are types in Java that don't have any declared behaviors (marker interfaces), but lets not get ahead of ourselves, that is further down the road. When you create a new class, you are defining a new Type. 
- **Object contract** - When you inherit from a class or implement an interface, you are entering into an object contract. Whatever behavior that your Parent class supports, you must support too
- **Polymorphism** -- When you inherit behavior or functionality from your Parent class, and you modified that behavior (method), it makes the behavior polymorphic. This is done by method overriding

# Day 8

- **Boundaries or encapsulation units** - Boundaries or encapsulation units from where and how far you can access member methods and variables of a given object. There are four access controls that govern these boundaries--*public, default, protected and private*
- **Packages** - a package is an encapsulation and organizational unit. They can restrict access to variables and methods of a given object. They can also be used as a way to group similar classes. Packages are like folders, and as such, they can function as namespaces---to prevent conflicts of names
- **Storage classes** - Methods and variables can belong to either the class or its instance. Static members (variables and methods that comes with the *static* keyword) are stored on the class. Non-static members are stored on the object. Non-static members are dedicated and non-shared copies of their respective objects) while static members are shared across all instances

### Code works

The *color* variable is declared as a non-static member. Any property change to a specific color variable of a specific object cannot impact the color variables owned by the other objects.

The *count* variable on the other hand is shared across all objects. A change of the count variable, from any object will impact all the instances.

### Code works

<script src="https://gist.github.com/3192789.js?file=Shape.java"></script>

# Day 9

- **Passing parameters** - When parameters are passed to a method, a local copy of that variable will be made for the method. Be careful to note that when you pass parameters of a primitive type, you are passing a local copy of value of the parameter; When you pass parameters of reference types, the copy of the variable being passed contains not the actual object but a reference to the actual object. Any change you make to the object (while inside) the method using the object reference received via parameters will persist, even when the method goes out of scope.

<script src="https://gist.github.com/3192789.js?file=SwapInt.java"></script>

Pass by value

<script src="https://gist.github.com/3192789.js?file=Swap.java"></script>

Pass by value also, but it hopelessly looks like a pass by  Reference

# Day 10

- **this** - a reserved word which means a reference to the current object's self. This is what a *constructor* returns.

### Code works

The String object is a built-in class. It allows us to manipulate words in an object oriented way rather than as a simple array of characters (you can still do that if you really want to). 

A sample code (below) shows how to walk through each character or a given String.

<script src="https://gist.github.com/3258037.js?file=Str.java"></script>

An exercise on the *this* keyword

<script src="https://gist.github.com/3192789.js?file=Person.java"></script>

# Day 11

## Concepts

- **Graphical User Interface programming (GUI)** is usually exposed by the O.S. as a set of APIs (Application Programming Interfaces)---this is also usually done using the C Programming language. If you have knowledge of programming GUI using the native SDK---say windows SDK (software development kit), you could do that as well. 

- **Java GUI programming** (desktop GUI) is done by utilizing either the *java.awt* or javax.swing* libraries. These libraries provides an object oriented (Java-ish) way of constructing widget and windows

## Vocabulary

- **JFrame** - a top level container. It can contain widgets like buttons, textfields, labels etc. It can also contain other containers. The nesting of containers makes it possible to create sophisticated layouts
- **Layout Manager** - A governor of sorts. It governs the distances and spacing of widgets relative to its siblings (other widgets) and relative to its container. There are many kinds of layout managers
- **BorderLayout** - A layout manager. divides the container into 5 regions (*north, south, east, west and center*). This is the default layout manager for the JFrame
- **FlowLayout** - Another layout manager. It arranges the widgets in succession, from left to right then top to bottom
 
### Code works

When main() is executed, it simply calls the constructor, which in turn simply creates and instance of the **Gui1** class (which is a subclass of JFrame). At this point, the program enters a never ending loop---this is the basic idea behind GUI programming, you wait for the user to do something. We need to wait for the user to shut down the window.

<script src="https://gist.github.com/3258037.js?file=Gui1.java"></script>

UserForm.java shows an example of how you can nest containers within other containers.

<script src="https://gist.github.com/3258037.js?file=UserForm.java"></script>


# Day 12

- **Listener object** - Special types within the Java library that are capable of *listening* to user generated events. There are various kinds of listeners that you can use e.g. MouseListener, KeyListener and ActionListener; these are the most common. You need to create objects of these types in order to have an event listening mechanisms. Most Listeners are Java Interfaces, so you need to be comfortable with Type inheritance

- **Event Trigger** - A widget e.g. JButton, JTextField event JFrame can be a source of an event


### Code works 


MyListener **is a kind of** ActionListener. ActionListener is a special interface that is capable of *listening* to events. The basic idea on event programming are;

1. Createlistener object that listens and processes specific events--like mouse clicks and keyboard actions.
2. Create widgets that you would like to act as triggers, e.g. buttons 
3. Connect the event trigger (like a button) to the listener 
4. When an event is generated by the user, the specific methods defined by the Listener objects will be activated---actually, *called-back*; 


<script src="https://gist.github.com/3258037.js?file=Gui2.java"></script>


# Day 13

The previous example (Gui2.java) essentially separates the JFrame and a Listener object. This approach is fine but it needs to marshall the object references (instances of Gui2 and MyListener) back and forth. Gui3.java takes a different approach. 


<script src="https://gist.github.com/3258037.js?file=Gui3.java"></script>


In this version, Gui3 is both a JFrame and a Listener in itself. Gui3 is inheriting from 2 Types--a JFrame so that we can get all the goodies of a Windowed frame. It is also a listener by implementing the ActionListener interface. The *actionPerformed()* method can now be written on the top-level of Gui3 because of the changes we did on the inheritance structure of Gui3. 

The fact that *actionPerformed()* is now a member of Gui3 means that it has access to all the other members of Gui3, namely tf (JTextField) and btn(the JButton). Now we can move away from passing object references between the frame and the listener--like we did in Gui2.java


<script src="https://gist.github.com/3258037.js?file=RandomWord.java"></script>

RandomWord extends Gui3. Notice how clean the code of RandomWord is? All the functionalities of Gui3 is automatically available for RandomWord. 

We wanted RandomWord to do something different than what Gui3 was doing. This was accomplished by simply overriding the *actionPerformed()* method in RandomWord. This way, we can put whatever functionality we want in RandomWord--Inheritance and Polymorphism in action.


# Day 14

## Vocabulary

- **abstract class** - the *abstract* keyword can be used for a method or a class. When used in a class, the class cannot be instantiated. Abstract classes are the stuff for OOP analysis, you will use this deliberately to craft an overall design for your class hierarchy. As a regular dev (non-designer and non-architect), you need to know some basic facts about an abstract class.

1. You cannot instantiate it
2. It is intended to be inherited
3. Some or all or none of the abstract class' methods can be abstract


- **abstract method** - when the *abstract* keyword is used on a method, it cannot have an implementation--meaning, it cannot have a *method block*, the stuff inside the enclosing curly braces, including the curly braces. An abstract method looks like this.

~~~

void foo(); 	// as opposed to
void foo() {} 	// which is a concrete method because it has a method body
				// a pair of curly braces constitutes a method body even if
				// the braces are empty

~~~

Facts you need to know about the abstract method and an abstract class

1. an abstract method is terminated by a semi-colon and does not have a method block
2. when one of the methods of a class is abstract, the whole class needs to be declared as abstract

A concrete class then, is a class without any abstract method(s) and is itself not declared as abstract


- **final class** - when the final keyword is used on a class, the class cannot be inherited. The decision to make a class final is a design decision--one that is not to be taken lightly; having said that, the java.lang.String class of Java is actually declared as final; you cannot inherit from the String class. 

- **final method** - when a method is declared as final, it cannot be overriden. You effectively stop polymorphism right there. Again, these are decisions best left for OO designers. As a dev, you just need to know the consequences of the final keyword

- **final variable** - when a variable is declared as final, it effectively makes the variable a constant. Once a final variable has been declared and initialized, you won't be able to assign a different value to that variable

- **.equals()** - to compare equality between primitive values, use the **==**. If you are comparing reference types, you cannot use the double equals operator which is effective only for comparing value types. To compare reference types, you need to use the **.equals()** method--this method is inherited by all classes in Java from java.lang.Object. 

**USAGE:**

~~~

String a = "HELLO WORLD";
String b = a.toUpperCase();

if(a.equals(b)) {
	
}

~~~

# Day 15

- **innner class** - You can define a class within another class. You can reference all the methods and variables (even private ones) of the enclosing class from an inner class.
- **anonymous class** -  Like an innner class, an anonymous class is also nested within another class--only, they don't have name. Anonymous classes are widely used for doing event handling in GUI programming
- **blocking ** - example, calling somebody on the phone. You cannot complete the phone call until the person on the other line picks it up. The whole task is blocking because the completion is dependent on the other person at the end of the line; if he picks up the phone or not 
- **non-blocking ** - example, sending an email or IM. All you have to do is send the email or message, you don't need to wait for the recipient to acknowledge the message
- **Thread** - A Java class which allows us to run some portions of our code in non-blocking mode.

### Code works

<script src="https://gist.github.com/3258037.js?file=Gui4.java"></script>

Gui4 demonstrates using both inner class and anymous class for doing event handling


<script src="https://gist.github.com/3258037.js?file=ThreadG.java"></script>


A small Thread Sample


# Day 16

Got a feel of SQLite. Most of the exercises for today are already on Java Shooters. No need to replicate here. For more resources on SQL commands, head over to [W3Schools/SQL](http://www.w3schools.com/sql/default.asp)



# Day 17

<span class="stress">Some new vocabularies</span>

- **GoF** (Gang of Four). Author of the Book Design Patterns
- **Design Patterns** - Authoritative work on elements of reusable designs. Should be read by programmers using an OO language. You might want to [read this](http://www.oodesign.com)

### Code works 

The annotated source of today's code is [here](/source-docs/DBSample.html)

If you will try this example, don't forget the following steps.

1. Create your test.db using the sqlite tool
2. Make sure sqlite-jdbc driver (the jar) file is available
3. Before you compile, ensure that the sqlite-jdbc jar file is included in the CLASSPATH

# Day 18


<span class="stress">Exceptions</span>

An Exception is an error, an abnormal condition, a disruption of normal pro- gram flow. Programmer’s throw Exceptions from their their codes if they think something has gone awry. As a (responsible and defensive) programmer, you will make sure that your code will be able to respond to non-fatal conditions. Surely you will not allow your program to crash because the user has inputted wrong data. The code must be robust enough to recover from and even rectify abnormal conditions (this is lifted straight from the Text of Java-Shooters)--You can't get away with Exceptions in Java, lots of codes you will deal with declares Exceptions. 

**How will you know when you need to handle exceptions**

1. Just keep on coding, the compiler will tell you anyway if you missed to handle an exception being thrown by some method you are using; or
2. Study the codes that you are about to use, get to know the API well enough before using it (I prefer this one, start doing this, start coding like a programmer) 

### Code works 

Today's code works is a combination of Swing Programming and JDBC programming. I annotated the codes for your reference, [you can view it here](/source-docs/DBProgGui.html)









