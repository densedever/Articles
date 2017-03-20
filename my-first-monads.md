TIL: I've just started working with monads using JavaScript!

I don't really know monads enough to be able to describe them to beginners, or even to experienced developers who've never heard of them, but if you make a large amount of functions in your programs, you've likely already used them without knowing it! In fact, if functions are your primary workhorse, you WILL make them eventually by yourself, given enough time. You just might not call them "monads."

The JavaScript I'm practicing with was stolen from Douglas Crockford's talk, "Monads and Gonads."

A lot of you have worked with macros, which are generalized instructions fed with some parameters of your choosing.

Here's a function that acts as sort of a macro, called a "macroid", used to define what's called an "identity monad":

```
function MONAD() {
    return function unit(value) {
        var monad = Object.create(null)
        monad.bind = function(func) {
            return func(value)
        }
        return monad
    }
    return unit
}


var identity = MONAD()
var mymonad = identity("Hello, world!")
mymonad.bind(console.log) //=> "Hello, world!"
```

This `MONAD()` macroid is a function that returns a function called `unit`, which takes a value you'll be using in the monad.

In this function, you're defining a function `unit` which takes a value and returns an object we've made inside it.

This object is called `monad`, and it has a `bind()` method on it that takes a function and returns it applied with the `value` parameter you passed into `unit()`.

`unit()` then returns the object `monad`, and then `MONAD()` returns `unit()`.

The way I use this function is that I make a variable to hold the function that `MONAD()` returns and another variable to store the value of that stored function after it's applied with a value, in this case it's the variable `mymonad` with the value `Hello, world!`.

I then call mymonad's `bind()` method passing in a function (as its definition requires) and that function is applied with the value passed into `identity` (or `bind` inside `MONAD()`'s `monad` object).

This results in me applying `mymonad.bind()`'s function (passed as an argument) with identity's argument (`"Hello, world!"`).

How is this useful?

I can put any function in there that I want (that plays nicely with its internal structure).

Say I have the function

```
function sayStuff(things) {
    console.log(things + " or something like that")
}
```

and I then call `mymonad.bind(sayStuff)`.

This will result in the string `Hello, world! or something like that` being echoed to the console.

This is a simple example, but on the whole, monads are used to wrap values (keeping them secure) and peek at them without gaining explicit access to them (for security reasons).

For example, anything in the `X` monad I can't access without explicitly wrapping my data up in the `X` monad, walling it off from the rest of the program.

Whenever I need to get a value within the `X` monad, I can't unless I use another version of the `X` monad that can work with the value.

Programming with monads makes your data more secure in a purely functional way (without having to use data encapsulation as in object-oriented programming) and doesn't require the use of classes at all! Only an already-existing primitive type: the function!

You've actually already been using monads in your everyday coding: the `Ajax` and `Promise` objects are monads!

I hope this helps you guys. It certainly helps me, as one of my main languages, Haskell, uses monads everywhere within it, and this will hopefully help your coding as well!

Using ES6, this code can be shortened to one or two lines:

```
const MONAD = () => value => ({bind: func => func(value)})
```

and works the same way:

```
const mymonad = MONAD()("Hello, world!").bind(console.log)
// "Hello, world!"
```

There's my call-to-arms for you guys to start learning ES6 if you haven't already. It really helps a lot!
