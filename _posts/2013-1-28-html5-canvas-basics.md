---
layout: html5

title: Canvas Basics 

description: Understanding the 2D context of HTML5 Canvas

tags:
- Canvas
- 2D

categories: 
- HTML5

---

The canvas is a 2D drawing surface. If you ever used Microsoft Paint before, then you have an idea of what it is. It basically exposes the capability to draw into a surface using pixels &mdash; it is bitmapped.

The idea is to draw a pixel at a specific location and then apply some colors into it. This is as close to the metal as you can get on canvas 2D, you need to manipulate each and every pixel of it in order to achieve some animations or some effects. 

The canvas element is declared as a child of the *body* tag, like this

{% highlight html %}
<!DOCTYPE html> 
<html>
  <head> 
  </head>

  <body>
    <canvas ID="thecanvas" WIDTH="300" HEIGHT="300">
    If you can see this message, your browser does not
    support the HTML5 canvas. Get a new browser    
    </canvas>
  </body> 
</html>
{% endhighlight %}
  
If your browser is quite antiquated and not up to standards, you will see the warning message in between the canvas element's start and end tags.

For something interesting to happen, we need to do something inside the canvas, specifically we need to draw on its surface. The canvas API defines a lot of things that you can do on the surface e.g. draw some text, draw boxes curves and beziers, change the alpha values of pixel(s) etc. All these capabilities are exposed by HTML5 via JavaScript


## Getting the programming handle

You need to get to the **2d** context, that is the drawing surface, not the canvas DOM element. The context can be obtained by calling the *getContext()* method of canvas element.

{% highlight javascript %}

window.onload = function() {

  var canvas = document.getElementById('canvasname');
  var context = canvas.getContext('2d');

}
{% endhighlight %}


## Primitive drawings

The canvas API defines some drawing primitives that you can use as building blocks for your animations. It defines rectangles, arcs, text and lines to name a few.

**context.fillRect(x,y,width,height)** - draws a rectangle object. The first two parameters are the location of the top and left of the rectangle, respectively; the width and height parameters are quite obvious.

The *x & y* location of the object is relative to the top-left location of the canvas and not the web page. The coordinate system of the canvas is similar to the cartesian plane &mdash; actually, the fourth quadrant of the cartesian plane. The top-left coordinate of the canvas is at **0,0**; 1 unit of movement on the canvas is 1 pixel, that is, coordinate **1,1** means x is 1 pixel down and y is 1 pixel to the right. 

**context.fillText(String, x, y)** - draws a text on the canvas. The first parameter is the text of the string to be drawn. The second and third parameters gives the location on where to draw the text.


### Lines

Drawing lines is a bit different, you will need to make some extra calls on the context for positioning the line and then finally drawing the line.

{% highlight javascript %}

window.onload = function() {

  var canvas = document.getElementById('canvasname');
  var context = canvas.getContext('2d');

  context.beginPath();
  context.moveTo(10,10);
  context.lineTo(10,100);
  context.closePath();
  context.stroke();

}

{% endhighlight %}

Before you can start drawing into a path, you will need to call the **beginPath()** method, note that this this is used not only for drawing lines but for others shapes as well like arcs, beziers and quadratic curves. The example above starts the line drawing at 10,10 and and ends at 10,100 &mdash; it will draw a vertical line.

### Circles

{% highlight javascript %}

window.onload = function() {

  var canvas = document.getElementById('canvasname');
  var context = canvas.getContext('2d');

  var x = 50;
  var y = 50;
  var r = 30;
  var beginAngle = 0;
  var endAngle = 360
  var clockwise = false;

  context.beginPath();
  
  context.arc(x,y,r,beginAngle,endAngle,clockwise);
  
  context.closePath();
  context.stroke();

}

{% endhighlight %}

There is no drawing primitive for drawing a complete circle, you would have to do that by drawing arcs. Try to experiment by making the **endAngle** less than 360 degrees.

## Erasing the canvas

You can simply overwrite the canvas with a call to *fillRect*, that will write over it or you can call **context.clearRect(top,left,height,width)** 

{% highlight javascript %}

window.onload = function() {

  var canvas = document.getElementById('canvasname');
  var context = canvas.getContext('2d');

  // CANVAS OPERATIONS
  
  context.clearRect(0,0,canvas.width, canvas.height);

}

{% endhighlight %}

You have to clear the canvas starting from the top-left, which is 0,0, then specify the width and height of the canvas. You can get the dimensions of canvas using the canvas DOM element, the height and width are properties of the DOM element.





