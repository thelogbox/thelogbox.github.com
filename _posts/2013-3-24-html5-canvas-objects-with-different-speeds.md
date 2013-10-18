---
layout: html5
title: Objects with Different Speeds
description: 
categories:
- html5

---

Most of the time, you will deal with more than one moving object inside the canvas, they might need to move at different speedss.  You could be tempted to set a different timer (setTimeout) for each box, that will be a mistake. You will mess up the timer of your canvas. The way to approach the problem of moving objects at different speed is to vary the pixel displacement of each individual object, rather than construct a timer for each object. 

The following example draws two boxes. Each box starts to fall from the top of the canvas, one moves at 5 pixels per refresh and the other moves at 8 pixels per refresh.



<a href='http://jsfiddle.net/tedhagos/gEjMD/embedded/result/' class='button'>See the Demo</a>

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
    box = new Box(5);
    box2 = new Box(8);
    box2.x = 70;
    
    update();
    
    function update() {
            
      cx.clearRect(0,0,c.width, c.height);
      cx.fillRect(box.x, box.y, box.width, box.height);
      cx.fillRect(box2.x, box2.y, box2.width, box2.height);
      box.y = box.y + box.speed;
      box2.y = box2.y  + box2.speed
      
      setTimeout(update,50);
    }
  }

  function Box(speed) {
    this.x = 0;
    this.y = 0;
    this.width = 50;
    this.height = 50;
    this.speed = speed;
  }
	</script>
</head>

<body>
  <canvas id='mycanvas' height='400' width='500'>
  </canvas>
</body>

</html>
{% endhighlight %}

