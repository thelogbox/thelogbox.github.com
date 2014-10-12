---
layout: java

title: Java Object Oriented Programming

description: Introduction to Java OOP

excerpt: 

tags:
- OOP

---



If you set out to truly understand how an automobile works, down to tiniest detail of how each nut and bolt performs, you could be in over your head---especially if do not have a degree in mechanical engineering. On the other hand, if the goal is a simpler one such as "to drive a car", it would seem to be a more achievable goal, by order of magnitudes. The mechanics of vehicle control such as steering, braking and accelerating are more manageable to keep in our heads as compared to principles of hydraulics or the inner workings of the internal combustion engine.  

### Complexity
We are surrounded by complex systems in our daily lives, and a career in programming will not shield you from that---au contraire. Our saving grace is that we have gotten pretty good at dealing with complexities. Take for example the plants that you have at home, you don't need to know the gory details of its biological structure in order to know that you need to give it some sun and water lest it will die. Another example is the light switch, you don't need a degree in electrical engineering to know that you if you flip the switch one way, its lights out---flip it another way and its lights on. 

Computer scientist have grappled with complexities through the ages and have managed to develop tools to manage software complexities. One of the goals of complexity management is to engineer the illusion of simplicity---to hide the working details of a complex system in order for it to be usable. 

There appears to be an inherent limit in the capabilities of our brain to deal with a swarm of information, we just can't deal with all of it---at once. The silver lining, like I mentioned earlier is that we have gotten pretty good at dealing with an avalanche of information. We have developed a coping mechanism called "abstraction"

A new employee on a large organization cannot and will not be able to comprehend all operational tasks that happens in the organization. He cannot possibly know the tiniest work details of each and every employee in the company. If you will just but give him a little time in the company, not only will be able to re-orient himself, he can also do something really productive that adds value to the company. So what happened between then and now? What makes us capable of navigating complex systems now but not then? The answer is, our minds oriented itself and adapted to its new environment.

Our minds focused on just a few items while ignoring the other inessential details of the others. It then moved on to other parts of the complex system forming hierarchies of concepts that builds on top of one and then another. The information bottleneck was broken by dealing with it in chunks. When we focus on specific chunks, we are choosing to deal with idealized and generalized model of the object right in front of us \cite{ooad} thus increasing its semantic content. This abstraction process is responsible why we are capable of understanding very complex systems.  

## Learning objectives
Abstraction is a key and foundational concept in OOP. There is no way around it. You will not go far in OOP and hence, Java programming without understanding the concept of process of abstraction. You also need the ability to leap from the OOP concepts to their Java implementations---those are the things we need to learn at the moment. 

## Key concepts

There are a couple of criteria that a programming language needs to meet before it can be considered a OOP language. It needs provide a facility to effectively implement the process of *abstraction*. It needs to provide a way to reuse functionality by means of extension---*inheritance*. It needs to have a mechanism to protect data and type from inadvertent and unintentional state changes---*encapsulation*. It needs to have a mechanism to effect *polymorphism* and it needs to have a mechanism for grouping some programming constructs such as methods and classes---*encapsulation*.  

### Abstraction

Abstraction is an activity where the essential characteristics of *something* is distilled. It makes that something different from other somethings. For example, if you think hard about an elevator and try to list down the characteristics, what would they be? How is an elevator different from other modes of transport such as an escalator or a conveyor? 

We cannot simply list *move up* and *move down*, while these set of behaviors differentiate the elevator from the conveyor (which simply moves to the left and to the right), it does not differentiate it effectively from an escalator. Even if we incorporate the idea that an elevator stops in between floors, it still does not differentiate it because the escalator also takes us from floor to floor. We can incorporate the behavior of *skipping floors* and that will be an effective differentiator because an escalator cannot skip floors. 

If we summarize the *behavior* of the elevator, we can come up with two behavior-item---**moveDownToFloor()** and **moveUpToFloor()**. That is the essence of an elevator object. The tricky part is how to know when to stop adding or removing behavior from an object. Unfortunately, abstraction is an acquired skill, and you can only get better at it overtime if you do it lots of times. I can tell you from practice that abstraction is not so much as identifying a thousand (unimportant) behavior for an object. On the contrary, abstraction is more an exercise on reduction. Try to remove behavior from an object until you are down to a bare minimum. Let's take a shoe object for an example. You can remove the heels of a shoe and it still will be a shoe. You can remove the laces and it still (barely) is a shoe---but you cannot remove its sole. 

The abstracted list of behavior of an object is known as a *Type*---this is an important terminology in OOP and Java, that is why I am emphasizing it in this section. All objects in Java **must have at least one type**---it can have more, but not less.  

### A discussion on Types

It might help if you think of a *Type* as some sort of a contract or a promise from an object. The object is making a committment that it will respond to any other object or program who calls anyone of the methods within this type. Going back to the elevator example, it means that any Java object or program can call *elevator.moveDownTo()* or *elevatorMoveUpTo()* and they are guaranteed to get a response.  

There are three ways to define a Type in Java, the *class*, *abstract class* and *interface*---each has its own strengths and inconveniences.  

## Objects, Classes and Types

An object is an abstraction of something useful to you (the programmer). An object represents an idealized and generalized model of something of interest. Take for example a Phone object, its protocols could be abstracted as *answerCall()* and *dialNumber()*. If we skip all the programming details of type creation, we can start using the object in a Java program.


	Phone phone = new Phone();
	phone.answerCall();
	phone.dialNumber("6321234567");


### Using an object

*Phone* with an uppercase first letter is a type declaration and *phone* all lowercase letter is variable of type *Phone*---in the statement \highlight{int i=1;} *int* or integer is the type and *i* is a variable of type integer. The *new* keyword is responsible for creating the Phone object and *Phone()* is actually a special function or method---its called a *constructor*. To invoke the behavior of an object, you simply need to call its method using the dot notation. That is what we did in the statements *phone.answerCall()* and *phone.dialNumber()*.  

Objects are made by instantiating *Classes*. Classes are actually what we define as abstraction construct. If we were to codify the Phone program example, it could look like the following:

	class Phone {

	   String phonenumber="6321234567";
   
   	void answerCall() {
   	}

   	void dialNumber(String args) {
   	}

	}

*Phone.java* is a Java class. It is constructed by using *class* keyword followed by a name of the class ^[A class name is something that you need provide as the author of the class]. The open and close curly brace is the body of the class.  

You can define methods and variables inside the class body. The methods as a group constitutes the protocols of the object. It is the set of methods that the Phone object guarantees to respond to. 

Java classes are written on source files---ideally, one class definition per source file but you can define more than one class in a source file. Classes are compiled using *javac sourcefile.java*, in our case, **java Phone.java**. This will produce a file named *Phone.class*, it is the compiled version of Phone.java---compiled classes is a requisite before you can create objects out of them.  

	import static java.lang.System.out;

	class Phone {

   	String phonenumber="6321234567";
   
   	void answerCall() {
      	out.println("Answering call...");
   	}

   	void dialNumber(String args) {
      	out.println("Calling " + args);
   	}

   	void setPhoneNumber(String args) {
      	phonenumber = args;
   	}

	}

	class PhoneTest {

   	public static void main (String [] args)
   	{
      	Phone p1 = new Phone();
      	p1.answerCall();
      	p1.dialNumber("6329876543");
      
      	Phone p2 = new Phone();
      	p2.answerCall();
      	p2.dialNumber("6327778888");
      
   	}

	}

The PhoneTest program shows a more complete example of how you might use the Phone object. The PhoneTest class is not necessary because the *main()* function could have been easily written inside Phone class, but the verbosity of two classes was chosen to make the example more readable and less confusing for beginner programmers. 

### Instantiation

To create an object, you need to instantiate a class. The resulting object now has the protocols or the *Type* of that class. You can begin using the object according to the protocols that was defined by its class. The protocols needs to be followed strictly, if the method defined is *dialNumber(String args)*, you need to call the method exactly as it was defined. The spelling needs to be right, the casing of the letters needs to be right and if the method expects an argument or parameter to be passed, you need to pass the expected parameter---in the case of the *dialNumber* method, it expects a String parameter. 

The PhoneTest program defines the *setPhoneNumber()* method and the *phonenumber* variable. The class initially defines its own phone number via the phonenumber variable, but it also offers a way to change this phone number. The *setPhoneNumber* method was declared to facilitate a way to change an internal detail of the class. If the *setPhoneNumber* method is called passing a new phone number, the object's state will change---it will have a new phone number.  

### Encapsulation

Classes provides a way to package data and behavior in a single construction. The *phonenumber* variable is not foreign or external to *Phone Type*, it is an instrinsic property of the Phone. The *setPhoneNumber* method is also intrinsic to the Phone. If you invoke the *setPhoneNumber* method, it will act on a data that belongs to the Phone object, not something alien to the Phone. Java enforces this kind of encapsulation in a strict fashion. There is no way to define a stand-alone method or a stand-alone variable, every method and every variable needs to be associated with a *Type*. 

The concept of objects, classes and types are intertwined. Understanding these concepts individually and collectively forms one of the basis of effective Java programming. 

Objects are created from classes, you cannot create an object without a class definition. When you create an object, the process is known as *instantiation* ^[An object is known as instance of a class]. An instantiated class (object) can respond to messages or methods as long as the methods are within the defined protocols of the class.  

A *Type* is a collection of methods. One way to define a *Type* is to define a class---there are two other ways, they will be discussed later in this chapter. It is not correct to say that a class has a type. It is correct to say that a class is a Type, just as it is correct to say that an object has a Type---the Type that was defined by the class.

To illustrate the relationship between a class and an object, try imagining a house plan, a blueprint if you may---the kinds of drawings that architects produce before building a house. If we build one house out of an architect's blueprint, we can say that the physical house that was built is an instance of the blueprint.  

If we build another house using the same architect's blueprint, we can say that the second house is another instance of the architect's blueprint. Now there are two houses built from the same blueprint. Even if the two houses will be identical because of their structural similarities, they are actually two distinct houses, they are not one and the same. They will be inhabited by different people, they may differ in roof colors or interior paints etc. That is exactly what's going on as well between **Classes** and **Objects**. Classes are the blueprints from whence objects are made from. 

Going back to the Phone example, if we wanted to create other Phone objects, we simply need to instantiate the Phone class again. 


	import static java.lang.System.out;

	class Phone {

   	String phonenumber="6321234567";
   
   	void answerCall() {
      	out.println("Answering call...");
   	}

   	void dialNumber(String args) {
      	out.println("Calling " + args);
   	}

		void setPhoneNumber(String args) {
      	phonenumber = args;
   	}

	}

	class PhoneTest {

	   public static void main (String [] args)
   	{
      	Phone p1 = new Phone();
      	p1.answerCall();
      	p1.dialNumber("6329876543");
      
      	Phone p2 = new Phone();
			p2.setPhoneNumber("6329995555");
      	p2.answerCall();
      	p2.dialNumber("6327778888");
      
   	}

	}


### State encapsulation

The variables *p1* and *p2* are both of type Phone but they are two distinct objects. They have two different states (phone numbers). You can manipulate one phone object without impacting the state of the other. This characteristic of objects allows for a more sane and rational programming environment. 

## Constructors

Object creation requires four things, the type of object to be created, a variable to store the reference of the created object, the *new* keyword to effect the actual creation and a *constructor*. You have seen and used all these things with the exception of the last one, the constructor. In the statement \highlight{Phone p1 = new Phone()}, *Phone* is the type and *Phone()* is the constructor. 

A constructor call is a function, first and foremost but it is not an ordinary function. It is special because it bears the same name as that of the class where it is declared and unlike ordinary functions, it is not written with a return type. 

Constructors are important, you cannot create objects without them. They are of extreme importance that Java will actually supply a default constructor in case you do not provide one explicitly. 


	class Phone {

		public static void main(String []args) {
			Phone p1 = new Phone();
		}
	}


In the preceding code sample, we did not define an explicit constructor but we were still able to call \highlight{new Phone()}. The reason for this is because Java supplied our code with a default no-arg constructor ^[No argument constructor]. As if we had written something like


	class Phone {

		Phone() {
		}

		public static void main(String []args) {
			Phone p1 = new Phone();
		}
	}


There is also no *return* statement within the body of the constructor. When the constructor returns, it will create an object of type Phone, the variable *p1* will hold a reference (an address) to actual Phone object. 


## Inheritance and Polymorphism

A class can re-use all the codes and functionalities of another class by means of extension. The class being extended is typically called the *parent class* ^[Sometimes also called super class or base class] and the extending class is called a *child class*.  Class extension grants the child class all the inheritable methods and variables of the super class ^[Not all members can be inherited. Members that were declared as private cannot be inherited. This is elaborated in chapter 10]. The instant functionality gained from class extension impacts the productivity of the programmer in a positive way. If the abstractions are done carefully and rationally, it becomes possible to write a piece of code that can be used in other applications. 


	import static java.lang.System.out;

	class Telephone {

		String phonenumber;
	
		void init() {
			out.println("connecting to carrier via land line");
		}
	
		void dialNumber(String args) {
			out.println("Dialling " + args);
		}
	
		void answerCall() {
			out.println("Answering call...");
		}	

	}

	class MobilePhone extends Telephone {

	}

	class TelephoneTest {

		public static void main(String[] args) {

			MobilePhone mp = new MobilePhone();

			mp.init();
			mp.dialNumber("6327775566");
			mp.answerCall();

		}
	}
	

### extends keyword
In the sample code, the *MobilePhone* type was created by defining a class. The class block does not contain any definition and yet we were able to call the *init*, *dialNumber* and *answerCall* methods against it---these methods, though not explicitly defined inside the *MobilePhone* class has been inherited from the *Telephone* class. The *extends* keyword is used to denote that one class is inheriting from another class.

### java.lang.Object is the root class in Java

Class extension is not an optional activity in Java programming. A Java class needs to extend *at least and at most* one other class. All newly defined classes, by default, extends the *java.lang.Object* class, unless otherwise overriden by an explicit *extends* declaration. In Listing 4.5, class Telephone is not explicitly extending any class, hence it is a child class of *Object*--it is as if we had written;


	class Telephone extends Object {

	}
	class MobilePhone extends Telephone {

	}


*MobilePhone* does not extend *Object* because we declared explicitly that it extends Telephone. You will realize soon enough that every class in Java descends either directly or indirectly from \code{java.lang.Object}. 


### Single rooted class inheritance

I would not advise that you explicitly declare all your classes to extend from Object. Firstly because Java will do that for you implicitly and secondly because you can only extend one class. There is no way to achieve multiple class inheritance. Java follows a single-rooted class inheritance, once you have extended a class, you cannot inherit from another one. That is not to say multiple inheritance cannot be achieved in Java, it can be, using *interfaces*.

### interfaces

Creating a class is one of three ways to define a *Type*. The second way is to create an *interface*. An interface is the purest form of a type because it only contains the protocols but not the implementing details of the object. The class on the otherhand contains both the protocol (the Type) and the implementing details (body of the functions). 


	interface Phone {
		void answerCall();
		void dialNumber(String args);
	}


An interface is declared using the *interface* keyword followed by a name ^[The name of interfaces are programmer defined, like the class]. The opening and closing curly braces comprises the body of the interface.

Methods are variables can be declared in an interface, but they are not the kind of variables and methods that you would declare insie the class. Interfaces can only contain *abstract methods*, which makes sense because interfaces are supposed to contain only the Type information and not the implementation detail. An abstract method declares only the method signature ^[Method signature is the return type, name of the method and parameters that it accepts] and has a semi-colon immediately right after, in place of the usual method body. If you declare variables inside the interfaces, they will be **automatically** *final, static* and *public* ^[These keywords are better discussed on the post RE methods].

	//PhoneToo.java

	interface IPhone {
	
		void answerCall();
		void dialNumber(String args);
	
	}

	class Phone implements IPhone {
	
		public void answerCall() {
			System.out.println("Answering call");
		}
	
		public void dialNumber(String args){
			System.out.println("Calling " + args);
		}
	
		public static void main(String[] args) {
			Phone p = new Phone();
			p.dialNumber("632444888");
			p.answerCall();
		}
	}


Interfaces are not meant to be instantiated, they are meant for type extensions (inheritance). To use interfaces, they must be *implemented* by a class. The code sample of listing 4.7 shows a Phone class inheriting the type *IPhone* using the *implements* keyword. 

### Inheriting from an interface binds you to a contract

When you *implement* an interface, you are entering into a contract, that you will *implement* whatever methods you have inherited. Implementing a method means that you will provide the details of the function---you will supply the function body. 

At first glance, it looks like more work for the programmer because you are duplicating code. First you will write the interface but the methods doesn't have details, then you will implement in a class then supply the details of the method. This argument maybe true for trivial applications ^[I would define a trivial application as something that you don't intend to maintain or improve in the course of years. A disposable application], but for non-trivial applications, coding against an interface rather than a concrete class is good way to use the Java typing system to achieve maintainability of code. Another reason to use interfaces is when you truly need multiple inheritance. Let us expand the Phone program.



	//MultiFunction.java

	import static java.lang.System.out;

	interface Printer {
		void print();
	}

	interface Phone {
		void answerCall();
		void dialNumber(String args);
	}

	interface Copier {
		void copy();
	}

	class MultiFunction implements Printer, Phone, Copier {
	
		public void print() {
			out.println("Printing");
		}
	
		public void answerCall() {
			out.println("Answering call");
		}
	
		public void dialNumber(String args) {
			out.println("Dialling " + args);
		}
	
		public void copy() {
			out.println("Copying");
		}	
	}

	class TestMultiFunction {

		public static void main(String[] args) {
		
			Printer printer = new MultiFunction();
			Phone phone = new MultiFunction();
			Copier copier = new MultiFunction();
		
			printer.print();
			phone.answerCall();
			copier.copy();
		
			System.out.println(copier.toString());
			copier.print();
		
		}

	}

The Multifunction.java code defines three interfaces, the *Phone*, *Printer* and the *Copier*. The class *MultiFunction* implements all three interfaces. If you think about it, what the code is saying is---MultiFunction *is a* Printer, it *is also a Copier* and a *Phone*. As such, a MultiFunction object should behave as a Phone, a Printer or Copier will behave. That is the object contract between these three interfaces and the class.  

If you review line 39-45 of Listing 4.8, I did not use the MultiFunction type when I created a MultiFunction object. I used the specific interfaces as the Type to be created. 


	Printer printer = new MultiFunction();
	Phone phone = new MultiFunction();
	Copier copier = new MultiFunction();
		
	printer.print();
	phone.answerCall();
	copier.copy();



*MultiFunction printer = new MultiFunction()* would have been fine, the code will still compile and run perfectly, so why didn't I do that? Because I only need a *Printer*, I chose a more general type because I am not sure that I will not change the implementation details of the *print()* method in the future. 

It can be argued that if I need to change some details of the print() function, I should just go inside the MultiFunction class and change it, but I would rather not do that for a host of reasons. The most important one being that at some point, some of my codes maybe depending on how I actually implemented the print function inside the MultiFunction class, and if I change that, some parts of the application could break. On the other hand, using the *Printer* interface as a type allows me to achieve loose coupling between the Type and its actual implementation. If I need to change some of the details of print() function, I could simply create another class that implements the *Printer* type and make that adjustments on the new class. This approach has some level of encapsulation because I am containing the possible (negative) impact of code change. 

	//If I need to change something on the print function()
	class ColorPrinter implements Printer {
		public void print() {
			...
		}
	}

	Printer printer = new ColorPrinter();


The above code shows a possible approach if I really need to make adjustments to the print() function in the future. 

### Looking closely into MultiFunction

All Java objects will have at least one type, but usually it has more than one. The MultiFunction object we have created actually has five. It is a *Copier, Printer, Phone, MultiFunction* and a *java.lang.Object*. The Copier, Printer and Phone types are easy to see, they were explicitly implemented by MultiFunction, so that's three. The fourth one (MultiFunction) is not very obvious, but whenever you create a new class, you are creating a new Type---hence, whatever object you will create out of that class will also bear its type. The fifth one (java.lang.Object) is because no matter what you do, at some point, your class will extend the Object class, either directly or indirectly. 

<img src="/img/object-type.png">



### Polymorphism

You will notice that the MultiFunction object needed to re-define all the methods it has inherited from the three interfaces. We had to re-define *print(), copy, answerCall() and dialNumber()*. Re-defining a method in a subtype is called *method overriding*. 

Overriding a method is done in order for the inheriting class to have a chance to define a unique behavior for the method. For example, the MultiFunction object inherited the *copy()* from the *Copier* interface. What it effectively means is that MultiFunction is making a promise that because it is now a *Copier* object, it will respond to the *copy()* message if invoked. The Copier interface did not specify any behavior for the method, it is up to the implementing class (MultiFunction) to provide the behavior. The provision of behavior for an inherited method can be done using method overriding.  

\lstinputlisting [caption=Shape example]
{source/04-OOP/Shape.java}

	//Shape.java
	interface Shape {
		void draw();
	}

	class Square implements Shape {
		public void draw() {
			System.out.println("Drawing a square");
		}
	}

	class Circle implements Shape {
		public void draw() {
			System.out.println("Drawing a circle");
		}
	}

	class TestShape {

		public static void main(String[] args) {
			Shape square = new Square();
			Shape circle = new Circle();
			square.draw();
			circle.draw();
		}
	}


The Shape program is a very trivial and non-realistic example, but the simplicity should aid our understanding of why we use overriding. 

The *Shape* type could have been written as a class. The *Square* and *Circle* classes could have **extended** a Shape class instead of implemented a Shape interface---why didn't we do that? Because:

1. Shape is not a real object (even in the real world). Shape is a name we give to describe the contour of something, the state of something---it is not **something**. Just like **Animal** is the classification we give to cats and dogs. A cat is a real thing, a dog is a real thing, an animal is not---Animal is a *Type*
2. If you think about it hard enough, can *Shape* really draw something, will it make sense?
3. It makes sense that Circle and Square descend from a common type, after all Circle and Square are---Shapes

The *draw()* method are both available in Circle and Square, but they have different implementations or behavior (method body). This was possible because we have overriden the draw() method where it makes sense. It makes the \code{draw()} method polymorphic, it changes its behavior depending on which object you are calling it against. 


<span class="stress">Bibliography</span><p>

1. Ivar Jacobson, Rumbaugh, Object Oriented Analysis and Design. 3rd ed, Ad- dison Wesley 1965

2. James Gosling, The Java Programming Language. 3rd ed, 1999.



 












