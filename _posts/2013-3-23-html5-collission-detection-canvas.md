---
layout: html5

title: Handling Collissions

description: When things inside the HTML5 Canvas bumps into each other

tags:
- Animation

categories:
- HTML5

---


Collission detection inside the canvas needs to be managed by you. Everytime you update the location of any object, you will need to provide the programming logic to check if any of your canvas objects is colliding with any other object or if it is colliding with the bounds of the canvas.

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
            
      if((box.y + box.height) < c.height) {
        cx.clearRect(0,0,c.width, c.height);
        cx.fillRect(box.x, box.y, box.width, box.height);
        box.y = box.y + box.speed;
      }
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

This code sample basically moves the box object along the *y-axis*. Notice that prior to the *clear-update-redraw* operation, the bounds of the box is checked against the height of the canvas. If the box's current *y-location* plus the height of the box is less than the value of the canvas' height, the animation continues, if not, then no action is taken. This gives the appearance that the box stops at the bottom of the canvas.

## Refactor 

You could make the codes a bit more modular if you move the programming logic of the collission detection away from the drawing logic.

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
      if(!isInCollission(box)) {
        cx.clearRect(0,0,c.width, c.height);
        cx.fillRect(box.x, box.y, box.width, box.height);
        box.y += box.speed;
        setTimeout(update,50);
      }
    }
  }

  function isInCollission(box) {
    if((box.x + box.width) < c.width &  
       (box.y + box.height) < c.height) {
         return false;
       }
    else {
      return true;
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

The function **isInCollission()** takes a parameter (a box parameter) and checks if either the bottom or the right side of the box is in contact with either the right boundary or the floor of the canvas &mdash; of course you make it more robust by including codes that checks for collission on ceiling or the left side of the canvas, but that is left to you as an exercise.







