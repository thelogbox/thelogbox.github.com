---
layout: post

title: Canvas Basics

description: 

excerpt: 

author: Ted Hagos

lastupdate: 


tags:


categories:

---



This works

The reference HTML file. Nothing fantastic. The script tag on head references the JavaScript file **hey.js**. We will need to generate or emit this file from **hey.ts**, our TypeScript file


~~~
<!DOCTYPE html>
<html>
<head lang="en">
  <meta charset="UTF-8">
  <script src="hey.js"></script>
  <title>Hey</title>
  <style>
    canvas {border: 1px solid gray;}
  </style>
</head>
<body>
<canvas id="thecanvas" width="500" height="500">
  You should not see this
</canvas>
</body>
</html>
~~~

This works

~~~
window.onload = function() {

  var canvas:HTMLCanvasElement = <HTMLCanvasElement> document.getElementById("thecanvas");
  var ctx:CanvasRenderingContext2D = <any> canvas.getContext("2d");

  ctx.fillRect(100,100,50,50);
}
~~~

This works too

~~~
window.onload = function() {

  var canvas:any = <any> document.getElementById("thecanvas");
  var ctx:CanvasRenderingContext2D = <any> canvas.getContext("2d");

  ctx.fillRect(100,100,50,50);

}
~~~

So does this

~~~
window.onload = function() {

  var canvas:any =  document.getElementById("thecanvas");
  var ctx:CanvasRenderingContext2D = <any> canvas.getContext("2d");

  ctx.fillRect(100,100,50,50);

}
~~~

This does not work. It says fillRect does not exist on HTMLCanvasElement. What is up with lib.d.ts, what is the answer to this.

~~~
window.onload = function() {

  var canvas:any =  document.getElementById("thecanvas");
  var ctx:HTMLCanvasElement = <any> canvas.getContext("2d");

  ctx.fillRect(100,100,50,50);

}
~~~

But this works

~~~
window.onload = function() {

  var canvas:any =  document.getElementById("thecanvas");
  var ctx:CanvasRenderingContext2D =  canvas.getContext("2d");

  ctx.fillRect(100,100,50,50);

}
~~~

So it looks like I don't have to cast the canvas nor the context. I only have to strongly type them. 


The code below works. I don't even have to strongly type the context. As long the canvas is typed.

~~~
window.onload = function() {

  var canvas:any =  document.getElementById("thecanvas");
  var ctx =  canvas.getContext("2d");

  ctx.fillRect(100,100,50,50);

}
~~~

If I remove the typing of the canvas, even if it is just **any**, like this.

~~~

window.onload = function() {

  var canvas =  document.getElementById("thecanvas");
  var ctx =  canvas.getContext("2d");

  ctx.fillRect(100,100,50,50);

}
~~~

It throws an error. It says **getContext** does not exist on HTMLElement. Really, there is a rule here that I don't understand. Welcome to the wonderful world of statically typed languages.

This works. Why is casting working. Clearly, the HTMLCanvasElement  do contain the getContext call.

~~~
window.onload = function() {

  var canvas =  <HTMLCanvasElement> document.getElementById("thecanvas");
  var ctx =  canvas.getContext("2d");

  ctx.fillRect(100,100,50,50);

}
~~~

This does not work

~~~
window.onload = function() {

  var canvas =  <HTMLElement> document.getElementById("thecanvas");
  var ctx =  canvas.getContext("2d");

  ctx.fillRect(100,100,50,50);

}
~~~

It appears HTMLElement does not contain the definition of getContext

