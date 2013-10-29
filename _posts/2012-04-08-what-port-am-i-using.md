---
layout: post

title: What Appication is Using Port 80

description: When IIS or Apache won't start, another is app is using port 80. Find out

excerpt: 

tags:
- network
- admin

categories:
- Windows

---


After installing WAMP (Windows Apache MySQL PHP) or Apache only, the service cannot start properly because some (other) application is using it. The errors you might get could be *Address already in use..*, *Bind Exception ..*, *Port 80 already in use..* etc. 

Apache needs port 80 to be free, unused that is in order to start properly. If in case, you have another application that is using port 80, this becomes a problem for Apache. 

# FIND THE APP BOUND TO PORT 80

Get to the command line, *cmd.exe* and run the *netstat* program. Netstat is built in to Windows, no need to download it.

<pre class="codeblock">

c:\>netstat -aon | findstr 0.0:80

</pre>

The first part of the command will list all active connections and their ports. The *-o* flag is important because it will tell you the process IDs of the applications running. The *-n* flag is to display the port numbers numerically (which is what we need).

The nestat command will list all of the currently running applications, which could be a lot. That is why we need to filter the results to limit the list to only the applications we are interested in. Only those application(s) that is running on port 80. That is the purpose of the second part of the command. 

# FIND THE APPLICATION'S NAME

Now we have the PID (Process ID) of the application currently running on port 80, but it doesn't tell us the name of the application, it only tells us the Process ID. 

<pre class="codeblock">

*TCP0.0.0.0:80 0.0.0.0:0 LISTENING 560*

</pre>

The line above is an example of what you could get after running the netstat command, **560** is the process id of the application currently bound on port 80.  

To find out who is application 560, type the command <code class="codeblock">tasklist | findstr 560</code>. After that command, it should give you the name of the application whose ID is **560** which is currently using port 80.  

If you need to free up port 80 so that Apache can run, you can kill the Skype application by using the *Process Manager* (CTRL-ALT-DEL), then find the app and kill it. You can also terminate a process on the command line using <code class="codeblock">taskkill /F /PID 560*</code>




