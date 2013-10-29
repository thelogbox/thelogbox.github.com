---
layout: html5

title: Line Graphing in HTML5 Canvas

description: Test driving Microsoft Typescript with HTML5 Canvas

excerpt: 

tags:
- TypeScript
- HTML5

categories:
- JavaScript

---



This is an exercise on the HTML5 canvas, so it will use canvas. Admittedly, this would (probably) be a lot simpler if this was done in SVG, because repositioning the vertices and the lines could be handled in a more straightforward way---each vertex and line is a DOM element, which means they can easily be bound to events such as click or mousedown. Anyway, it still a good coding calesthenics, so canvas it is.  

The exercise has lots of parts. The cartesian plane needs to be drawn, a way to remember what has been drawn on canvas is also needed and the canvas needs a little bit of state management (counting the number of clicks)---one click means that we are about to draw a line, two clicks means we have chosen the second vertex and we need to do three things 1) complete the data of the line 2) store the information of the newly created line and then 3) redraw all of the previous lines we have created. It could be an ardous task if we won't try apply some form of abstractions on all of these things---a procedural-ish code might cut it, will cut it, but an OO style programming I think is warranted, even on this trivial exercise. 

[TypeScript](/typescript-first-notes/) came out just recently, even at its early stages, its OO and static type checking could be useful to this exercise, hence, TypeScript it is

<img class="shadow" src="/img/cartesian-canvas.png">



# How to do it

## 1. Create the HTML part (filename = line-draw.html)

{% highlight javascript %}

<!DOCTYPE html>
<html>
	<head>
		
		
		<title></title>
		
	</head>
	<body>
	<noscript>This demo will not work if JavaScript is disabled in your browser. 
		Please enable JavaScript in your browser then load this page again. 
		Thanks
	</noscript>
	<script src="MathE.js"></script>
	<div id="output"></div>
	<canvas id="default-canvas">
	Your browser is not capable of displaying HTML5 canvas components		
	</canvas>
	</body>
</html>

{% endhighlight %}

The default-canvas html element is not important to the actual code, it is just a quick and dirty way to check if the browser being used does not support the canvas element, you could use Modernizr.JS for a more proper way of checking for HTML5 capability of the browser. The NOSCRIPT tag is also a quick and dirty way of detecting if JavaScript is disabled in the browser---I just don't see how this can kind of exercise can degrade gracefully if JavaScript is diabled, so its an all or nothing deal; No JavaScript, no demo.


## 2. The TypeScript file

Create a TypeScript source file on the same directory as *line-draw.html*, for the exercise, I named it *MathE.ts*, this will later emit a file called *MathE.js* which is the **src** of our script tag on the HTML file 

<pre class="codeblock">

// filename : MathE.js 
// An example of using HTML5 canvas to do primitive lines on a cartesian plane.


class Paper {

	private isDirty = false;
	private clickcount = 0;
	private cartesian: Cartesian;
	private vertices : Vertices;
	private canv: any;
	private ctx : any;
	private lines : Lines;
	private line : Line = {x1:0,
			y1:0,
			x2:0,
			y2:0,
			pname1:"",
			pname2:""
	};
	
	private output : any = null;
	
	constructor(){
			
		// setup the canvas
		this.canv = <HTMLCanvasElement>document.createElement("canvas");
		this.canv.width = 600;
		this.canv.height = 600
		this.canv.style.border = "1px solid gray";
		
		// BEGIN events
		// this gave me a problem, when I am using idiomatic JS to assign 
		// a function to onclick, there are weird problems, the number is resulting
		// to isNan, I should investigate why TypeScript is behaving this way.
		// I had to use the arrow functions for closures
		
		this.canv.onmousedown = ()=> {this.canvClick();};
		this.canv.onmousemove = ()=> {this.canvMouseMove();}
		
		// END events
		
		document.body.appendChild(this.canv);
		
		this.ctx = this.canv.getContext("2d");
		this.cartesian = new Cartesian(this.ctx, this.canv);
		this.vertices = new Vertices();
		this.lines = new Lines();
		
		this.output = <HTMLElement>document.createElement("div");
		this.output.setAttribute('id', "output"); 
		
		//this.output.style.border = "1px solid #fafafa";
		//this.output.style.padding = "15px";
		//this.output.style.font-size = "11px";
		document.body.appendChild(this.output);
		
		this.output.innerHTML = "READY";
		//this.output = <HTMLElement>document.getElementById('output');
		//this.output.innerHTML = "I am ready";
		
		
				
	}
	
	private clearPaper() : void {
		this.ctx.clearRect(0,0,this.ctx.width, this.ctx.height);
		this.cartesian.drawX();
		this.cartesian.drawY();
		this.output.innerHTML = "READY";
	}
	
	private canvMouseMove(){
		
		if(this.isDirty){
			
			this.redraw();
			
			this.ctx.beginPath();
			this.ctx.moveTo(this.line.x1, this.line.y1);
			this.ctx.lineTo(event.clientX, event.clientY);
			//this.ctx.closePath();
			this.ctx.stroke();
			
			//this.redraw();			
			//this.output.innerHTML = "MouseMove";
		}
	}
	
	
	private canvClick() : void {
		
		switch(this.clickcount){
			case 0:
				this.line.x1 = event.clientX;
				this.line.y1 = event.clientY;
				this.line.pname1 = this.vertices.getNext(); 
				this.markPoint();
				
				this.clickcount++;
				this.isDirty = true;
				break;
			case 1:
				this.isDirty = false;
				
				this.line.x2 = event.clientX;
				this.line.y2 = event.clientY;
				this.line.pname2 = this.vertices.getNext();
				this.lines.addLine(this.line);
				
				this.line = {x1:0,y1:0,x2:0,y2:0,pname1:"",pname2:""};
				
				this.redraw();
				
				this.markPoint();
				this.clickcount = 0;
				
				break;
			default:
				break;
				//I don't know what to do with this one
		}
	}
	
	private markPoint() : void {
		
		var tempstyle : any = this.ctx.fillStyle;
		this.ctx.fillStyle = "blue";
		
		if(this.isDirty){
			this.ctx.fillText(this.line.pname2, this.line.x2 + 10, this.line.y2 + 10);
			this.ctx.fillRect(this.line.x2, this.line.y2, 5,5);
		}
		else {
			this.ctx.fillText(this.line.pname1, this.line.x1 + 10, this.line.y1 + 10);
			this.ctx.fillRect(this.line.x1, this.line.y1, 5,5);
		}
		
		this.ctx.fillStyle = tempstyle;
	}
	
	private redraw() : void {
		
		var tempStrokeStyle : any = this.ctx.strokeStyle;
		var tempFillStyle : any = this.ctx.fillStyle;
		var tempLineWidth : any = this.ctx.lineWidth;
		
		this.ctx.strokeStyle = "gray";
		this.ctx.fillStyle = "blue";
		this.ctx.lineWidth = 0.5;
		
		this.ctx.clearRect(0,0,this.canv.width,this.canv.width);
		
		var deleteme: any = null;
		var arrlength = this.lines.length();
		
		this.lines.currpos = 0;
				
		for(var i = 0; i < arrlength; i++){
						
			var templine = this.lines.getNext();
		
			this.ctx.fillText(templine.pname1,templine.x1 + 10, templine.y1 + 10);
			this.ctx.fillText(templine.pname2,templine.x2 + 10, templine.y2 + 10);
			this.ctx.fillRect(templine.x1, templine.y1, 5, 5);
			this.ctx.fillRect(templine.x2, templine.y2, 5, 5);
		
			this.ctx.beginPath();
			this.ctx.moveTo(templine.x1, templine.y1);
			this.ctx.lineTo(templine.x2, templine.y2);
			this.ctx.closePath();
			this.ctx.stroke();
					
		}
		
		
		// temporary code, because the mousemove erases the first vertex drawn
		this.ctx.fillText(this.line.pname1, this.line.x1 + 10, this.line.y1 + 10);
		this.ctx.fillRect(this.line.x1, this.line.y1, 5,5);
		// end temporary code
		
		this.ctx.strokeStyle = tempStrokeStyle;
		this.ctx.fillStyle = tempFillStyle;
		this.ctx.lineWidth = tempLineWidth;
		
		this.cartesian.drawX();
		this.cartesian.drawY();
		
		this.output.innerHTML = this.lines.toString();
		
	}	
}

// Vertices class
// A simple stack of vertex names
// currently, it is only from A - Z

class Vertices {
	
	private varr = new Array();
	private currpos = 0;
	
	constructor(){
		for(var i = 65; i <= 90; i++){
			this.varr.push(String.fromCharCode(i));
		}
	}
	
	printAll(){
		for(var i = 0; i < this.varr.length; i++){
			console.log(this.varr[i]);
		}
	}
	
	// get the next available vertex name
	
	getNext(){
		var retval = this.varr[this.currpos];
		this.currpos++;
		return retval;
	}	
}


class Cartesian {
	
	private context;
	private canvas;
	
	public cartesian_unit: number = 40; // 40 pixels per cartesian unit
	ax_tick_count: number;
	ay_tick_count: number; 
	
	constructor(cx: any, c: any) {
		this.context = cx;
		this.canvas = c;
		
		this.ax_tick_count = Math.round(c.width / this.cartesian_unit);
		this.ay_tick_count = Math.round(c.height / this.cartesian_unit);
		
		this.drawX();
		this.drawY();
	}
	
	// this is not working as expected ;
	public static getCartesianUnits() : number {
		return this.cartesian_unit;
	}
	
	public drawX() : void {
		
		var cx : any = this.context;
		var c : any  = this.canvas; 
		var tickcount : number = c.width / this.cartesian_unit; 
		var y_coord : number = this.cartesian_unit * Math.round(tickcount/2)//c.height /2;
		var x_coord : number = 0;
		var counter : number = Math.round(tickcount/2) * (-1);
		
		//cx.beginPath();
		//cx.moveTo(0,c.height/2);
		//cx.lineTo(c.width, c.height/2);
		//cx.stroke();
		
		// draw the tick marks
		
		for(var i = 0; i <= tickcount; i++){
			cx.beginPath();
			if(counter == 0){
				cx.moveTo(0,y_coord);
				cx.lineTo(c.width,y_coord);
			}
			else {
				cx.moveTo(x_coord, y_coord);
				cx.lineTo(x_coord, y_coord + 5);
			}
			cx.closePath();
			cx.stroke();
			if(counter != 0) cx.fillText(counter, x_coord - 5, y_coord + 15);
			counter++;
			x_coord += this.cartesian_unit;
		}
	}
	
	public drawY() : void {
		
		var cx : any = this.context;
		var c  : any = this.canvas;
		var tickcount : number = Math.round(c.height/this.cartesian_unit);
		var x_coord : number =  this.cartesian_unit * Math.round(tickcount/2);//c.width/2;
		var y_coord : number = 0; 
		var counter : number = Math.round(tickcount/2) * -1;	
					
		// draw the tick marks
		
		for(var i = 0; i <  tickcount; i++){	
			cx.beginPath();
			if(counter == 0){
				cx.moveTo(x_coord,0);
				cx.lineTo(x_coord,c.height);
			}
			else {
				cx.moveTo(x_coord, y_coord);
				cx.lineTo(x_coord+5, y_coord);
			}
			cx.closePath();
			cx.stroke();
			if(counter != 0) cx.fillText(counter * -1, x_coord - 15, y_coord + 5 );
			counter++;
			y_coord += this.cartesian_unit;
		}
	}
}


interface Line {
	
	x1 : number;
	y1 : number;
	x2 : number;
	y2 : number;
	pname1 : string;
	pname2 : string;
	
}

class Lines {
	
	CU = 40; // cartesian units, this needs to be refactored
	
	linearr  = new Array();
	currpos = 0;
	
	addLine(line : Line){
		this.linearr.push(line);
	}
	
	public getNext() : Line {
		var retval = this.linearr[this.currpos];
		this.currpos++;
		return retval;
	}
	
	public length(){
		return this.linearr.length;
	}	
	
	public toString() : string {
		
		var temp = "";

		for(var i = 0; i < this.linearr.length; i++){
			var x = this.linearr[i];
			temp += x.pname1 + x.pname2 + " : ";
			temp += x.x1/this.CU + " , " + x.y1/this.CU + " | " + x.x2/this.CU + " , ";
			temp += x.y2/this.CU + "<br/>";
		}
		return temp;
	}
	
}

var paper = new Paper();

</pre>

Compile the TypeScript source; **$ tsc -c MathE.ts**. The -c flag is there so that even the comments in the TypeScript source file will be emitted in resulting JavaScript file. 











