---
layout: html5


title: Handling Clicks 

description: Capturing events inside the HTML5 Canvas

tags:
- Event
- Client
- JavaScript

---

To capture click events on the canvas, you will need to attach an event handler on the canvas itself, not the context. Since the canvas element is just like any other DOM element, attaching a click event to it is very straightforward. It can be done in any number of ways, the simplest is probably

{% highlight javascript %}

window.onload = function() {
  
  var canvas = document.getElementById('mycanvas');
  // SOME CODES
  
  canvas.onclick = function() {
    // CLICK CODES
  }
}

{% endhighlight %}

The following code sample demonstrates how to trap the click event inside the canvas. It also showcases some capabilities of the canvas which makes the example a bit interesting.

<a href='http://jsfiddle.net/tedhagos/wNxpG/1/embedded/result/' class='button'>See the Demo</a>

{% highlight html %}
<!DOCTYPE html>
<html>

<head>
	<style>
	#mycanvas {
		margin:10px;
		border: 2px solid #CACACA;
	}
	#watch {
		margin:20px;
		font-size:130%;
	}
	</style>
	
	<script>
	
	window.onload = function(){
		
		var c = document.getElementById('mycanvas');
		var context = c.getContext("2d");
		var watch = document.getElementById('watch');
		
		var mousex;
		var mousey;
		var mousepos;
		var mouseoffset = 20;
		
		c.onclick = function() {
			
			mousex = event.clientX;
			mousey = event.clientY;
			
			mousepos = "X : " + mousex + " | Y :" + mousey;
			watch.innerHTML = mousepos;
			draw(mousex,mousey);
		}
		
		function draw(x,y) {

      var R = Math.floor(Math.random() * 255);
      var G = Math.floor(Math.random() * 255);
      var B = Math.floor(Math.random() * 255);
      var color = "rgb(" + R + "," + G + "," + B + ")";
      
      var dim = Math.random() * 50;
      
      context.fillStyle = color;
			context.fillRect(x-mouseoffset,y-mouseoffset,dim,dim);
		}		
	}
	</script>
</head>

<body>
	<canvas id='mycanvas' width='400' height='300'>
		Time to get a new browser
	</canvas>
	<div id='watch'>
		X: Y:
	</div>
</body>

</html>
{% endhighlight %}

The current location of mouse is given by **event.clientX & event.clientY**. The sample code uses the current location of the mouse to draw the *X & Y* of the rectangle. The *offset* variable was used simply to reposition the top-left of the rectangle in order to coincide with tip of the mouse cursor.




  
  
  