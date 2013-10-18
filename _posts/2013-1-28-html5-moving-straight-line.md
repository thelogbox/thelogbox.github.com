---
layout: html5
title: Animation, Linear Movement
description: 
categories:
- html5

---


The canvas is a basic drawing surface. Making things move in a canvas is very similar in process to [flip-book](http://en.wikipedia.org/wiki/Flip_book) or flick-book animation. The three things you will neeed to do in order to animate things are;

1. Update the location of the objects
2. Erase the canvas
3. Redraw the object

To illustrate this basic concept, the next coding sample draws a box initially. A simple timer is provided by the **setTimeout** function. Each time the timer is called, the *y* position of the box is increased by 5 pixels. 

{% highlight html %}
<!DOCTYPE html>
<html>
<head>	
	<script>
	
  var c = null;
  var cx = null;
  var box = null;
  
  window.onload = function() {
    
    c = document.getElementById('mycanvas');
    cx = c.getContext('2d');
    box = new Box();
    
    update();
    
    function update() {
      cx.clearRect(0,0,c.width, c.height);
      cx.fillRect(box.x, box.y, box.width, box.height);
      box.x = box.x + box.speed;
      setTimeout(update,50);
    }
  }

  function Box() {
    this.x = 0;
    this.y = 0;
    this.width = 50;
    this.height = 50;
    this.speed = 5;
  }
	</script>
</head>

<body>
  <canvas id='mycanvas' height='400' width='500'>
  </canvas>
</body>
</html>
{% endhighlight %}

The *speed* of animation is not affected by number of milliseconds on the setTimeout function, rather, the speed is function of the number of pixels that is displaced on each frame refresh.








