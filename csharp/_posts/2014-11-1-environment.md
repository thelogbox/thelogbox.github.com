---
layout: csharp

title: Environment

description: 

excerpt: 

author: Ted Hagos

lastupdate: 


tags:


categories:

---


The .NET framework includes a large collection of libraries and a runtime environment. The FCL or Framework Class Library consist of a large class library allows us a developer to do lots of things like create a Windows Desktop application, build a web page, write a custom control. The library also allows a program written in a language other than C# to be used from within a C# program and vice versa. This language interoperability if part of the FCL.

.NET programs are meant to run on a virtual machine called the CLR which is short Common Language Runtime. The virtual machine runtime provides some services that the operating system cannot provide e.g. garbage collection. 

A short list of things included in the .NET framework is found below

-   Common Language Runtime (CLR)
-   The .Net Framework Class Library
-   Common Language Specification
-   Common Type System
-   Metadata and Assemblies
-   Windows Forms
-   ASP.Net and ASP.Net AJAX
-   ADO.Net
-   Windows Workflow Foundation (WF)
-   Windows Presentation Foundation
-   Windows Communication Foundation (WCF)
-   LINQ

# Tools

The best tool for writing C# applications is Visual Studio. You need to pay for it, it is not free. But you can get alternative tools to start developing C# apps. You can download **Express for Web**, **Express for Windows** and **Express for Windows Desktop**. You can read about the detailed descriptions of these tools from the [Visual Studio download page](http://www.visualstudio.com/en-us/products/visual-studio-express-vs.aspx).

## Command Line Tools

If you download any edition of the Visual Studio Express, either for Web, Windows or Windows Desktop, it will already include the .NET framework SD. The SDK contains tools and binaries that will allow you compile C# programs from the command line. Alternatively, the .NET framework SDK can also be downloaded without downloading Visual Studio.  You can download the framework SDK from the [MSDN download site](http://msdn.microsoft.com/en-us/vstudio/aa496123.aspx).

The framework SDK is applicable to Windows users, if you are on Linux or OSX, you can use **mono** which can you download from the [mono project site](http://www.mono-project.com/download/). You will need to install both the mono runtime environment (MRE) and the mono development kit (MDK).
