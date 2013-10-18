---
layout: post

title: HTML5 Canvas Programming

description:

except:

categories:
- html5

---



<div id="update-history">
<h3>Doc History</h3>
<br/>
18.Oct.2012 &mdash; created<br/>
22.Oct.2012 &mdash; rewrite sections, added basic straight line and circular movements<br/>
28.Oct.2012 &mdash; added some sections on acceleration. embedded live demo within tutorial<br/>
</div>


<div id="minitoc">
<h3>Contents</h3>

0. Prep
1. Basic plumbing
	+ Drawing primitives
	+ Timed animation
2. Basic movements
	+ Moving in a straight line
	+ Moving in a uniform circular motion
3. Acceleration
	+ Accelerate, then stop

</div>

# Prep

1. HTML5 compliant browser. It is easy to find out, open whatever browser you are using and go http://html5test.com
2. Good programmer's editor
3. JQuery
5. CoffeeScript
6. Haml
7. Sass
8. Source control (git, mercurial, svn, cvs etc), whatever you are comfortable with

Item numbers 3 until 8, you can live without (I suggest you don't though)


## Prior knowledge

You need a (really) solid background on **JavaScript**, a passing knowledge of the lanaguage might tie you up for drawing some simplistic primitives and less complex animations (straight line movements with fewer than 10 objects), however, when the complications gets to a higher order (lots of objects flying around independently, oscillations, movements along curvatures etc), it means only one thing--time to get some more programming knowledge and experience. A really good book will help, a really good teacher/mentor/community support will be even better.

Programmers coming from other languages (such as Java, C++, Ruby, Python) who are quite adept with data structures and algorithms will feel right at home. HTML5 canvas programming requires programming experience because it is quite close to the metal. There are frameworks that may help doing some basic animations, but you do really need to understand the JavaScript language, be comfortable structuring data (in OO way would be very helpful) and you need to genuinely enjoy breaking down problems into component solutions. As mentioned before, it is close to the metal programming; canvas lets you manipulate individual pixels in a bounded region, after that, you are pretty much on your own.

# 1. Basic plumbing

A canvas HTMLElement needs to be defined in the page. 

~~~
#!html

<!DOCTYPE html>
<html>
  <head></head>
  <style>#mycanvas {border:1px solid gray;}</style>
  <title>"canvas programming"</title>
  <script>src="canvas.js"</script>
  <body>
    <canvas id='mycanvas'>width=500 height=300</canvas>
  </body>
</html>

~~~

<p>

~~~
#!javascript

// filename: canvas.js

window.onload = function(){
	
	var canv = document.getElementById("mycanvas");
	var context = canv.getContext("2d");
	
}

~~~

The HTMLElement canvas is not the programming platform, you need it simply to get the actual reference to the 2d platform. The **mycanvas** is just a DOM element, think of it as a viewport, you cannot paint 2d drawing primitives in that element. The **context** object is the 2d platform, use this to draw the drawing primitives. 


## 1.1 Drawing primitives of the Canvas 
<p>
~~~
#!javascript

// filename: canvas.js

window.onload = function(){
	
	var canv = document.getElementById("mycanvas");
	var context = canv.getContext("2d");

	ctx.fillRect(10,10,50,50);
	ctx.strokeRect(70,10,50,50);
			
	ctx.fillStyle = "rgb(255,0,0)";
	ctx.fillRect(10,70,50,50);
			
	ctx.strokeStyle = "#ababab";
	ctx.strokeRect(70,70,50,50);
			
	// DRAW LINES
			
	//The line is gray bec the curr strokeStyle
	//is #ababab
			
	ctx.lineWidth = 1;
	ctx.beginPath();
	ctx.moveTo(130, 130);
	ctx.lineTo(0,0);
	ctx.closePath();
	ctx.stroke();
			
	// DRAW some text
			
	ctx.fillText("Hello", 130,20);
	ctx.font = "40px serif"; // you can add italics here, just like in css
	ctx.fillText("Hello", 130,60);
	ctx.strokeText("Hello", 130,100);
			
	//DRAW CIRCLE
			
	ctx.fillStyle = "green";
	ctx.beginPath();
	ctx.arc(60,180,50,0,Math.PI * 2, false);
	ctx.closePath();
	ctx.fill();
			
	ctx.fillStyle = "orange";
	ctx.beginPath();
	ctx.arc(60,280,50,0,Math.PI, false);
	ctx.closePath();
	ctx.fill();
	
}

~~~

Lots of things you can do with the **context (ctx)** object, in fact, everything has to be drawn using the context object, you need to be very comfortable with it. The sample code above demonstrates some primitives of the context object (line, text and arc). There are more examples of Canvas basics at [HTML5 Canvas tutorials](http://www.html5canvastutorials.com/tutorials/html5-canvas-tutorials-introduction/)


## 1.2 Animation using a timer 

Using barebones JavaScript should still be okay to use for the following examples, but there is no point delaying using the tools mentioned in **Section 0**, so we will use them. 

## Prep Steps

1. Download [jquery-1.8.x.js](http://jquery.com/download/) and put it on same directory where the .coffee files and .haml files are
2. Get Haml (via rubygems), **gem install haml**
3. Get coffeescript (via node package manager) **npm -g install coffee-script** 

<p>

~~~
#!haml

/ filename: animate.haml
/ compile: haml animate.haml animate.html

/ author: Ted Hagos

!!!5

%html
	%head
		%title Basic Time Animation

		%script{:src => "jquery-1.8.1.js"}
		%script{:src =>  "animate.js"}

	%body

		%canvas{:id => "mycanvas", :width => 500, :height => 300}
~~~

<p>

~~~
#!ruby

###

BSD License: Copyright (c) 2009-2012 Ted Hagos
All rights reserved.

License text: http://thelogbox.com/source-docs/software-license.txt
	
###

###

filename: animate.coffee
compile: coffee --compile animate.coffee 

Desc:

	Basics of a game loop
	1. Update positions of objects in the canvas
	2. Clear the canvas
	3. Redraw eveything in the canvas

	This one is pretty basic, it draws a square primitive
	everytime the canvas is redrawn. Experiment with the
	code by removing the hash sign (comment) before the
	line "ctx.clearRect..." if that line is commented out
	then the screen will fill up with random sized squares
	overtime; if the line is not commented, a randomly sized
	square object will appear everytime the canvas is 
	redrawn

###

class Paper

	c = 0;
	ctx = 0;
	counter = 0;

	constructor: (canvas,context) -> 
		c = canvas
		ctx = context
		@draw()

	draw: =>
		#ctx.clearRect 0, 0, c.width, c.height
		sq = Square.getSquare(c)
		ctx.strokeRect sq.x, sq.y, sq.width, sq.height
		setTimeout @draw, 300


class Square

	@getSquare: (canvas) ->
		x = Math.random() * canvas.width
		y = Math.random() * canvas.height
		width = Math.random() * 75
		height = width
		{x, y, width, height}

$(window).ready ->
	canvas = $('#mycanvas').get(0)
	context = canvas.getContext('2d')

	paper = new Paper(canvas,context)

~~~

<p>

# 2. Basic movements 

## 2.1 Moving in a straight line 

<p>

~~~
#!haml

/ filename: straight.haml
/ compile: haml straight.haml straight.html

/ author: Ted Hagos

!!!5

%html
	%head
		%script{:src => "jquery-1.8.1.js"}
		%script{:src => "straight.js"}

	%body
		%canvas{:id => "mycanvas", :width => 500, :height => 300, :style => "border:1px solid gray"}


~~~

<p>
~~~
#!ruby

###

BSD License: Copyright (c) 2009-2012 Ted Hagos
All rights reserved.

License text: http://thelogbox.com/source-docs/software-license.txt
	
###

####

filename: straight.coffee
compile: coffee --compile straight.coffee

Desc: 

	Basic horizontal movement of a context primitive. Each time the screen is
	redrawn (setTimeout @draw, 30), the y-coordinate of the box object is
	incremented

	This code sample also demonstrates basic principle of collision detection,
	once the right edge of the box object (box.x + box.width) has touched the right
	edge of canvas ( > c.width), we stop redrawing the canvas--sure the JavaScript
	timer goes chugging along still, you cannot stop it, but there is an branching
	of the logic inside the draw() function -- unless stop_drawing is true, we 
	draw, if stop_drawing is true already, we stop

####


class Stage

	c = ctx = box = null
	stop_drawing = false

	constructor: (canvas, context) ->
		c = canvas
		ctx = context

		box = 
			x: 10
			y: c.height /2
			width: 40
			height: 40
			speed: 1

		@draw()
		
	draw: =>

		unless stop_drawing

			ctx.clearRect 0, 0, c.width, c.height
			box.x += box.speed
			ctx.strokeRect box.x, box.y, box.width, box.height
			setTimeout @draw, 30

			if box.x + box.width is c.width then stop_drawing = true


$(window).ready ->
	canvas = $('#mycanvas').get(0)
	context = canvas.getContext('2d')

	stage = new Stage(canvas, context)

~~~

<p>

## 2.2 Moving in a uniform circular motion 

There is no direct way to make a an object move along a circular path. The circular path has to be calculated, then set the *x,y* of the object to move along those coordinates

<!--
<img src="/res/article-pix/notes-canvas/circlepath.png" width=500/>
-->
<iframe src="/source-docs/circlepath.html" width="100%" height=350px frameBorder=0>
</iframe>

<p>

~~~
#!haml

/ filename: circlepath.haml
/ compile: haml circlepath.haml circlepath.html

/ author: Ted Hagos

!!!5

%html
	%head

	%script{:src => "jquery-1.8.1.js"}
	%script{:src => "circlepath.js"}

%body
	%canvas{:id => "mycanvas", :width => 600, :height => 600}
	#watch

~~~

<p>

~~~
#!ruby

###

BSD License: Copyright (c) 2009-2012 Ted Hagos
All rights reserved.

License text: http://thelogbox.com/source-docs/software-license.txt
	
###

###

filename: circlepath.coffee
compile: coffee --compile circlepath.coffee

Desc:
	Trace the path of circle object (defined in the constructor). That specific
	circle will not be drawn, but instead its perimeter will be used as the 
	path as we draw (and animate) a smaller circle (drawn using ctx.arc) 
	
###


class Paper

	c = null
	ctx = null

	ball = {}
	circle = {}

	counter = 0

	constructor: (canvas, context) ->
		c = canvas
		ctx = context
		$('#watch').html "On the CTOR"

		ball = 
			x:0
			y:0
			speed: 0.1

		circle = 
			centerX: 250
			centerY: 250
			radius: 125
			angle: 0

	draw: =>
		
		counter += 1
		
		ctx.clearRect 0, 0,  c.width, c.height
		ball.x = circle.centerX + Math.cos(circle.angle) * circle.radius
		ball.y = circle.centerY + Math.sin(circle.angle) * circle.radius

		ctx.beginPath()
		ctx.arc ball.x, ball.y, 15, 0, Math.PI * 2, true
		ctx.closePath()
		ctx.stroke()

		circle.angle += ball.speed
		
		# why is this not being called
		
		$('#watch').html "Loop counter = #{counter}"
		setTimeout @draw, 1000


$(window).ready ->
	canvas = $('#mycanvas').get(0)
	context = canvas.getContext('2d')

	paper = new Paper(canvas, context)
	paper.draw()

~~~

<p/>

# 3. Acceleration

To immitate the motion of freely falling bodies, the downward movement along a straight line needs to incorporate acceleration. Our box need not only update its *y* position, it also needs to update its speed. Each time the canvas is redrawn, the speed increases *(box.speed += box.acceleration)*

<iframe src="/source-docs/acceleration.html" width="100%" height=550px frameBorder=0>
</iframe>

~~~
#!haml

/ filename: acceleration.haml
/ author: Ted Hagos


!!!5

%html
	%head
		%link{:rel => "stylesheet", :href => "stylesheet.css"}
		%script{:src => "http://code.jquery.com/jquery-1.8.2.min.js"}
		%script{:src => "jcanvas.min.js"}
		%script{:src => "acceleration.js"}
	%body
		%canvas{:id => 'mycanvas', :width => 500, :height => 500, :style => "border: 1px solid gray"}


~~~

<p/>

~~~
#!ruby

###

BSD License: Copyright (c) 2009-2012 Ted Hagos
All rights reserved.

License text: http://thelogbox.com/source-docs/software-license.txt
	
###

# filename: accelerate.coffee
# date: Sat Oct 27 15:33:22 PHT 2012 

###

To accelerate, increase the speed of the box each time it is redrawn. 

###

class Stage 

	c = ctx = box = null
	stopAnimation = false

	constructor: (canvas, context) ->
		c = canvas
		ctx = context

		box = 
			x: c.width/2
			y: 0
			width: 10
			height: 10
			speed: 1 
			acceleration: .98 

		@draw()

	draw: =>

		unless box.y > c.height

			ctx.clearRect 0,0, c.width, c.height
			box.y += box.speed
			box.speed += box.acceleration

			ctx.strokeRect box.x, box.y, box.width, box.height
			setTimeout @draw, 60

			if box.y > c.height
				box.speed = 1
				box.y = 0
				box.x = Math.random() * c.width


$(window).ready ->
	canvas = $('#mycanvas').get(0)
	context = canvas.getContext('2d')

	stage = new Stage(canvas, context)

~~~

## 3.1 Accelerate, then stop 

Combination of techniques now. Make the box accelerate as it falls down, then detect if the bottom of the box *(box.y + box.height)* has already touched the canvas floor *(canvas.height)*. Make the box rest there.

Click **fall** button below to see the demo

<iframe src="/source-docs/fall-stop.html" width="100%" height=550px frameBorder=0>
</iframe>

~~~
#!haml

/ filename: fall-stop.haml
/ author: Ted Hagos


!!!5

%html
	%head
		%script{:src => "http://code.jquery.com/jquery-1.8.2.min.js"}
		%script{:src => "fall-stop.js"}
	%body
		%canvas{:id => 'mycanvas', :width => 500, :height => 500, :style => "border: 1px solid gray"}

~~~

<p/>

~~~
#!ruby

###

BSD License: Copyright (c) 2009-2012 Ted Hagos
All rights reserved.

License text: http://thelogbox.com/source-docs/software-license.txt
	
###

# filename: fall-stop.coffee
# date: Sat Oct 27 19:13:30 PHT 2012

###

Accelerate downwards, apply collision detection when the bottom of the
box hits the floor (height value of the canvas) to make the box rest on
the bottom

###

class Box

	canvas = null
	box = null

	constructor: (@canvas) ->
		
		@x = Math.random() * canvas.width
		@y = 0
		@width = 50
		@height = 50
		@speed = 1
		@acceleration = .98
		@at_rest = false

class Stage 

	c = ctx = box = null
	stopAnimation = false

	constructor: (canvas, context) ->
		c = canvas
		ctx = context
		box = new Box(c)

		@draw()

	draw: =>

		ctx.clearRect 0, 0, c.width, c.height
		
		# to smooth out the collission
		if (box.y + box.height) <= (c.height - box.height)

			box.y += box.speed
			box.speed += box.acceleration
			ctx.strokeRect box.x, box.y, box.width, box.height
			foo = setTimeout @draw, 60
		else
			ctx.strokeRect box.x, c.height - box.height, box.width, box.height
			#clearTimeout foo
		
		# What happens to this box after it has fallen off the canvas? does it
		# still consume memory?


$(window).ready ->
	canvas = $('#mycanvas').get(0)
	context = canvas.getContext('2d')
	stage = new Stage(canvas, context)

~~~

<p/>






