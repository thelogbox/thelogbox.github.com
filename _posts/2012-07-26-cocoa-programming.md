---
layout: mac

title: Programming for the Mac

description: If you want to build iOS apps, you must know Objective C first

except:

tags:
- Cocoa
- Fundamentals

---



<div id="update-history">
<h3>Doc History</h3>
<br/>
26.Jul.2012 &mdash; started/created<br/>
18.Nov.2012 &mdash; published
<br/>
</div>


<div id="minitoc">
<h2>Contents</h2>

<h4>Objective C</h4>

1. Compilation
2. Data types
3. Classes
4. Getting and Setting values
5. Properties
6. Object Construction
7. Instance members
8. Protocols


</div>

# Required reading 

Allocate time for this, there is no way around the required reading. You won't learn objc (properly) by simply looking at videos on youtube or some other video tutorials. The mind needs to absorb the concepts, techniques and idioms of Objective C, it needs to be read and practiced deliberately.

1. [The Objective C Languge](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/ObjectiveC/Introduction/introObjectiveC.html) - Mac Developer Library
2. [Programming with Objective C](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/ProgrammingWithObjectiveC/Introduction/Introduction.html) - Mac Developer Library
3. [Cocoa Fundamentals Guide](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CocoaFundamentals/Introduction/Introduction.html#//apple_ref/doc/uid/TP40002974) - Mac Developer Library
4. [Cocoa Core Competencies](https://developer.apple.com/library/mac/#documentation/General/Conceptual/DevPedia-CocoaCore/AccessorMethod.html) - Mac Developer Library
5. [Cocoa Tips & Tricks](https://developer.apple.com/library/mac/#samplecode/CocoaTipsAndTricks/Introduction/Intro.html) - Mac Developer Library
6. [Coding Guidelines for Cocoa](http://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingBasics.html#//apple_ref/doc/uid/20001281-1002242-BBCIJGDB) - Mac Developer Library


## Other materials 

1. Programming in Objective C, by Stephen Kochan, Addison Wesley, 2012
2. Objective C Phrasebook


# Infrastructure

Objective C requires XCode, get it from the AppStore&mdash; On the Pref pane, download the *command line tools*. Practicing on Objective C sources can also be done on Linux/UNIX using GNUStep, but if you intend to build and release IOS or Mac apps, you will really need a Mac. 

# Readiness

Programming experience in C is beneficial. If you don't know C yet, It's probably not a good idea to pick up C now, then go to Objective C&mdash;just to straight to Objective C and try pick up along the way the parts of C that you need. Learning a procedural language like C, then moving to an object oriented language like Objective C is probably a less than ideal route. 



# Objective C core competencies 

*Objective C* is a superset of C, all valid *C* codes are valid in Objective C. Test your environment. 

{% highlight objective-c%}

#import <stdio.h>
#import <stdlib.h>

int main() {
	
	printf("Hello World\n");
	return EXIT_SUCCESS;

}

// compile:
// 	gcc Hello.c
// output
//	a.out

{% endhighlight %}

Environment testing with *Foundation Framework* 

{% highlight objective-c%}

#import <Foundation/Foundation.h>
#import <stdlib.h>

int main (int argc, const char* argv[]) {
	
	NSLog (@ "Hello World\n");
	return EXIT_SUCCESS;

}

// compile:
//	gcc -framework Foundation Hello.m -o Hello.out

{% endhighlight %}

You need to tell gcc that you will use the Foundation framework using the -framework flag, lest the Foundation headers won't be resolved by the compiler.

*NSLog* is a Foundation framework function, the arguments to this function are sent out to stdout. You need to pass an *NSString* object to this function (NSString strings are not the same as C-style strings)

The next set of codes is a simple Cocoa test

{% highlight objective-c %}

#import <Foundation/Foundation.h>
#import <Appkit/Appkit.h>


int main() {

	NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];
	[NSApplication sharedApplication];

	NSRunAlertPanel(@ "One", @ "Two", @ "Three", nil, nil);

	[pool drain];
}

// compile:
//	clang -framework Cocoa Hello.m

{% endhighlight %}

You can use *clang* in place of *gcc*, it is another front end to LLVM (Low Level Virtual Machine) which Objective C uses. The AppKit was *#include*(d) because of the use of  NSRunAlertPanel.

NSAutoReleasePool provides a managed environment for your codes (A garbage collected environment). Remember to *drain* the pool once you are done, lest you will leak memory.


# Data Types 

The usual primitives of C (int, float, char) are, of course usable, as well the qualifiers *long, long long, short, unsigned and signed*.

There is another type in Objective C called **id**, but its discussion is deferred to later sections.

{% highlight objective-c %}

#import <Foundation/Foundation.h>

int main() {

	NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];

	int a = 100;
	float b = 100.00;
	double c = 100e+2;
	char d = 'g';
	BOOL e = true;

	NSLog(@ "Integer a = %i" , a);
	NSLog(@ "Float b = %f" , b);
	NSLog(@ "Double c = %e" , c);
	NSLog(@ "Double c = %g" , c);
	NSLog(@ "Char d = %c" , d);
	NSLog(@ "BOOL e = %d" , e);

	[pool drain];

	return 0;
}

{% endhighlight %}

**NSLog** takes format specifiers like fprintf. The reference page for [String format specifiers are here](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/Strings/Articles/formatSpecifiers.html)

You can use **c99** bool instead of BOOL. You need to keep in mind though that Cocoa and the other Frameworks uses BOOL instead of bool&mdash;peeking into Foundation/objc.h, you can find the definition of BOOL.

{% highlight objective-c %}

typedef signed char     BOOL; 
// BOOL is explicitly signed so @encode(BOOL) == "c" rather than "C" 
// even if -funsigned-char is used.
#define OBJC_BOOL_DEFINED


#define YES             (BOOL)1
#define NO              (BOOL)0

{% endhighlight %}

Be prudent, use BOOL to future proof your code a little bit, in case Apple decides to change the implementation (not likely, but who knows).

# Classes 

To create classes, you need to declare an *interface* and an *implementation*. They don't need to be in the same source file but it is a good idea to keep them separate&mdash;the reason should be faily obvious to you already if Objective C is not your first OOP language.

### A Person class example 


{% highlight objective-c%}

// filename: Person.h

#import <Foundation/Foundation.h>

@interface Person: NSObject {

	int theint;

}

- (int) 	getInt;
- (void) 	setInt: (int) var;
- (void) 	foo; 

@end

// filename: Person.m

#import <Foundation/Foundation.h>
#import "Person.h"

@implementation Person

- (int) getInt {
	return theint;
}

- (void) setInt: (int) var {
	theint = var;
}

- (void) foo {
	NSLog(@ "Word");
}

@end

{% endhighlight %}

The *@interface* section declares member variables and member methods. The member method only contains the method signature (return type, method name and argument).

The colon signifies that the Person class is inheriting from *NSObject*. The area i between the opening and closing curly brace is where you can write member variable declarations.

Member methods (getInt, setInt and foo) are written enclosed in the @interface and @end declarations. The minus sign means that the method belongs to the instance rather than the class. If the method is preceded by a plus sign, it means the method belongs to the Class rather than its instance. The return type of the method can be any valid type in Objective C (classes, primitives or id), it is written by enclosing the return type in parens.


The *@implementation* section details the method implementation. 

You cannot compile the code yet, it will complain because an entry point to the program has not been defined. You need to define a *main()* function to test this code. The main() function can be in a different implementation source file, but it is not a requirement.

{% highlight objective-c %}

// filename: Person.m

#import <Foundation/Foundation.h>
#import "Person.h"

@implementation Person

- (int) getInt {
	return theint;
}

- (void) setInt: (int) var {
	theint = var;
}

- (void) foo {
	NSLog(@ "Word");
}

@end

/////////////////////////////////////////////////////

int main() {

	// Setup a garbage collected pool
	NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];

	Person * person = [[Person alloc] init];
	[person setInt: 100];
	int x = [person getInt];

	printf("%d \n", x );
	// To do the printf in NSLog
	NSLog(@"Value of getInt = %i ", x);

	[person foo];
	[pool drain];

}

// compile:
//	clang -framework Foundation Person.m 

{% endhighlight %}

The person object could have been created using the *new* message [Person new] &mdash;  **new** is not a keyword in Objective C, it is a method of the NSObject which actually calls allo, then init. The Person class in the example is inheriting from NSObject, which means it has everything that NSObject has, including the  *new* method.

Sending a message (calling a method) to an object is semantically different from the way Java, C# or C++ does it. A message send is done by enclosing the object reference and the message (method) in square braces. Read some history of the Objective C language if you want to gain insight why message sending is done like this in ObjC rather than using the dot notation. 

According to Tom Love (one of the designers of Objective C), the square bracket syntax is sign post that you are leaving C land and now entering object land. 

The dot operator is used in C to access structures or union members. Object oriented programming is a departure from C, hence the bracket notation to highlight the use of a new semantic.

## Getting and setting values 

Getting and setting values of member vars of an object is a very common programming practice, it is a necessary technique in creating value objects.

{% highlight objective-c %}

// filename: Person.h

#import <Foundation/Foundation.h>


@interface Person : NSObject {

	NSString * name;
	NSString * email;

}

- (void) setName: (NSString *)  var;
- (void) setEmail: (NSString *)  var;
- (NSString *) getEmail;
- (NSString *) getName;

@end

// filename: Person.m

#import <Foundation/Foundation.h>
#import "Person.h"

@implementation Person

- (void) setName: (NSString *) var {
	name = var;
}

- (void) setEmail: (NSString *) var {
	email = var;
}

- (NSString *) getName {
	return name;
}

- (NSString *) getEmail {
	return email;
}

@end

/////////////////////////////////////////////

int main() {

	NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];
	Person * person = [[Person alloc] init];

	[person setName: @ "Ted"];
	[person setEmail: @ "tedhagos@gmail.com"];

	NSLog(@ "%@", [person getEmail]);
	NSLog(@ "%@", [person getName]);

	[pool drain];

}

// compile: clang -framework Foundation Person.m

{% endhighlight %}


# Properties

You do not need to write individual getters and setters methods for member vars. Objective C as the @property and @synthesize to do that automatically

{% highlight objective-c %}

// filename: Prop.h

#import <Foundation/Foundation.h>

@interface Prop : NSObject {
	int one;
	int two;
}

@property  int one, two;

- (void) printem;
- (void) divideem;
- (void) multiplyem;
- (void) addem;

@end

// filename Prop.m

#import <Foundation/Foundation.h>
#import "Prop.h"

@implementation Prop

@synthesize one, two;

- (void) printem {
	NSLog(@ "One is %i and Two is %i", one, two);
}

- (void) divideem {
	NSLog(@ "%i / %i = %f ", one, two, one/(float)two);
}

- (void) multiplyem {
	NSLog(@ "%i * %i = %i ", one, two, one * two);
}

- (void) addem {
	NSLog(@ "%i + %i = %i ", one, two, one +  two);
}

@end

/////////////////////////////////////////////////


int main() {

	NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];
	Prop * prop = [[Prop alloc] init];
	[prop setOne: 1];
	[prop setTwo: 2];

	[prop divideem];
	[prop addem];
	[prop printem];
	[prop multiplyem];

	[pool drain];

}

{% endhighlight %}

@property is declared on the interface declaration and @synthesize on the implementation portion. In the example code above, the member vars *one & two* were synthesized. Accessor methods were automatically generated for these vars. 

The accessor method which was generated for our member vars one & two are the following;

{% highlight objective-c %}

/*

The acccessor to get the member var is exactly the same name as
the member var.

In Objective C 2.0, the dot notation was allowed to access properties of 
an object, hence we could have written prop.one instead of [prop one]. Note 
though that you are not resolving the name of member val literally (Java and
C# programmers, take note), you are in fact sending a -one or -two message 
to the object named prop. It is not a direct access to the value of the member
vars

*/

[prop one];
[prop two];

/*

To set the value of the member var the general the convention is to 
	1. Capitalize the first letter of the member var
	2. prepend the word "set" to the upper-cased member var

*/


[prop setOne: <value>];
[prop setTwo: <value>];


{% endhighlight %}

# Constructors

This heading is misleading, there is concept of a constructor in Objective C, at least not in the way that I think about constructors in Java, C++ or C#. 

On the other hand, each object, before they are created, are sent the messages *alloc* then *init*. It's probably not a good idea to fool around with *alloc* but it is a very common practice to override *init* and perform initialization codes. 

{% highlight objective-c %}

filename: Obj.h

#import <Foundation/Foundation.h>

@interface Obj : NSObject {

	NSString * objname;

}

@property (nonatomic, retain) NSString * objname;

+ (void) foo;
- (void) goo;

@end

// filename: Obj.m

#import <Foundation/Foundation.h>
#import "Obj.h"


@implementation Obj 
@synthesize objname;

- (id) init {

	self = [super init];

	if (self) {
		NSLog(@"In the CTOR of Obj");
	}

	return self;
}

+ (void) foo {

	// NSLog(@ "Class method foo printing %@ ", objname);
	// Cannot do this, Class methods cannot access instance
	// members
	
	NSLog(@"Class method foo");

}

- (void) goo {
	NSLog(@ "Instance method goo printing %@", objname);
}

@end


///////////////////////////////////

int main() {

	NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];

	Obj * obj = [[[Obj alloc] init] autorelease];
	[obj setObjname: @"The object name"];
	NSLog( @ "%@", [obj objname]);

	[Obj foo];
	[obj goo];

	[pool drain];

}

{% endhighlight %}

The **self** is conceptually equivalent to **this** in Java, it is a reference to one's instance. In our example, self was assigned the value returned by a call to the *init* of its parent object. It is a good idea to call the superclass' init to ensure that proper initialization is also happenning up the object graph.

## Another example of self

A simple use of the *self* keyword. The following code is an adaptation of the Leaf.java source by Bruce Eckel, it was used as an example demonsrating the use of the *this* keyword. The [Java source can be found here](http://www.cs.hut.fi/Docs/Eckel/TIJ3ed/code/c04/Leaf.java).


{% highlight objective-c %}

#import <Foundation/Foundation.h>

@interface Leaf : NSObject{}

-(id) getLeaf;
-(void) printStats;
@end


@implementation Leaf

static int instance_counter;
static int leaf_counter;

-(id) init {
	[super init];
	instance_counter++;
	return self;
}

-(id) getLeaf {
	leaf_counter++;
	return self;
}

-(void) printStats {
	NSLog(@ "instance counter : %i" , instance_counter);
	NSLog(@ "leaf counter : %i" , leaf_counter);
}

@end

////////////////////////////////////////////////////

int main() {

	NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];

	Leaf * leaf = [[[Leaf alloc] init] autorelease];
	[[[leaf getLeaf] getLeaf] printStats]; 

	[pool drain];
}

{% endhighlight %}

# Instance members and class members 

Again, the heading is misleading because there is no such thing as a class member in Objective C, I am simply using it as my own mnemonic (mental cheatsheet) to remember how to declare vars that are global to all instances. 

Vars that are declared within @interface are unique to each instance (object), while vars declared within @implementation is global to all instance &mdash; hence, equivalent of static members in Java. There is a keyword *static* in Objective C but it refers to a storage class, it is not semantically equivalent to the *static* keyword in Java or C#. 

{% highlight objective-c %}

// filename: instancecount.m

#import <Foundation/Foundation.h>

@interface InstanceCount : NSObject {

	// You cannot declare a static type here, only in the
	// implementation source. Otherwise you will get the error
	// error: typename does allow storage class to be specified

	// Besides, the static keyword in ObjC does not have the
	// same semantic meaning as the one in Java or C#

	// A static variable in ObjC refers to a storage class, it is
	// a variable that does not lose its value even after the
	// block that defined it goes out of scope

	int counterInterface;

}
@end


@implementation InstanceCount

int counterImplementation;

- (id) init {

	self = [super init];
	
	NSLog(@ "counterInterface = %i", ++counterInterface);
	NSLog(@ "counterImplementation = %i", ++counterImplementation);
	return self;
}

- (void) foo {
	//But you cannot access it here if you declared counter to be a 
	//a local variable inside the constructor.
	NSLog(@ "Foo: counterInterface = %i", counterInterface);
	NSLog(@ "Foo: counterImplementation = %i", counterImplementation);
}

@end

////////////////////////////////////////////

int main() {

	NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];

	@autoreleasepool {

		InstanceCount * obj1 = [[InstanceCount alloc] init];
		InstanceCount * obj2 = [[InstanceCount alloc] init];
		InstanceCount * obj3 = [[InstanceCount alloc] init];
		InstanceCount * obj4 = [[InstanceCount alloc] init];
		InstanceCount * obj5 = [[InstanceCount alloc] init];
		InstanceCount * obj6 = [[InstanceCount alloc] init];

		[obj6 foo];
	
	}
}

// compile:
// 	clang -framework Foundation instancecount.m

/* OUTPUT

2012-11-18 22:52:30.332 a.out[6614:707] counterInterface = 1
2012-11-18 22:52:30.333 a.out[6614:707] counterImplementation = 1
2012-11-18 22:52:30.334 a.out[6614:707] counterInterface = 1
2012-11-18 22:52:30.334 a.out[6614:707] counterImplementation = 2
2012-11-18 22:52:30.335 a.out[6614:707] counterInterface = 1
2012-11-18 22:52:30.335 a.out[6614:707] counterImplementation = 3
2012-11-18 22:52:30.335 a.out[6614:707] counterInterface = 1
2012-11-18 22:52:30.336 a.out[6614:707] counterImplementation = 4
2012-11-18 22:52:30.336 a.out[6614:707] counterInterface = 1
2012-11-18 22:52:30.337 a.out[6614:707] counterImplementation = 5
2012-11-18 22:52:30.337 a.out[6614:707] counterInterface = 1
2012-11-18 22:52:30.338 a.out[6614:707] counterImplementation = 6
2012-11-18 22:52:30.338 a.out[6614:707] Foo: counterInterface = 1
2012-11-18 22:52:30.339 a.out[6614:707] Foo: counterImplementation = 6

*/

{% endhighlight %}

Another example 


{% highlight objective-c %}

// filename: instance.m

#import <Foundation/Foundation.h>

@interface Obj : NSObject {
	NSString * color;
}
@property (nonatomic, retain) NSString * color;
@end

@implementation Obj
@synthesize color;

NSString * shape;

- (id) init {
	[super init];

	color = @ "Black";
	shape = @ "No shape";

	return self;
}

-(NSString *) getShape {
	return shape;
}

- (void) setShape: (NSString *) var {
	shape = var;
}

@end

/////////////////////////////////

int main() {

	NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];

	Obj * one = [[[Obj alloc] init] autorelease];
	Obj * two = [[[Obj alloc] init] autorelease];

	NSLog(@ "One color = %@", [one color]);
	NSLog(@ "Two color = %@", [two color]);
	NSLog(@ "One shape = %@", [one getShape]);
	NSLog(@ "Two shape = %@", [two getShape]);

	[two setColor: @"Red"];
	[two setShape: @"Circle"];

	NSLog(@ "One color = %@", [one color]);
	NSLog(@ "Two color = %@", [two color]);
	NSLog(@ "One shape = %@", [one getShape]);
	NSLog(@ "Two shape = %@", [two getShape]);

	[pool drain];

	return 0;

}

// compile:
//	instance.m

/* OUTPUT

2012-11-18 23:05:24.540 a.out[6662:707] One color = Black
2012-11-18 23:05:24.542 a.out[6662:707] Two color = Black
2012-11-18 23:05:24.542 a.out[6662:707] One shape = No shape
2012-11-18 23:05:24.542 a.out[6662:707] Two shape = No shape
2012-11-18 23:05:24.543 a.out[6662:707] One color = Black
2012-11-18 23:05:24.543 a.out[6662:707] Two color = Red
2012-11-18 23:05:24.543 a.out[6662:707] One shape = Circle
2012-11-18 23:05:24.544 a.out[6662:707] Two shape = Circle

*/

{% endhighlight %}

Changing the value of the *color* member var in object two affected only the color value of object two, it did not have any effect on the color value of object one because the color member var was defined within the @interface. Each instance have their own copy of the color variable.

Changing the value of the *shape* member var in object two actually affected the shape value in object one as well. The *shape* variable is global to all instances because it was defined within the @implementation declaration, it is a shared copy amongst all instances of *class Obj*.

# Protocols

A Protocol is just a list of methods that do not have implementation. In Java or C# programming, they might resemble the concept of an *interface* because when class includes a protocol declaration, the class has to implement the methods in the protocol. 

One thing to note though is that a protocol is not a type. You may not declare an object having the name of a protocol as a type &,dash; you may however declare that an instance of an object *is conforming* to a specific protocol. 

{% highlight objective-c %}

// filename: poly.m

#import <Foundation/Foundation.h>

@protocol Printing
-(void) print;
-(void) clean;
@end

@protocol Faxing
-(void) print;
-(void) fax;
@end

@interface Multi : NSObject <Printing, Faxing> {

}
@end

@implementation Multi

-(void) print {

}
-(void) fax {

}

-(void) clean {

}

@end

/////////////////////////////////////////////////

int main() {

	NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];

	Multi * multi = [[[Multi alloc] init ] autorelease];
	[multi print];
	[multi fax];

	/*
	
		Here, we declare the what variable as type id, but that it
		needs to conform the Printing protocol. Well, the actual object
		is a Multi type, which of course conforms to the protocol Printing
		among other things.

	*/

	id <Printing> what = [[[Multi alloc] init] autorelease];
	[what print];

	[pool drain];
	return 0;

}

// compile:
// 	clang -framework Foundation poly.m

{% endhighlight %}

A class may declare that it conforms to more than one protocol. Protocol conformance in a class is denoted by enclosing the protocol names inside the angle brackets as part of the @interface declaration.


# Cocoa Core competencies 

[tbd]

# References



