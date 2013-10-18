---
layout: post

title: How to Install MySQL on OSX

description: 

excerpt: 

categories:
- blog

---


This was done on Leopard, Snow Leopard, Lion and Mountain Lion

## Motivation

1. Install a mysql-server for development purposes on OSX Lion
2. Use the include mysql CLI (Command Line Interface), specifically mysql client

## Possible routes

1. Using BREW -- *$ sudo brew install mysql*
2. Using MacPorts -- *sudo port install mysql*
3. Download from  [MySQL developer website](http://dev.mysql.com/downloads/)

I went with No. 3 above. Installation went smoothly, except that the MySQL CLI was not included in the path, I had to manually add it to the PATH variable.

<pre class='codeblock'>

	$ vi ~/.bash_rc
	… some entries in the .bash_rc
	… export PATH=PATH$:/usr/local/mysql/bin:.

</pre>


## To use MySQL on OSX

1. The server is not started by default. There is a utility in the *System Preferences* under the entry *Others* right at the bottom part of the screen. Use it to start and stop MySQL server
2. To communicate with MySQL, use the CLI client &mdash; <code class="codeblock">$ mysql -u root -p</code>

