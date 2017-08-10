# What's the Simplest Programming Language?

A beginner question I see a lot is "what are programming languages capable of?" This is a question that has really gotten my computer science gears churning the last few years and I got to wondering "what is the simplest a programming language can be and still do everything?"

It turns out that a programming language made up of nothing but single-argument functions is all you need. Just something that accepts one value, returns one value, and does nothing in-between.

But wait, doesn't that need two things: functions and values? No!

The common paradigm popular programming languages like Ruby, Java, or C++ gives you is that functions are separate constructs from data. JavaScript programmers, however, know better. Functions are data too! They can be passed to functions, returned from functions, used in expressions, etc.

How would you define primitives with functions? Aren't functions actions, not the things being acted on?

Again, it has been demonstrated that need not be the case.

In a format called "Church encoding", defined in the "Church-Turing thesis", it defines an integer *n* as the *n*-fold composition of single-argument functions f:

```
0 -> f(x) = x
1 -> f(x) = f(x)
2 -> f(x) = f(f(x))
3 -> f(x) = f(f(f(x)))
... -> ...
```

As you should already know, *function composition* is feeding the output of one function into the input of another, chaining them together so that instead of having two functions: one from `A -> B`, and one from `B -> C`, you get one function from `A -> C`!

So these numbers are defined as a function being applied to itself n times, and being fed an x, x being a stand-in for zero.

Floating-point numbers can be defined the same way by representing the whole part and the division part as a pair (represented as a higher-order function, which is a function that takes and/or returns other functions). Numbers are not needed!

Booleans can also be defined in terms of functions! Think of them not as primitive data types, but of functions that choose between two arguments:

```
True = function(a) {
  return function(b) {
    return a
  }
}
```

```
False = function(a) {
  return function(b) {
    return b
  }
}
```

Notice that neither of these are actually taking two arguments, but are returning functions that take the rest of the needed arguments, one argument per function, one-after-the-other. This is a process of *partial application* of function arguments through a method called *currying*. You can do all if-logic with just function application! 


```
predicate x if-clause else-clause
```

```
Predicate = function(p) {
  return (function(t) {
    return (function(f) {
      return p
    })(f) // false value passed in
  })(t) // true value passed in
}
```

See the pattern? If/else statements are not needed!

Logical operators like `&&`, `||`, `!`, and others can be defined in similar ways to the if clause.

```
And = (function(p) {
  return (function(q) {
    return p
  })(p)
})(q)

Or = (function(p) {
  return (function(q) {
    return p
  })(q)
})(p)

Xor = (function(t) {
  return (function(f) {
    return Not(f)
  })(f)
})(t)

Not = function(p) {
  return (function(t) {
    return (function(f) {
      return p
    })(t)
  })(f)
}
```

How about operators like `==`, `<=`, `>=`, etc.? Same pattern!

```
isZero = (function(n) {
  return n
})((function(x) { // function passed into the first function
  return false
})(true))
```

Note that we're working with Church numbers, not integers, and `false` and `true` can be substituted with their definitions.

How about a `<=` operator?

```
LEQ = function(m) {
  return function(n) {
    return isZero(minus(m, n))
  }
}
```

An equality operator?

```
EQ = function(m) {
  return function(n) {
    return and(LEQ(m,n), LEQ(n,m)) // notice that m and n are switched around in the two calls!
  }
}
```

Other operators can be done as well, such as all the arithmetic operators, as well as functions that increment and decrement, but I'm not there yet, I'm working on understanding them well enough to explain them.

Lists/arrays can be defined as pairs:

```
Pair = function(x) {
  return (function(y) {
    return (function(z) {
      return z
    })(y)
  })(x)
}

// gets the first element of the pair
First = (function(p) {
  return p
})(function(x) {
  return function(y) {
    return x
  }
})

// gets the second element 
Second = (function(p) {
  return p
})(function(x) {
  return function(y) {
    return y
  }
})

```
A bunch of list functions can be defined as well, such as `nil` (makes an empty list), `isNil` (checks whether a list is empty), `cons` (prepends a value to a list), `head` (returns list's first element), `tail` (returns everything in the list but the first element), and others. You would not believe how much you can do with just these functions.

What about repetitive operations such as loops and iteration? These are captured in a few different ways, the most common being a `fold` operation (which can be used to define `filter()` and `map()` operations as well), and substitution by feeding a function into itself.

To do looping using nothing but single-argument functions requires a certain type of function called a *combinator*. This is simply a function that only takes local variables and doesn't mess with global variables inside it.

There are many types of combinators such as the S, K, I combinators, and others, but what we're interested in is the *Y combinator*.

```
Y = function(le) {
    return (function(f) {
        return f(f)
    }(function(f) {
        return le(function(x) {
            return f(f)(x)
        })
    }))
}
```

Here is an example:

```
var factorial = Y(function(fac) {
    return function(n) {
        return n <= 2 ? n : n * fac(n - 1)
    }
})
```

And its application:

```
var number120 = factorial(5)
```

I'm not even going to try to explain how this combinator works in this article because I'd be here for an hour, but if you look into it, there are great explanations on YouTube building it up from first principles and defining it with easier combinators such as fixed-point combinators.

Basically the repetition is done with substitution and recursion instead of iteration. Feeding in larger and larger function expressions into the Y combinator, expanding out just like the counter variable is incremented in a for loop.

In short, functions can do everything loops can do and more, and these concepts are actually used in the real world. These types of functions are what "pure functional" programming languages such as Haskell and ML are broken down into by their compilers. This reduction is very powerful for mathematically proving programs to be correct; something almost impossible to do with sufficiently large C programs, for example.
