# Functional Programming in a Nutshell

I saw a post in another group on the features of OOP and was inspired to put together my own post (because I hate OOP)!

Features of functional programming:

1. Functions as first class-citizens
2. Referential transparency 
3. Function type signatures
4. Currying 
5. Partial application
6. Inheritance through function composition 
7. Functors
8. Categories
9. Groups
10. Monoids
11. Monads
12. Encapsulation through closures
13. Call chaining 
14. Recursion
15. Polymorphism through pattern-matching

Functions in a functional programming style are thrown around as often as variables in imperative programming languages. Being the main workhorses of your calculations, they're "first-class citizens" in your program.  

As a rule, functions must only take arguments and return expressions, and that's it. They must not reference any outside data or change the value of any outside variables (behaviors that are called *side-effects*). Outside data they might need to work on are passed into the function as arguments. They do just what the label says and nothing more. These functions are called *pure* functions, and have "referential transparency", meaning they're black boxes interchangeable with any other function having the same type. 

Functions have types too, even if the language doesn't explicitly specify them! They're categorized by the types of each argument they take (in order!) and what they return. This info is separated by arrows. Example: the function

```
function add(x, y) {
  return x+y;
}
```

is a pure function of type
`number -> number -> number`
which means it takes two numbers and returns another number (assuming we're coding in JavaScript). 

Functions of n arguments (formally called *n*-ary functions) can optionally take one argument and return a function expecting the rest of the arguments, which can be assigned to a variable and used to make factories. 

N-ary functions can be passed one argument and applied on it with another application of the rest of the arguments ("applying" a function == "calling" a function). Example:
```
function add(x) {
  return function(y) {
    return x+y;
  }
}.autoCurry(); // defined in wuJS

add(2); => function()
add(2)(5); => 7
```

Functions can be applied on other functions using the same data for both applications. The output of one function is used as the input for the other. An example is a pipe in command line scripting. Example:

```
function sum(list) {
  return list.reduce(add);
}

function square(list) {
  return list.map(function(x) {
    return x*x;
  });
}

function sumSqrs(a) {
  return sum(square(a));
}
```

The function `square` was applied on `a`, and that result was passed into an application of `sum` returned by `sumSqrs` applied with `a`.

Functions can be passed into other functions as arguments or be returned from functions. Such functions are called *functors*, or *higher-order functions* (but there's a subtle distinction between these two terms that's relatively unimportant for this article). Example:

```
[1,2,3,4,5].map(function(x) {
  return x*2;
});
=> [2,4,6,8,10]
```

Here I'm going to be throwing some terminology at you that will help you understand oft-mentioned topics in functional programming and mathematics.

*Categories* are groups of data and functions relating that data. They're the building blocks of *category theory*, a branch of mathematics that generalizes a bunch of other branches of mathematics like formal logics, combinatorics, and topology. Category theory is often the basis for pure functional programming languages, and learning a bit about this will only ever help you use these languages to their fullest, though an understanding of it is not required, so don't freak out if you can't understand it. 

A function mapping a category to itself is called an *endofunctor* and that operation is part of the basic laws of how functions work. It's a scary word, but a simple thing, so don't run for the hills yet. 

A *group* is a set and a rule for transforming any two elements of the set into a value. A classic example is a set of integers with the addition operation, making a third element: the addition of two of the group's elements. 

*Monoids* are a set of things and a rule for combining those things that itself obeys the rules of associativity, commutativity, and identity with a pre-packaged identity element. An example is a measure of the hours on an analog clock. You put any integer in, and always get back 1-12, and can combine operations any which way and still get back 1-12. 

A *monad* is a category mapped to itself that comes packaged with some methods to transform it (that morph one functor into another): 
  * a transformation from an identity to an endofunctor, 
  * and from an endofunctor to itself. 
They're often used for pulling values out of nested structures or combining impure function operations. 

*Closures* are functions that use data inside them when you call them. Example: 

```
function adder(x) {
  function inc(y) {
    return x + y;
  }
  return inc;
}

var incBy = adder(3);
incBy(5); => 8
```

What's going on is that `incBy` is being substituted with `inc`, 5 is being substituted by `y`, and in the variable binding of `incBy`, `incBy` is substituted with `adder`, and `x` is substituted with 3. `5 + 3 = 8`

This is a good way of encapsulating data without using classes, just functions. 

As well as being composable, functions can be chained together. 

```
[1,2,3].concat([4,5,6])
    .map(function(x) {
        return 2*x*x;
    })
    .filter(function(x) {
        return x>10;
    })
    .reduce(function(x,y) {
        return x*y;
    })
    .toString()
    .split();
```

This sequentially applies multiple functions to the same piece of data, putting it through a transformation pipeline. This is a fairly common thing in shell scripting and is brought to you in functional programming! In fact, this is a general programming model of functional programming (basically). 

*Recursion* is extending the definition of a function by applying said function inside its own definition. 

Here's an example of a function defined recursively that sums up every number from 1 to n:

```
function sum(n) {
  return n<=0? 0: n+sum(n-1);
}
```

Unrolling the function calls reveals a very long function definition declared in an extremely succinct way. Such recursive functions can be used (pretty much) anywhere loops can in imperative programming languages (with a few edge cases). They can draw fractals, operate over lists, navigate tree nodes, and on and on...

A *polymorphic function* is a set of functions that do the same thing, but have unique type signatures. A function that adds numbers is different than one that adds strings, for example. In pure functional languages like Haskell, these can be captured with *equations*. An example of equations in C++ (forgoing the use of templates) would be a set of functions with different prototypes:

```
int add(int x, int y);
double add(double x, double y);
. . . 
```

Another way of doing that in one function without using equations is with *pattern-matching*: comparing the type of variables, and returning a different value based on that type. In imperative languages like C, `switch` is the construct most often used for a pattern match on a value. Example:

```
function double(x) {
  switch(typeof(x)) {
    case "number":
      return x+x;
    case "string":
      return concat(x, x);
  }
}
```

Functional programming is one of the oldest styles of writing code, yet a majority of working programmers consider it difficult, foreign, and even useless!, but it's not that hard. It just requires a shift in thinking. 

When learning a coding style, don't worry about the language, worry about what you're *doing* with it. What is happening to your data? How is it related? Can that relatedness be exploited?

Don't think of interrelationships and interaction of data like OOP teaches you to think. 

Instead think of what the problem you're solving looks like. Don't focus on *how* to solve the problem, focus on defining how the problem *looks*, and the solution will fall into place. 

Here's an example: you want to double every integer in a list. 

The imperative way of doing that says to iterate over that list and double each value one-by-one. 

```
var nums = [1,2,3,4,5];
for(var a=0; a<nums.length; a++) {
  a *=2;
}
```

The functional way says to define a version of that list where each element is double the value:
```
var nums = [1,2,3,4,5];
nums.map(function(x) {
  return x*2;
});
```

The functional way cuts out unnecessary crap. You don't have to worry about a loop, you don't have to worry about having a counter variable around and assigning values, instead it's just one definition. No assignment. No loops. No worries.
