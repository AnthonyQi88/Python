# Crash Course On Python - Google IT Automation with Python

## Useful links
Below, you’ll find links to some of the most popular online interpreters and codepads. Give them a go to find your favorite.

https://www.python.org/shell/
https://www.onlinegdb.com/online_python_interpreter
https://repl.it/languages/python3
https://www.tutorialspoint.com/execute_python3_online.php
https://rextester.com/l/python3_online_compiler
https://trinket.io/python3
Additional Python resources
While this course will give you information about how Python works and how to write scripts in Python, you’ll likely want to find out more about specific parts of the language. Here are some great ways to help you find additional info: 

Read the official Python documentation.
Search for answers or ask a question on Stack Overflow. 
Subscribe to the Python tutor mailing list, where you can ask questions and collaborate with other Python learners.
Subscribe to the Python-announce mailing list to read about the latest updates in the language.



## Arithmetic operators
Python can operate with numbers using the usual mathematical operators, and some special operators, too. These are all of them.

a + b = Adds a and b
a - b = Subtracts b from a
a * b = Multiplies a and b
a / b = Divides a by b
a ** b = Elevates a to the power of b. For non integer values of b, this becomes a root (i.e. a**(1/2) is the square root of a)
a // b = The integer part of the integer division of a by b
a % b = The remainder part of the integer division of a by b


## Comparison Operators
In Python, we can use comparison operators to compare values. When a comparison is made, Python returns a boolean result, or simply a True or False. 

To check if two values are the same, we can use the equality operator: == 
To check if two values are not the same, we can use the not equals operator: != 
We can also check if values are greater than or lesser than each other using > and <. If you try to compare data types that aren’t compatible, like checking if a string is greater than an integer, Python will throw a TypeError. 

We can make very complex comparisons by joining statements together using logical operators with our comparison operators. These logical operators are and, or, and not. When using the and operator, both sides of the statement being evaluated must be true for the whole statement to be true. When using the or operator, if either side of the comparison is true, then the whole statement is true. Lastly, the not operator simply inverts the value of the statement immediately following it. So if a statement evaluates to True, and we put the not operator in front of it, it would become False.


## Conditionals Cheat Sheet
In earlier videos, we took a look at some of the built-in Python operators that allow us to compare values, and some logical operators we can use to combine values. We also learned how to use operators in if-else-elif blocks. 

It’s a lot to learn but, with practice, it gets easier to remember it all. In the meantime, this handy cheat sheet gives you all the information you need at a glance. 

Comparison operators
a == b: a is equal to b
a != b: a is different than b
a < b: a is smaller than b
a <= b: a is smaller or equal to b
a > b: a is bigger than b
a >= b: a is bigger or equal to b
Logical operators
a and b: True if both a and b are True. False otherwise.
a or b: True if either a or b or both are True. False if both are False.
not a: True if a is False, False if a is True.


## Loops Cheat Sheet
Check out below for a run down of the syntax for while loops and for loops.

While Loops
A while loop executes the body of the loop while the condition remains True.

Syntax:

'''
while condition:
    body
Things to watch out for!
'''
Failure to initialize variables. Make sure all the variables used in the loop’s condition  are initialized before the loop.
Unintended infinite loops. Make sure that the body of the loop modifies the variables used in the condition, so that the loop will eventually end for all possible values of the variables.
 Typical use:

While loops are mostly used when there’s an unknown number of operations to be performed, and a condition needs to be checked at each iteration.

For Loops
A for loop iterates over a sequence of elements, executing the body of the loop for each element in the sequence.

Syntax:

12
for variable in sequence
    body
The range() function:

range() generates a sequence of integer numbers. It can take one, two, or three parameters:

range(n): 0, 1, 2, ... n-1
range(x,y): x, x+1, x+2, ... y-1
range(p,q,r): p, p+r, p+2r, p+3r, ... q-1 (if it's a valid increment)
Common pitfalls:

Forgetting that the upper limit of a range() isn’t included.
Iterating over non-sequences. Integer numbers aren’t iterable. Strings are iterable letter by letter, but that might not be what you want.
Typical use:

For loops are mostly used when there's a pre-defined sequence or range of numbers to iterate.

Break & Continue
You can interrupt both while and for loops using the break keyword. We normally do this to interrupt a cycle due to a separate condition.

You can use the continue keyword to skip the current iteration and continue with the next one. This is typically used to jump ahead when some of the elements of the sequence aren’t relevant.

If you want to learn more, check out this wiki page on for loops.
