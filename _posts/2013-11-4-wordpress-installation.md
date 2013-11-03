---
layout: wordpress

title: Installation and Configuration

description: How to setup a local instance of WordPress for Development. You must have Apache, MySQL and PHP installed already before proceeding with this 

excerpt: 

tags:
- installation

author: Ted Hagos

categories:
- WordPress

---

Presumably, you have completed the Apache, MySQL and PHP setup. This chapter walks through the steps on how to install and configure a WordPress instance.

The process involves downloading the installer from the WordPress website, expanding a zip file, editing a configuration file and creating a database. It may seem a bit complex for a beginning programmer but it can be managed by simply following the steps detailed below.

***

Download the installer from the [WordPress site](http://wordpress.org/download/). This is usually a zipped file.

Unzip the file and put it inside the folder *C:\Users\yourname\wamp\www*. This is the directory of our WAMP installation. Technically you can place the unzipped file anywhere and still manage to have the Apache web server find it. That however requires intermediate knowledge of the Apache configuration files &mdash; which I did not assume you have at this point. Hence, it will be best to simply put our expanded *wordpress* folder inside the default *Document Root* of Apache which is *C:\Users\yourname\wamp\www*.


## DATABASE CREATION

Check if the WAMP server is still running. You need WAMP to be in the running state to perform the following procedure.

Launch a browser session and go to *http://localhost* (assuming that you did not change the port of Apache in your WAMP installation). The opening screen of WAMP contains a *tool* section, try to find it and click *phpmyadmin*. 

Go to the *SQL* tab and enter the following

<pre class="codeblock">
CREATE database wppractice;

GRANT ALL PRIVILEGES ON wppractice.* TO yourname@’localhost’ IDENTIFIED BY 'yourpassword';

FLUSH privileges;
</pre>

Replace *yourname* and *yourpassword* with any value you like &mdash. Just a make a point to remember them because you will need them later.

![PHPMyAdmin SQL Page](/img/wordpress/phpmyadmin-sql.png)
<div id='lst'>phpmyadmin SQL page</div>

Click the *GO* button on the page. That will execute the three lines of SQL commands you typed up on the SQL editor. This is probably your first and last personal encounter with the MySQL database in WordPress unless you are doing something crazy, advanced or both with WordPress.

## CONFIGURE WP-CONFIG.INI

Go to Wordpress folder you created, it should be in C:\Users\yourname\WAMP\wordpress-project &mdash; if you did not stray from the instructions.

The core files contains a file named *wp-config-sample.php. Make a copy of that file and name it *wp-config.php*. Open it up for editing &mdash; don't double click it, your system might be configured to launch a browser instead of opening an editor. Right-click on it and choose an editing program e.g. notepad. You need to make some changes to its contents.


<pre class="codeblock">

// ** MySQL settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define('DB_NAME', 'wppractice');

/** MySQL database username */
define('DB_USER', 'yourusername');

/** MySQL database password */
define('DB_PASSWORD', 'yourpassword');

/** MySQL hostname */
define('DB_HOST', 'localhost');

/** Database Charset to use in creating database tables. */
define('DB_CHARSET', 'utf8');

/** The Database Collate type. Don't change this if in doubt. */
define('DB_COLLATE', '');

</pre>

This part will tell WordPress what database to use, which user has access to the database and what is the password of that user. This is why you needed to remember the username and password during the database creation time on the SQL editor of phpmyadmin. Replace *yourusername* with the username you used when you created the database using phpmyadmin (the SQL part). Do the same with *yourpassword*.

Save the file and launch a browser session. Go to *http://localhost/wordpress-project/wordpress* 

You will be taken to the WordPress Site initialization page. That is straightforward to fill up. Think of a site name and give it an administrator password.

<aside>

**NOTE:** The WordPress administrator password being requested on the WordPress site installation is different from your database password. Each wordpress installation must have at least one Admin user, so don’t lose your Admin password.

</aside>