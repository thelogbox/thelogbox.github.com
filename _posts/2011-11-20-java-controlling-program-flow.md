---
layout: java

title: Control Flow

description: Branching and Looping in Java

excerpt: 

tags:
- flow
- structure
- procedural

---



Your ability to direct and command the flow of control in your program is one of the defining skills for a programmer. There are basically 3 ways that you can arrange the commands in your program code. They are;

1. You can execute commands one after another -- **sequencing**
2. You can execute certain commands when certain conditions are met -- **branching**
3. You can keep on repeating certain commands while certain conditions are still true -- **looping or iteration**


# LEARNING OBJECTIVES

- Write loops and nested loops
- Write if conditions and nested if conditions
- Identify the legal arguments that you can write inside a for loop
- Identify the legal arguments that you can write inside a while loop
- identify legal argumentns you can write inside if statements
- Use the switch statement (when possible) 

# IF statement

{% highlight java %}

if(condition) {
	statement 1;
	statement 2;
	statement n;
}

{% endhighlight %}

The *if* statement allows you to conditionally perform some commands. It allows you side-step the main flow of your code. If you remember the flowcharting symbols, when you see the diamond shape, it means you have a fork in the road. When a condition is met, you either go left or right. That is what the *if* statement does. It allows you to test for conditions. When the condition is true, you go to the beginning of the if block (the opening curly brace) and begin executing all the statements there until all the statements are exhausted. When you have reached the end of the block (the closing curly brace), then there are no more commands to execute. The flow of control will resume immediately after the end of the curly brace. 


The *condition* in the *if* statement can be written as expressions that will evaluate to either true or false. This is the most common use you will have of the if statement. On some occassions, you may see the condition written as the literals *true* or *false* &mdash; this is rare, but it will still be a legal code. 

**GOTCHA**

{% highlight java %}

int i = 0;
if(i = 1) {
	System.out.println("but i is equal to one");
}

{% endhighlight %}

If you have coded in **C** before, you might fall into this gotcha. Do not  worry though, Java will not allow you to make a mess like this. This will be caught by the compiler. 

The reason that the gotcha code above is not legal is because *i = 1* is not a boolean expression. It is an assignment operation. Java requires that the condition evaluate to either true or false.

***

You can put an if statement inside another if statement. You can in fact nest them up pretty deeply. While there is no set limit on how deep you can nest if statements, practical considerations and code readability should knock some sense into your code. 

From my experience, whenever I am treading dangerously deep into a web of if-else-if-else …  I usually take a step back and look if there are other ways of going about routing the program flow. It could be a design or analysis problem already and that using the if-else statement is not the right tool to solve the problem at hand. 

# WHILE statement

The *while* loop and *for* loop may overlap at times because they have a similar function. For a beginner, it may not be quite obvious when to use one and not the other. The basic difference of the two loops though is that;

1. Use the *while* loop if you do not know how many times you need to loop
2. Use the *for* loop if you actually know how many times you will need to go through the loop

The canonical form of the **while loop**


<pre class='codeblock'>

while(condition) {
  
	statement 1;
	statement 2;
	statement n;

}

</pre>

The *condition* is either a literal (the keywords true or false) or an expression that will evaluate to either true or false (boolean values).

The basic ideas in the while loop are the following.

1. The condition is evaluated for the first time, if the condition is true or resolves to true, then;
2. Perform statement 1, then;
3. Perform statement 2, then;
4. Perform statement n, then;
5. The program detects that we are at the end of while block (the closing curly brace is the end of the while block)
5. The program will loop back to the condition and re-evaluate it again, if it still true, then;
6. Perform statement (again)
7. rinse repeat until you get the end of the end of the block again and until you get to re-evaluate the condition (again). 

You will only drop off end of the while block if and when the condition evaluates to false. This is the reason it is best to remember that you need write code inside the while block that will make the condition false at some point in time, lest you end up in a perpetual loop.

Example code:


{% highlight java %}

    import static java.lang.System.out;

    class While {

        public static void main (String [] args){
    
            boolean condition = true;
            int counter = 0;

            while(condition) {
                out.println(counter);
                counter = counter + 1;
                if(counter >10) {
                    condition = false;
                }
            }
        }
    }

{% endhighlight %}

Like the *if* statement, you can also nest a while loop inside another while loop.

# FOR statement

{% highlight java %}

    for(beginning value; ending value; step) {
        statement 1;
        statement 2;
        statement 3;
    }

{% endhighlight %}

The *for loop* like the *while loop* allows you to iterate and perform a group of statements over and over again. The for loop though, allows for more control.  


A key concept in using the for loop is the counter (the **step**). Loop will perform all the statements inside the block for a finite and determined number of times. Each time that the whole block is evaluated, the **step** value is incremented. The incremented step value is then compared to the **ending value**, and when the ending value is reached, the for loop will then terminate. The program control will fall over to first statement immediately after the for loop block. 


In this example, we print some numeric values from zero (0) to ten (10). This is the exact thing that our *while* example was doing earlier.  


{% highlight java %}

    class for_sample {

        public static void main (String [] args) {
            for(int i=0; i<=10;i++) {
                System.out.println(i);
            }
        }

    }


{% endhighlight %}


# SWITCH statement

When the nature of the decision you need to make is a bit on the fuzzy side, it could be impractical to use the if-statement, for those kinds of decisions, you will use the switch-statement.

The syntax of the switch statement is;

{% highlight java %}

switch(expression) {
  case CONSTANTEXPR:
  case ENUMCONSTANTNAME:
  default:
}

{% endhighlight %}

Where expression can either be a char, byte, short, int OR Character, Byte, Short, Integer OR an enum type. By the way, Character is not the same as char, that wasn't a typo. Character is a Java class which is a wrapper class for the char primitive. 

Let's take a look at some sample code. The *SwitchSample.java* code extracts the *Day of Week* value from a Java Calendar object. The Day of Week is returned as integer, which makes it perfect to filter using a Switch statement rather than nested *ifs*

{% highlight java %}

import java.util.Calendar;

class SwitchSample {

	public static void main(String args[]){

		Calendar now = Calendar.getInstance();
		int dow = now.get(Calendar.DAY_OF_WEEK);

		switch(dow) {
			case 0:
				System.out.println("Sunday");
				break;
			case 1:
				System.out.println("Monday");
				break;
			case 2:
				System.out.println("Tuesday");
				break;
			case 3:
				System.out.println("Wednesday");
				break;
			case 4:
				System.out.println("Thursday");
				break;
			case 5:
				System.out.println("Friday");
				break;
			case 6:
				System.out.println("Saturday");
				break;
			default:
				System.out.println("What the value really is = " + dow);
			}
		}
}

{% endhighlight %}

The switch is really simple to use, just put the expression which you'd like to test as an argument to the switch statement, then have a series of case statements inside the switch body.

Each case statement corresponds to a value, if the value of the expression is equivalent to a case value, then instructions immediately right after the colon of the case statement will be executed/evaluated, in fact the rest of the statements will be evaluated, all the way down, until it gets to the last instruction at the bottom of the switch statement; that's not what your intention might be; that is the reason why I put a break statement. Once a case statement evaluates to true, Java blindly executes all the statements after that case, it won't even bother checking the other cases -- so note this, and be careful.

***
							
A *for loop* within another for loop is useful when you need to work with product of more than one set. That maybe a little vague, I would say -- when you need to work with Cartesian products, but I don’t think that will help the vagueness at all. Let me try again. 

Imagine the multiplication table, if we were to generate the multiplication table, the size of which is 3 rows by 5 columns, it would look like this

    
    1  2  3  4  5  6 
    2  4  6  8  10 12   
    3  6  9  12 15 18
    4  8  12 16 20 24


We all know how to do this arithmetically, but if we were to write a code for this using Java, it may stomp us for a little while. Look closely though and you will start to see a plan of attack. That is, if I write a *for loop* to walk through the values of the first column (1..6), it would look like.

{% highlight java %}

    for(int i=1; i<=6 ; i++) {
        print(i);
		}
    
{% endhighlight %}


Let’s make a minor change on the statement inside the *for loop*

{% highlight java %}

	for(int i=1; i<=6 ; i++) {
		print(i * 1);
	}	
  
{% endhighlight %}

This does not really change our output arithmetically, anything multiplied by 1 is equal to itself. This small modification though gives us further insight into our Cartesian problem and one step closer to the solution.



We can programatically increase the value of the multiplier by one, which then allows us to generate the values for the rows (2..4). We can use another loop inside the first *for loop*.


{% highlight java %}

	for(int i=col; col<=6 ; col++) {
		for(int row=1;row<=4;row++) {
			print(col*row);
		}
	}

{% endhighlight %}

## BREAK AND CONTINUE

The **break** and **continue** keywords disrupts program flow inside loops, whether the for-loop or while-loop. 

{% highlight java %}

while(condition) {
	statement 1;
	statement 2;
	break;
	statement 3;
	statement 4;
}

statement 5;
statement n;

{% endhighlight %}

The **break** statement causes the program flow inside a block to forcibly exit (whether for-loop or while-loop). In example code above, as soon as the **break** statement is encountered, the program control will ignore statement 3 and 4. The while loop will go out of scope and program control will be transferred to the first executable statement immediately after the while block -- in this case, statement 5.  

You normally will not use the **break** statement in this fashion because it doesn't make sense. This statement is usually deployed with more logic finesse. Let me show you an example.

{% highlight java %}

while(condition) {
	statement 1;
	statement 2;
	
	if(someCondition) {
		break;
	}	

	statement 3;
	statement 4;
}

statement 5;
statement n;

{% endhighlight %}

This is a more likely use of the **break** statement. I should warn you though that this is a frowned upon practice. A truly structured programming should have only one entry point and one exit point. Because of the introduction the **break** statement, our control structure now has one entry point and two exit points.  

While this code is innocent enough right now, it could get very hairy and complicated. You will appreciate following the 1-entry-1-exit rule when you have had your fair share of debugging someone else's code and you are wading through a maze of nested structures with lots of breaks peppered into the source code. 

Next is the **continue** keyword. Here is how it behaves.

{% highlight java %}

while(condition) {
	statement 1;
	statement 2;
	continue;
	statement 3;
	statement 4;
}

statement 5;
statement n;

{% endhighlight %}

When the **continue** statement is encountered, statements 3 and 4 will be ignored (just like how it was with the break). Unlike the case in **break** though, the loop will not go out of scope and will not be immediately terminated.  

What the continue statement will do is to go back to the beginning of the loop and forcibly re-evaluate condition. If the condition is still true, then the loop continues normally.  




