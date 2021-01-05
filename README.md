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


## Additional Recursion Sources
In the past videos, we visited the basic concepts of recursive functions.

A recursive function must include a recursive case and base case. The recursive case calls the function again, with a different value. The base case returns a value without calling the same function.

A recursive function will usually have this structure:

1234
def recursive_function(parameters):
    if base_case_condition(parameters):
        return base_case_value
    recursive_function(modified_parameters)
For more information on recursion, check out these resources:

Wikipedia Recursion page
See what happens when you Search Google for Recursion

## Advanced String Methods
We've covered a bunch of String class methods already, so let's keep building on those and run down some more advanced methods.

The string method lower will return the string with all characters changed to lowercase. The inverse of this is the upper method, which will return the string all in uppercase. Just like with previous methods, we call these on a string using dot notation, like "this is a string".upper(). This would return the string "THIS IS A STRING". This can be super handy when checking user input, since someone might type in all lowercase, all uppercase, or even a mixture of cases.

You can use the strip method to remove surrounding whitespace from a string. Whitespace includes spaces, tabs, and newline characters. You can also use the methods  lstrip and rstrip to remove whitespace only from the left or the right side of the string, respectively.

The method count can be used to return the number of times a substring appears in a string. This can be handy for finding out how many characters appear in a string, or counting the number of times a certain word appears in a sentence or paragraph.

If you wanted to check if a string ends with a given substring, you can use the method endswith. This will return True if the substring is found at the end of the string, and False if not.

The isnumeric method can check if a string is composed of only numbers. If the string contains only numbers, this method will return True. We can use this to check if a string contains numbers before passing the string to the int() function to convert it to an integer, avoiding an error. Useful!

We took a look at string concatenation using the plus sign, earlier. We can also use the join method to concatenate strings. This method is called on a string that will be used to join a list of strings. The method takes a list of strings to be joined as a parameter, and returns a new string composed of each of the strings from our list joined using the initial string. For example, " ".join(["This","is","a","sentence"]) would return the string "This is a sentence".

The inverse of the join method is the split method. This allows us to split a string into a list of strings. By default, it splits by any whitespace characters. You can also split by any other characters by passing a parameter.

## String Formatting
You can use the format method on strings to concatenate and format strings in all kinds of powerful ways. To do this, create a string containing curly brackets, {}, as a placeholder, to be replaced. Then call the format method on the string using .format() and pass variables as parameters. The variables passed to the method will then be used to replace the curly bracket placeholders. This method automatically handles any conversion between data types for us. 

If the curly brackets are empty, they’ll be populated with the variables passed in the order in which they're passed. However, you can put certain expressions inside the curly brackets to do even more powerful string formatting operations. You can put the name of a variable into the curly brackets, then use the names in the parameters. This allows for more easily readable code, and for more flexibility with the order of variables.

You can also put a formatting expression inside the curly brackets, which lets you alter the way the string is formatted. For example, the formatting expression {:.2f} means that you’d format this as a float number, with two digits after the decimal dot. The colon acts as a separator from the field name, if you had specified one. You can also specify text alignment using the greater than operator: >. For example, the expression {:>3.2f} would align the text three spaces to the right, as well as specify a float number with two decimal places. String formatting can be very handy for outputting easy-to-read textual output.


## String Reference Cheat Sheet

String Reference Cheat Sheet
In Python, there are a lot of things you can do with strings. In this cheat sheet, you’ll find the most common string operations and string methods.

String operations
* len(string) Returns the length of the string
* for character in string Iterates over each character in the string
* if substring in string Checks whether the substring is part of the string
* string[i] Accesses the character at index i of the string, starting at zero
* string[i:j] Accesses the substring starting at index i, ending at index j-1. If i is omitted, it's 0 by default. If j is omitted, it's len(string) by default.

String methods
* string.lower() / string.upper() Returns a copy of the string with all lower / upper case characters
* string.lstrip() / string.rstrip() / string.strip() Returns a copy of the string without left / right / left or right whitespace
* string.count(substring) Returns the number of times substring is present in the string
* string.isnumeric() Returns True if there are only numeric characters in the string. If not, returns False.
* string.isalpha() Returns True if there are only alphabetic characters in the string. If not, returns False.
* string.split() / string.split(delimiter) Returns a list of substrings that were separated by whitespace / delimiter
* string.replace(old, new) Returns a new string where all occurrences of old have been replaced by new.
* delimiter.join(list of strings) Returns a new string with all the strings joined by the delimiter 
Check out the official documentation for all available String methods.  



## Formatting Strings Cheat Sheet
Python offers different ways to format strings. In the video, we explained the format() method. In this reading, we'll highlight three different ways of formatting strings. For this course you only need to know the format() method. But on the internet, you might find any of the three, so it's a good idea to know that the others exist.

Using the format() method
The format method returns a copy of the string where the {} placeholders have been replaced with the values of the variables. These variables are converted to strings if they weren't strings already. Empty placeholders are replaced by the variables passed to format in the same order.

```python
# "base string with {} placeholders".format(variables)

example = "format() method"

formatted_string = "this is an example of using the {} on a string".format(example)

print(formatted_string)

"""Outputs:
this is an example of using the format() method on a string
```
If the placeholders indicate a number, they’re replaced by the variable corresponding to that order (starting at zero).
```python
# "{0} {1}".format(first, second)

first = "apple"
second = "banana"
third = "carrot"

formatted_string = "{0} {2} {1}".format(first, second, third)

print(formatted_string)
"""Outputs:
apple carrot banana
"""
```
If the placeholders indicate a field name, they’re replaced by the variable corresponding to that field name. This means that parameters to format need to be passed indicating the field name.

```python
# "{var1} {var2}".format(var1=value1, var2=value2)
```
```python
"{:exp1} {:exp2}".format(value1, value2)
```
If the placeholders include a colon, what comes after the colon is a formatting expression. See below for the expression reference.

Official documentation for the format string syntax

```python
# {:d} integer value
'{:d}'.format(10.5) → '10'
```
Formatting expressions
Expr|Meaning|Example
---|---|---
{:d}|integer value|'{:d}'.format(10.5) → '10'
{:.2f}	|floating point with that many decimals	|'{:.2f}'.format(0.5) → '0.50'
{:.2s}	|string with that many characters	|'{:.2s}'.format('Python') → 'Py'
{:<6s}	|string aligned to the left that many spaces	|'{:<6s}'.format('Py') → 'Py    '
{:>6s}	|string aligned to the right that many spaces	|'{:>6s}'.format('Py') → '    Py'
{:^6s}	|string centered in that many spaces	|'{:^6s}'.format('Py') → '  Py  '

Check out the official documentation for all available expressions.

Old string formatting (Optional)
The format() method was introduced in Python 2.6. Before that, the % (modulo) operator could be used to get a similar result. While this method is no longer recommended for new code, you might come across it in someone else's code. This is what it looks like:

 "base string with %s placeholder" % variable

The % (modulo) operator returns a copy of the string where the placeholders indicated by %  followed by a formatting expression are replaced by the variables after the operator.

 "base string with %d and %d placeholders" % (value1, value2)

To replace more than one value, the values need to be written between parentheses. The formatting expression needs to match the value type.

 

"%(var1) %(var2)" % {var1:value1, var2:value2}

Variables can be replaced by name using a dictionary syntax (we’ll learn about dictionaries in an upcoming video).

 

"Item: %s - Amount: %d - Price: %.2f" % (item, amount, price)

The formatting expressions are mostly the same as those of the format() method. 

Check out the official documentation for old string formatting.

Formatted string literals (Optional)
This feature was added in Python 3.6 and isn’t used a lot yet. Again, it's included here in case you run into it in the future, but it's not needed for this or any upcoming courses.

A formatted string literal or f-string is a string that starts with 'f' or 'F' before the quotes. These strings might contain {} placeholders using expressions like the ones used for format method strings.

The important difference with the format method is that it takes the value of the variables from the current context, instead of taking the values from parameters.

 Examples:

>>> name = "Micah"

>>> print(f'Hello {name}')

Hello Micah

 

>>> item = "Purple Cup"

>>> amount = 5

>>> price = amount * 3.25

>>> print(f'Item: {item} - Amount: {amount} - Price: {price:.2f}')

Item: Purple Cup - Amount: 5 - Price: 16.25

 Check out the official documentation for f-strings.


## Lists Defined
Lists in Python are defined using square brackets, with the elements stored in the list separated by commas: list = ["This", "is", "a", "list"]. You can use the len() function to return the number of elements in a list: len(list) would return 4. You can also use the in keyword to check if a list contains a certain element. If the element is present, it will return a True boolean. If the element is not found in the list, it will return False. For example, "This" in list would return True in our example. Similar to strings, lists can also use indexing to access specific elements in a list based on their position. You can access the first element in a list by doing list[0], which would allow you to access the string "This".

In Python, lists and strings are quite similar. They’re both examples of sequences of data. Sequences have similar properties, like (1) being able to iterate over them using for loops; (2) support indexing; (3) using the len function to find the length of the sequence; (4) using the plus operator + in order to concatenate; and (5) using the in keyword to check if the sequence contains a value. Understanding these concepts allows you to apply them to other sequence types as well.


## Modifying Lists
While lists and strings are both sequences, a big difference between them is that lists are mutable. This means that the contents of the list can be changed, unlike strings, which are immutable. You can add, remove, or modify elements in a list.

You can add elements to the end of a list using the append method. You call this method on a list using dot notation, and pass in the element to be added as a parameter. For example, list.append("New data") would add the string "New data" to the end of the list called list.

If you want to add an element to a list in a specific position, you can use the method insert. The method takes two parameters: the first specifies the index in the list, and the second is the element to be added to the list. So list.insert(0, "New data") would add the string "New data" to the front of the list. This wouldn't overwrite the existing element at the start of the list. It would just shift all the other elements by one. If you specify an index that’s larger than the length of the list, the element will simply be added to the end of the list.

You can remove elements from the list using the remove method. This method takes an element as a parameter, and removes the first occurrence of the element. If the element isn’t found in the list, you’ll get a ValueError error explaining that the element was not found in the list.

You can also remove elements from a list using the pop method. This method differs from the remove method in that it takes an index as a parameter, and returns the element that was removed. This can be useful if you don't know what the value is, but you know where it’s located. This can also be useful when you need to access the data and also want to remove it from the list.

Finally, you can change an element in a list by using indexing to overwrite the value stored at the specified index. For example, you can enter list[0] = "Old data" to overwrite the first element in a list with the new string "Old data".

## Tuples
As we mentioned earlier, strings and lists are both examples of sequences. Strings are sequences of characters, and are immutable. Lists are sequences of elements of any data type, and are mutable. The third sequence type is the tuple. Tuples are like lists, since they can contain elements of any data type. But unlike lists, tuples are immutable. They’re specified using parentheses instead of square brackets.

You might be wondering why tuples are a thing, given how similar they are to lists. Tuples can be useful when we need to ensure that an element is in a certain position and will not change. Since lists are mutable, the order of the elements can be changed on us. Since the order of the elements in a tuple can't be changed, the position of the element in a tuple can have meaning. A good example of this is when a function returns multiple values. In this case, what gets returned is a tuple, with the return values as elements in the tuple. The order of the returned values is important, and a tuple ensures that the order isn’t going to change. Storing the elements of a tuple in separate variables is called unpacking. This allows you to take multiple returned values from a function and store each value in its own variable.


## Iterating Over Lists Using Enumerate
When we covered for loops, we showed the example of iterating over a list. This lets you iterate over each element in the list, exposing the element to the for loop as a variable. But what if you want to access the elements in a list, along with the index of the element in question? You can do this using the enumerate() function. The enumerate() function takes a list as a parameter and returns a tuple for each element in the list. The first value of the tuple is the index and the second value is the element itself.

## List Comprehensions
You can create lists from sequences using a for loop, but there’s a more streamlined way to do this: list comprehension. List comprehensions allow you to create a new list from a sequence or a range in a single line.

For example, [ x*2 for x in range(1,11) ] is a simple list comprehension. This would iterate over the range 1 to 10, and multiply each element in the range by 2. This would result in a list of the multiples of 2, from 2 to 20.

You can also use conditionals with list comprehensions to build even more complex and powerful statements. You can do this by appending an if statement to the end of the comprehension. For example, [ x for x in range(1,101) if x % 10 == 0 ] would generate a list containing all the integers divisible by 10 from 1 to 100. The if statement we added here evaluates each value in the range from 1 to 100 to check if it’s evenly divisible by 10. If it is, it gets added to the list.

List comprehensions can be really powerful, but they can also be super complex, resulting in code that’s hard to read. Be careful when using them, since it might make it more difficult for someone else looking at your code to easily understand what the code is doing.

Lists and Tuples Operations Cheat Sheet
Lists and Tuples Operations Cheat Sheet
Lists and tuples are both sequences, so they share a number of sequence operations. But, because lists are mutable, there are also a number of methods specific just to lists. This cheat sheet gives you a run down of the common operations first, and the list-specific operations second.

Common sequence operations

* len(sequence) Returns the length of the sequence
* for element in sequence Iterates over each element in the sequence
* if element in sequence Checks whether the element is part of the sequence
* sequence[i] Accesses the element at index i of the sequence, starting at zero
* sequence[i:j] Accesses a slice starting at index i, ending at index j-1. If i is omitted, it's 0 by default. If j is omitted, it's len(sequence) by default.
* for index, element in enumerate(sequence) Iterates over both the indexes and the elements in the sequence at the same time
 Check out the official documentation for sequence operations.

List-specific operations and methods

* list[i] = x Replaces the element at index i with x
* list.append(x) Inserts x at the end of the list
* list.insert(i, x) Inserts x at index i
* list.pop(i) Returns the element a index i, also removing it from the list. If i is omitted, the last element is returned and removed.
* list.remove(x) Removes the first occurrence of x in the list
* list.sort() Sorts the items in the list
* list.reverse() Reverses the order of items of the list
* list.clear() Removes all the items of the list
* list.copy() Creates a copy of the list
* list.extend(other_list) Appends all the elements of other_list at the end of list
 Most of these methods come from the fact that lists are mutable sequences. For more info, see the official documentation for mutable sequences and the list specific documentation.

List comprehension
* [expression for variable in sequence] Creates a new list based on the given sequence. Each element is the result of the given expression.
* [expression for variable in sequence if condition] Creates a new list based on the given sequence. Each element is the result of the given expression; elements only get added if the condition is true.  


## Dictionaries Defined
Dictionaries are another data structure in Python. They’re similar to a list in that they can be used to organize data into collections. However, data in a dictionary isn't accessed based on its position. Data in a dictionary is organized into pairs of keys and values. You use the key to access the corresponding value. Where a list index is always a number, a dictionary key can be a different data type, like a string, integer, float, or even tuples.

When creating a dictionary, you use curly brackets: {}. When storing values in a dictionary, the key is specified first, followed by the corresponding value, separated by a colon. For example, animals = { "bears":10, "lions":1, "tigers":2 } creates a dictionary with three key value pairs, stored in the variable animals. The key "bears" points to the integer value 10, while the key "lions" points to the integer value 1, and "tigers" points to the integer 2. You can access the values by referencing the key, like this: animals["bears"]. This would return the integer 10, since that’s the corresponding value for this key.

You can also check if a key is contained in a dictionary using the in keyword. Just like other uses of this keyword, it will return True if the key is found in the dictionary; otherwise it will return False.

Dictionaries are mutable, meaning they can be modified by adding, removing, and replacing elements in a dictionary, similar to lists. You can add a new key value pair to a dictionary by assigning a value to the key, like this: animals["zebras"] = 2. This creates the new key in the animal dictionary called zebras, and stores the value 2. You can modify the value of an existing key by doing the same thing. So animals["bears"] = 11 would change the value stored in the bears key from 10 to 11. Lastly, you can remove elements from a dictionary by using the del keyword. By doing del animals["lions"] you would remove the key value pair from the animals dictionary.

## Iterating Over Dictionaries
You can iterate over dictionaries using a for loop, just like with strings, lists, and tuples. This will iterate over the sequence of keys in the dictionary. If you want to access the corresponding values associated with the keys, you could use the keys as indexes. Or you can use the items method on the dictionary, like dictionary.items(). This method returns a tuple for each element in the dictionary, where the first element in the tuple is the key and the second is the value.

If you only wanted to access the keys in a dictionary, you could use the keys() method on the dictionary: dictionary.keys(). If you only wanted the values, you could use the values() method: dictionary.values().


## Dictionary Methods Cheat Sheet
Dictionary Methods Cheat Sheet
Definition

x = {key1:value1, key2:value2} 

Operations

len(dictionary) - Returns the number of items in the dictionary
for key in dictionary - Iterates over each key in the dictionary
for key, value in dictionary.items() - Iterates over each key,value pair in the dictionary
if key in dictionary - Checks whether the key is in the dictionary
dictionary[key] - Accesses the item with key key of the dictionary
dictionary[key] = value - Sets the value associated with key
del dictionary[key] - Removes the item with key key from the dictionary
Methods

dict.get(key, default) - Returns the element corresponding to key, or default if it's not present
dict.keys() - Returns a sequence containing the keys in the dictionary
dict.values() - Returns a sequence containing the values in the dictionary
dict.update(other_dictionary) - Updates the dictionary with the items coming from the other dictionary. Existing entries will be replaced; new entries will be added.
dict.clear() - Removes all the items of the dictionary
Check out the official documentation for dictionary operations and methods.  

## Object-Oriented Programming Defined
In object-oriented programming, concepts are modeled as classes and objects. An idea is defined using a class, and an instance of this class is called an object. Almost everything in Python is an object, including strings, lists, dictionaries, and numbers. When we create a list in Python, we’re creating an object which is an instance of the list class, which represents the concept of a list. Classes also have attributes and methods associated with them. Attributes are the characteristics of the class, while methods are functions that are part of the class.


## Classes and Objects in Detail
We can use the type() function to figure out what class a variable or value belongs to. For example, type(" ") tells us that this is a string class. The only attribute in this case is the string value, but there are a bunch of methods associated with the class. We've seen the upper() method, which returns the string in all uppercase, as well as isnumeric() which returns a boolean telling us whether or not the string is a number. You can use the dir() function to print all the attributes and methods of an object. Each string is an instance of the string class, having the same methods of the parent class. Since the content of the string is different, the methods will return different values. You can also use the help() function on an object, which will return the documentation for the corresponding class. This will show all the methods for the class, along with parameters the methods receive, types of return values, and a description of the methods.


## Defining Classes (Optional)
We can create and define our classes in Python similar to how we define functions. We start with the class keyword, followed by the name of our class and a colon. Python style guidelines recommend class names to start with a capital letter. After the class definition line is the class body, indented to the right. Inside the class body, we can define attributes for the class.

Let's take our Apple class example:

1234
>>> class Apple:
...     color = ""
...     flavor = ""
... 
We can create a new instance of our new class by assigning it to a variable. This is done by calling the class name as if it were a function. We can set the attributes of our class instance by accessing them using dot notation. Dot notation can be used to set or retrieve object attributes, as well as call methods associated with the class.

123
>>> jonagold = Apple()
>>> jonagold.color = "red"
>>> jonagold.flavor = "sweet"
We created an Apple instance called jonagold, and set the color and flavor attributes for this Apple object. We can create another instance of an Apple and set different attributes to differentiate between two different varieties of apples.

123
>>> golden = Apple()
>>> golden.color = "Yellow"
>>> golden.flavor = "Soft"
We now have another Apple object called golden that also has color and flavor attributes. But these attributes have different values.


## What Is a Method?
Calling methods on objects executes functions that operate on attributes of a specific instance of the class. This means that calling a method on a list, for example, only modifies that instance of a list, and not all lists globally. We can define methods within a class by creating functions inside the class definition. These instance methods can take a parameter called self which represents the instance the method is being executed on. This will allow you to access attributes of the instance using dot notation, like self.name, which will access the name attribute of that specific instance of the class object. When you have variables that contain different values for different instances, these are called instance variables.


## Special Methods
Instead of creating classes with empty or default values, we can set these values when we create the instance. This ensures that we don't miss an important value and avoids a lot of unnecessary lines of code. To do this, we use a special method called a constructor. Below is an example of an Apple class with a constructor method defined.
```python
>>> class Apple:
...     def __init__(self, color, flavor):
...         self.color = color
...         self.flavor = flavor
```
When you call the name of a class, the constructor of that class is called. This constructor method is always named __init__. You might remember that special methods start and end with two underscore characters. In our example above, the constructor method takes the self variable, which represents the instance, as well as color and flavor parameters. These parameters are then used by the constructor method to set the values for the current instance. So we can now create a new instance of the Apple class and set the color and flavor values all in go:

```python
>>> jonagold = Apple("red", "sweet")
>>> print(jonagold.color)
Red
```
In addition to the __init__ constructor special method, there is also the __str__ special method. This method allows us to define how an instance of an object will be printed when it’s passed to the print() function. If an object doesn’t have this special method defined, it will wind up using the default representation, which will print the position of the object in memory. Not super useful. Here is our Apple class, with the __str__ method added:

```python
>>> class Apple:
...     def __init__(self, color, flavor):
...         self.color = color
...         self.flavor = flavor
...     def __str__(self):
...         return "This apple is {} and its flavor is {}".format(self.color, self.flavor)
...
```
Now, when we pass an Apple object to the print function, we get a nice formatted string:

```python
>>> jonagold = Apple("red", "sweet")
>>> print(jonagold)
This apple is red and its flavor is sweet
This apple is red and its flavor is sweet
```
It's good practice to think about how your class might be used and to define a __str__ method when creating objects that you may want to print later.




## Classes and Methods Cheat Sheet
In the past few videos, we’ve seen how to define classes and methods in Python. Here, you’ll find a run-down of everything we’ve covered, so you can refer to it whenever you need a refresher.

Defining classes and methods
```python
class ClassName:
    def method_name(self, other_parameters):
        body_of_method
```
Classes and Instances
* Classes define the behavior of all instances of a specific class.
* Each variable of a specific class is an instance or object.
* Objects can have attributes, which store information about the object.
* You can make objects do work by calling their methods.
* The first parameter of the methods (self) represents the current instance.
* Methods are just like functions, but they can only be used through a class.
Special methods
* Special methods start and end with __.
* Special methods have specific names, like __init__ for the constructor or __str__ for the conversion to string.
Documenting classes, methods and functions
* You can add documentation to classes, methods, and functions by using docstrings right after the definition. Like this:
```python
class ClassName:
    """Documentation for the class."""
    def method_name(self, other_parameters):
        """Documentation for the method."""
        body_of_method
        
def function_name(parameters):
    """Documentation for the function."""
    body_of_function
```



## Object Inheritance
In object-oriented programming, the concept of inheritance allows you to build relationships between objects, grouping together similar concepts and reducing code duplication. Let's create a custom Fruit class with color and flavor attributes:

``` python
>>> class Fruit:
...     def __init__(self, color, flavor):
...         self.color = color
...         self.flavor = flavor
...
```
We defined a Fruit class with a constructor for color and flavor attributes. Next, we'll define an Apple class along with a new Grape class, both of which we want to inherit properties and behaviors from the Fruit class:

```python
>>> class Apple(Fruit):
...     pass
... 
>>> class Grape(Fruit):
...     pass
... 
```
In Python, we use parentheses in the class declaration to have the class inherit from the Fruit class. So in this example, we’re instructing our computer that both the Apple class and Grape class inherit from the Fruit class. This means that they both have the same constructor method which sets the color and flavor attributes. We can now create instances of our Apple and Grape classes:

```python
>>> granny_smith = Apple("green", "tart")
>>> carnelian = Grape("purple", "sweet")
>>> print(granny_smith.flavor)
tart
>>> print(carnelian.color)
purple
```
Inheritance allows us to define attributes or methods that are shared by all types of fruit without having to define them in each fruit class individually. We can then also define specific attributes or methods that are only relevant for a specific type of fruit. Let's look at another example, this time with animals:

```python
>>> class Animal:
...     sound = ""
...     def __init__(self, name):
...         self.name = name
...     def speak(self):
...         print("{sound} I'm {name}! {sound}".format(
...             name=self.name, sound=self.sound))
... 
>>> class Piglet(Animal):
...     sound = "Oink!"
```
We defined a parent class, Animal, with two animal types inheriting from that class: Piglet and Cow. The parent Animal class has an attribute to store the sound the animal makes, and the constructor class takes the name that will be assigned to the instance when it's created. There is also the speak method, which will print the name of the animal along with the sound it makes. We defined the Piglet and Cow classes, which inherit from the Animal class, and we set the sound attributes for each animal type. Now, we can create instances of our Piglet and Cow classes and have them speak:

```python
>>> hamlet = Piglet("Hamlet")
>>> hamlet.speak()
Oink! I'm Hamlet! Oink!
... 
>>> class Cow(Animal):
...     sound = "Moooo"
... 
>>> milky = Cow("Milky White")
>>> milky.speak()
Moooo I'm Milky White! Moooo
```
We create instances of both the Piglet and Cow class, and set the names for our instances. Then we call the speak method of each instance, which results in the formatted string being printed; it includes the sound the animal type makes, along with the instance name we assigned.




