# From Scheme to JavaScript

In May 1995, Brendan Eich was hired by Netscape with the promise that he could implement a "[scheme in the browser.](https://brendaneich.com/2008/04/popularity/)" He convinced Netscape's boss that a unique, quickly-made language aimed at designers and developers was the right direction for Netscape Navigator, which was fighting tooth-and-claw with Java at the time.

Netscape founder Marc Andreessen named the language prototype Mocha at first, but it went through [several different names](https://www.w3.org/community/webed/wiki/A_Short_History_of_JavaScript) over the next few years.

Netscape decided that the best course of action to make the web more dynamic and accessible to enthusiasts, designers, and developers was to give HTML a simple-to-understand scripting language that laymen could pick up, but could also play alongside larger, more "enterprise-grade" languages like [Java](http://www.computerworld.com.au/article/255293/a-z_programming_languages_javascript/).

The original idea was that the language was meant to be scheme-like, however that idea was [scrapped](http://www.infoworld.com/article/2653798/application-development/javascript-creator-ponders-past--future.html) by Sun in agreements with them and Netscape in December of 1995, as license agreements had to be put in place if it was to be a language that played alongside Java.

Even though Scheme and JavaScript are mostly separate languages nowadays, and indeed throughout their histories, [some features](http://community.schemewiki.org/?scheme-vs-javascript) are common between the languages. Here are some of those common features.

## First-Class Functions

Scheme and JavaScript both support functions as first-class citizens. While functions in JavaScript aren't really functions, but spinoffs of Object(), functions in Scheme are similar to functions in Rust, in that they have implicit return statements and are first-class.

In JavaScript, functions can be set to variables, passed to functions, returned from functions, used in expressions, and many other things. In Scheme it's no different.

## Single Namespace

There really is no true concept of a namespace in either Scheme or JavaScript. The global execution context is considered the only namespace. Languages like Python have implicit namespaces defined by the name of the current file, while languages like C++ have explicit namespaces defined by the user with the `namespace` language keyword. JavaScript didn't inherit any kind of mechanism like this, instead implementing it with the use of IIFEs, but [ES6's modules](http://exploringjs.com/es6/ch_modules.html) might serve a similar role.

## Closures

[Lexical closures](https://en.wikipedia.org/wiki/Closure_(computer_programming)) are a feature of JavaScript's scoping rules applied to functions. If you define a function inside an outer function, along with some local variables, the inner function has access to those other local variables beyond the lifetime of the function's execution, meaning the scoping access is preserved among successive applications of the outer function. Here's one of the simplest examples I can come up with:

```
function closure() {
    let x = "world"
    return function() {
        return "Hello, " + x
    }
}
let clo = closure()
console.log(clo()) //=> "Hello, world"
```

I made a function (the aformentioned "outer function") called `closure` that defined a local variable `x` and returned another function (the "inner function") that returned the value of "Hello, " plus the value of the local variable in the scope of the outer function. 

Successive applications of `clo()` will ensure that `clo()` has access to `x` in every application of it. It's a function that brings a scope along with. This is all closures are. It's a very simple concept, but one that's talked about as if it's hard to understand, difficult, or mysterious.

Scheme is a terse, simple, yet powerful language that has done the computing world good, but in the end, JavaScript is not Scheme. It has a few similarities, and can even be written in a similar way, but the two languages are largely orthogonal. In my opinion, that's how they should stay. JavaScript brought many useful concepts such as higher-order functions and lexical closures to the mainstream programming world, and that it branched off so far can only be a good thing. While many people might think JavaScript broke the web programming world, in a way it made it what it is today, and the language's flexibility is one of its biggest boons contributing to its wide success.








