# Python (3.3.x) Tutorial

## Contents:

* Introduction
* Beginning the Tutorial: Variables
* Writing to and from the Screen
* List of Math Operators in Python
* Conditionals
* Comments
* Loops
* For Loops, Lists, and the Connection Between the Two
* Slicing Lists
* Boolean Values
* Generating Random Numbers
* Functions
* Handling a Lot of Code
* Intro to Classes
* Working with Files

## Introduction

Python is a good transition into the world of programming because it is a simple language and it is easy to learn, while being a very powerful language capable of making pretty much anything from games to graphical interfaces to animated ads to internet databases ([more information](http://www.python.org/about/) about Python’s features).

Python is an interpreted language, what some would call a *scripting* or *scripted* language, meaning it is a series of commands sent one-at-a-time to a piece of software that executes each line of code it reads immediately.

To use Python, you need to [download it](https://www.python.org/download/releases/3.3.5). Install either the 32-bit or 64-bit version depending on your architecture, but keep in mind many of Python’s add-ons only work for 32-bit Python. The download contains the Python language interpreter, documentation that explains many aspects of the language and its use, and a graphical editor called IDLE, which isn’t that great, but is good for finding errors in your scripts with its built-in debugger. PyCharm, Spyder, and Geany are good alternative choices if you don't want to use IDLE.

If you’re running GNU/Linux, BSD, or Mac OS X, you may already have it installed. Go to a command line and type in `python` or `python3` to check and see. Once typed in, provided that it is installed, you will get a prompt that looks something like this:

```
Python 3.3.0 (v3.3.0:bd8afb90ebf2, Sept 29, 2012, 10:55:48) [MSC v.1600 32 bit (Intel)] on win32
Type "help", "copyright", "credits", or "license" for more information.
>>>
```

The top line just shows info about the version of Python you’re using (32-bit or 64-bit, for whatever architecture your system has). The second line shows some commands you can type into the interpreter to get more information about Python.

The third line is the Python prompt (`>>>`). This is where you will be typing stuff in (providing you’re not using scripts). When you type something into the prompt and press return, the thing you typed gets parsed, executed, and sent to the output, and the interpreter waits for the next instruction, all in real time.

Typing lines of code into the Python prompt is a mode of programming I will call *interactive mode*. I will be switching my examples between interactive mode and scripting just to get you used to both formats. The code will work largely the same both ways.

Like any other script, you have to tell the Terminal that it is going to be working with a Python script, so at the beginning of every script, type:

```
#!/usr/bin/python
```

to tell your system where Python is located in your filesystem (Windows users do not have to type this line). Save the script as `something.py`. "`.py`" means "Python."

This paper will be going fast, it won’t explain everything, even though I try to explain most hard concepts. However, this shouldn’t be a problem because Python is an easy language with plenty of helpful documentation along with it (in the Docs folder of Python's install directory) or [online](http://docs.python.org/3/).


## Beginning the Tutorial: Variables

A variable is a box where you can store information such as numbers, text (called *strings* in programming), lists, other variables, or even the return values of functions. Variables are workers in a step of a process, and with numbers disguised as variables, anything a computer can do can be done.

A program is a fancy way of doing math. It computes something that does something else to the hardware to give you input. It is math, it is computing, that’s what computers do. Every variable is a number that has stuff done to it.

There is no declaring (giving a type, such as `int` or `float`) of variables in Python like there is in C++ or Java. Once you put a value into a variable, Python sets some memory aside for it and puts the data into it automatically. All you have to do is give the variable a name and *initialize* it (give it a value to hold). The variable’s type is determined by the type of value put into it.

To make a variable, type the variable’s name, an equals sign, and what you want the variable’s value to be:

```
a = 1                 # an integer
b = "cherries"        # a string
currentExp = 126500   # an integer
pi = 3.141592653589   # a float
nil = None            # a null-value
```

The equals sign (`=`) here has a different meaning than what you might be used to. It does not mean "equals", it means "associate the name on the left with the thing on the right." You’re putting data into the memory spaces that the variable points to, you’re not comparing the variable to something. This is called *assigning to a variable* or *variable assignment*.

To change the value of a variable once it’s made, simply change what the variable is set to.

```
>>> a = 1
>>> a
1
>>> a = 3
>>> a
3
>>>
```

Python supports multiple variable assignments in one statement. You can do some very cool things with this:

```
>>> a = b = c = 2
>>> a
2
>>> b
2
>>> c
2
>>> b = 5
>>> b
5
>>>
```

The first line made three variables: `a`, `b`, and `c`, and set them equal to 2. Python reads variable assignment from right to left, which is why this is possible. So what’s really going on underneath this is that `c` is bound to the value 2 first, then `b` is assigned the value of `c`, and then `a` is assigned the value of `b`.

```
>>> a, b = b, a
>>> a
5
>>> b
2
>>>
```

This is another interesting assignment. What this is doing is mapping the variables to each other. `a` is assigned the value of `b`, and `b` is assigned the value of `a`. The result is that the two values are exchanged between variables. The values are swapped.


## Writing to and from the Screen

Your Python programs will be executed inside the Python interpreter, no matter if you’re running the programs directly inside the interpreter or in a script, and that interpreter is an application that does not make use of your operating system’s window-drawing API calls. In other words, it is a textual program, one without a graphical interface. Programs without graphical interfaces are run in your computer’s command line (also an interpreted program with its own interpreted programming language).

The interface you will be in is at the basest level in which an interface can be in computing. There’s only text. This is what we will be replicating this early in the game. When you open a command line, what you see is called *standard output*, also called `stdout`. Messages can easily be printed to `stdout` in Python using several different printing functions.

To send a text string to standard output, use the `print()` function:

```
print("Hello, World!")
```

Because Python is interpreted, this is actually a complete program. There is no additional code you have to include (the entire language is parsed and interpreted and set up automatically every time you start the interpreter), this one line is an entire working program. It doesn’t do much, but it is a complete program.

**Note:** the `print` function automatically puts a newline at the end of the string. To change this, put a comma after the string, make a variable called `end`, and set it to another string. Example: `print("You’re in a merry mood today, Mr. Todd.", end = "")`

Instead of printing straight text, what if you want to print the contents of a variable? To print a variable's contents, just put the name of the variable in the `print` function:

```
a = 2
print(a)
```

To send a message from `stdin` (standard input, the keyboard), make a variable to store the value and put the value into the variable using the `input()` function:

```
user_input = input() #user_input is a variable
```

Here’s an example to show this:

```
#!/usr/bin/python
print("Halt!")
name = input("Who goes there? ")
print("You may pass, " + name)
```

The program will wait for you to type something in, and use what you typed in later in the program.

If what you’ll be inputting must specifically be an integer, type:

```
user_input = int(input())
```

If you’re working with a floating-point (decimal) number, type:

```
user_input = float(input())
```

If a string is going to be included before the input, type:

```
response = input("Message introducing thing to be inputted")
```

When working with string values and variables that hold string values, you can concatenate (stick together) strings or parts of strings using the `+`  and `*` operators:

```
>>> "This " + "is " + "joined."
'This is joined.'
>>> "Ha, " * 5 #the asterisk creates several instances of the string
'Ha, Ha, Ha, Ha, Ha, '
>>> "Ha, " * 5 + "ha!"
'Ha, Ha, Ha, Ha, Ha, ha!'
>>> "Ha, " + "ha, " * 3 + " ha!"
'Ha, ha, ha, ha, ha!'
>>> a = "Hello, "
>>> b = "world!"
>>> a + b
>>> 'Hello, world!'
```

What you can’t do with strings is math. You can’t subtract the string "5" from the string "3" to get the string "2". Here’s what happens if you try:

```
>>> print("5" + "3")
53
>>> print("5" - "3")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for -: 'str' and 'str'
>>> 
```

This means that Python is trying to do something with both the strings using the "`-`", but the `-` can't do anything with strings that actually makes sense to the Python interpreter.

**Note:** quotes in Python do the same thing as apostrophes. Python doesn’t make the distinction. In fact you don’t even need to escape internal string quotes with backslashes like in bash scripting or something, although you can if you want. So the strings `"abc"`, `'abc'`, `''abc''`, and `"'abc'"` are all equivalent. The only time where quotes do something different is when there are three straight quotes in a row: `"""abc"""` OR `'''abc'''`. These make a special string called a *docstring*, which is a comment that can span multiple lines for the purpose of documenting author/company/copyright information or explaining bits of your code. Docstrings can be printed out with the `print()` function, and can be set to variables just like normal strings.

Here’s another example of input/output: a temperature converter:

```
#!/usr/bin/python
temp = float(input("Fahrenheit temperature: "))
print("Celsius temperature: ", (temp - 32.0) * (5.0 / 9.0))
```

Which outputs:

```
Fahrenheit temperature: 212
Celsius temperature: 100
```

If you want to print different types of data, such as a string, and then a variable, and then another string, and on and on, just separate the pieces of data with commas:

```
>>> a = 5
>>> b = 2
>>> print(a * b)
10
>>> print(a, " times ", b, " = ", c)
5 times 2 = 10
```

### A Note on Scripts

If you’re running Python scripts instead of typing the commands in interactive mode, you will notice that the program executes and then disappears almost immediately after it has output something. In this case, you will need to pause the program in order to see the results of the output (because error messages are part of the output as well).

If you’re running Windows, you need to import the `os` library (Type the line `import os` at the top of the program. `os` means "operating system") and type in `os.system("pause")` wherever you need to pause the program.

If you’re running Linux/Unix, there is no good way to pause your programs. The way that works most reliably for me is putting an `input()` at the end of the program and pressing enter when it gets to that point. Even this method isn’t great. It will throw an "`Unexpected EOF while parsing`" error, which isn't bad, but is annoying and unprofessional.

However, if you’re running Python scripts from the command line in the first place, as is common in Unix/Linux-based systems, you won’t really need to pause your programs unless there’s a lot of information that the user must read beforehand such as copyright information or tutorials. If you still find yourself needing to pause the program in the middle, you could try `os.system("sleep")`.


## List of Math Operators in Python

This part will be quick, and is only prerequisite material for the upcoming parts of the paper. I assume you all can do grade-school math.

Python supports these basic mathematical operators, as well as many others for higher math:

```
+    does addition
-    does subtraction
*    multiplies
/    performs real division
//   performs floored division (rounds down)
**   raises a to the power of b (a**b)
%    "modulus" - divides two numbers and returns the remainder
```

*Modulus* is sometimes called *modulo*. They’re both the same operator.


## Conditionals

Normally the instructions in a Python script are read from top to bottom one-line-at-a-time until the last instruction has been carried out and the program exits. Conditionals such as `if` statements change the reading of the code so that your program can do multiple things depending on the type of input it gets.

The first conditional we will be learning is the `if` statement, which is only interpreted *if* certain conditions are met within the program. The syntax of the `if` statement is:

```
if condition:
    do something.
```

**Note:** Printing the following `print` statement after the `if` statement in the Python prompt requires that you indent the code before you type it in. The interactive prompt will look like this:

```
>>> if some_condition:
...#Type additional code here
```

Those three dots are *not* the prompt indenting for you, they’re a placeholder for the prompt itself (`>>>`). You have to manually type in the spaces. This will happen otherwise:

```
>>> numerator = int(input())
>>> denominator = int(input())
>>> if denominator == 0:
... print("you can’t divide by zero!") #notice no spaces after the dots
  File "<stdin>", line 2
    print("you can’t divide by zero!")
         ^
IndentationError: Expected an indented block
>>>
```

The correct look of the prompt would be this:
```
>>> numerator = int(input())
>>> denominator = int(input())
>>> if denominator == 0:
...     print("you can’t divide by zero!") # I added spaces now
... 
```

This same error will also happen if you mix tabs and spaces. If you use tab characters to indent, stick with them, otherwise Python will complain. Use either tabs or spaces, not both. The traditional Python convention is 4 spaces, because tabs are configured different in every document and document-viewing application, thus your code will look different from application to application. Spaces don’t have this behavior, so their use will make for more portable source code.

`if/else` statements are not much different than `if` statements, but they test for two conditions instead of one, or they provide an enclosed environment where code can be interpreted if that condition is not met. This is useful for catching errors.

```
#!/usr/bin/python
num = input("Type in a number: ")
num2 = input("Type in another number: ")
result = (num/num2)
if num2 == 0:
    print("You can't divide by zero!")
    exit(1) #exits with error
else:
    print(result)
```

The syntax is this:

```
if condition:
    do this
else:
    do this other thing
```

A statement that tests for three conditions is the `if/elif/else` statement.

```
#!/usr/bin/python
num = input("Type in a number: ")
if num < 10:
    print("That's a small number.")
elif num > 10: # 'elif' = 'else if'
    print("That's a big number.")
else: #if num == 10
    print("That number is 10.")
input() #to pause the script so you can see the results
```

Syntax:

```
if condition 1:
    do this
elif condition 2:
    do this
else:
    do this instead
```

How Python differentiates between conditional statements is by indentation, not by braces like in C or Java or 'begin' and 'end' instructions like in Pascal or Basic. The end of the conditional is the end of the block of code that is indented in the same way. Since proper brace placement is required of other languages, it logically follows that proper indentation is needed for Python to work right.

As I said before, Python is picky about the type of spacing you use for indentation. If you use tabs for indentation, you need to stick with tabs. If you use spaces, stick with spaces. You can't mix them or you will get an error because they're two different characters and are parsed differently.

There is one more type of conditional that is used less frequently, yet is actually very useful. It's an *if expression*! Normal `if` conditionals are *statements*: lines of code that change the state of the program. An `if` expression reduces down to a value, and so can be assigned to a variable, passed to a function, returned from a function, or used in a bigger expression. It takes the form

```
value if trueExpression else falseExpression
```

Here's an example:

```
a = True
b = False
c = 5 if a else b
print(c) # => 5
```

Here's another example:

```
a = 10
max = a if a > 2 else 2
```

## Comments

Comments are notes to anyone reading the code you write. They’re ignored by the interpreter. Since Python is an interpreted language, comments can only be one-liners. To make a comment, type in an octothorpe character (#) and everything after that (while still on the same line) is commented.

This can be a good way of deleting code without deleting code such as when you need to rewrite something but want to keep the draft, or when you want to provide extra code that is optional or at least conditional, such as code that will only run on certain architecture. Just put a # in the very beginning of the line and the code will be "commented out."


## Loops

Loops execute certain code repeatedly until the execution point hits a way to stop. There are two different loops in Python: the `while` loop and the `for` loop.


### while Loops:

The `while` loop executes a block of code over and over again *while* a given condition is met. Once that condition is no longer satisfied, the loop exits. Here’s an example of a `while` loop that counts from one to nine:

```
i=1 # keeps track of how many loops have been done
while (i < 10): # while i is less than 10, execute the below lines
    print(i)
    i += 1 #increase i by 1
```

The syntax is:

```
while (condition is met):
    do this stuff
```

**Note:** the condition for `while` loops need not be contained in parentheses.

### Infinite loops:

Infinite loops are in some cases one of the most undesirable things to have in a program. Let’s say you have a loop that goes like this:

```
i = 1
while i > 0:
    print(i)
    i += 1
```

When do you think this loop will stop? Well, are positive numbers always greater than zero? Yes, always. The given condition is always true. Since this is the case, the loop will keep going until the heat death of the universe or you end the program because you didn’t put in a way for the code to stop. If you ever find yourself inside an infinite loop, press `Ctrl+C` and it will quit out of it. 


## For Loops, Lists, and the Connection Between the Two

`for` loops are a whole different beast than while loops. `for` loops actually initialize the variable as it is introduced into it to a value inside a list of values and reinitializes it along the way to one list value after another until it gets to the end of the list. This eliminates the need to increment the variable in each iteration or even to make the variable beforehand in the first place. Here’s an example of this:

```
for i in range(1, 11): #if i is between 1 and 10
    print(i)
```

The syntax of one version of the `for` loop is:

```
for variable in range(variable’s first value, variable’s last value plus one):
    do stuff
```

**Note:** the conditions in `for` loops can be contained in parentheses if desired, but they cannot end without a colon, as the colon is the delimiter that separates the `for` loop declaration from its statements.

Here’s another example:

```
for i in range(5): #starts at zero
    print(i)
```

Which outputs:

```
0
1
2
3
4
```

The reason I had to write that first loop as `for i in range(1, 11)` to get a value from 1 to 10 is that the function `range()` defines what’s called a *list*, a bunch of values bundled together, and those start counting elements at zero instead of one. They exclude the last element in the loop, which is why you need to add one, and is also why the above loop starts at zero.

To show this, type this in at the prompt:

```
list(range(5))
```

This will output:

```
[0, 1, 2, 3, 4]
```

Try typing this in now:

```
list(range(1, 6))
```

You will get the output:

```
[1, 2, 3, 4, 5]
```

Remember, `range()` excludes the last element, so you have to add one to the second argument.

The `list()` function makes a list out of whatever it has as its parameter.

Lists are variables that contain multiple pieces of data. Instead of a variable holding just one number or just one string, they hold many, and in differing types as well. The list `[6, 7, 42, None, "life", "the universe", "everything", 2.7182818, True]` is perfectly valid. Lists are identified by square brackets (`[]`).

**Note:** the keyword `None` literally means "none." It tells the Python interpreter that there is nothing currently in this variable or list element, but that the memory for a potential value is reserved anyway.

Try typing this at the prompt:

```
>>>ls = [1, 2, 5, 8, "peas"]
>>>print(ls)
```

You will get:

```
[1, 2, 5, 8, ‘peas’]
```

`for` loops can make the variable change based on list elements:

```
for i in [5, 8, 2, 3, 5]:
    print(2*i)
```

This outputs:

```
10
16
4
6
10
```

This can be rewritten as:

```
values = [5, 8, 2, 3, 5]
for i in values:
    print 2*i
```

A more Pythonic way of writing the above loop would be to mimic the name of the list you're looping over:

```
for value in values:
```

and this style is preferred by the majority of Python programmers. 

Because `for` loops work with lists, you can do some pretty interesting things with them:

```
for i in range(1, 6):
    print(list(range(i)))
```

This outputs:

```
[0]
[0, 1]
[0, 1, 2]
[0, 1, 2, 3]
[0, 1, 2, 3, 4]
```

```
foo = [] # foo is a list with no elements, an "empty list"
for k in range(5):
    foo.append(k)
```

What `.append()` does is it adds an element to the end of the list, increasing the total length of the list by one. There are also similar methods for manipulating lists such as `.remove()` and `.insert()`, which do exactly what they say they do. Consult the Python documentation for a full listing of list manipulation methods.

You initialize lists using this syntax:

```
mylist = [elements, separated, by, commas]
```

Example:

```
fibonacci = [1, 1, 2, 3, 5, 8]
```

and if you want to change just one element of that list:

```
fibonacci[0] = 5 # changes first element 
```

if you print fibonacci out now, it will look like this (although now it won’t be representative of a Fibonacci sequence):

```
[5, 1, 2, 3, 5, 8]
```

You can even embed `for` loops inside lists to initialize them in a concise way:

```
squares = [x*x for x in range(10)]
```

This gives you a table of squares for every number from 0 to 9. For every value in the list returned by range(10), the values are changed from their current value x into the first expression you put in before the for, which in this case is x*x.

Or, if you want to print a list of a bunch of even numbers:

```
even = [x for x in range(100) if x % 2 == 0]
```

This feature is called *list comprehension* and can have many uses. For example, if you want to create a dungeon floor for a text-based videogame, you could make it like this:

```
map_width = 10
map_height = 10

# init all elements to zero:
floor = [[0 for y in range(map_height)] for x in range(map_width)]

#print the dungeon:
for rows in range(map_height):
    for cols in range(map_width):
        print(floor[rows][cols], end="")
    print()
```

And if you want the dungeon to have a room:

```
for rows in range(4, 7):
    for cols in range(3, 6):
        floor[rows][cols] = 1
```

This puts a room in the middle left of the array, so when you print it, you will have a map with one room ready to go with 0s representing impassible terrain and 1s representing traversable floors. Put similar routines in functions, and you have a small tool for making the dungeons of a Roguelike game. For example:

```
def print_room(width, height):
    '''local'''floor = [[0 for y in range(height)] for x in range(width)]
    for rows in range(height):
        for cols in range(width):
            print(floor[rows][cols], end="")
        print()
```

This function makes a list of lists, `floor`, initializes the whole thing to zero, and prints the list one element at a time, `x`’s then `y`’s. All you need to do to use this code is put it in your program somewhere before it’s used, and whenever you want to use it just type `print_room(x, y)` to make a room `x` by `y` cells big. You’ll learn more about functions later.

**Note:** pay very close attention to the position of the square brackets in the list comprehension above. I actually embedded a list comprehension within a list comprehension to make a list of lists.

The basic syntax of list comprehension in Python is much like the syntax of [set-builder notation](http://www.mathsisfun.com/sets/set-builder-notation.html) in mathematics. You have an expression that you start with, a `for` loop, and an optional conditional to control which values will be present in the list. 

```
[expression for variable in list]
[expression for variable in list if filter and filter or filter else value2]
```

Going back to the list that calculates even numbers, let’s dissect another that calculates the odd numbers:

```
odd = [x for x in range(100) if x % 2 != 0]
```

We have a list called `odd`. `odd`'s expression uses a variable to assign a value to each of the list elements called `x`. The list would now look like

```
odd = [x]
```

But what do we do with the `x`? To initialize the array, we’re using a `for` loop that loops until `x` is at a certain value, I’ll use 100 again.

```
odd = [x for x in range(100)]
```

To calculate odd numbers, we have to see if every number between 0 and 99 can divide evenly by two, and if they cannot, they get put into the list.

```
odd = [x for x in range(100) if x % 2 != 0]
```

This is really all there is to list comprehensions in the grand scheme of things, yet this can have a wide variety of uses in your applications. 


### Slicing Lists

Since Python has so much to do with lists, it would be incomplete without operations to dissect them. This is where slicing comes in.

Slicing a list is done with the `:` operator.

Let’s say you have a list called `foo` that is enumerated 0 to 4:

```
foo = [x for x in range(5)]
```

To get just the first two elements of the list, you would put

```
>>> foo[:] #gets all elements
[0, 1, 2, 3, 4]
>>> foo[:2] #gets all elements up to element 2
[0, 1]
```

The colon means *include every list element from one point to another*.

Here is a handy guide for remembering what every positioning of the colon does when referencing list elements:

```
a[start:end:step] # syntax
a[start:end]      # every element from start to end
a[start:]         # every element from start to end
a[:end]           # every element until the end
a[:]              # every element in the list
```

You can even do this with negative numbers:

```
>>> foo = [1, 2, 3, 4]
>>> foo[-1]
4
```

This is equivalent of `foo[len(foo)-1]`. When iterating through a list, negative numbers go through the list backward, starting at -1 for the very last element in the list, and -2 for the element before that, and so on.

Knowing this, and using list slicing operations, you can easily reverse every item in the list like this:

```
>>> foo = range(5)
[0, 1, 2, 3, 4]
>>> foo[::-1]
[4, 3, 2, 1, 0]
```

This works by going through the list and displaying each element with a step of -1 (as a result it goes backward through it) starting at the last list element.

If you want to include every list element besides the beginning and ending elements, it would be:

```
>>> foo[1:-1]
[1, 2, 3]
```

Everything you can do with lists, you can do with the aid of list slicing operations. For example:

```
>>> foo = range(5)
>>> foo
[0, 1, 2, 3, 4]
>>> bar = range(5) # save foo’s value for later if needed
>>> foo.insert(2, 10) # inserts a 10 at element 2
>>> foo
[0, 1, 10, 2, 3, 4]
>>> len(foo) # notice the length has been increased
6
>>> foo.remove(10) # this removes by name/value, not element index
>>> foo # 10 is now removed from foo
[0, 1, 2, 3, 4]
>>> len(foo) # the array is now back to its original values
5
>>> foo.insert(0, foo[:])
>>> foo
[[0, 1, 2, 3, 4], 1, 2, 3, 4]
>>> foo = bar # we’ve screwed this list up, so let’s reset foo
>>> foo # now it’s back
[0, 1, 2, 3, 4]
>>> foo[2:] = [] #let’s remove some elements from the 2nd onward
>>> foo
[0, 1]
>>> foo = bar # we’ve screwed up our list again, so let’s reset it again
>>> foo
[0, 1, 2, 3, 4]
>>> foo[1] = ‘apple candy’
>>> foo
[0, ‘apple candy’, 2, 3, 4]
>>> foo = bar
>>> foo[1:] = [2]
>>> foo
[0, 2]
>>> 
```

As you can see, both methods are very good for manipulating lists.


## Tuples

Tuples are a data type sort of like a list, but instead of referencing many different pieces of data, they merge several pieces of data together and treat it as one value, such as a combination of an `x` value and a `y` value to make a point on a coordinate grid, like `(2, -4)`. 

Here’s a better analogy for those who don’t understand math. Let’s say you’re thinking to yourself one day, “It’s such a nice day out today.” What constitutes a nice day? Sunny weather? Cloudless sky? Light breeze? How about all of these combined? The tuple is the day, the data are the state of the weather that day. Written in code, it would look like this:

```
nice_day = (sunny, cloudless, light_breeze)
```

The syntax for the tuple is:

```
mytuple = element1 ,element2, ...,elementN
```

A tuple with one value (a singleton), is initialized with a trailing comma like this:

```
mytuple = value,
```

The only real difference between tuples and lists are

a) list elements are changeable ("mutable"), and tuple elements are not, and
b) tuples are surrounded by ( and ), not [ and ].


## Boolean Values

Boolean values are values that are either true or false. They are denoted as `True` and `False` in Python (always starting with a capital letter).

```
>>> a = True
>>> b = False
>>> a and b
False
>>> a or b
True
>>> a is not b
False
```

These values follow logical operations dealing with `True`/`False` values:

```
==    equal
!=    not equal
is    identical
not    not identical
<    less
>    greater
<=    less than or equal
>=    greater than or equal
and    true if both values are true, false otherwise
or    true only if either a or b is true
```

To distinguish between ambiguous statements such as `not a or b`, which can mean either "neither `a` nor `b`", or "`b` or not `a`", use parentheses: `(not a) or b` is different from `not (a or b)`.

The use of boolean values in your program allows you to turn your program into a state machine, only allowing certain code to execute if certain conditions are either true or false. If it is false that you have saved your progress, and you try to exit the application, a dialogue box will come up saying "Would you like to save?" and will give you the option to save. If it's true you've saved your progress, there's no need to display the box.

This is how you can use booleans, and in fact, you’ve already been using these for a while now. Going back to `if` statements, the statement that is evaluated after the `if` clause resolves internally to `True` or `False` because it isn’t just math that’s being calculated, it is a comparison between two values. It is either true or false that those two values are the same. 


## Generating Pseudo-random Numbers

If you’re going to be making a game, for example, you’re gonna need some element of randomness in it. You’re never gonna have any fun if you know what’s coming. The best games are unpredictable.

Fortunately, random numbers are easy to make, and there are a large amount of functions in Python’s standard library that can handle the generation of random numbers.

Here’s an example of the generation of some random numbers:

```
>>> import random #allows you to make random numbers
>>> random.random() #generates high precision random float from 0.0 - 1.0
0.6323892385638248
>>> random.randint(1, 101) #generates random int from a to b-1
85
>>> random.getrandbits(4) #generates random int from number of bits
7
>>> random.choice([1, 5, 7, 9]) #picks a random element from a list
5
```

The catch with these generators, though, is that the numbers they generate are not random, they are picked from a list of random numbers in the same sequence every time. In order to make them truly random, we need to *seed* the pseudorandom number generator, or make it pick from the list at a different point every time the random functions are called. To do this, type:

```
random.seed(None)
```

This will seed the PRNG to a different value every time providing that your operating system has no randomness-generating features of its own.

Here’s an example program that uses random numbers:

```
#!/usr/bin/python
import random
random.seed(None)

print("Welcome to my guessing game.")
print("I bet you can't guess what number I'm thinking!")
print("I’ll give you a hint: it’s from one to ten.")
secret_number = random.randint(1, 11)
# pay close attention to how I used that random function
# I used it to initialize a variable.
tries = 0
guess = None #guess is otherwise undefined because it's inside the while loop
while (guess != secret_number):
    guess = int(input("Go on, try: "))
    tries += 1
    if guess < secret_number:
        print("Too low!")
    elif guess > secret_number:
        print("Too high!")
    else:
        print("That's right! You got it in ", tries, " guesses!")
input()
```


## Functions

Functions are an easy way for you to use code that needs to be executed over and over again in different parts of your program. If you wrote something before, why write it again? Just use the function and save yourself the typing! After all, one of the big guidelines of programming is to avoid duplicate code, the *DRY* Rule: *d*on't *r*epeat *y*ourself. 

Here are the basics of functions. A function is defined with the word `def`, followed by the function's *name*. After the name is a set of parentheses containing the data you're going to feed into it (called *arguments*). A colon separates the parentheses from the business end of the function, the *body*. Finally, a value is returned to the code that invoked it in the first place. 

Using a function is called "applying" it, or "calling" it, and is done by saying its name followed by the data you're giving it in parentheses. `print()` is one function you're already familiar with, the data being the string you're printing. Feeding data into a function is called "passing" data to it. 

All you have to do to make a function is give it a name and put in the code you want to reuse in the body. Here's an example:

```
def Perimeter():
    print("Enter side lengths of a rectangle: ")
    length = input("Length: ")
    width = input("Width: ")
    return (2*(length+width))

print("This program will calculate the perimeter of a rectangle.\n")
print(Perimeter())
input()
```

So what exactly does a function do? A function is simply something that takes a value, does something to it, and spits out a new value, effectively defining a correspondence between a value and a transformation of that value. Sometimes the value isn't transformed, but simply passed on:

```
def identity(x):
    return x
```

The `return` statement gives a value back to the code that applied the function. Here’s an example:

```
def getNum():
    return 1
def giveNum():
    return getNum() # whose value is 1

print(giveNum()) #prints 1
```


## Function Arguments:

If you’re familiar with mathematical functions, then you should already know what these are. A function’s `argument` is something in the function itself that, when changed, changes the final output.

Take a function in math:

```
f(x) = x + 3
```

(This function is more often displayed as `y = x + 3` in math classes)

`x` is the function’s argument. If you substitute a value in for `x`, you will get a value out for `f(x)`. Let’s say you put in 2:

```
f(x) = x + 3
f(2) = 2 + 3
f(2) = 5
```

In Python, this would be:

```
>>> def f(x):
...  return x + 3
...
>>> print(f(2))
5
>>>
```

If you have a function that takes two arguments, `a` and `b`, you separate them with commas:

```
f(a, b)
```

Let’s say you have a function called `Add(a, b)` that returns the sum of `a` and `b`. When the function is called with two values, let’s say 3 and 7 (`Add(3, 7)`), it puts the value 3 into `Add()`’s first argument, `a`. It puts the value 7 into `Add()`’s next argument, `b`. It then returns the sum of the two.

A good use for function arguments is using them to initialize variables or create objects. Here's an example:

```
def generateWeapon(type, name, dmin, dmax, dur):
      print("Weapon type: ", type)
      print("Your weapon is a ", name)
      print("It does ", dmin, "-", dmax, "damage")
      print("It has", dur, "durability")

generateWeapon("Sword", "Dagger", 1, 3, 15)
```

Voila! You have a basic weapon generator for an RPG. It's a function that takes five parameters that define everything about the weapon that could be useful for your game. If this were actually integrated into a game, it would have to be modified to raise your damage (by changing the values of the global variables for damage and whatnot) or creating/updating a data structure with the weapon's information, but it's a start.


### Lambda

There is a special keyword in Python called `lambda`, which is used to make functions on-the-fly. Here is an example of its use:

```
>>> a = lambda x: x**3
>>> print(a(2))
8
>>> b = lambda a: "Hello "*a
>>> print(b(a(2)))
Hello Hello Hello Hello Hello Hello Hello Hello 
>>> 
```

Let’s look at this line-by-line. 

```
a = lambda x: x**3
```

This makes a short-lived, nameless function that takes an `x` and returns `x` raised to the third power, with `x` being the function's argument. This function can be applied like any other function because its name is what variable you assigned it to. In other words, you basically just did this:

```
def a(x):
    return x**3
```

except this is more concise.

This is pretty much no different than defining a real function, except the function is a value in a variable instead of an immutable name. It is used in the same way, except now it’s a bit more short-lived.

```
b = lambda a: "Hello "*a
```

This defines another nameless function that returns the string "Hello " `a()` times.

```
print(b(a(2)))
```

This prints the value of `b` when passed the return value of `a(2)`.

One of the simplest lambda functions I can think of is this identity function, which simply returns the number given it.

```
>>> f = lambda x: x
>>> f(67)
67
```

You have a variable named `f`. Now you set it to the word `lambda`, which basically means "I’m going to make a function now, and here is an argument for it." The argument is `x`. Now that I have the function’s reference, `f`, and list of arguments, `x`, all we need is a return statement. We make a colon and define an expression describing what we want to have happen to `x`. In this case, nothing mathematical happens to it, so I just write `x`. And it is done. Just call it with the variable name, and you’ll be able to use it just like any other function. Just remember that the variable can be set to different values, and you could lose the function, so be careful.

Lambda functions take this form:

```
<function name> = lambda <arguments>: <expression>
```

Example:

```
>>> product = lambda x, y: x * y
>>> product(3, 3)
9
>>> 
```

Just in case you thought they might be useless or unimportant, consider that lambdas are so powerful that they have an entire branch of math behind them called *lambda calculus*, describing everything you could possibly do with lambdas. It turns out you can make entire programming languages out of absolutely nothing but lambda expressions! Do not underrate their usefulness.


## Handling a Lot of Code

After writing a lot of code and taking on bigger and more complex projects, you’re gonna want to manage all that code in some way and the more code you write, the harder it will be to manage. There will come a point where you will just not feasibly be able to put all your code on one script anymore.

There is a way to divide one program into multiple scripts, and connent the multiple scripts into one coherent program. The way to do that is to *import* the separate scripts.

Let’s say you have a file called `main.py` and another file called `add.py`. `add.py` looks like this:

```
def Add(a, b):
    return a + b
```

and `main.py` looks like this:

```
print(Add(3, 7))
```

Go and try to run `main.py`. What happens? You get an error, right? Why? Well what does the error say?

```
Traceback (most recent call last)
  File "<stdin>", line 1, in <module>
NameError: name ‘Add’ is not defined
```

This means that `Add` is not recognized in `main.py` because you defined it in `add.py`. `main` and `add` can’t communicate yet.

The way to get your modules (scripts) to communicate is by importing them with the `import` keyword. Here’s the version that works:

`add.py`:

```
def Add(a, b):
    return a + b
```

`main.py`:

```
import add
print(add.Add(3, 7))
```

The syntax of the `import` statement is `import <filename without extension>`

An alternative way to write that same `import` statement, but specifying which specific functions you want to use within the module, would be `from <modulename> import <function>`. This particular syntax lets you exclude the module name when calling the function in your code. Using that syntax on the above example, it would look like this:

```
from add import Add
```

Now you can call the `Add()` function as if you defined it in your current script.

A *module* is a fancy name for a Python file (actually a chunk of your program, but Python chunks programs up by file anyway).

**Note:** do not include the file extension in your module name. Python treats this as a file in a higher directory because the dot is a file separator instead of an extension separator. As a result, you will get an error like `no module named ".py"` if you don’t have the file "py.py" in the folder "add" in the current directory in which you ran the program. Saying `import add.py` in your script translates to "import the module `py` from the folder `add` in your current directory."

An important thing to remember is that Python takes your imported function and executes it, it doesn’t just copy and paste it like it does in C/C++. Using the `from/import` syntax does not speed up your program though, because the Python interpreter searches through the entire module anyway.

If you have a module that has a lot of functions that you want to import, type:

```
from <module_name> import *
```

The `*` is what’s called a *wildcard*. It stands for "everything in this module." Basically all you have to remember is that `*` is short for "everything."

You can also import other classes and modules under an alias, so you can use the functions defined therein under a different name, and this is done with the `as` keyword. Here is an example:

```
>>> import random as r
>>> r.randint(1, 4)
3
>>>
```

I typed in `r.randint` instead of `random.randint`, and it still worked. The name was changed, but the behavior wasn’t.

This weird way of making your code visible throughout files seems overly complicated, and it trips up so many beginning Python programmers. Just look at how many threads there are on Stack Overflow about it! The secret that even the Python documentation seems to fail to effectively get across to so many people is that what you’re doing with your code when you import a module is making what’s called a *namespace*. A namespace is a container for code you plan to use often, but don’t want interfering with other code. This approach is effective for preventing naming collisions (you can’t have two variables or functions with the same name, but you can if they’re in different namespaces!).

If you’re coming from C#, C++, or VB, you already know what these are. They are the same in Python as they are in C++. Remember `std::cout`? This is calling the `cout` operator inside the `std` namespace. In Python, this would be `std.cout`. That is, the namespace name, a dot/period/full stop, and the function name. Earlier in this section, whenever I mentioned the word *module*, I was referring to a namespace, since that’s what Python calls those.

You’ve already been using namespaces for a good chunk of this tutorial. Remember `random.randint()`? `random` is a namespace! You’re calling the `randint()` function from the `random` namespace.

This works with normal variables too. Here is an example that lists a bunch of random variables in one file, and prints them off in another file:

values.py:

```
color = "blue"
opacity = 0.0
thickness = 0.2
style = "standard"
```

print.py:

```
import values

print values.color
print values.opacity
print values.thickness
print values.style
```

This prints:

```
blue
0.0
0.2
standard
```


## Intro to Classes

We’re going to turn away from conventional top-down programming now and steer into the world of *object-oriented programming* (OOP), since Python is, at its core, an object-oriented language. While not the best way of programming [by](https://www.youtube.com/watch?v=QM1iUe6IofM) [far](https://www.youtube.com/watch?v=o9pEzgHorH0), it is still fairly useful in large projects when you need to keep huge amounts of data in check. 

An object is a thing: something with features (height, color, shape) and uses (can block things, can pour liquids, can draw pictures). Objects in everyday life are no different than objects in programming. They mean pretty much the same thing.

Working with objects is the heart of game programming, model-making, and most big ventures in the world of software development, for better or worse. It is a bit hard to understand and get used to at first, but with practice and examination of its usage in actual source code, it will eventually click.

Your tool for the use of object creation is the *class*. A class is a template for an object, like a blueprint for a house. It's the muffin tin to the muffin. Classes are set up in such a way so as to be used many times for multiple things, such as models in a 3D environment or monsters in a game. You only have to set up the code once and you can refer back to it and even change some of the values by typing one line of code thereafter. This greatly saves on typing.

Why do classes exist? What makes them useful? Well imagine you’re trying to define a wall with just variables. You’d have a variable for the wall’s height, its width, the material it’s made of, its thickness, etc. Now let’s say you have to make a wall with a window in it. You’d have to make all new variables and everything. You’d basically have to make a completely new wall. What is the point of this? Why not use a copy of the wall you already have and just change a little bit of it? This is what classes are, they are templates for objects, think of stencils used for tracing out shapes. If you want to make a tree, you can use a class to do it. If you want to make a tree with different-color leaves, you don’t have to build another tree from scratch, just change the color of it in the class definition. A change in the template makes a change in the shape. Why give yourself more work to do?

Classes are made with the `class` keyword, followed by the name of the class and the class’s functions (called *methods* in object-oriented programming):

```
class MyClass():
    def my_method(self, arg1, arg2, arg n):
        statement 1
        statement 2
        …
        statement n
```

Let’s make a class that describes a circle, and I’ll go through the basics of what class-making is all about in the process.

```
class Circle():
    def __init__(self):
        self.pi = 3.14159265358979
        self.radius = 1.0
        self.diameter = 2.0*self.radius
        self.circumference = self.pi*self.diameter
    def display(self):
        print("Your circle has a radius of {0}.".format(self.radius))
        print("It has a diameter of {0}.".format(self.diameter))
        print("And its circumference is {0}.".format(self.circumference))

c = Circle()
c.display()
input()
```

This class has defined most common things about a circle. Let’s see the output:

```
Your circle has a radius of 1.0.
It has a diameter of 2.0.
And its circumference is 6.23818530718.
```

Let’s go through the class method-by-method. First, we defined the class with the name `Circle()`, with no arguments. Then we defined the method `__init__()` with the parameter `self`. I think this is a good place to stop and explain.

The first of this particular class’s methods is called `__init__`, which is a reserved keyword in Python. “init” means “initialize”, so this method is where you will be initializing the variables that serve as data for the object of which you’re trying to make a template. This special method is called a `constructor` in other programming languages, but it is technically not a constructor in Python because the object is made before this function is applied. Nevertheless, it serves largely the same purpose.

What happens after the method name is the listing of whatever arguments the method takes. In this case, the `__init__` method takes one parameter: `self`. The `self` parameter is a placeholder for the name of the object you will be using when using the class in your code.

Any variables you declare in the class look like `self.pi` or `self.HP` or `self.height` inside the class definition, but in the code outside the class, the word `self` changes to whatever you’ve named your object.

In the `Circle` class, the object is defined with the line `c = Circle()`. You’re setting a variable, `c`, to your class in order to use it. Your object, in this case, will be called `c`. You can’t use the class’s methods directly, you have to go through the object to do it, the reason being that the things you define in your class belong to the class and nowhere else, requiring you to bring your class with you throughout the program.

What use are classes? For one, they have the potential to cut down the amount of bugs in your program (if used correctly). As well as templates, classes are supposed to be interfaces, something you can use without thinking about how it works on the inside. You use stuff like this every day, such as TV remotes. You can use your remote to turn the TV off and on, change the volume, etc. and to do that does not require you to know exactly how the internal architecture of the remote works. Aliens could take your remote while you’re sleeping and replace the innards with different but compatible hardware, and you might never even know it. You just press buttons and stuff happens. Classes take this paradigm. 

How exactly do classes make code potentially more bug-free? One of the many big, complex-looking pieces of OOP jargon is the word *encapsulation*. Encapsulation means to wall something off, to separate it, to surround it in a capsule so that it stays hidden. This is the case with the innards of your TV remote and with your class’s methods. It protects the programmer from the code, and, in some cases, the code from the programmer. All you need to worry about is how to use the class, not what’s in it. As a result, the class could be completely changed around and, if the names and usage of the methods stay the same, you’d never know it.

Going back to our `Circle` class, we have the variables we will be using: `pi`, `radius`, `diameter`, and `circumference`. Again, they have to be preceded by the `self` keyword and the member selector operator (a dot). Inside a class, variables are called *members* of the class. The reason they must be preceded by `self` is that, as I said before, the class’ members can’t be accessed outside the class, they have to go through the class object to be modified. This keeps them inside the class.

Now we’re on to the second method, `display()`. This method takes the `self` parameter again, and actually uses the members we made earlier by sending them to `stdout`.

The `.format()` function along with the `{0}` is a special way to print the contents of your class members (or anything else for that matter). It cleans up the string output code a lot. The braces encapsulate an integer representing the number of the current variable in the string, from left to right starting at zero. The `{x}` construction is a placeholder for a variable value in your string. The `printf()` function in the C language does something similar with format specifiers, which is really what the `.format()` method is. To output multiple members in the string, use multiple sets of numbers and braces and put the members in the string in the order of their use:

```
print("{0} + {1} + {2} = {3}".format(self.a, self.b, self.c, self.d))
```

Just an aside, why is the `self` parameter something that needs to exist? Why do we have to put it as the first argument of every method in our class? Well the answer has to do with what Python does with class methods internally upon interpreting the program.

On the inside, Python translates the line `c.display()` into `Circle.display(c)` at runtime. Why? Because that’s how Python interprets the calling of its methods through its class object. Take a close look at that second line. `Circle.display(c)`. What is `c`, our class object, inside the class? It’s `self`, right? So, if I change `Circle.display(c)` to `Circle.display(self)`, I think this should start to make a little bit more sense, because `display()` is a method of the class `Circle`, that takes the parameter `self` (`c`). Methods have to go through the class, so the line `Circle.display(c)` translates to "call the method `display()` belonging to the class `Circle` through the object `c`."

**Note:** the `self` keyword isn't actually a built-in keyword in Python. It's the name of a pointer to your object and it can be named anything. I sometimes call it `this` because that's what it's called in other languages such as C++ or Java and is easier to understand for me. The general convention is to use `self`, and it's a convention that is irrationally clung to with iron claws in the Python community, but I'm not encouraging you to stick to that convention just because of that. You're not a robot. Do it how you do it. If something other than `self` is easier for you to understand, than by all means, use it. 

You can read the Python documentation for more on classes and how they work, but this is stuff that will get you well on your way to their usage quickly.

Understanding of these concepts, as well as the big picture of what a class is, nothing more than a collection of completely normal Python variables and functions under a common name, is important if you are going to be programming with classes and objects, so read and reread this section until you understand it, and look at implementations of classes in actual source code to see how people program this way. This will help a lot if you’re stuck.




### Class Inheritance

Let’s say you have the `Circle` class above and you want to extend it into a unit circle on which to describe a right triangle. You don’t have to remake all the variables in the `Circle` class, you can just pass `Circle` as a parameter to another class, and all the variables in the `Circle` class will be available in the new class. The child class inherits the variables from its parent. Here is a simple example of inheritance:

```
>>> class Parent():
...     def __init__(self):
...        self.foo = 3
...     def display(self):
...        return self.foo
...
>>> class Child(Parent): # See? Parent is Child’s argument
...     def display(self):
...        return self.foo + 1 # inherited from Parent
...
>>> p = Parent()
>>> c = Child()
>>> p.display()
3
>>> c.display()
4
>>>
```

You don’t have to make a whole new class if you want to add features to your template, just add on to your existing class through inheritance.


### Class Terminology Refresher:

Now that I’m talking about classes and object-oriented programming, it is pertinent to get the terminology down so as not to be misunderstood. I tried to explain all the new terms in context as best as I could, now I’m going to give you a refresher in order to ingrain this into your mind.

* *Class* - a template or representation in code of a real-life thing.
* *Method* - a function inside a class that defines or does stuff to class members.
* *Member* - a variable inside a class.
* *Object* - an instance of a class.
* *Attribute* - a member accessible through an object (i.e. one of the features of your template). If I have the member `person.age`, `age` is the attribute of the object `person`.


## Working with Files

Python has the capability to read from and write to text files (or any other type of files), and add to already-existing text files. This is called “file input and output”, or “file I/O” for short. Python has a number of I/O methods to do this that are easy to use and holds your hand throughout the file manipulation process.

The file manipulation methods are based on a class object, so the first thing you have to do to use the class’s methods is make an object for the file.

### Opening files

If you want to open a file, make the object, and set it to the `open()` method. `open()` takes two string arguments: the file you want to work with (including the extension), and the file mode (what you want to do with the file). If you forget to put a file mode argument into the method, Python will add in a read mode for you, setting you up to read from the file. Let’s try opening a file for writing.

```
f = open("file.txt", "w") # makes the object and opens the file for writing
f.close() # closes the file with close() through object "f"
```

This is pretty straightforward. `f = open()` sets the object for the file class and calls `open()` with the respective arguments. We’re going to be opening `file.txt` for "w"riting. The various file modes for reading and writing are:

* "r" = read from a file.
* "w" = write to a file, overwriting what might already be there.
* "a" = append new text to a file that already has some text in it.
* "r+" = read and/or write to a file.

For example, `f = open("file.txt", "r")` will open the file for reading instead of writing.

**Note:** if the file you’re trying to write or read doesn’t exist, `open()` will make it for you.

### Writing to files:

To write to a file, there is a `write()` method that does that for you. It takes one string argument. 

```
f.write("Oh, hello there!")
```

This writes the string "Oh, hello there!" to the file. If there is text already in the file, and the file is opened for writing, whatever’s in the file will be overwritten and replaced with the string.

If you’re going to be writing a lot to a file, or if you want to preserve the file’s contents, make sure to open the file for appending, rather than writing:

```
fh = open("foo.txt", "a")
fh.write("Hello, ")
fh.write("world!")
fh.close()
```

This will put the full string "Hello, world!" to the file, because the `write()` method doesn’t add a newline to the end like `print()` does. To add a newline, just put a newline character (`\n`) at the end of the string.

This is something I’m not sure of yet, but the behavior seems to stay the same if I run the `open()` and `write()` methods together in one line, omitting the file object:

```
open("file.txt", "w").write("What the flibbity flobbity?")
```

I can call this again and append another thing to the file:

```
open("file.txt", "a").write("P. Sherman 42 Wallaby Way, Sydney")
```

I don’t seem to need to close the file afterward, because opening it again yields the result:

```
What the flibbity flobbity?P. Sherman 42 Wallaby Way, Sydney
```


### Reading from files:

In order to read characters from a file, we can use the read() method.

```
f = open("file.txt", "r+")
f.write("Holy crap, I’m being read!")
f.read()
f.close()
```

You should know what everything in this does by now, except the `read` method. The `read` method reads a set number of characters in the file and sets those characters to string format as the function’s return value. This means that if you want to send a file’s contents to `stdout` (like Windows' `type` command), all you need to do is print it out:

```
f = open("file.txt", "r")
print(f.read())
f.close()
```

This outputs:

```
Holy crap, I’m being read!
```

You can also read a set amount of characters from a file by passing an integer parameter to `read()`:

```
f = open("file.txt", "r+")
f.write("I love eggs.")
f.read(6)
f.close()
```

This outputs the first 6 characters of the file:

```
I love
```

There’s an alternate method for reading a file that reads one line at a time: `readline()`.

Here I am going to be using the string method `.strip()` with the output, because oftentimes it will be botched otherwise. The `strip()` method removes tabs, spaces, and newlines from the beginning and ending of the line (what are called "leading" and "trailing" whitespace).

```
>>> fl = open("file.txt", "r")
>>> fl.write("Eggs, spam, and milk\n")
>>> fl.write("with salt and pepper\n")
>>> fl.write("make for a nutritious breakfast!")
>>> fl.readline().strip()
‘Eggs, spam, and milk\n’
>>> print(fl.readline().strip())
with salt and pepper
>>> print(fl.readline().strip().split())
[‘make’, ‘for’, ‘a’, ‘nutritious’, ‘breakfast!’]
>>> fl.close()
```

This outputs the first line of the file, and if you call it again, it will read the next line, and the next, and the next, until the end of the file. If you call the `readline()` method after that, only an empty list is returned. As you can see, you can use a number of string methods on the output to change it and manipulate the individual words.

### Using `with`

Python has a statement that makes the file manipulating process much easier, cleaner, and bug-free, and this is the method that should always be used in real-world programs: `with`!

`with` is a way to manipulate files with safety nets that will catch you if the program crashes or skips execution before you have a chance to properly close the file.

Here is an example:

```
with open("file.txt", "r+") as f:
    f.write("Here I am!")
```

This opens the file, defines the object with the `as` keyword, and does whatever’s in the indented block. Once the indented block is finished, or an error happens in the program before the block is executed, with ensures that the file with always always *always* be properly closed, no matter what happens in the program along the way. 

This is the syntax for the with statement:

```
with open(args) as <file object>:
    do stuff here...
```

Here is a function I made that uses with to write to a file:

```
def write_to(fobj, s):
    with open(fobj, "a") as f:
        f.write(s)

write_to("file.txt", "This is shorter!")
```

You could also easily change it around to include a flag to set whether or not the function will add a newline to the end of the string or not:

```
def write_to(fobj, s, newln):
    with open(fobj, "a") as f:
        if newln:
            f.write(s + "\n")
        else:
            f.write(s)

write_to("file.txt", "This call adds a newline!", True)
write_to("file.txt", "This one does not!", False)
```

**Note:** the above could be shortened to
`f.write(s+'\n' if newln else s)`
if you'd like to use an `if` expression. 

For more on file I/O, see http://www.pythonforbeginners.com/files/reading-and-writing-files-in-python


```
TODO: 
put earlier section on .format()
explain dictionaries
explain function recursion
generators
more standard library functions?
exception handling 
```

