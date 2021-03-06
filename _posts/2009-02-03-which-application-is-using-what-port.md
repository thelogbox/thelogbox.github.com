---
layout: post

title: How to Find Out Which App is Using What Port

description: How to hunt down that pesky app hogging port 80

excerpt: 

tags:
- Admin
- Networking

---

**UPDATE (June 3,2009)**

The original article describes the steps to take on how to find applications that are using your port in a Windows machine, using only tools that came with your Windows installation--no third party apps. I am updating the article now to include a third party tool; WinNetstat is a GUI tool for netstat, it's at winnetstat.zapto.org

***


Network-aware applications are a pain in the __ when they are acting up. They are particularly annoying and infuriating when they don't want to start. If you have tried starting Apache or MySQL etc either in stand-alone mode or service mode (daemon mode in UNIX), you'd know what I'm saying.

The first thing to check when network-aware applications won't start, is of course -- their log files, try to see what's preventing them from starting; Almost always, the log file is going to tell you the reason why the app won't start.

Lots of times, I encounter the problem of two applications using exactly the same port number &mdash; just to be clear, that's bad. What the heck is a port number? &mdash; I'd point you to Wikipedia, but it's too geeky and too academe-ish. I'll take a shot of defining what an application port number is instead; I'll segue a bit, then I'll come back to the main point, which is how to hunt an app that's hostaging a port number .. (holding my breath now)


# WHAT IS AN APPLICATION PORT NUMBER

Every application that needs to talk to other applications, needs to have a port number. Every computer can give out port numbers ranging from 0 - 65535, and once a port number is given, it cannot be given to another application (while it is running at least) -- so, one application is to one port number. The reason why application have port numbers is so that, when one application (say Firefox) wants to talk to another application (in another computer, say Apache; a web server), Firefox needs to know that when he sends out a message, it will be received by the intended recipient (Apache), and this can only be done if Firefox knows exactly where Apache is. There are 2 components that make up a unique address of an application -- one is the IP address of the machine where the application is running, and the other component is -- you guessed it, the port number; Collectively these two (IP address and port number) are known as a socket, but that's another story, let's stop here -- What's important to know is that, port numbers are -- well, important; they determine the uniqueness of an application within a machine.
How to hunt down applications via their port numbers

I'm sure there could be a more neat - albeit geekier - way of finding out which app is using which port; but will do it verbosely; easier to follow too.

You will use a command line tool called netstat (network status); netstat is available on Windows, UNIX, and Linux, there are few differences in the parameters though, so I will cover UNIX and Linux separately (in another post that is)

You will also use another command line utility called findstr (short for find string), it's a Windows command line utility which does -- well, find strings. It locates patterns of strings within a stream of other strings. So, it's a handy utility when searching for very specific words (or part of words) within a large text file. If you've ever used the Find function in a word processor, you get the picture already. The UNIX folks have been enjoying this tool for a long time, it's called grep.

Anyway, the basic idea is to use the netstat command so that we can list all the applications that are either accepting or sending network traffic, and we'd like to list their port numbers and their process IDs too. Then, when we find the port number we are looking for, we will list all the running processes and make the match using the process ID -- then we'll know who the culprit is.

Let's say that we are looking for port 80 -- IIS, Apache and other web servers listen in port 80, so when you are having problems starting Apache, this technique will be useful. The command to use is <code class="codeblock">netstat -aon | findstr 0.0:80</code>

*-a* means list all active connections and their ports. -o means include their process IDs. -n means display the port numbers numerically.

The pipe symbol  means, that instead of the result of netstat being displayed on the screen, feed it's result to the findstr process -- we are looking specifically for the line which has 0.0:80 -- you actually don't need findstr, but I don't want to scroll down and hunt down manually which app is using port 80. You might see something like this.

~~~
TCP 0.0.0.0:80 0.0.0.0:0 LISTENING 560
~~~

Now we know that process 560 is using port 80 (that last column right there, is the process ID), you could press CTRL-ALT-DEL now to show the **Process Manager** window, and manually look up which app has the process ID 560. You can also do that on the cmd line using the command **tasklist | findstr 560**

***tasklist*** is another Windows command line utility which shows you a list of all active processes, again I'd feed it to the findstr utility via the pipe operator, and voila -- Skype is the culprit.

Skype actually doesn't have to use port 80, it can use other port numbers, but for some reason it just does. To free up port 80, you need to shutdown Skype and give your webserver a chance to grab port 80, then start Skype all over again so it can choose which port it will bind to.

1. Shutdown skype, either via the GUI; or if you're feeling geeky enough, you can try taskkill /F /PID 560 (this will be different on your system)
2. Start Apache, or IIS or whatever it is that needs to use port 80
3. Then start skype again

if you repeat the procedure of netstat and tasklist, you'll see that skype now happily uses another port number.
