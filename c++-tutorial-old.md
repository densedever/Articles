# C++ Programming

C++ is an object-oriented, procedural programming language derived from C, a language used for making operating systems. Since that is its origins, C++ allows the programmer to control his computer directly, manipulating the bare metal. This low level of programming allows the developer to have a lot of control over his programs, with the downside that he has to be careful of his programming. The C++ compiler assumes you know what you're doing and will let you do anything with your code, even things that don't make computational sense. This can lead to program crashes if your coding is sloppy. It's important to know what's going on behind the scenes to really take advantage of C++'s power.

A program is a set of instructions sent to the computer's CPU to tell the system to do stuff. These instructions and the data the instructions deal with exist in RAM. When programming, you are dealing with raw data in memory that is interpreted a bunch of different ways by the CPU. This allows the computer to do pretty much anything just with numbers. 

Computers have an IQ of zero, so your job as a programmer is to teach the computer how to do a task. This is done in a number of specific steps. If you want to add 2 plus 2, you have to tell the computer to bookmark a specific memory space and put a 2 into it, bookmark another memory space, put a 2 in it, and call a piece of code with instructions that tell it how to add data together on those memory spaces you just bookmarked. This process is called an *algorithm*. To program, you need to be able to think about problems in this manner. Don't just think about what the problem is, but what it takes to solve it and the specific process needed to go through to solve it.


## C++ Code

Code itself looks a certain way. Programming languages may be languages, but they're not really written like normal, everyday language. C++ is *procedural*, which means it gets its work done through the use of "procedures", which are subprocesses or subroutines, basically a mini program inside your big one. These are called *functions* in C++ and *methods* or 
*procedures* in other languages. Each function holds code in the form of instructions to send to the computer to tell it what to do.

Your C++ program will be set up in a certain fashion, due to how the C++ compiler works and the system layout of the files that make up the language.

When preparing to code, make a file to put your code on (called a *source file*) that ends in `.cpp` or `.h`. `.cpp` files hold actual code, `.h` files (called header files) hold definitions for your code. You'll learn more about these later.

The skeleton of the most basic C++ programs looks like this:

```cpp
#include <iostream>

int main(void)
{
    //code instructions go here
    return 0;
}
```

Assume from this point on that, unless specifically written, all code examples are to be written inside the main function before the `return 0;` line.

C++ is a large language, and it has to be defined before the computer can recognize it. C++ itself is split into a bunch of different parts so that your programs stay as small as possible. The `#include` directive is a statement carried out not by the compiler, but by the *preprocessor* (a tool which basically does nothing but copying and pasting), and adds a code file to your program. In this case, `iostream` is the file that will be loaded, which contains instructions for writing messages to a shell terminal.

The next line that you see in a lot of beginner C++ programs is the line `using namespace std;` *Namespaces* are sections of code that are referred to under a specific name, so that the code stays separate from the rest of the program, eliminating the possibility of accidentally duplicating names of variables, functions, etc. The *standard namespace*, or `std`, is a namespace that holds definitions for a bunch of core stuff under the name `std`, and is needed for command line programs, which we'll be making throughout this tutorial. `using namespace <name>;` includes a namespace into your program so that you can use the code inside it.

I will not be using the `std` namespace in this tutorial because it is very bad practice with a lot of drawbacks.

After the preprocessor gets to your code and does the proper text substitutions, the compiler starts reading your code at a specific place within your program, and that is the main function, which will be explained in the section on functions.

Code instructions take two forms: expressions and statements. *Expressions* are things that can be simplified into a single value while retaining their meaning. 2+2 is an expression because it evaluates to 4. *Statements* tell the computer to do something and aren't stating a value, so cannot be simplified. Setting aside a chunk of memory for storing data is a statement, because you're not dealing with a value, but the place that stores the value.

```cpp
int var = 20; 
//this is a statement. It sets aside 8 bytes of RAM 
//called 'var', and puts the number 20 into it.
//remember, 'int' reserves 8 bytes of memory.

sqrt(23.0 * (2.0 + 4.0));
//this is an expression. It calculates the square root of 23 * (2 + 4).
//semicolons end code statements.
```

Computers can do pretty much anything, but their hardware can only do so much. You have a limited toolset at your disposal, so you need to be resourceful in using the tools in a way that will solve your problem. Here I will give you a look at the things you are going to be using in C++, and programming in general, and then I will give you some example programs to show how these will be used.


## Functions

A *function* in programming is a mapping from inputs to outputs. It's a mathematical hoop you make a number jump through to give you a specific result. It's also a place to put pieces of code that do specific things. 

Every C++ program has at least one function in it: the main function. Here's what the main function looks like in real C++ code:

```cpp
int main()
{
    return 0;
}
```

This is a full function definition. There are a few different parts to it. The first word, `int`, is short for integer, which is just a whole number. This is the data type the function will return. The word `main` is the name of the function. The parentheses hold whatever inputs the function needs. It's empty in this case because `main()` generally doesn't need any for simple programs. The curly braces,  `{}`, denote the beginning and ending of the function. The main function, instead of returning a value to its caller, returns what's called an *exit status code* to the operating system. An exit status of zero indicates that your program ran successfully. Anything else, and something went wrong.

Functions, as well as holding and containing specific code, can also be used to calculate values. There are entire programming languages that are made up of nothing but these. Remember that functions are a mapping from inputs to outputs. If a function takes an input, it has to give one, single, specific output corresponding to that input, by definition. Function input goes inside variables, which are just reserved memory in the computer. These variables are the function's arguments. The values of the variables are the function's parameters.

Here is a function that takes two inputs and adds them together, returning the sum as its output:

```cpp
int add(int x, int y)
{
    return x + y;
}
```

It is *called*, or invoked, by saying its name and what inputs you want in it:

```cpp
add(2, 3);  //  => 5
add(7, 10); //  => 17
```

When the compiler sees this code, it looks for the definition of `add()`, throwing an error if it doesn't find it, and reads the arguments left-to-right. `add()` takes two arguments: `x` and `y`. If `add()` is called with 2 and 3, like above, the compiler sets `x` to 2 and `y` to 3 and returns `x + y`: 5.

If you add too many inputs or not enough, you will get errors:

```cpp
add(3); //wrong. Add 3 to what?
add(2, 6, 6); //wrong. How will the function use the extra argument?
```

The syntax for writing functions is:

```
<return type> <name>(<argument list>) {<function body>}
```

According to that syntax, the add() function is defined like this:

```cpp
int add(int x, int y) {return x+y;}
```


## Variables

Variables are reserved memory spaces used for holding the data you're working with. They have many different types, and the type of the variables determine how much memory is set aside and what that memory looks like to the CPU. Integers, `int`s, reserve 8 bytes of memory for your use. Characters, `char`s, reserve one byte. There are a few more types as well.

```cpp
int foo = 5;
// reserves 8 bytes and puts a 5 into that space
```

The `=` sign here does not mean in C++ what it means in math. This is called the *assignment operator*, and is telling you that the value of the thing to the left of it (the *l-value*) is going to be changed to be the same value as the thing to the right of it (the *r-value*). If you want to test for equality, use two equals signs (`==`).

The different variable types are `int`, which reserves 8 bytes of memory on a 64-bit system, `char`, which reserves 1 byte, `float`, which reserves 4 bytes in floating-point (fractional) format, `double`, which reserves 8 bytes in floating-point format, and a few more variations on these. Both `int`s and `double`s have `long` formats, `long int`s and `long double`s, which reserve twice the memory for vastly bigger values. You can find out how big a variable is with the `sizeof()` function.

```cpp
std::cout << sizeof(int); 
//prints how many bytes an int reserves (8 on x64 processors, 4 on x86)

std::cout << sizeof(foo); 
//`std::cout <<` prints out the thing to the right of it
//this prints the size of a variable, 'foo', based on its data type.
//sizeof() returns an unsigned int.
```

Each variable has a signed and unsigned version. A *signed* variable is a variable that can hold negative values, and an *unsigned* variable cannot hold a negative value, but can hold large positive values. Whether a value is negative or positive depends only on how the CPU interprets the same string of bits in those memory spaces, so if you try to make an unsigned value negative, you will get a very large positive value instead. `int`s and `char`s are signed by default.

Setting aside memory in a variable for later use is called *variable declaration*, and putting something inside that memory space for the first time is called *initialization*.

```cpp
int num; 
//an int is initialized. The memory marked as 'num' can now be used.

num = 4000;
//the number 4000 is put into the 8 bytes marked as 'num'
```

You can also declare sets of variables instead of single values. These are called *arrays*. They are allocated on contiguous memory spaces (that is, one space after the other).

```cpp
int vals[5] = {2, 3, 6, 6, 8};
//declares an array of 5 ints
```

Arrays are *zero-indexed*, which means the enumeration of their individual values starts at zero. In other words, the first value in the array is element 0, the second is element 1, etc. This is because the computer references the array's elements by how far away they are from the array's first element. 

The third element would be two places away in memory from the first element, or `vals[0+2]`, or just `vals[2]`, and so is said to have an *offset* of two from the array's first index. The memory addresses of individual array elements change based on the size of the array's data type. `vals` is an array of `int`s, and `int`s are 8 bytes, so `vals[2]` would be 16 bytes away from `vals[0]`, or `2 * sizeof(int)`.

That bracket notation there is actually how you reference single elements in an array:

```cpp
int vals[5] = {2, 3, 6, 6, 8};
int foo = vals[2]; //'foo' is now what vals[2] is: 6
```

Variables are memory set aside by the processor, and that variable's memory exists somewhere. To see *where* a variable is in memory, as opposed simply to what's inside that location, all you need to do is print it out with an `&` beside it.

```cpp
char foo = 77;
std::cout << &foo << std::endl; //this outputs foo's memory address.
```

The `&` is called the *address-of* operator. It resolves to the address of the variable, instead of the contents of that address, which is the default.

You can declare variables that hold the memory address of other variables, too. These are called *pointers*, and are very important to understand for low-level data manipulations. Arrays use pointers to reference their elements, for example.

To use pointers, you have to have a variable, and the pointer you want looking at it.

```cpp
int foo;          // a random variable
int *p = nullptr; // a pointer to some memory address.
p = &foo;         // p now points to foo's memory address.
```

Here we have the variable `foo`, and a pointer to it, called `p`. In the variable declaration, the `*` tells you that this will be a pointer. Its type is 'pointer to integer.' You can see its size with `sizeof(int *)`, however `int`s and `int*`s have the same size anyway. `nullptr` points to something called the *null address*, a pointer to the memory address 0. This memory address is out-of-bounds because it is reserved by the operating system, and trying to write to or read from this memory will cause your program to crash. If you are not using a pointer right this minute, or if you want to effectively delete it, set it to `nullptr`, otherwise if you accidentally do something with it, you might corrupt important memory that your program is already using.

To make a pointer look at a variable, set the pointer to that variable's address:

```cpp
char foo = 65;  //this char lies at address 0x826blahblah
char *p = &foo; //this pointer holds the address 0x826blahblah
```

To look at what value is in the memory space the pointer is looking at, print it out with a `*` next to it:

```cpp
cout << *p << endl; // => 'A'
```

This is called *dereferencing* the pointer. You're getting a value from a memory address with the `*`, which is called the *contents-of* operator.

There aren't just variables with changeable values, you can also make variables that have fixed values, values that cannot change. These are called *constants*. Prepend the word `const` to the variable declaration, and make sure to initialize it on the same line.

```cpp
const double PI = 3.141592;
```

These come in handy when making arrays or when you have single values prevalent in your code. Common convention is to write the constant's name in uppercase to distinguish it from other variables. To make your programs predictable, it's good practice to define as many variables constant as you can.

Constants can be declared with the preprocessor. Anything starting with `#` is a command for the preprocessor.

```cpp
#define NULL_ADDR (unsigned char * const)0x0
// this defines a constant pointer 
// to the null address in hexadecimal format.
// unsigned chars are raw bytes, not text characters like chars.
```

The `#define` keyword is a preprocessor directive that defines a constant. Put the `#define`, the name of the constant, and the value of the constant, all separated by spaces. Do not end this with a semicolon.

Constant pointers, pointers that can only point to one specific memory address, are declared with the `const` keyword as well:

```cpp
int foo = 5;
int *p = &foo;
int * const pc = &foo;
pc = nullptr; // error: assignment of read-only variable 'pc'
```

## Input and Output

To make an interactive program, you need to be able to send and receive messages from the user. This is done with `std::cout` and `std::cin`, some special functions in the `std` namespace.

```cpp
std::cout << "Hello!"; 
//prints Hello! to the screen.
std::cin >> foo; 
//asks for a single word of text from the keyboard 
//and puts it in memory starting at 'foo'.
```

`std::cin` can only take one word at a time, though, because it stops reading what you typed when it hits whitespace (a space, tab, newline, etc.). To read a whole line including whitespace, use `std::getline()`:

```cpp
std::string name;
std::cout << "What is your name?";
std::getline(std::cin, name);
std::cout << "Oh, hello " << name << "!" << std::endl;
```

This makes a variable with the type `std::string`, defined in the `std` namespace, which reserves one byte per letter and ends with a byte that contains all zeros (called the *zero-byte*, *null byte*, or *null-terminator*). This null byte tells the processor that this is the end of the `std::string`. `std::string`s are not of a fixed size, so the length has to be calculated and set at compile-time. This is why strings are null-terminated. Naturally, this makes strings one byte longer than the amount of characters you put into it, so getting the length of the string with `length()` will only give you the length of the string, minus the null terminator. You have to include the `string` header to be able to use `length()`.

**Note:** The two slashes in the code above are *comments*, which are simply notes you write to yourself in your code to remind you what it does or to explain to others what you're intending to do. everything from the `//` to the end of the line is ignored by the compiler and treated as if it isn't even there. You can comment out entire blocks of code or write a long comment by starting it with `/*` and ending it with `*/`.


## Conditional Control Structures

Control flow structures change the order in which the compiler reads your code based on the fulfillment of certain conditions, allowing programs to make decisions and gives them the ability to be dynamic. If you have not saved your progress (in LibreOffice or PowerPoint, for example), you will be asked if you want to save when exiting the program, otherwise you will simply quit. These conditions are in the form of `if/else` statements.

```cpp
int age = 15;
if(age < 18) {
    std::cout << "You can't enter here." << std::endl;
} 
else if(age >= 18) {
    std::cout << "Enjoy your visit." << std::endl;
} 
else { // if age == 18
    std::cout << "I don't believe you're really that young." << std::endl;
}
```

The reading of the code normally goes down one-line-at-a-time, but these `if` statements change the reading of the code around in order to skip code that does not meet the needed condition. This program defines a signed `int` called `age` and sets it to the value of 15. Once the `if` statement is reached, the value of `age` is compared with the value 18, and the comparison itself is simplified to a basic `true`/`false` value. Since the age is 15, the conditional resolves to `false`, and the code that prints `"You can't enter here."` will be run and the code that prints `"Enjoy your visit."` and `"I don't believe you're really that young."` will be skipped.

The `switch` statement is an `if` statement you use only when comparing the value of a single variable. 

```cpp
char letter;
std::cout << "Type in a letter: ";
std::cin >> letter;
switch(letter) {
    case 'a':
    case 'e':
    case 'i':
    case 'o':
    case 'u':
        std::cout << letter << " is a vowel!" << std::endl;
        break;
    default:
        std::cout << letter << " is a consonant!" << std::endl;
        break;
}
```

It goes by cases. In the case that the variable equals this, do this, and then `break` out of the switch statement. The `break` keyword gets you out of a switch or a loop and jumps you past it. If you don't include the `break`, the reading will continue until a `break` or the `default` case is found. You can see this happening in the above code. If there are no breaks or default case, an error will occur. The default case is executed if what the variable equals doesn't match any of the other cases given.

One other control structure in C++ is the *ternary operator*. It's used in assignment and is shorthand for an `if/else` structure.

It evaluates a condition in parentheses just like `if` statements do, and then puts the `if` and the `else` block between a colon.

```cpp
(<condition>) ? <runs if true> : <runs if false>;

int a = 0, b = 2;
int c = (a < b) ? a : b;
```

You're making two variables, `a` and `b`, and setting them to 0 and 2. Then, a third variable is made that gets the value of either `a` or `b`, depending on the truth/falsity of the expression `a < b`. If `a` is less than `b`, `c` will get the value of `a`, otherwise it will get the value of `b`.

```cpp
int max(int x, int y) {
    return (x > y) ? x : y;
}
```

This resolves to the maximum value of two numbers. It will return `x` if `x` is greater than `y`, otherwise it returns `y`. You can also put these operations inside of each other, and it's good practice to indent so that it's easy to tell what belongs to what. Here's an example of a function using nested ternary operators that finds out whether a number is signed or not:

```cpp
int signum(int x)
{
    return (x != 0)
            ? (x < 0) 
               ? -1 
               :  1 
            : 0;
}
```

It takes a number, `x`, and asks if it is equal to zero or not. If it is, it returns just zero. If it isn't, it asks whether the number is less than zero or not. If it is, -1 is returned, otherwise it returns 1. This operator is hated on by many people, but it's actually a very powerful operator that comes in handy a lot.


## Loops

Let's say you have a text string and you want to check and see if it contains specific characters. There is no command to just tell the computer to look at the text and tell you whether the character's there. It has to look at each character in the string one-at-a-time and raise a flag when the specific character is found. Or what if you had an array with 1000 elements that had to be set to specific values? This would take a long time to code in by hand. Luckily, there are constructs that make these long, tedious tasks simple and instantaneous.

A *loop* is a code construct that executes instructions repeatedly until a certain end condition is met; you reached the end of the string, for example, or your hit points ran out. 

Like `if/else` constructs, loops change the reading of the code so that the same code is read repeatedly, all while performing tests telling whether or not the end condition has been met. The simplest type of loop in C++ is called the `while` loop.

```cpp
int i = 0;
while(i++ < 10) 
{
    std::cout << i << std::endl;
}
```

This counts from one to ten. It's better than writing `std::cout << i++ << endl;` a million times. This makes a counter variable, `i`, sets it to an initial value of zero, and enters the while loop. When in the while loop, the first thing that is done before any of the loop's code is executed is the end condition is checked. In this case, the value of `i` is compared with the raw value 10, and if it is less than 10, a flag is set telling the CPU that the end condition is false. The code inside the loop will now be executed, and the value of `i` is now incremented by one after the loop's code is done. This is what the `++` does: increments a variable after its value is calculated and returned. 

The loop will not be broken out of until the end condition is met, or until a `break` statement is executed. Just like breaking out of a case, `break` jumps you out of a loop and sets the reading of the code to the first line after the loop's end. Alternately, `continue` tests the end condition again immediately and if it is not met, jumps the reading of the loop back to the beginning.

```cpp
int i = 0;
while(i++ <= 10) 
{
    if(i == 5) 
    {
        continue;
    }
    std::cout << i << std::endl;
}
```

When you run this loop, you'll see that it skips the number 5. This is because you told the program, using the `continue` statement, to jump back to the beginning of the loop and increment `i`, so the `std::cout` statement printing `i` in that iteration of the loop was never read by the compiler.

The second type of loop is called a `for` loop. Instead of having to keep track of an outside counter variable, you can initialize one right inside the loop. 

```cpp
for(int i = 1; i <= 10; i++) 
{
    std::cout << i*i << ' ';
}
```

This prints `1 4 9 16 25 36 49 64 81 100`.

`for()`'s parameters include the declaration and initialization of your counter variable, the loop's ending condition, and how much to change the counter after every iteration of the loop. Here, I set it to increment by one each time with `i++`.

`for` loops are great for initializing array elements or scanning strings or parts of strings.

```cpp
#include <iostream>
#include <cstring>

int main()
{
    std::string b = "Hey Jude";
    for(unsigned int i = 0; i < b.length(); i++)
    {
        std::cout << b[i] << ' ';
    }
    return 0;
}
```

A few things to note about this program. If you're going to be working with `std::string`s, include the `cstring` header as I've done. This will give you a bunch of functions you can use on `std::string`s, such as `length()`, used in the for loop.

Second, you can get the length of a string with `<string name>.length()`, but this returns an unsigned integer, so you have to use an unsigned integer as your counter variable inside the for loop.


## Logical Operators

While we're on the topic of conditionals and loops, it would be a good idea to understand the conditionals that go on behind those constructs if you want to be able to understand them. C++ gives specific types to the memory spaces it reserves so that the CPU can do the correct calculations with the numbers. 

There are only two numbers in all of computing: zero and one. The CPU interprets groups of these zeros and ones in different ways depending on the setting of [flags](http://en.wikipedia.org/wiki/FLAGS_register), special bits in the CPU that tell it what kind of number it's dealing with in the current instruction of the program. 

If the compiler comes across a statement that compares values, such as what we've been doing with the conditionals and loops, it will change the variables to their raw values and subtract one from another. Say we have something like this:

```cpp
int a = 1, b = 2;
if(!(a < b)) std::cout << "A is bigger." << std::endl;
```

When the compiler gets to the `if` statement, it evaluates the `!(a < b)` expression by breaking it down and simplifying it in a number of steps:

```cpp
!(a < b)
!(1 < 2)
!true
false
```

Underneath, it is pulling the values of `a` and `b` out of their memory spaces and subtracting `b` from `a`. If the result is positive and greater than zero, the left is greater than the right, and the code resolves to `true`. If the result is negative, the left is less than the right, and it resolves to `false`. If the result is zero, both left and right are the same, but it still resolves to `false`, because we want less than, not less-or-equal.


## Command Line Arguments

Using Code::Blocks, you're not really going to be using command line arguments, but you might if you're making command line projects. In this case, you'll often need to give the program certain inputs upon startup so it knows in which mode to run, for example. The handling of command line arguments is similar to that of normal variables, but with some extra things to keep in mind.

When calling `g++` (your C++ compiler) from the command line, you'd type something like this:

```
$ g++ file.cpp -o program_name -std=c++11
```

`g++` is the name of the program you're running, and everything after it is an option you set or data you input. In this example, you're giving `g++` the name of the source file it is to compile and what the name of the end program will be, and you're also telling it to use the C++11 standard (the standard of C++ I've been using throughout this tutorial). I like to use a few extra options:

```
$ g++ file.cpp -o program_name -std=c++11 -Wall -Werror -pedantic -O3 
```

Now, as well as telling `g++` the name of the source file and the end program, I'm also telling it to warn me about any and all sloppy coding I'm doing (`-Wall`), to treat those warnings as compiler errors so a faulty program won't be made (`-Werror`), to warn me if I'm writing code that doesn't conform to the standard (`-pedantic`), defining the standard as C++11 (`-std=c++11`), and optimizing the code so that it will run faster (`-O3`).

These are all there to make `g++` a very flexible and versatile tool. These options are command line arguments to `g++`. Your programs can use these kinds of inputs as well.

First, when making a program that uses command line arguments, you need to add a few arguments to `main()`. When counting arguments, you need a count of how many there are, and an array to store them. Here's what `main()` looks like with these:

```cpp
int main(int argc, char* argv[])
{
}
```

where `argc` is the number of arguments (*argument count*) and `argv` (*argument vector*, a list of strings containing the text you typed in) is a list of all the arguments.

Using the arguments is as simple as referencing them through `argv`:

```cpp
#include <iostream>

int main(int argc, char* argv[])
{
  if(argc != 3) {
    std::cout << "Error: program takes 3 arguments, "
              << argc << "given." << std::endl;
    return -1; // return an error condition.
  }
  std::cout << argv[1] + argv[2] << std::endl;
  return 0;
}
```

This program takes two inputs, adds them together, and prints them to the screen. Compile it with this:

```
g++ file.cpp -o add -Wall -std=c++11
```

And then run it:

```sh
> add 2 3
5
```


## Random Numbers

There are a lot of instances where you're going to need randomness in your programs, such as games, which need to be unpredictable to be fun and replayable. C++ provides basic utilities to make random numbers, but note that better random number generators exist, such as the Mersenne Twister. 

C++ really doesn't generate truly random numbers, but *pseudo*random numbers, as the order in which they're generated is the same. To get around this, you need to give the pseudorandom number generator a starting point, called a *seed*. This allows you to start picking numbers at different places in the list every time you need a random sequence of numbers.

First, to use the generator, you need to include both the `cstdlib` and `ctime` headers, which define the generator.

```cpp
#include <iostream>
#include <cstdlib>
#include <ctime>
```

To make a random number, you first need to give the generator a seed.

```cpp
srand(time(nullptr));
```

This sets the seed to the current system time. `srand()` is a function that sets the seed for the random number generator. `time()` returns the current system time.

Next, you need a variable to store the random number.

```cpp
int r = rand();
```

`rand()` generates a random integer from zero to `RAND_MAX`, which is a value that is different for every system and compiler. Send it to `std::cout` to see what exactly it is. 

To make a number in a certain range, modulo the value with the upper limit you want and add 1:

```cpp
int dieRoll = 1 + (rand() % 6);
```

Since modulo (`%`) returns the remainder after a division, no matter how big the number is, you'll be able to get a value between 1 and 6. What's happening is that `rand()` is returning some possibly huge number. That number is divided by 6 and the remainder is returned. 

No matter how big the number, dividing it by something and taking the remainder drastically cuts down the end value. You can only have a remainder as small as zero or as big as one less than the number you're dividing by. So the list of possible values for `dieRoll` will be between 0 and 5 inclusive. Adding one to that will shift the distribution curve to the right, making the possible range of values fall between 1 and 6 inclusive.

Since this is how C++ defines the usage of random numbers, getting a number in a specific range is a bit backwards. Here's how to get a number between 3 and 10, for example. First, calling `rand()` with a modulo returns a list of possible values (called the range) from zero to one less than what you're modding it by. Adding one, as we did with the previous example, moves that range up by one, returning a range between 1 and the number modded by. So to get between 3 and 10, you need to mod `rand()` by the range of numbers (10 - 3, or 7 possible values) and add the lowest number in the range (3). You'll get:

```cpp
int r = 3 + ((rand() % 7) + 1);
```

To make this easier, you can just put all that in a function:

```cpp
int rand_int(int x, int y)
{
    return x + (rand() % ((y - x) + 1));
}
```

However, one thing to note is that this function can be misused and can give errors or weird results. What if `x` is greater than `y`? What's a random number between 35 and 12? That doesn't make sense. We need to be able to catch this error case and correct it, or we risk messing up the program.

```cpp
int rand_int(int x, int y)
{
    if(x > y) { // swaps x with y.
        int tmp = x;
        x = y;
        y = tmp;
    }
    int range = (y - x) + 1;
    return x + (rand() % range);
}
```

This function is relatively safe, disallowing you to screw up the value very much, but it can be made a little bit shorter and more readable. Here's another version:

```cpp
int randint(int max, int min = 0)
{
  return (min <= max)
    ? ((rand() % ((max + 1) - min)) + min)
    : ((rand() % ((min + 1) - max)) + max);
}
```

This uses a ternary to swap the values just based on if the first is less than the second, all in one return statement, making a pure function from two numbers to a number.


## Structures and Classes

There are going to be times when writing complex code that you have a lot of similar variables that are all related to each other. While having them hanging around is alright, this can become cumbersome when you have very large programs with a lot of different names. As well as becoming too much to manage, things can get clobbered, overwritten, or inadvertently changed. 

If you're making a database for a company's employee records, you have to have a variable for the person's name, personal information, company information, wage, hours worked, etc. and each of these for each person. This is absolutely unruly and is often too much to manage for humans.

To make this easier, you can make a data structure out of the variables you need instead of making individual variables for each person. There are two types of data structures in C++. The most basic is the C-style data structure, denoted with the name `struct`. Here is a basic struct that defines the coordinate information of a point in ℝ²:

```cpp
struct Point2D
{
    int x, y; //make x and y
};

int main()
{
    Point2D p; //make a name for the struct: p
    p.x = 2;   //set x inside struct
    p.y = 3;   //set y inside struct
    std::cout << p.x << ' ' << p.y << std::endl;
    return 0;
}
```

You're making a group of variables with the `struct` and setting them to initial values in `main` before printing them out. You're grouping together the two variables `x` and `y` and putting them in a nice, neat little package called `Point2D`. This effectively binds them to a name, so their individual names, `x` and `y`, don't clash with any `x`s and `y`s you might have in your main code. Once a variable is bound under a `struct`, it is called a *field* of that `struct`. You can only access that field by going through the `struct`'s name, which in the above program is `p`.

What's great about `struct`s is that you can make several of them without having to define them again. They're like variables that way. All you need to do is make multiple names for them. This way each `struct` will have its own set of variables that you can set to whatever you need.

The other type of data structure is the `class`, which one-ups `struct`s by giving them enhanced functionality. Classes bind variables and functions together under a single name that can be set to a variable and can have multiple copies, all different.

A simple example could be made from the `rand_int()` function I defined earlier. Note that classes are defined before the main function starts.

```cpp
class Random
{
    int x, y, range;

public:
    
    Random() : x(0), y(1), range(1) {
        srand(time(nullptr));
    }
    ~Random() {}
    
    // setters and getters:
    void setX(int x) {this->x = x;}
    void setY(int y) {this->y = y;}
    void setRange(void) {this->range = (this->y - this->x) + 1;}
    
    int getX(void) {return this->x;}
    int getY(void) {return this->y;}
    int getRange(void) {return this->range;}
    
    // member functions:
    
    void swapXY(void) {
        if(getX() > getY()) { // swaps x with y.
            int tmp = getX();
            setX(getY());
            setY(tmp);
        }
    }
    
    int getRandIntFrom(int a, int b) {
        setX(a);
        setY(b);
        setRange();
        swapXY();
        return getX() + (rand() % getRange());
    }
};
```

This class demonstrates most of the basic syntax for classmaking. I'm going to dissect this class and show you several of the main concepts you'll need to know to be able to use these complex data structures. 

A class is defined with the `class` keyword like this:

```
class <name> {<body>};
```

Classes are fundamental to a style of programming called *object-oriented programming*, a way of building programs that treat the programs' individual parts as objects that interact with each other. A class is basically a template, outline, or description for such an object. You use classes basically like you use `struct`s, except instead of just variables, you have functions, too.

The above class may look scary, but it does nothing different than the `rand_int()` function I made earlier. If you understood that, you only need to understand C++'s object-oriented concepts to be able to understand and utilize this `Random` class.

Let's look at the data items that make up this class. 

```cpp
int x, y, range;
```

These are some variables defined inside the class. Inside a class, variables are called the class's *members*. Class members can be hidden from things outside the class, making the class an interface for code. These variables are private to only the class, and can't be seen by the rest of the program because they're only meant to be used inside the class. 

```cpp
public:
```

This is a keyword called an *access specifier*, and this keyword is responsible for telling C++ which members the program can see and which ones it can't. The `public` keyword means anything defined after it is able to be utilized by the rest of the program. Members are `private` by default, which means they are hidden to the rest of the program, which is also why I didn't explicitly put a `private` keyword inside the class. These members are private because if other code changes them, the end result will be screwed up.

```cpp
Random() : x(0), y(1), range(1) {
    srand(time(nullptr));
}
```

This is a special, class-specific function called the *constructor*, which is called when the class is made, before any of the class's other code is run. 

Constructors are used to prepare the class for whatever it might need to do. It sets variables to default values, allocates memory, or calls another function to start things off.

The constructor doesn't take a return value, not even void, and is always the same name as the class.

The syntax for making the constructor is:

```
<Class name>() : <initializer list> {body;}
```

The *initializer list* sets the class's private members to default values so you don't get garbage output. Start the initializer list with a colon between the argument list and the body, and type the names of each of the variables, separated by commas, along with the value you want them to have in parentheses. The above initializer list sets `x` to 0, `y` to 1, and `range` to 1.

```cpp
~Random() {}
```

This is the class's *destructor*, the opposite of its constructor, which is called automatically when the class is no longer used by the program. It takes no arguments and no return value, doesn't have an initializer list, cannot be called by outside code, and is always the same name as its class. This is used for freeing up memory or handling errors that might come up if the program is stopped and there are still calculations going on.

```cpp
// setters and getters:
void setX(int x) {this->x = x;}
void setY(int y) {this->y = y;}
void setRange(void) {this->range = (this->y - this->x) + 1;}

int getX(void) {return this->x;}
int getY(void) {return this->y;}
int getRange(void) {return this->range;}
```

Assigning different values to class members is done with setters, and getting their values back is done with getters. These functions are used so that access to class members is as explicit as possible. Remember you want variables to do what they say on the label, so they need to be changed as little as possible.

The `this` and the arrow (`->`) used here tells us that we're going to be referencing the value of a class member specifically, and not some other random value in the program. `this` is a reference to the class, and the arrow just maps the class to the value.

(unfinished)




