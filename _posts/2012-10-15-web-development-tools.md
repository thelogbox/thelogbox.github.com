---
layout: post

title: Web Development Tools

description: A list of tools for the web programmer

excerpt: 

tags:
- Tools
- Development

categories:
- Web

---


# HAML FOR TEMPLATING

Can be used stand alone or integrated into frameworks like Sinatra, Rails etc. It can be downloaded form the Haml Site or simply via rubygem---gem install haml. If you use it stand alone, it is an HTML generator, if you use within a framework, it can be a filter or a template 

<pre class="codeblock">

/ filename: first.haml
/ forward slash is an inline comment

-# a minus sign followed by hash char is also another way
-# comment. This kind of haml comemnt, this won't be emitted to html

!!!5  / <!DOCTYPE html>
%html
  %head

    %title First haml
    %link{:rel => "stylesheet", :href=>"stylesheet.css"}
    %script{:src => "one.js"}
    
  %body
        
    %div{:id=>"canvas"} / this a way to define a div

    #hello Hi there / shorter way to define a div with id
    .content Output a div with class attribute

    %a{:href => "http://haml.info/docs/yardoc/file.REFERENCE.html"} Haml Site - Reference

    %something-else{:class => "define-this-in-css"} Inside something else

</pre>

**$ haml first.html** emits the resulting HTML file into stdout (screen).

**$ haml first.haml first.html** emits the output to *first.html*. The syntax reference can be found at [Haml Ref Site](http://haml.info/docs/yardoc/file.REFERENCE.html). Haml syntax is sensitive to indentation, so be careful, a really good editor will be very helpful here.


# 2. SaSS (Syntactically Awesome Style Sheets)

# SASS (SYNTACTICALLY AWESOME STYLE SHEETS)

Install using ruby gems &mdash; <code class="codeblock">gem install sass</code>


{% highlight css %}


#main {
  width: 80%;
  height: 23px;

  ul { list-style-type: none; }
  li {
    float: left;
    a { font-weight: bold; }
  }
}

{% endhighlight %}

When processed using the **saas** command, it will emit the following;

{% highlight css %}

#main {
  width: 80%;
  height: 23px; }
  #main ul {
    list-style-type: none; }
  #main li {
    float: left; }
    #main li a {
      font-weight: bold; }

{% endhighlight %}

The **saas** command line tool has a **--watch** option, it runs continuosly and watches the scss that you created, everytime you change the scss file, it will automatically emit the resulting CSS file

SAAS is a superset of CSS3, the extra syntax are syntactic sugar to enable cleaner nestings, provide modular approach to CSS source file management using @import, string interpolations, mixins (for inheritance), use of variables inside the CSS etc. Head over to [SasS lang site tutorial](http://sass-lang.com/tutorial.html) for more info.


# WEB SERVER


For quick and dirty serving up of static files without server-side processing, here are my favorites

### PYTHON 

invoke *python -m SimpleHTTPServer* on any directory or folder, the contents of the folder will be served up on **http://localhost:8000**

### NODE

Get a terminal window,

<pre class="codeblock">

$ sudo npm -g install http-server
$ cd /path/to/your/web/files
$ http-server

</pre>

This will serve the contents of the dir to http://localhost:8080

### PHP STANDALONE SERVER

Since PHP 5.4, you can use the stand alone server. There is no need for Apache anymore &mdash; provided that you have installed PHP CLI as well.

From a terminal window type <code class="codeblock">php -S localhost:8080</code>. It will start serving the files of the current directory.


# QUICK RESTFUL ENDPOINTS

### SINATRA

Sinatra a small ruby DSL (Domain Specific Language), it's often referred to as a microframework. There are other microframeworks e.g. [Spark (Java)](http://www.sparkjava.com/), [Flask (Python)](http://flask.pocoo.org/), [CherryPy (Python)](http://www.cherrypy.org/), Limonade (PHP), [Slim (PHP)](http://www.slimframework.com/) and many others.

You need **ruby & rubygems** before you can install sinatra. Install instructions for Ruby are on the ruby site

<pre class="codeblock">

# install sinatra

$ gem install sinatra
$ gem install sinatra-contrib
$ gem install thin

</pre>

You actually don't need thin, but might as well install, it seems to be the favored setup of programmers using Sinatra. You will need to install sinatra-contrib if you will use the hot-reloading of Sinatra (and you will really need to hot-reload, lest you want to be very proficient pressing CTRL-C to stop the server then start it all over again)

{% highlight ruby %}

# quick (but not dirty) and simple
# restful web endpoint

# this app will listen on http://localhost:4567

# filename: first.rb 
# how to run : $ ruby first.rb 

require 'rubygems' if RUBY_VERSION < '1.9'
require 'sinatra'

get '/' do
    "return something"
end

get '/somethingelse' do
    "return something else"
end

{% endhighlight %}

*http://localhost:4567* displays "return something"; *http://localhost:4567/somethingelse* displays "return something else" in the browser.

Each get in the sinatra source file is a method call, a route actually. You don't have to write literal ruby strings, it can be function calls, expressions etc, as long as it resolves to a string. This is handy when (quickly) mocking up server end points for AJAX clients. There are some [Sinatra notes here](/sinatra/).


### NODE

Node is JavaScript on the server side. You need to understand JavaScript core language (pretty well, cut and paste JavaScript experience won't cut it here).

The [NodeJS site](http://nodejs.org/) has the install instructions, head over there to download, install npm too (Node Package Manager). It can also be instlled via brew on OSX (brew install node)

The simplest node program from the (NodeJS website)

{% highlight javascript %}

// server.js

var http = require('http');
http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World\n');
}).listen(1337, '127.0.0.1');
console.log('Server running at http://127.0.0.1:1337/');

{% endhighlight %}

Run the code using <code class="codeblock">node server.js</code>. Get a browser and open *http://localhost:1337*. You can already use this to mock REST endpoints, just replace the string inside res.end('Hello World');

A more involved node server code sample is below

{% highlight javascript %}

var http = require('http');
var path = require('path');
var fs = require('fs');
var url = require('url');

var pages = {
	'': "Landing page",
	about: 'About',
	foo: "Yeah Foo",
	goo: "Yeah Goo",
	xoo: callxoo()
};

function callxoo(){
	var retval = {
		empname: "Ted Hagos",
		email: "tedhagos@gmail.com"
	};
	// I cannot return the bare JS object because
	// the HTTP object of node will throw an error.
	// First type argument must be a string or buffer
	return JSON.stringify(retval);
	
}

http.createServer(
	function(request,response){
		
		var lookup = path.basename(decodeURI(request.url));
		var thedata = null;
		var temp = null;
		
		// Check first if we are looking for an HTML file
		fs.exists(lookup, function(exists){
			if(exists){
				fs.readFile(lookup, 'utf-8', function(woops, filecontent){
					if(!woops) {
						//console.log(filecontent);
						response.writeHead(200, {'Content-Type': 'text/html'});
						response.end(filecontent);
					}
				});				
			}
			else {
				console.log("inside the else");
			}
		});
				
		if (pages[lookup] != undefined){
			console.log("inside pages");
			response.writeHead(200, {'Content-Type': 'text/html'});
			response.end(pages[lookup]);
		}						
	}
).listen(8080);

{% endhighlight %}

This will listen on *locahost:8080*, if you want to change the port of the webserver, just replace the port number, it's the line .**listen(8080)**, remember not to pick port numbers lower than 1024, they are privileged ports.

The routes here are inside the pages object literal, replace them with your own RESTful endpoints

# OOP FRAMEWORKS FOR JAVASCRIPT

You can just tough it out, do not pay attention to OO abstractions for HTML5 Canvas, SVG or WebGL programming; just code it on the fly, really up to you, but it can get very hairy (it will, and pretty quickly too). 

A coarse grained abstractions of the animation objects goes a long way. JavaScript is equipped with Prototypal inheritance and Functions are pretty much object factories; You can use them to achieve coarse grained abstractions of the problem domain.

To use a more classical OO approach in JavaScript there are plenty of extensions to the JavaScript language, a [list of things that compile or extend JavaScript is here](https://github.com/jashkenas/coffee-script/wiki/List-of-languages-that-compile-to-JS).

# 6. DEBUGGING, TESTING & PROFILING TOOLS

Developing in JavaScript is painful without debug and watch tools. Webkit browsers (Safari and Chrome) have Developer tools, they can very useful during development. Another tool to use is [FireBug](http://getfirebug.com/) of Mozilla FireFox browser.

You've got to do unit-testing, you just got to---this shouldn't be up for debate anymore. Things to use are;

1. [Jasmine](http://pivotal.github.com/jasmine/) - A BDD (Behavior Driven Development) test framework
2. [QUnit](http://qunitjs.com/) - Used by JQuery, JQueryUI and JQuery Mobile projects. A unit test framework.
3. [FuncUnit](http://funcunit.com/) - uses JQuery syntax
4. [YUITest](http://developer.yahoo.com/yui/yuitest/) - by Yahoo












