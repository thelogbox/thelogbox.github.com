---
layout: html5

title: Managing Complexity

description: How to animate multiple objects inside the HTML5 Canvas

tags:
- Animation
- OOP
- Array

categories:
- HTML5

---

When you start working with non-trivial Canvas applications, you will need to deal with multiple objects, having multiple shapes moving at different speeds and having different locations in the canvas. If you try to manage them all procedurally, you will soon run into the problem of very confusing and hard to maintain codes. JavaScript is an object oriented programming language and it has decent data structures built-in, you can use them to tame the complexity of dealing with multiple objects.

The following code sample allows the user to click inside the canvas. Each click produces a random shape e.g. circle, rectangle and square. The app constructs a random object on each click, which will then fall from the top of the canvas and eventually drops off the border.

<a href='http://jsfiddle.net/tedhagos/FYbwH/embedded/result/' class='button'>See the Demo</a>

{% highlight javascript %}
window.onload = function() {
  
  
  var c = document.getElementById('mycanvas');
  var cx = c.getContext('2d');
  var watch = document.getElementById('watch');
  
  var stage = new Stage();
  
  var counter = 0;
  
  draw();
  
  /* EVENT HANDLERS */
  
  c.onclick = function() {
    var mshape = null;
    var mx = event.clientX;
    var my = event.clientY;
    
    switch(Math.floor(Math.random() * 2)) {
      case 0:
        mshape = new Circle(mx, my);
        log("Circle");
        break;
      case 1:
        mshape = new Box(mx,my);
        break;
      case 2:
        mshape = new Rect(mx, my);
        break
      default:
        break;
    }
    stage.addShape(mshape);
  }  
  
  /* UTILITY FUNCTION */
  
  function draw() {
    stage.clear();
    stage.redraw();
    setTimeout(draw, 60);
  }
  
  function log(message) {
    var temp = watch.innerHTML;
    watch.innerHTML  = temp + new Date() +  '<br/>' + message;
  }
  
  /*
    OBJECT TEMPLATE DEFINITIONS
  */

  function Stage() {
 
    this.memory = new Array();
    
    this.clear = function(){
      cx.clearRect(0,0,c.width, c.height);
    }
    
    this.redraw = function() {
      for (var i =  0; i < this.memory.length; i++) {
        this.memory[i].draw();
      }
    }
    
    this.addShape = function(shape) {
      this.memory.push(shape);
    }
  }
  
  function Box(x,y) {
    this.x = x;
    this.y = y;
    this.width = Math.floor(Math.random() * 40 + 20);
    this.height = this.width;
    this.speed = 3; // 3 pixel displacement per redraw
    this.acc = 1; // acceleration constant
    
    this.draw = function() {
      cx.strokeRect(this.x, this.y, this.width, this.height);
      this.y += this.speed;
      this.speed += this.acc;
    }   
  }
   
  function Rect(x,y) {
    this.x = x;
    this.y = y;
    this.width = Math.floor(Math.random() * 40 + 20);
    this.height = this.width/2;
  }
  
  Rect.prototype = new Box;
  
  function Circle(x,y) {
   this.x = x;
   this.y = y; 
   this.radius = Math.random() * 40 + 20;
   this.speed = 2;
   this.acc = 1;
   
   this.draw = function() {
     cx.beginPath();
     cx.arc(this.x, this.y, this.radius, 0, 360, false);
     cx.closePath();
     cx.stroke();
     
     this.y += this.speed;
     this.speed += this.acc;
   }
  }   
}
{% endhighlight %}


The basic approach of the code above to abstract the whole canvas into an object **function Stage()**, it also abstracts the shapes Box, Rectangle and Circle using the OOP idioms. The basic idea is that each time a shape is created, it is stored and managed inside an array. Each time the timer expires, it is the responsibility of the **Stage** to process all the objects stored in the array then draw them to the canvas. The logic of drawing to the canvas was coded inside every shape object, so that when the **Stage** calls the *draw()* method against each shape that is processed,  it is oblivious to the details on how each shape should be drawn.




