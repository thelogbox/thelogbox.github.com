---
layout: post

title: What Application is Using Port 80

description: When IIS or Apache won't start, another is app is using port 80. Find out which one

excerpt: 

tags:
- network
- admin

---

This guide shows detailed steps on to find and terminate a specific network related process in Windows 8. The guide is also applicable to Windows 7, Vista or XP users. 

The commands used are usually employed by server administrators. But developers, from time to time, encounter difficult situations related to network processes. It may not be apparent as a network related problem, and that is part of the difficulty.

The most common use of these commands is resolve errors which may manifest themselves as one of the following, but not limited to

1. Address already in use
2. BindException
3. Port 80 already in use

For purposes of illustration and specificity of example, we will take on the following problem:

We are trying to start a web server, it could be Apache, IIS or NGINX, it doesn't matter what. We cannot successfully start the web server for one reason or another. The error message said "Address already in use". 

## 1 Basic concepts

A network aware application, like a web server, need to bind itself to a socket. Think of a socket from the context of a [tin can telephone](http://en.wikipedia.org/wiki/Tin_can_telephone). The two cans are connected via a string which can transmit soundwaves from one endpoint to the other. The socket is one the cans and the network cable is the string. Instead of transmitting soundwaves like the string, we stream data packets from one socket to another. 

A socket needs two things before it can be opened. It needs the IP address of the machine where you will run the web server. The application can easily grab that IP address, so that is rarely a problem. The other thing it needs is a port number. Most web servers use port 80. When a webserver is started, it will attempt to latch itself into a socket using 80 as the port number. 

Some of the times, port 80 is also used by an application other than a webserver, skype for example. Only one application can use port number 80, or any port number for that matter, at any point in time. If an application like skype has already latched itself into port 80, no other application can use it until skype is terminated. This sets the stage for our troubleshooting exercise. We have used skype in here as an example of an app that prevents use from launching the web server. In reality, we do not know what application is using the port. So we need to find out. 

## 2 Steps

**1. Launch a terminal window**

On Windows 7, press the Windows superkey on the keyboard. When the **Start** menu pops, type **cmd** inside the textbox labeled **Run** then press ENTER. 

On Windows 8, press the Windows superkey, type **cmd** then press ENTER. 

**2. List the network processes**

List all the processes that are using network resources and filter the results. We are looking for a specific process that uses port number 80. Windows has the commands **netstat** and **findstr** which can do the job for us.

~~~
C:\> netstat -aon | findstr 0.0:80
~~~

The two commands above are joined by the pipe operator. The netstat command will list all network related processes. Its output is used as an input to findstr. The resulting list is filtered such that only applications using port 80 will show up.

**3. Find the application name of the app using port 80**

The **netstat** command will not give us the name of the application that uses port 80. It will give us only its process id or pid. We need to use another command to find out the application name

~~~
C:\> tasklist | findstr 560
~~~

The number 560 above may not be applicable for you. In my machine, the pid of the offending app was 560, it may not be the same for you. 

**4. Kill the offending process**

You can use the **taskkill** command to terminate the application

~~~
C:\> taskkill /F /PID 560
~~~

Alternatively, you can use GUI tools like the Windows **Task Manager**  to terminate running programs or a third-party tool like **Process Explorer** from SysInternals.



## 3 Further reading

1. The **netstat** command documentation can be found at the [Technet page for netstat](http://technet.microsoft.com/en-us/library/ff961504.aspx)
2. The **tasklist** command documentation can be found at [Technet page for tasklist](http://technet.microsoft.com/en-us/library/cc732459.aspx)
3. The **taskkill** command documentation can be found at the [Technet page for taskkill](http://technet.microsoft.com/en-us/library/bb491009.aspx)
4. **Port numbers** and service name assignments can be found at the [IANA page](http://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml?&page=2)

## 4 Resources 

1. **ProcessExplorer** - You can download ProcessExplorer from the [SysInternals website](http://technet.microsoft.com/en-us/sysinternals/bb896653.aspx)