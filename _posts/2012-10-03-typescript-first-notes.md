---
layout: post

title: TypeScript

description: 

excerpt: 

categories:
- blog

---

Official website is at [TypeScriptLang.org](http://www.typescriptlang.org). The language was borne out of Microsoft. It looks a lot like JavaScript, because it is a superset of JavaScript;  This means all existing, valid and native JavaScript codes are already valid TypeScript codes. 


# INFO

1. licensed under Apache 2.0
2. Anders Hejlsberg is responsible for it. He gave us C#, before that he wrote Pascal compilers which got him hitched with Borland (Turbo Pascal) 
3. typescript an be installed in lots of ways - via **npm -g install typescript**, or as a Visual Studio plugin. You can also get the source via **git clone https://git01.codeplex.com/typescript** 
4. the anguage specification (currently v .08) is only 97 pages (in PDF). There is no excuse not to read it 


# WORKFLOW

1. Create a source file with a *.ts* file extension
2. Compile the .ts file using *tsc* (typescript compiler)
3. Use the emitted JavaScript code any which way you need
4. Go through your testing motions
5. Rinse, repeat 


# SETUP

Get the compiler, either via npm (Node Package Manager) or Visual Studio Plugin or via sourcecode

Make sure your environment is setup properly. Try out the **tsc** command on a terminal window (cmd.exe in Windows, Terminal.app in OSX or xterm, gnome-terminal on Linux); you should get something like this;

<pre class="codeblock">

$ tsc
Syntax:   tsc [options] [file ..]

Examples: tsc hello.ts
          tsc --out foo.js foo.ts
          tsc @args.txt

Options:
  -c, --comments  Emit comments to output
  --declarations  Generates corresponding .d.ts file
  -e, --exec      Execute the script after compilation
  -h, --help      Print this message
  --module KIND   Specify module code generation: "commonjs" (default) or "amd"
  --nolib         Do not include a default lib.d.ts with global declarations
  --out FILE      Concatenate and emit output to single file
  --target VER    Specify ECMAScript target version: "ES3" (default), or "ES5"
  -w, --watch     Watch output files
  @<file>         Insert command line options and files from a file.

</pre>


Try out the **greeter.ts** sample in [typelang.org/tutorial](http://www.typescriptlang.org/Tutorial/) 

If you are using TextMate in OSX, it won't know how to handle .ts files, so when you see the "Recommended Grammars" dialog box, just use JavaScript.  

***

The "Hello World" test

{% highlight javascript %}

// filename: Hello.ts

function Hello(args) {
    console.log("Hello " + args);
    return 0;
}
Hello("John");

{% endhighlight %}

Compile it using **tsc Hello.ts**, it will emit exactly the same code in JavaScript. It's supposed to happen because TypeScript is a superset of JavaScript. A (valid) existing JavaScript code should compile cleanly using TypeScript compiler.

{% highlight javascript %}

function Hello(args) {
    console.log("Hello " + args);
    return 0;
}
Hello("John");

{% endhighlight %}

You can run the resulting **.js** code either via *node Hello.js* or ***js Hello.js** if you have it setup on your machine.

To test the syntactic sugar, add a bit of type checking, modify Hello.ts like this

{% highlight javascript %}

function Hello(args: string) : number {
	console.log("Hello " + args);
}

Hello("John");

{% endhighlight %}

If you try **tsc Hello.ts** again, you will get and error like *Function declared a non-void return type, but has no return expression*. The reason for that is because we added a type-checking information on both the *args* variable and the our function itself. **args : string** means that args needs to be a string and that function Hello should return a number. The type checking is done on compile time, not runtime. 


# CODING NOTES


## CLASS CONSTRUCTION

Trying out the class and interface facilities of TypeScript

{% highlight javascript %}

//BoxSample.ts

interface IBox {
	
	x : number;
	y : number;
	height : number;
	width : number;
	
}

class Box {
	
	public x: number;
	public y: number;
	public height: number;
	public width: number;
	
	public setDim(obj: IBox){
		
		this.x = obj.x;
		this.y = obj.y;
		this.height = obj.height;
		this.width = obj.width;
	
	}	
}

var b = new Box();
var a = new Box();

a.setDim({x:0,y:0,width:10, height:10});
b.setDim({x:1,y:1,width:10, height:10});

console.log(b.constructor);
console.log(typeof b);

console.log(b.x);
console.log(b.y);

console.log(a.x);
console.log(a.y);

/*

compile using;

	tsc BoxSample.ts

outputs;

	BoxSample.js

*/

//BoxSample.js

var Box = (function () {
    function Box() { }
    Box.prototype.setDim = function (obj) {
        this.x = obj.x;
        this.y = obj.y;
        this.height = obj.height;
        this.width = obj.width;
    };
    return Box;
})();
var b = new Box();
var a = new Box();
a.setDim({
    x: 0,
    y: 0,
    width: 10,
    height: 10
});
b.setDim({
    x: 1,
    y: 1,
    width: 10,
    height: 10
});
console.log(b.constructor);
console.log(typeof b);
console.log(b.x);
console.log(b.y);
console.log(a.x);
console.log(a.y);

{% endhighlight %}

The TypeScript version does look a lot cleaner, looks like it really has potential. Just a bunch of things to remember initially;

**1.** TS adds static type checking, so the general form is **variable name [ : type ]**. It seems I can use **string, bool and number** for static type checking. In the language spec of TypeScript, there was also a mention of the **any** type, which can stand for either *bool, string, number and undefined**. If I use the **any** type though, I lose the static type checking that TS performs, I probably should not do it, since I like type checking. 

**2.** There is an **implements** keyword supported for class constructs, so I could have written the example as

{% highlight javascript %}

interface IBox {
	// …
}

class Box implements {
	// class body
}

{% endhighlight %}

It doesn't seem like I needed it though (note to self => read the spec over and over again to find out why). 

## INHERITANCE AND POLYMORPHISM

{% highlight javascript %}

class Shape {
	
	mname: string = "default name";
		
	getName() {
		return name;
	}
	
	setName(val : string) {
		this.mname = val;
	}
	
	draw() {
		console.log("drawing Shape");
	}
	
}

class Circle : Shape {
	
	draw(){
		console.log("Drawing Circle");
	}

}


var a = new Shape();
var b = new Circle();
b.setName("the circle");

console.log(a.mname);
console.log(b.mname);

a.draw();
b.draw();

{% endhighlight %}

Inheritance works as expected, no big surprises. TypeScript uses the **extends** keyword to denote both class and interface inheritance. One thing I noticed though is that if you replace the *extends** keyword with a colon (pretty much like in CSharp), it seems to have the same effect as **extends** too&mdash;but better stick with *extends*, that is what the lang spec specifies for inheritance anyway.

The rule is pretty basic on inheritance. Everything that on the base class that is defined to have **public** access is automatically inherited on the derived class. That is why the *Circle* type has a **setName() and getName()** method, they were inherited from *Shape*.  

Override works as expected also, just redefine the method on the the derived class and the method becomes polymorphic 

## SUPER

**super** refers to an instance of the super class or the parent class. Old hands of Java, CSharp, C++ should not be surprised, the super behaves as expected. 

{% highlight javascript %}

class Base {
	
	foo(){
		console.log("base::foo");
	}
	
	constructor(){
		console.log("base::ctor");
	}
	
}

class Derived extends Base {
	
	foo(){
		super.foo();
		console.log("derived::foo");
	}
	
	constructor(){
		super();
		console.log("derived::ctor");
	}	
}

var a = new Derived();
a.foo();

{% endhighlight %}

## OPTIONAL ARGUMENTS TO FUNCTIONS

Two ways to do optional parameters/arguments. 1) You can add a question mark right after the argument name, or 2) you can provide a default value for the argument. The constructor of class Square below uses method #2 and class Circle uses method #1 

{% highlight javascript %}

class Square {
	
	pname: string;
	pcolor: string;
	
	constructor(mname? :string , mcolor? : string){
		if(!mname) { this.pname = "empty";}
		else {
			this.pname = mname;
		}
		
		if(!mcolor) {this.pcolor = "empty";}
		else {
			this.pcolor = mcolor;
		}
	}
}

class Circle {

	pname: string;
	pcolor: string;

	constructor(mname = "def name" , mcolor = "black"){
		this.pname = mname;
		this.pcolor = mcolor;
	}
}

var c = new Circle();
console.log(c.pcolor);
console.log(c.pname);

var s = new Square();
console.log(s.pcolor);
console.log(s.pname);

var s2 = new Square("new square","red");
console.log(s2.pcolor);
console.log(s2.pname);

{% endhighlight %}


## Overloading

Don't get too excited yet about overloading, it's not like C# or Java (yet, I hope)

{% highlight javascript %}

class Line {

	
	x: number;
	y: number;
	
	width: number;
	height: number;
	
	/*
	
	this does not work, if you vary the number of arguments on the overload
	declarations, it throws a compile error

	constructor();
	constructor(x:number, y:number);
	
	*/


	constructor(dim: {x:number; y:number; width:number; height:number;}){
	
		this.x = dim.x;
		this.y = dim.y;
		this.width = dim.width;
		this.height = dim.width;
	
	}
	
	/*

	The overloaded forms of foo() is accepted because I only varied the type of x.		

	*/

	foo(x:number);
	foo(x:string);
	foo(x:any){
		
	}
		
}

{% endhighlight %}

You can have multiple declarations of method, but only one of them can have an implmentation. Also, you cannot vary the number of arguments in the method.


## ARROW EXPRESSIONS

This looks purely like syntactic sugar, but just the same, note it. The **() => {}** notation was added so that you don't have to say **function() {}** &mdash; this reminds me of CoffeeScript though. 

{% highlight javascript %}

var box = {
	
	mname: "Hello Box",
	goo: () => {
		console.log("Hello Goo");
	}
	
}

box.goo();

{% endhighlight %}



1. TS looks usable if you want to add some OO organization to your code; CoffeeScript will do that for you too, so it comes down to a choice whether you like the Ruby syntax or JavaScript 
2. TS is not a replacement for JavaScript. You need to know JavaScript first before you can move conveniently in TypeScript &mdash; after all, TypeScript is a superset of JavaScript
3. You need a basic understanding of classical OO (Object Oriented) concepts before you can use the class abstractions of TypeScript. C#, Java and C++ programmers should be right at home
4. Classical JavaScript and TypeScript syntax can be mashup-ed, it's up to you &mdash; but I found it confusing, I think this is where coding practices and conventions can help a lot
5. Type checking is a relief, I like that a lot &mdash; this is probably due to my experience bias (statically typed languages) 



















