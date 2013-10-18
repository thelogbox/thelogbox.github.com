---
layout: androidtutorial

title: How Much Java Do you need for Android Development

description: 

excerpt: 

categories:
- android-programming


---



If you want to build **native** applications in Android, you've got to know Java---there's no way around it. Yes, there are tools like PhoneGap, Titanium etc. but you will eventually hit limitations and ceilings if you choose to code on non-native development platform. So learn Java, it's not that bad. 


1. Set up the development environment
2. Get some tools
3. Learn to construct the simplest program
4. Learn the keywords
5. Dig some OOP, actually dig a lot of OOP
6. Learn how Java treats value types and reference types
7. Learn how to write methods and what access control means
8. Discover how GC works
9. Learn the data types
10. Exercise on some operators
11. Dig the control structures, so you can learn block level practices
12. Learn how Java does Exception handling
13. Some tinsy bitsy java.lang.Util
14. Some tinsy bitsy I/O
15. Learn parameter passing
16. Now, the Thread
17. Do the simplest UI in java.swing
18. Do the simplest event handling (actionListeners)
19. Learn how to use inner classes
20. Do some basic CRUD (Create, Read, Update, Delete) using SQLite
21. Dig (but not too deep) some sockets
22. Exercise on some httpClient programs
23. Get some XML
24. Learn ANT a little bit 


# 1. Set up the environment

Whether you are working on Windows, Linux or OSX, the downloads can be found at [Oracle Technet site](http://www.oracle.com/technetwork/java/javase/downloads/index.html). Choose just the JSE without the bundles, to keep it simple. 

OSX (Lion and Mountain Lion) actually has a simpler way of downloading. Open a Terminal.app, then type *java* on the command line. OSX wizards will kick in and ask you to download the JDK. Just say **yes** to prompt and Java installation will kick in. 

If you are using Windows, you will download the JDK (Java Development Kit), get the latest stable release. Be careful that you are downloading the JDK and not the JRE (Java Runtime Environment) only, you need the JDK to create Java apps. 

Install what you downloaded, it will guide you through the installation process. The questions are straight forward so they don't need to be expounded here. 

## Set up the PATH and CLASSPATH variable

**NOTE for OSX Users** - do absolutely nothing, the CLASSPATH AND PATH variable are already setup for you

On Windows;

1. Open the *System* window via the *Control Panel*, go to *Advanced*, then *Environment variables*
2. Create a variable named *JAVA_HOME*, the value is where the JDK is installed, if you said yes to the defaults of the installation, it must have been in *c:\Program Files\java\jdk1.7xxxxxx*.
3. Edit the PATH variable (on the same window). There is an edit button for the PATH variable. 
4. Append this entry to the PATH variable - **;%JAVA_HOME\bin;.%**. The semicolons and the dot are pretty important, so type this slow. If you forget to put these in, you will encounter *Bad command or file name* kinds of errors later when you execute java and javac
5. Create another variable names *CLASSPATH*, put the value **%JAVA_HOME\jre\lib\rt.jar;.%** -- again, don't forget the semi colon and the dot at the end


# 2. Get some tools

Get Apache Ant and a decent program editor. Yes you can use notepad, you can use vi, even nano---that is really up to you. I won't even prescribe an editor at this point, this is the subject of a really intense, almost-religious but quite pointless debate. Just keep coding and try out a couple of editors. Don't get cheap, not because it's free it is the best. I like opensource, I love opensource, but it doesn't mean I will always use it. Choose the best tools for the job, even if it costs money. 

With that disclaimer out of the way, I do use the following editors; Vi and TextMate (if you are on the Windows platform, the e-TextEditor is fine too)


# 3. Learn how to write the simplest programs 

Do the *Hello World* program. It's mundane, boring and dry but its the simplest program. You need to know how to write the simplest programs before you can try out the more complex ones. This is a larger discussion, [so I wrote it here](/java-beginning-to-program/)

# 4. Learn the keywords of Java 

There are a couple of things you will name in Java---meaning, you will think of the name and declare it in your code. These are names of **classes, variables, methods, interfaces, parameters passed to methods and packages**. Collectively, these are known as Java identifiers. 

## Rules to remember when creating identifiers

1. You can use alphanumeric characters, but the first letter can't be a number
2. You can't use special characters, but you can use the dollar sign and underscore
3. You can't use a Java keyword (also known as reserved word). You also can't use a Java literals like **true, false or null**


**The Java keywords**

~~~
for while do throw
case try catch return 

goto [not used]

break continue

byte short int long float double boolean char

if switch throws else

finally class interface implements extends static new this super

public private protected package default

native transient synchronized import instanceof volatile 
void abstract final assert enum strictfp 

const[not used]
~~~




# 5. Dig some OOP, dig a lot of it

OOP is short for Object Oriented Programming. Java is an object oriented language. Sure you can write all of your codes inside public static void main, but that will not take you far in Android when you encounter stuff like **class MySplashPad extends Activity**.

OOP is so entrenched in Java---in fact, I think a little bit too entrenched that some developers I know get over excited about creating objects, so they create a gazillion of it. Anyway, I hope you learn temperance about creating objects in your own coding journey, but the point remains, [you need to know OOP. Read more here ...](/java-object-oriented-programming/)




6. Learn how Java treats value types and reference types
7. Discover how GC works
8. Learn the data types
9. Exercise on some operators



# 10. Dig the control structures, so you can learn block level practices

Your ability to direct and command the flow of control in your program is one of the defining skills for a programmer. There are basically 3 ways that you can arrange the commands in your program code. They are;

- You can execute commands one after another -- **sequencing**
- You can execute certain commands when certain conditions are met -- **branching**
- You can keep on repeating certain commands while certain conditions are still true -- **looping or iteration**. [Continue reading about control structures ...](/java-controlling-program-flow/)


11. Learn how Java does Exception handling
12. Some tinsy bitsy java.lang.Util
13. Some tinsy bitsy I/O
14. Learn parameter passing
15. Now, the Thread
16. Do the simplest UI in java.swing
17. Do the simplest event handling (actionListeners)
18. Learn how to use inner classes
19. Do some basic CRUD (Create, Read, Update, Delete) using SQLite
20. Dig (but not too deep) some sockets
21. Exercise on some httpClient programs
22. Get some XML
23. Learn ANT a little bit 





