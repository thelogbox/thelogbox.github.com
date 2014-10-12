---
layout: mac

title: Objective C Language Fundamentals

description: If you want to build iOS apps, you must know Objective C first.

excerpt: 

tags:
- Fundamentals

---



# Preparation and setup

1. You need a Mac. You can get by using Linux or even Windows at first because you can get gcc running on it. I don't think though that you are simply trying to learn objective c for the fun of it---face it, you want to go to IOS or Cocoa programming; and for that, you need to get a Mac hardware
2. Get Xcode setup. In OSX Lion (and Mountain Lion), Xcode is available as download from the App Store (it's free). It's a hefty download so prepare to wait for a bit
3. Once the download is over, open Xcode and go to *Preferences*, go to *Downloads* section. Click *Install* button next to the **Command line** tools. Yes you can use the Xcode GUI to create Objective C CLI apps, but try to learn the CLI way of compiling Objective C codes---this will pay off later; How? It forces your brain to work harder when you are doing things harder---which is what you need when you are learning an unfamiliar language for the first time

# Baby steps

Learn how to write the simplest code in Objective. The purpose of this exercise is not to gobble up a lot of chunks of Objective C, in fact, you won't do anything remotely object oriented. The point of the exercise is to write the simplest code, compile and run it. Objective C is, after all, still C---so in the tradition of K & R's *The C Programming language*, we will do the **Hello World** example.

Create a file named *Hello.m*---why *.m* extension, because the convention for file name extensions is:

- *.c* - C language source file
- *.cc, .cpp* -  C++ language source file
- *.h* - Header file
- *.m* - Objective-C source file
- *.mm* - Objective-C++ source file
- *.pl* - Perl source file
- *.o* - Object (compiled) file

It actually doesn't much matter if you wanted to use any extension you want, the compiler will happily compile it for you. However, it sure is easier to tell what kind of code a file contains if you just follow the convention---easier for others to read your code and easier for you (when you are looking at your code months after you first created it)

Type the contents of the following code

{% highlight objective-c %}

#import <Foundation/Foundation.h>

int main (int argc, const char* argv[]) {
	
	NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];
	NSLog (@ "Hello World\n");
	
	[pool drain];
	return 0;
}

{% endhighlight %}

Compiling this code requires the *gcc* toolchain. If you already have set it up using XCode, you can compile the code on the terminal using <code class="codeblock">$ gcc -framework Foundation Hello.m -o Hello</code>

Never mind the *-framework Foundation* directive for now, you will have plenty of time to explore it later. Just mind the *-o* (that is a minus sign and a small letter oh), it means that you would like the output of the compilation to be named *Hello*. You could have gotten by compiling it with <code class="codeblock">$ gcc -framework Foundation Hello.m</code>

That would have been fine, but the *Hello.m* source file will be compiled into a file named *a.out*---this is the default output if you did not use the *-o* flag; by the way, this flag means **output to**

Run the code

<pre class='codeblock'>

	$ Hello
	2012-07-26 23:19:58.900 Hello[2103:707] Hello World

</pre>

That's it. That's the workflow. 

1. Write the code, give it proper extension
2. Compile it using gcc (with the proper -framework flag)
3. Run the code

Provided you did not misspell anything while you are typing, you should not encounter any errors at this point. The compiler will happily die silently after invoking *gcc* if everything is in order, if not, it will scream and spit out really cryptic error messages. 

# References

1. [Apple Developer](https://developer.apple.com/library/mac/#documentation/Cocoa/Reference/Foundation/Classes/NSString_Class/Reference/NSString.html)
2. Programming in Objective C, Stephen G. Kochan














