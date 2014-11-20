---
layout: mac

title: Install MySQL on OSX

description: Simple steps to get MySQL working on a Mac, Yosemite, Mountain Lion, Lion, Snow Leopard, Leopard

excerpt: 

tags:
- MySQL
- Database

---

MySQL Installations on OSX Leopard, Snow Leopard, Lion and Mountain Lion have been pretty straightforward using the packaged installed from the [MySQL developer website](http://dev.mysql.com/downloads/). All you need to do is to download the package, run the package and the start the MySQL server using the tools provided on **System Preferences**. 

In OSX 10.10, the packaged installer of MySQL is with a slight hiccup. Yosemite will report that the installation has failed. It will show you a window stating that it was not able to complete the installation. But in fact, it got installed. The hiccup might be fixed in the future. For now, just go to the Mac System Preferences, find the MySQL menu and start it.

If you have **HomeBrew** in your system, you can also install mysql that way.

~~~~
brew install mysql*
~~~~

If what you have is **MacPorts**

~~~~
sudo port install mysql*
~~~~

In most occassions, these installers will create a symlink of the **mysql** command in the usual search paths of OSX. Just in case the symlinks were not created, you can include the mysql tools to your system path. Edit **~/.bash_profile** or **~/.profile** and add the following entries

~~~~
export PATH=PATH$:/usr/local/mysql/bin:.
~~~~

Close the terminal window and re-open it so that the new entries in bash_profile or profile will be read and properly exported to your shell environment.


## Using MySQL

The server is not started by default. There is a utility in the **System Preferences** right at the bottom part of the screen. Use it to start and stop MySQL server 

From a terminal window, use the command

~~~~
mysql -u root -p
~~~~

Press **RET**. The default installation of MySQL has a blank password for the root user.


