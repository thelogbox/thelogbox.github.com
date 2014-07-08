---
layout: post

title: Workbook on Programming Concepts

description: Exercise problems for the beginning Java programmer

excerpt: 

tags:
- Exercises

---



## Part 1. Machine problems

**Problem 1.** Given a String name, e.g. "John", return a greeting of the form "Hello Bob!". 

helloName("John") -> "Hello Bob!"

helloName("Alice") -> "Hello Alice!"

helloName("X") -> "Hello X!"

{% highlight java %}

class One {

	public static void main(String[] args) {
		hello("John");
	}
	
	private static void hello(String var){
		//Write your code here
	}
}

{% endhighlight %}

**Problem 2.** Given two strings, a and b, return the result of concatenating them. e.g., "Hello" and "World" returns "HelloWorld"

{% highlight java %}

//Two.java 
//Item # 2 Java Programming Workbook

class Two {

	public static void main(String[] args) {
		bang("Hello", "World");
	}
	
	private static void bang(String a, String b){
		//Write your code here
	}
}

{% endhighlight %}

**Problem 2.1** Make some modifications to Two.java such that it returns "Hello World" with a space in between.

**Problem 2.2** Make some modifications to Two.java such that it returns 

"Hello
Java"

Insert a CRLF (Carriage Return Linefeed) after the String "Hello"

**Problem 2.3** Still following the principle of item 2 above, given two strings, a and b, return the result of putting them together in the order abba, e.g. "Hi" and "Bye" returns "HiByeByeHi". 

bang("Hi", "Bye") -> "HiByeByeHi"

bang("Yo", "Alice") -> "YoAliceAliceYo"

bang("x", "y") -> "xyyx"

**Problem 3.** Print out the multiplication table (5 columns and 5 rows)

{% highlight java %}

//Three.java 
//Item # 3 Java Programming Workbook

class Three {

	public static void main(String[] args) {
		printmult();
	}
	
	private static void printmult(){
		//write your code here	
	}
}

{% endhighlight %}

**Problem 3.1** Modify Three.java such that you can pass two integers are parameters *printmult(int row, int col)* to make the size of the multiplication table dynamic.


**Problem 4.** Find the GCD (greatest common factor) of 15 and 12 using Euclid's algorithm. You need to research this one. There is no need to provide a skeleton code because you can write the entire solution inside *public static void main()*

**Problem 4.1**  Do this program in GUI using javax.swing. Use TextFields to input the number. Use a button to start the calculation. Use the JDialog to output the result

**Problem 5.** Consider a string, return a string where for every letter in the original, the letter will be printed twice 

twice("The") -> "TThhee"

twice("AAbb") -> "AAAAbbbb"

twice("Hi-There") -> "HHii--TThheerree"

**Problem 6.** Create a function that will take a String and prints out the String in reverse. e.g. "Hello" --> outputs "olleH"

**Problem 6.1.** Now, check to see if the String is a palindrome. A palindrome is a word(s) which is spelled exactly the same whether read backwards or forward. If it is palindome, output should be e.g. "madamimadam is a palindrome" 

**Problem 6.2** Create this function using javax.swing, create a textfield for the user to input the string and a button. When the button is pressed, run your algorithm. Use the JDialog to output the results

**Problem 7.** Write a program that counts from 1..10,000. Process each number. If the number is even, print out if it is even. e.g. "2 is even", "3 is odd"

**Problem 7.2** Find the sum of all even numbers below 5,000, print it out

**Problem 7.3** Revise the program, if the number is a multiple of 3, print out "Crunch", if it is a multiple of 5, print out "Bang". If the number if both a multiple of 3 and 5, print out "!#"

**Problem 7.4** Revise the program, as the program is counting from 1..10,000; check to see if the number is a palindrome, if it is, print it out, if not, ignore it

**Problem 7.5** continuing from 7.4, find the sum of all palindromic numbers  in the series 1..10,000

**Problem 7.6** Revise the program. Now, add all the numbers below 1000, that are multiples of 3 or 5. Print out the sum

**Problem 8.** Write a program that will print out the following;

<pre class='codeblock'>

*
* *
* * *
* * * *
* * * * * 
* * * * * * 
*  * * * * * *

</pre>

Use either a for loop or a while loop

**Problem 9.** Write a program that will print out the following;

<pre class='codeblock'>

 1 
 1 1 
 1 2 1 
 1 3 3 1 
 1 4 6 4 1 
 1 5 10 10 5 1 
 1 6 15 20 15 6 1 
 1 7 21 35 35 21 7 1 

</pre>

**Problem 10.** Create a function that takes in two java.util.Date parameters, return the difference in terms of number of days 

**Problem 11.** Create a database driven GUI application (todo list) that keeps the following data points;

- todo item (string)
- date created (date)
- status (string) 

The application should also be able to display the list of all todo items in a separate window.


## Part 2. Self check questions

**Question 1)**

Which of the following lines will compile without warning or error.

1) float f=1.3; 

2) char c="a"; 

3) byte b=257; 

4) boolean b=null; 

5) int i=10; 

**Question 2)**

What will happen if you try to compile and run the following code

{% highlight java %}

public class MyClass {
    public static void main(String arguments[]) {
	amethod(arguments);
    }
    public void amethod(String[] arguments) {
	System.out.println(arguments);
	System.out.println(arguments[1]);
    }
}

{% endhighlight %}

1. error Can't make static reference to void amethod. 
2. error method main not correct 
3. error array must include parameter 
4. amethod must be declared with String

**Question 3)**

Which of the following will compile without error

1)

import java.awt.*;
package Mypackage;
class Myclass {}

2)

package MyPackage;
import java.awt.*;
class MyClass{}

3)

{% highlight java %}

/*This is a comment */

package MyPackage;
import java.awt.*;
class MyClass{}

{% endhighlight %}

**Question 4)**

Which of the following are keywords or reserved words in Java?

1. if 
2. then 
3. goto 
4. while 
5. case


**Question 5)**

What will happen when you compile and run the following code? 
 

{% highlight java %}

public class MyClass{
 static int i;
 public static void main(String argv[]){
 System.out.println(i);
 }
}

{% endhighlight %}

1. Error Variable i may not have been initialized 
2. null 
3. 1 
4. 0

**Question 6.**

What is the difference between a constructor and a method

**Question 7.**

What are access modifiers in Java?


**Question 8.**

What is the difference between method overloading and method overriding


**Question 9.**

What is the difference betwen abstract class and interface 


**Question 10.**

What is the difference between a non-static variable and a static variable?