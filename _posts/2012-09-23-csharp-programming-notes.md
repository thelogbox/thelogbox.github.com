---
layout: csharp

title: C# Fundamentals

description: C# Language Fundamentals. Data types, Reference types, Loops and Branch

except:

tags:
- Introduction
- Language
- Fundamentals

---


## 1 Variables

Think of variables as if they are shoe boxes. You can put things inside a shoe box like a ball or paper etc. The box functions basically as a storage mechanism. And variables are exactly like that. They store things inside them so you can get them out for later use.  

At one time you can put a red ball on the shoe box. You can take it out at a later time and probably put something new, perhaps a green ball. But it has to be a ball. It can't be anything else, you can't put a pen to a box that previously held a ball. The technical reason for this constraint is called strict typing. If defined a variable to be of a specific type, it can only hold that type and nothing else.

C# variables are created by specifying the **type** of data you want it to hold, giving the variable a **name** and optionally setting it to an initial value. 

    int x = 10;

The code sample above has all the elements for a proper definition of a variable. The type is **int**, the name of the variable is **x** and we gave it an initial value of **10**. The int word has a special meaning in C#. It is a keyword or a reserved word. I did not make that up. The name **x** is made up. It could have been any other word like thisvar or thisnumber or mynumber. We can freely choose names for our variables. There are some simple rules we need to follow when naming variables, which we will discuss later.

### 1.1 Basic Data Types

You can work with a variety of data in C#. You can work with numbers, booleans and words or **Strings** just to name a few. The following table lists the available types of data in C#

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="left" />

<col  class="left" />

<col  class="left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="left">Type</th>
<th scope="col" class="left">Description</th>
<th scope="col" class="left">Range of values</th>
</tr>
</thead>

<tbody>
<tr>
<td class="left">bool</td>
<td class="left">Truthyness</td>
<td class="left">true or false</td>
</tr>


<tr>
<td class="left">byte</td>
<td class="left">8 bit unsigned integer</td>
<td class="left">0 to 255</td>
</tr>


<tr>
<td class="left">char</td>
<td class="left">16 bit Unicode character</td>
<td class="left">U +0000 to U + FFFF</td>
</tr>


<tr>
<td class="left">decimal</td>
<td class="left">128 bit precise decimal value</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">double</td>
<td class="left">64 bit double precision float point type</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">float</td>
<td class="left">32 bit single precision float point type</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">int</td>
<td class="left">32 bit signed integer</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">long</td>
<td class="left">64 bit signed integer</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">sbyte</td>
<td class="left">8 bit signed integer</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">short</td>
<td class="left">16 bit signed integer</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">uint</td>
<td class="left">32 bit unsigned integer</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">ulong</td>
<td class="left">64 bit unsigned integer</td>
<td class="left">&#xa0;</td>
</tr>


<tr>
<td class="left">ushort</td>
<td class="left">16 bit unsigned integer</td>
<td class="left">&#xa0;</td>
</tr>
</tbody>
</table>


The code snippet below shows how to declare variables of these types

    bool a = true;
    byte b = 1;
    char c = 'a';
    decimal d = 1.0m;
    double e = 1.0;
    float f = 1.0f;
    int g = 1;
    long h = 1;
    sbyte i = 1;
    short j = 1;
    uint k = 1;
    ulong l = 1;
    ushort m = 1;

Most of code sample above looks straightforward except for the declarations of **decimal** and **float**. The literal value "1.0" is actually a **double** literal hence you cannot assign a double value to a float variable because the float type is a smaller container than a double type. You will lose some data and .NET will prevent you from making silly mistakes like that. It will throw you an error if you try to assign a double value to a float variable. Hence, we needed to suffix our literal value with **f**, which means float. Does this mean we can assign a float value to a variable of type double? Yes.  

If float is smaller than a double and double is smaller than decimal, then we should be able to assign a double value to a variable of type decimal. Not quite. It is quite convenient to remember the heuristics that a small fish can be eaten by a bigger fish which can be eaten by a yet bigger fish, but unfortunately this does not always hold true, generally it does but not always. When working with values of different data types, the final arbitter is the language specification. Numeric conversions or type coercions are are predefined by C#. **This is way to deep to discuss here. Need to keep it simple**

Explicit conversions: <http://msdn.microsoft.com/en-us/library/yht2cx7b.aspx>

Implicit conversions: <http://msdn.microsoft.com/en-us/library/y5b434w4%28v=vs.80%29.aspx>

### 1.2 Strict and Static Typing

1.  TODO Additional notes

    1.  dynamic type
    2.  String type and the @ literal
    3.  and pointer types
    4.  sizeof

### 1.3 Variable naming rules

When naming your variables, just keep the following in mind. Do not:
1.  Start the name with a number
2.  Include special characters or the white space
3.  Use a word that is special or reserved

You can use the underscore or the the @ symbol as the first letter of the variable name.

### 1.4 Keywords

You don't have to memorize this right now, but in time maybe you will. For now, just don't use any of these when naming your variables

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="left" />

<col  class="left" />

<col  class="left" />

<col  class="left" />
</colgroup>
<tbody>
<tr>
<td class="left">abstract</td>
<td class="left">as</td>
<td class="left">base</td>
<td class="left">bool</td>
</tr>


<tr>
<td class="left">break</td>
<td class="left">byte</td>
<td class="left">case</td>
<td class="left">catch</td>
</tr>


<tr>
<td class="left">char</td>
<td class="left">checked</td>
<td class="left">class</td>
<td class="left">const</td>
</tr>


<tr>
<td class="left">continue</td>
<td class="left">decimal</td>
<td class="left">default</td>
<td class="left">delegate</td>
</tr>


<tr>
<td class="left">do</td>
<td class="left">double</td>
<td class="left">else</td>
<td class="left">enum</td>
</tr>


<tr>
<td class="left">event</td>
<td class="left">explicit</td>
<td class="left">extern</td>
<td class="left">false</td>
</tr>


<tr>
<td class="left">finally</td>
<td class="left">fixed</td>
<td class="left">float</td>
<td class="left">for</td>
</tr>


<tr>
<td class="left">foreach</td>
<td class="left">goto</td>
<td class="left">if</td>
<td class="left">implicit</td>
</tr>


<tr>
<td class="left">in</td>
<td class="left">in(generic modifier</td>
<td class="left">int</td>
<td class="left">interface</td>
</tr>


<tr>
<td class="left">internal</td>
<td class="left">is</td>
<td class="left">lock</td>
<td class="left">long</td>
</tr>


<tr>
<td class="left">namespace</td>
<td class="left">new</td>
<td class="left">null</td>
<td class="left">object</td>
</tr>


<tr>
<td class="left">operator</td>
<td class="left">out</td>
<td class="left">out (generic modifier)</td>
<td class="left">override</td>
</tr>


<tr>
<td class="left">params</td>
<td class="left">private</td>
<td class="left">protected</td>
<td class="left">public</td>
</tr>


<tr>
<td class="left">readonly</td>
<td class="left">ref</td>
<td class="left">return</td>
<td class="left">sbyte</td>
</tr>


<tr>
<td class="left">sealed</td>
<td class="left">short</td>
<td class="left">sizeof</td>
<td class="left">stackalloc</td>
</tr>


<tr>
<td class="left">static</td>
<td class="left">string</td>
<td class="left">struct</td>
<td class="left">switch</td>
</tr>


<tr>
<td class="left">this</td>
<td class="left">throw</td>
<td class="left">true</td>
<td class="left">try</td>
</tr>


<tr>
<td class="left">typeof</td>
<td class="left">uint</td>
<td class="left">ulong</td>
<td class="left">unchecked</td>
</tr>


<tr>
<td class="left">unsafe</td>
<td class="left">ushort</td>
<td class="left">using</td>
<td class="left">virtual</td>
</tr>


<tr>
<td class="left">void</td>
<td class="left">volatile</td>
<td class="left">while</td>
<td class="left">&#xa0;</td>
</tr>
</tbody>
</table>

The list of keywords are maintained at this page <http://msdn.microsoft.com/en-us/library/x53a06bb.aspx>. Microsoft's MSDN team does a decent job of keeping these pages updated.

## 2 Constants

Constants are placeholders, pretty much like variables, but once you define a constant, you cannot change their values at a later time. 

To declare a constant, use the **const** keyword

    const double PI = 3.14159;

### 2.1 Literals

Literals are fixed values which do not change. In that way, they seem a lot like constants

## 3 Data Types

## 4 Operators

## 5 Control Flow

Beyond the most basic programs, you will need more control in taming program flow. Non trivial programs require program flows that are beyond mere sequencing of statements. Sometimes we need to repeat some statements and sometimes we need to side step or avoid some statements. 

### 5.1 Compound statements

Whenever you see a pair of curly braces, you will usually find a group of statements inside them. That is precisely their purpose, to group statements.

    {
      /*
        Statements inside a block are executed in linear fashion.
        Start from the first statement on the top, and work
        your way down until there are no more statements
        to execute
      */
    }

A compound statement is a statement itself, you can use it whenever you can use a statement. Although you will usually see compound statements alongside flow-control keywords such as if, while, for etc.

### 5.2 If statement

Use the **if** statement when you need to execute a group of statements if a certain condition is met. This is useful in side stepping some statements in response to a certain condition that is happening in your program. The general form of the **if** statement is as follows.

    if (condition) {
      // statment to execute
      // if the condition is true
    }

The **condition** part on the code above comes in the form of equivalence expression, equality or inequality tests. Just like the ones you encountered in basic Aritmetic.

    a > 50
    b == 10
    c < 0

#### 5.2.1  Else and Else If

The if statement actually includes some optional forms, like the else if and else branches. The complete form of the if statement is as follows;

{% highlight csharp %}    

        if(condition is true){
          // statement
        }
        else if(another condition){
          // statement
        }
        else if(yet another condition){
          // statement
        }
        else if(condition_n…){
          // statement  
        }
        else {
          // statement  
        }
{% endhighlight %}

You can write as many else ifs as you need. The way this works is that, the first condition will be tested (the first if condition), if that is true, the statements inside the first if block will be performed and then the if block is exited. The other conditions stated on else ifs and else will not be executed.
    
On the other hand, if the condition stated on the first if is not true, the program flow will trickle down to the else ifs and will test each condition specified in them. If one of the conditions evaluates to true, then that else if block will be executed.
    
If none of the conditions on the if and else ifs return true, then the group of statements inside the else branch will be executed. If you did not have an else block, then none of the statements will be executed if none of the specified conditions evaluates to true.
    
        using System;
        
        class If {
          public static void Main(){
           int a = 101;
           if(a == 1){
             Console.WriteLine("One");
           }
           else if(a == 2){
             Console.WriteLine("Two");
           }
           else if(a == 101){
             Console.WriteLine("One Hundred and One");
           }
           else {
             Console.WriteLine("Clueless");
           }
          }
        }
    
In this example, “One hundred and One” will be printed.
    
        using System;
        
        class If {
          public static void Main(){
            int a = 101;
            if(a == 1){
              Console.WriteLine("One");
            }
            else if(a == 2){
              Console.WriteLine("Two");
            }
            else {
              Console.WriteLine("Clueless");
            }
          }
        }
    
The code snippet above will print "Clueless" because there are no conditions that evaluate to true.
    
        using System;
        
        class If {
          
          public static void Main(){
            
            int a = 101;
            
            if(a == 1){
              Console.WriteLine("One");
            }
            else if(a == 2){
              Console.WriteLine("Two");
            }
          }
        }
    
The code snippet above will not do anything. It will not print anything because none of the conditions evaluated to true, and there is no else branch.


### 5.3 Switch statement

The switch statement is another branching mechanism. It passes control though each case statement inside the switch block. The case statement expects a constant value, so you cannot do something like case == 1. See the example code for more info.

    using System;
    
    class Switch {  
      public static void Main(){
        int a = 3;
        switch(a){
          case 1:
            Console.WriteLine("One");
            break;
          case 2:
            Console.WriteLine("Two");
            break;
          case 3:
            Console.WriteLine("Three");
            break;
          default:
            Console.WriteLine("Default");
            break;
        } 
      }
    }

Why is there a break statement inside each case–because withou the break statement, the flow of control will cascade to the next case or default statement–that is not what you want. As a matter of exercise, try removing the break on the case statements and see what happens.

The switch can also handle string arguments, not only integers.

    using System;
    
    class Switch {
      public static void Main(){    
        string a = "1";
        
        switch(a){
          case "1":
            Console.WriteLine("One");
            break;
          case "2":
            Console.WriteLine("Two");
            break;
          case "3":
            Console.WriteLine("Three");
            break;
          default:
            Console.WriteLine("Default");
            break;
        } 
      }
    }

### 5.4 While statement

A looping mechanism. Use this if you would like to perform a group of statements repeatedly. General format is while(expression) statement – if you need to execute more than one statmeent, use the curly braces to group the statements.

    using System;
    
    class While {
      
      public static void Main(){
        
        int a = 0;
        
        while(a < 10){
          Console.WriteLine("Value of a = " + a++);
        }
        
      }
    }

The expression a++ is syntactically equivalent to a = a + 1, it simply adds one to current value of **a**.

### 5.5 For statement

The for loop is doing what the while loop is doing as well, it executes a group of statement repeatedly. The format of the for loop is a bit more involved though. The for loop has three (optional) arguments inside it. The arguments, if you provide it, changes the behavior of the for loop.

Let’s rewrite the while loop example using the for loop.

    using System;
    
    class ForLoop {
    
      public static void Main(){
        for(int a = 0; a < 10 ; a++){
          Console.WriteLine("Value of a = " + a);
        }   
      }
    }

Take a closer look at the form of the for-loop, it is actually like this; for(initializer ; condition ; iterator) statement.

1.  **initializer** - sets the initial value of a counter, in our sample, this counter is the variable a
2.  **condition** - you have to stop somewhere, other wise you will have a loop that doesn’t terminate. This is an expresion that evaluates to a boolean value. While this expression evaluates to true, the statement inside the body for-loop will keep on executing. When this expression evaluates to false, the loop terminates.
3.  **iterator** - this expression defines what happens after each iteration of the loop, this is typically used to either increment or decrement a counter variable, but you can get creative with it

The **initializer** and **iterator** arguments of the for loop takes more than one value, you just need to separate them with commas. As a beginning programmer though, you probably would have a less easy time making sense of convoluted codes like that, but just to show what else you can do with for-loops, take a look at the following code.

    using System;
    
    class ForLoop {
      public static void Main(){
        for(int a = 0, b = 10; a < 10 ; a++, b--, foo()){
          Console.WriteLine("Value of a, b = " + a + " , " + b);
          }   
        }
      
      static void foo(){
        Console.WriteLine("Foo");
      }
    }

In this sample code, two variables (a and b) were initialized. Variable a was set to 0 and variable b was set to 10, they are just separated by commas (not semi colon). In the iterator part of the loop, variable a is incremented by 1 and variable b is decremented by 1—not only that, you can also insert function calls in the iterator section, just like what we did in this sample code. Each time the for-loop iterates, function foo() is called.

### 5.6 Nesting

You can write loops inside other loops, ifs inside other ifs, switches inside ifs or whatever combination you can imagine (or need). Here is an example of a for-loop nested inside a for-loop.

    using System;
    
    class ForLoop {
    
      public static void Main(){
    
        for(int i = 1; i <= 5; i++){
          for(int j = 1; j <= 5; j++){
            Console.WriteLine("values of i and j are {0} {1}", i,j);
          }
        }   
      }
        
    }
    
    /*
    
    the above code produces the output
    
    values of i and j are 1 1
    values of i and j are 1 2
    values of i and j are 1 3
    values of i and j are 1 4
    values of i and j are 1 5
    values of i and j are 2 1
    values of i and j are 2 2
    values of i and j are 2 3
    values of i and j are 2 4
    values of i and j are 2 5
    values of i and j are 3 1
    values of i and j are 3 2
    values of i and j are 3 3
    values of i and j are 3 4
    values of i and j are 3 5
    values of i and j are 4 1
    values of i and j are 4 2
    values of i and j are 4 3
    values of i and j are 4 4
    values of i and j are 4 5
    values of i and j are 5 1
    values of i and j are 5 2
    values of i and j are 5 3
    values of i and j are 5 4
    values of i and j are 5 5
    
    */

The outer loop counts from 1 to 5 using the iterator (variable) i, the inner loop counts from 1 to 5 also. This kind of program produces what you might call a cartesian product. Notice how the variable i is printed 5 times–i is printed for each iteration of j. That is the reason why you have 25 rows of output; i iterates up to 5 and j iterates up to 5 also (5 \* 5 = 25).

NOTE : - The curly braces inside the string is called a formatter, it is somewhat similar to the sprintf of the C language—but you haven’t coded in C, which means you will need some more explanation and examples;

    int a = 10;
    int b = 20;
    
    Console.WriteLine("The value of a is {0}", a);
    // the actual value of the variable a will be substituted to {0}
    
    Console.WriteLine("a is {0} and b is {1}",a,b);
    //value of a will be substituted to {0}, and value of b will be subsituted to {1}
    //0 corresponds to the first actual number right after the string, and 1 to next, so on
    // and so forth. 0 and 1 are actually positional values of the arguments that follow
    // string

You can generate the multiplication table using nested loops, like the code snippet below

    using System;
    
    class ForLoop {
    
      public static void Main(){
    
        for(int i = 1; i <= 5; i++){
          for(int j = 1; j <= 5; j++){
            Console.Write(i * j + "\t");
          }
          Console.WriteLine();
        }   
      }
        
    }
    
    /*
    
    1 2 3 4 5 
    2 4 6 8 10  
    3 6 9 12  15  
    4 8 12  16  20  
    5 10  15  20  25
    
    */

The **\t** escape sequence is to simply add a tab in between the numbers. I used Console.Write so that the line won’t add a carriage return/line feed after every number. I needed the CRLF at the end of the row, that is the reason why there is an empty WriteLine outside the inner loop.


## Bibliography

1. Title: Inside C#. Author: Tom Archer, Publisher: Microsoft Press 2001
2. Title: Real World Functional Programming with examples in F# and C#. Authors: Thomas Petricek with John Skeet, Publisher: Manning Publications 2010



