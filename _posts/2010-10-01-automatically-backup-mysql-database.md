---
layout: post

title: Automatic Backup of MySQL

description: Simple steps to automatically backup MySQL

except:

tags:
- database
- backup

categories:
- MySQL

---


# USE CASE

1. To backup a MySQl database regularly, in fixed periods of time
2. To do No. 1 using freely available tools.

# SOLUTION

You need to do this on a Terminal window.

<span class='codeblock'>$ sudo mysqldump -u UserName -p --all-databases > /path/to/file.backup </span>


*UserName* - replace this with the username you are using to access MySQL

*--all-databases* - This will back up everything in MySQL. if you don't want to backup everything, specify the database name here<br/>

*The > redirection sign*  after the <span class='codeblock'>--all-databases</span> portion is necessary because mysqldump basically sends the textual content of the database to the screen, that is why we need to redirect the output to a file, so that we can restore it a later time.  


The result of mysqldump is actually a series of SQL commands that contains both the structure and contents of the database. It is very straightforward to restore it using

<pre class='codeblock'>
  
$ mysql -u UserName -p

mysql > create database name_of_name_database
mysql > use name_of_new_database
mysql > .\file.backup
    
</pre>

##How to perform MySQL backup automatically

**TODO**

1. Put this in a cron job
2. Refine by gzipping redirected text-output
3. Refine further by adding time stamp to the backup files
4. Refine by setting up Rsync to work with this backup approach
5. I could actually put backup file inside DropBox, then I won't need rsync. However, mostly likely, if the installation is enterprise grade, chances are the Dropbox code won't be an optoin -- but hey, investigte it.

And there you have it, a respectable DRM for your database


