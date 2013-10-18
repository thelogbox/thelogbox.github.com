---
layout: html5

title: Acceleration 

description: 

categories:
- html5

---

Making objects fall inside the canvas is pretty straightforward. You simply need to move the object along the *y-axis* of the canvas. Each time you redraw the frame, incrase the *y position* of the object.

To make the fall a bit more realistic, you need to add some acceleration. Speed of the object is simply the number of pixels displaced on every refresh. To accelerate the object, you need to increase the speed on every refresh. This code sample demonstrates basic acceleration of a falling object.

<a href='http://jsfiddle.net/tedhagos/HXsxa/embedded/result/' class='button'>See the Demo</a>

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
        box.speed += box.acceleration;
        
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
    this.acceleration = 1;
  }
	</script>
</head>

<body>
  <canvas id='mycanvas' height='400' width='500'>
  </canvas>
</body>
</html>
{% endhighlight %}  