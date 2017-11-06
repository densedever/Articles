# Expressive JavaScript

JavaScript is one of the main backbones of the modern web, and anyone who's planning to make a website even with Wix, SquareSpace, or WordPress will benefit from some knowledge of one of the first real programming languages in widespread use on the web: JavaScript!

JavaScript was originally a language for performing simple manipulation of parts of a webpage, but now it's grown into its own bona fide programming language! It's capable of anything from webpage manipulation to server-side tasks to database requests to desktop apps to animations, drawings, and games!

If you're going to be a web developer of any competence, it would only help you to learn JavaScript, as its usage domain is only getting larger and more widespread!

One of the biggest benefits of using JavaScript (JS) is that you already have something that runs the language: a web browser! It doesn't need any setup to start using right now, there's nothing to install.

Given that, there are some tools that will help you write programs in an easy way. Get a text editor such as Atom, Sublime Text, Visual Studio Code, Notepad++, or Vim. 

The purpose of this book is to teach you how to write JavaScript in a more modern way that intends to be simple, yet future-proof and scalable. There's been a huge shift in the way JavaScript is written in the past 10 years, and this teaches you a way of writing code using nothing but expressions, hence the title, *Expressive JavaScript*. 


## Part 1: The Basics

### Basic Data Types

In this chapter I'll teach you how to get to a place where you can actually write and execute code, and I'll talk about how programs work and what's in them.

To get to a place where you can write JS code, go to your browser and hit F12 (or control + shift + i in most popular browsers), or look for the "Developer Tools" to bring up a "console" where you can write JS code and immediately see the results. This console allows you to write one line of JavaScript code, press enter, and run the code you just wrote. It's perfect for practicing, playing around, calculating stuff, or testing things.

For example, try typing in `2 + 2` into the console and pressing enter. You'll get a 4 back. `2 * 5` will give you 10, as an asterisk is a computer's multiplication symbol. So now we've established that web browsers can do math. This math works the same as real-life math, too. Did you know that 2 + 3 is equal to 3 + 2? Is that true? We can test that! Type in some parentheses to group the terms, and between them put two equals signs:

```js
(2 + 3) == (3 + 2)
```

Now press enter. What comes up? The word `true`! Now we've established that not only can web browsers do math, but they can do logic! We'll see more of this a bit later.

*Note:* The things you're typing into the console so far are called *expressions*, which are just terms that can be reduced to a single value. `2 + 2` is an expression because it can be reduced to `4`. Expressions are flexible and can build on top of each other or be stuck together to make larger expressions, all reducing to one value in the end. They're the basis for a large amount of complexity, capable of making whole programs by themselves.

This interactive console is not the only way to run JS code. If you don't want to use the console, you can write JS into a file ending with the extension `.js`. This file is included in an HTML file and the results can be seen either on the webpage or in the console.

Now for some actual code instead of boring numbers. Typing in the phrase `alert("Hello world")` will bring up a dialog box saying `Hello world`. `alert()` is code that brings up this box, and the thing between the parentheses is what will be displayed inside it.

To give JavaScript data to work with as opposed to just output, instead of `alert()`, you'd use `prompt()`. These two pieces of code are good for quick testing on personal projects and small tests of ideas, but should rarely be used in actual websites. There are *far* better alternatives.

For those who have never programmed before, such as those whose first languages were HTML and CSS, there are a certain set of things you can do with programming. You have things you can store, things you can say, things you can tell the program, things you can repeat, things you can structure, things you can decide on, and many other things. 

 * Things you can store are called *data*.
 * Things you can say are *output*.
 * Things you can tell the program are *input*.
 * Things you can repeat are *maps* (and others).
 * Things you can structure are *objects*.
 * Things you can decide on are *conditionals*.

A thing you do to get a result is a *process*, and a thing you do repeatedly to get a result is an *algorithm*. Computers work in terms of processes and algorithms, and it is your job as a programmer to tell the computer how to do what you want.

The previous program using `alert()` introduced two different types of data: functions and strings. `alert()` is a function, a piece of code that can be run by typing its name. The data you put inside the parentheses is a string of text reading "Hello, world!", called a *string*. 

Functions are one of the most important types of data in all of JavaScript. They will be your go-to tool for everything to come, so let's get familiar with them early on.

The `function` keyword tells the browser that we're about to define a function. Functions define a relationship between two pieces of data. You can put data into them, and get data back out. The input is called an *argument*, and the output is called the *return value*. Here's a function that adds two numbers:

```js
function add(a, b) {
  return a + b; // gives you back the sum of a and b
}
```

This can also be written as

```
const add = (a, b) => a + b
```

without the `function` and `return` keywords, and the curly braces. This will be the most common function syntax I'll be using here.

The two pieces of data the function takes in, the two arguments, are `a` and `b`. These are just two numbers, any numbers you like. You use this function by saying its name, `add`, putting the parentheses, and then putting two numbers inside, separated by commas. Example:

```js
add(2, 3)
→ 5
add(3, 2)
→ 5
add(0, 0)
→ 0
add(2, -5)
→ -3
add(add(1, 2), 3)
→ 6
```

As you can see, it works as expected, and follows the laws you usually expect addition to have. This is insanely important as you'll see to come, because these laws define how your functions can be used without you having to explain them in documentation. Less work for you in the end!

What I was just doing by running the `add` function and getting back a result is *function application*. I was *applying* the `add` function to the data I put inside. The last example above put an application of `add` inside another. In this case, the inside gets applied first, then the outside, always.

Now you've been introduced to a third type of data: numbers! Usually in programming, the number `3` is different than the number `3.0` due to how the hardware is. A whole number `3` would normally be called an `int` or an `integer`, and `3.0` would be called a `float`, or *floating-point value*. You don't need to worry about this in JavaScript though, because they're both just called `Number`s.

Another data type is called an *array*, or a *list*. This puts together a bunch of different data into one structure - a data structure! Lists are surrounded by `[` and `]`, and the data is separated by commas. Some examples are:

```js
[1, 2, 3]
["a", "b", "c"]
[true, true, true]
[3, null] // with an empty value at the end
```

The cool thing about these is that there are a whole bunch of different things you can do with them. They don't act like numbers, but there are a few key things that will define the rest of what we'll be doing here, so it will pay off to look at a few of the array's *methods*, which are functions that are attached to a data type.

Here's a playful one:

```js
[1, 2, 3].reverse()
→ [3, 2, 1]
```

This reverses the list's elements.

Here's one that joins a list of letters into a string:

```js
["h", "e", "l", "l", "o"].join("")
→ "hello"
```

`.join()` takes a string, and puts everything in the list together using that string. It was empty, so the letters were just smushed together by themselves.

You can also put more methods onto the end:

```js
["h", "e", "l", "l", "o"].join("").toUpperCase()
→ "HELLO"
```

And more!

```js
["h", "e", "l", "l", "o"].join("").toUpperCase().concat("!!!")
→ "HELLO!!!"
```

You can see where I'm going with this...

At each method, the original list at the beginning is being changed slightly until the last method application. This a smooth pipeline of transforms that the data is going through that gives a result at the end. This is a very powerful thing called *function composition*, which has entire branches of math behind it. Lists, their methods, and their being chained together like this make up an entire model of computation just by themselves, and this is what I'll be teaching you in this paper.

Writing long pipelines is fun and all, but there should be a way to hold intermediate values, right? This is where I'm going to touch on arguably one of the most dangerous aspects of writing code that is both simple and predictable: storing data as program state.

Let's take the last example. This pipeline transforms the data one step at a time, and the transformations look like this:

```
["h", "e", "l", "l", "o"] → "hello" → "HELLO" → "HELLO!!!"
```

Now what if you just want the `"hello"`? You could just use the expression `["h", "e", "l", "l", "o"].join("")`, but it gets hard to read when you have to reuse the same expression in many places of the same part of code. In this case you'd store away the value in a space called a *variable.* This is done with a keyword called `const`. Example:

```js
const hello = ["h", "e", "l", "l", "o"].join("")
alert(hello) //=> "hello"
alert(hello.concat(" there")) //=> "Hello there"
```

Using the `const` keyword this way is not dangerous at all, because that just says "the following name will be equal to this value, and also can never change." The trouble comes when you use two other keywords that do roughly the same thing as `const`, but allow the value to be changed: `var` (the obsolete word), and `let`. 

The reason `var` and `let` should be used very rarely (if at all) is that these allow you to change the values behind their names with another equals sign. This destroys any predictability in your code because the variables are no longer guaranteed to do what they say on their labels. These data are called *mutable state* because they're values that can mutate, or change.

I will be using `const` as much as possible here, possible for every value I assign names to. Consider it good practice to do the same. 

The next few things I'll go over are logical values and some common list and string methods, including the ones we just saw.

## Logic and Lists

## Part 2: The DOM
