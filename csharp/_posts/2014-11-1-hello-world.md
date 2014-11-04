---
layout: csharp

title: Hello World

description: 

excerpt: 

author: Ted Hagos

lastupdate: 


tags:


categories:

---


Beginning programmers get their feet wet on a new language by writing the hello world program. It is a useless program because it provides no measurable utility value except that it allows you to learn the flow and the steps of how to write the simplest code.

C# is a simple language but it is not the simplest. Our program will contain some items that may not make sense to you immediately because they require and understanding of other more advanced concepts e.g. classes and namespaces. The complexity cannot be helped even in the simplest program because C# is an object oriented language. You cannot write anything outside a class, even the lowly instruction of printing "Hello World" to the screen.

Create a folder where you will store all your practice source files. Create a file and name it "Hello.cs". Once the file is created, we can type the contents of our program.

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

The C# compiler is accessible via the command line. You may notice however, that simply launching cmd.exe and typing **csc** will yield an error instead of letting us compile our program. 

If the framework SDK has been properly setup, the installer would have created a script named **vcvars32.bat** which contains commands that will include the framework SDK's binaries to the system path. You need launch vcvars32.bat first before attempting any compilation on the command line. The installer would also have created a menu shortcut for vcvars32.bat, find that on the Windows menu and launch it. 

Launching vcvars32 will also launch a cmd terminal window. You will use that window to compile and run our program

{% highlight bash %}
C:\> cd \path\to\your\project\folder
C:\> csc Hello.cs
C:\> Hello.exe 
{% endhighlight %}

## Using mono

On Linux and OSX, if you have installed the mono development kit and mono development runtime, you will use the **mcs** command to compile and the **mono** command to run our program.

{% highlight bash %}
$ cd /path/to/your/project/folder
$ mcs Hello.cs
$ mono Hello.exe
{% endhighlight %}

You cannot simply type "Hello.exe", .NET programs needs a runtime environment to execute, that is why you need to run mono first before you can run Hello.exe. This runtime is called the CLR (Common Language Runtime). I will tackle this subject, but not now.

On a windows machine, you did not need to invoke the .NET runtime, you simply typed Hello.exe and it runs just fine.Why?--because recent versions of Windows actually includes the .NET runtime already, and if it is intelligent enough to invoke the .NET runtime when it needs to. 

# Walk through of the Hello program 

**using System** - The "using" keyword allows you to use the Types defined in the *System* namespace. When .NET was released, it came not only with the languages, it also came with lots of built-in Types that you can use immediately. There will be a discussion of Types way down the road, but for now, just settle for the explanation that if we did not use the System namespace, instead of writing **Console.WriteLine()** we needed to write **System.Console.WriteLine()**.  

**class Hello {}** - CSharp is very object oriented, you cannot write anything meaningful outside of a class construct. Unlike C++, where you can still program in a procedural way and only optionally use the OOP constructs, CSharp forces you to use the class constructs---even for a trivial program like the Hello program; **class** is a keyword (reserved word) which denotes that what follows is a name of class you are trying to define.  The pair of curly braces is the body of the class. You can write lots of things inside the class' body, although for now, we just wrote *main()*.

**public static int Main()** - this is called a method, some people may refer to it as a function, they will be right also but in OO languages, generally functions are referred to as methods--I will tell you why later, but not now. Main() is a very special method, all console applications (like our Hello program) is expected to have the Main() method because this is the entry point of the program. When you invoke the program, the .NET runtime will look for method, and if you did not define it---I mean exactly as it is written in the sample code, nothing will happen when you run your program. So make sure you type it exactly as it appeared in the sample code

**Console.WriteLine()** - Console is a built-in type under the System namespace, it does lots of things and it has lots of methods. One of the method is WriteLine(). What WriteLine does is to send a string data straight to the stdout (standard out, which means your screen). 

**Semi colon** - You will notice that all statements in CSharp are terminated using a semi colon, this is important because the semi colon will tell the compiler that you are finished with a statement. It signals the end of a programming statement pretty much as a period signals the end of a sentence in the English language. 

CSharp is a case-sensitive language, **main()** is not the same as **Main()**, so type carefully.


## Vocabulary

1. **Source code** - sometimes called source file. It is a text file where you write CSharp statements.
2. **High level language** - a computer programming language undertandable by mere mortals, it looks a lot like the English language, but a computer programming language, unlike English does not contain ambiguities. Each statement you write in a programming language has very precise meaning---strive to know them well
3. **Compiler** - a computer program that takes in a source file as an input, processes it (parsing) then translates it to a format understandable by machines (machine code). CSharp comes with **csc** on Windows and **msc** on mono platform (which can run on platforms other than Windows)
4. **Main()** - a special function in CSharp, if you will write console applications, you need to be very acquainted with the format of Main(). Whenever you invoke a compiled .NET CLI (command line interface) program, .NET will always look for **public static int Main()**. This is the entry point of your app
5. **CLR** - The common language runtime is a rich environment which abstracts a lot of what the Operating System can do for your programs. The CLR can open files, network connections, database connections etc. There are things also that a CLR can do for you that the Operating System cannot---the OS cannot do automatic garbage collection for your app, the CLR can; but let's leave the garbage collection for another discussion