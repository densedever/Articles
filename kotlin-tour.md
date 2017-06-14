# A Tour of Kotlin

Since I read about a lot of different languages, I thought I'd do a write-up on what I've found out about Kotlin: what it is, what its advantages are, and why you should care. 

Kotlin's popularity has been blowing up lately as Google endorsed it as an official development language for Android. Yet the most common thing I seem to see is people complaining "I've spent months/years of my life trying to learn Java! No way am I throwing that away to learn something new after spending so much time on it!" I have to say: you are making your life harder because of your stubbornness, and you will never realize it without taking that plunge. After learning this, I feel like my two years of Java were a complete waste!

Kotlin is a more simple transition from Java than having to learn a whole new language. Its base is the same, as well as many of the language constructs you already work with. It just doesn't overuse classes, so if you're sufficiently brainwashed into thinking that's necessary, you're gonna have a hard time. Otherwise, the code is simpler, MUCH more readable, and requires less structure, typing, and consideration. 

A similarity it has to Java is the existence of a main function, except divorced from a main class. This is simpler, and in addition makes the language more familiar and accessible to people used to programming in C, C++, Rust, Go, or Haskell.

Here I will give a short introduction to some of the highlights of the language and how you can immediately benefit, even if you don't think you will. 

Type declarations are a bit different, but don't vary much from a language like Rust or Scala.

In Java, a type is declared before the variable name, but in Kotlin, two different generic keywords introduce the identifier: `var` (for mutable variables), and `val` (for immutable constants): 

```
var foo: Int = 42
```

What sets this apart from Java is implicit type inference. After all, it's not a variable that has a type, it's a value. Put a value into a variable, and that's what type the variable will assume. Python programmers already take this to heart. Since this behavior is present, you can forget about declaring an explicit type!

```
var foo = 42 // has type Int!
```

Java's `auto` keyword has this behavior, but who needs to type that anyway? The `var`/`val` keywords also do away with having to type `final` for constants, because why work harder when you can change one character instead of typing a whole new word? 

Speaking of working harder, you also don't need to worry about typing semicolons, doing away with the most infamous class of errors!

Smart casting does away with planning out the type of your data and requires fewer explicit casts, especially in type checks. Stay tuned. 

Strings in Kotlin contain built-in template expressions, turning arbitrary code into a value inside the string inline, doing away with formatted printing and string building. 

Errors stemming from null values are vastly more difficult to make due to null values being baked right into native types! Instead of having a `String` variable that could contain a null value, you declare a variable with a type of `String?`, analogous to `Optional<String>` in other languages. Not only that, there's also `Int?`, or any other type, simply suffixed with a question mark. 

In addition, special operators allow dereferencing a nullable type that falls back on an alternate value should the dereference come up null:

```
var nullableStr: String? = "Hi"
println(nullableStr?.length)
// => 2
nullableStr = null
println(nullableStr?.length)
// => null
println(nullableStr?.length ?: -1)
// => -1
```

The main function is simple and so is its argument list:

```
fun main(args: Array<String>) {
    // cool stuff in here
}
```

Function syntax:

```
fun name(arg: Type = someDefaultVal): RetType {
    // stuff
    return SomethingOfRetType
}
```

Example:

```
fun even(n: Int): Boolean {
    return n%2 == 0
}
```

Function arguments support default values:

```
fun hello(arg: String = "world"): String {
    return "Hello, $arg!"
}
```

`$arg` is that awesome string template working its magic!

```
println(hello())
println(hello("Tom"))
println(hello(arg = "Baller")) // set a variable inline!
```

Variadic functions couldn't be easier:

```
fun numArgs(vararg argc: Int) {
    println("$argc passed.")
}
println(numArgs())
// => 0 passed.
println(numArgs(1, 5, 6))
// => 3 passed.
```

Due to type inference, a function's return type doesn't need to be specified! Furthermore, the curly braces can be omitted if the function returns a single expression, making concise yet readable code:

```
fun odd(n: Int) = n%2 != 0
```

Did I mention that functions are values too? Oh yes!

```
fun not(f: (Int)->Boolean): (Int)->Boolean {
    return {n -> !f.invoke(n)}
}
```

This `not` function takes an argument `f` that has the type of a function from `Int` to `Boolean`. It returns the value of a function from `Int` to `Boolean`. A function that works on other functions is called a "higher-order function."

Use this `not` function like this:

```
val notOdd = not(::odd)
```

A named higher-order function passed as an argument is prepended with the double-colon operator (`::`). 

We can also have unnamed functions!

```
val notZero = not {n -> n!=0}
```

This `notZero` variable has the value of an anonymous function (called a lambda) from `Int` to `Boolean`, indicated by `not`'s return value (`Int -> Boolean`) and the `Boolean` expression it returns. 

Lambdas are going to be some of your best friends, so since you're going to be spending so much quality time together, you don't have to do all that typing. Simple lambdas can just return their end values without specifying a variable (you're instead supplied one called `it`):

```
val negative = not {it >= 0}
```

Notice that it's good practice to declare functions with `val`, and indeed that should be your go-to declaration word for most variables, as there's really very little excuse to use `var`. 

The implication of this is that there are very few mutable variables in normal Kotlin code. This turns out to be a good thing, because variables are then what you expect them to be, without any surprises!

Here's what a basic `for` loop looks like:

```
for (i in [0..5]) {
    println("
        ${notZero(i)}
        ${notOdd(i)}")
}
```

`[m..n]` is a short way of stating a range from `m` to `n`. How great is that? Much more concise and readable than the horrendous eyesore that is `i=0; i<blah; i++`, especially for beginners!

Class-lovers rejoice because they're in here as well!

```
class Foo(val x: Int) {
    fun memberFn(y: Int): Int {
        return x-y
    }
    infix fun infixFn(y: Int): Int {
        return x*x + y*y % 12
    }
}

val bar = Foo(6)
println(bar.memberFn(4))
// => 2
```

What's cool about functions inside classes (which are called "member functions" instead of "methods" as if this is C++ or something) is that not only can they be applied the same way as in Java, but if they're declared as `infix`, they can be applied between their operands (something Java can't do)!

```
println(foo infixFn 4)
// => 4
```

Structs exist as well! Declare a class as a "data class", and the list of fields within parentheses:

```
data class Point(val x: Int, val y: Int)
val origin = Point(0, 0)
```

Data classes have several built-in methods such as `toString` that I don't yet have memorized, but are automatically generated along with the struct. 

Struct field destructuring is a thing:

```
val (x, y) = Point(2, 5)
println("$x $y") // => 2 5
```

Of course classes and structs aren't the only data structures, there are also lists:

```
val myList = listOf("a", "b", "c")
println(myList.size) // => 3
println(myList[1]) // => b
```

Lists have built-in methods such as `first()`, `last()`, etc. as well as a size property. 

A mutable list:

```
val myMutableList = mutableListOf("a", "b", "c")
myMutableList.add("d")
println(myMutableList.last())
// => d
```

But wait; there's more! You can also have sets:

```
val mySet = setOf("a","b","c")
println(mySet.contains("q"))
// => false
```

And hash maps:

```
val myMap = mapOf("x" to 1, "y" to 2, "z" to 3)
println(myMap["z"])
// => 3
```

Lazy evaluation made it into Kotlin in the form of generator sequences! This allows you to make collections of arbitrary size through dynamic calculation rather than static declaration:

```
val seq = generateSequence(1, {it + 1})
val n = seq.take(5).toList()
println(n)
// => [1, 2, 3, 4, 5]
```

You know how sets of infinite size can be defined by mathematical induction? Yeah. That's in here. Infinitely-large data structures! Bask in the glory!

Why not dynamically create some Fibonacci numbers?

```
fun fibSeq(): Sequence<Long> {
    var a = 0L
    var b = 1L
    fun next(): Long {
        val result = a + b
        a = b
        b = result
        return a
    }
    return generateSequence(::next)
}
val fibs = fibSeq().take(10).toList()
println(fibs)
// => [1,1,2,3,5,8,13,21,34,55]
```

If you guys know me at all at this point, you know this feature is really high on my list: composable higher-order collection methods! Who here loves dot-chaining?

```
val n = (1..9).map {it * 2}
                .filter {it > 5}
                .groupBy {it%2==0}
                .mapKeys {if (it.key) "even" else "odd"}
```

If-conditionals are not only statements, but also expressions. This cuts down on language features, and thus Kotlin does not have (or need) a ternary operator!

`for` loops are very flexible, able to work the same on any iterable object:

```
for (ch in "hello") {
    println(ch)
}
```

`while` and `do/while` loops work how you're used to, and also there's increment/decrement operators:

```
var cnt = 0
while (cnt < 10) {
    println(cnt++)
}
```

`when` is Kotlin's `switch` statement, except it works on any arbitrary condition, turning a switch from a simple pattern-match like it is in Java into a true, full-fledged alternative to an `if/else` ladder!

```
val i = 5
val greeting = "whatup"
when {
    i < 7 -> println(i)
    greeting.startsWith("what") -> println("second choice")
    else -> println("default case")
}
```

But if you really need to use it for pattern matching like usual `switch` statements you're already used to in Java, that's fine too, you can do that:

```
when (i) {
    0, 1 -> println("0 or 1")
    1..21 -> println("anywhere from 1 to 21 inclusive")
    else -> println("none of that")
}
```

Did I mention `when` is also an expression? Yeah!

```
var res = when (i) {
    0, 1 -> "0 or 1"
    in 1..10 -> "between 0 and 11"
    else -> "some weird shit"
}
println(res)
```

Do typechecks with implicit casting with `is`:

```
fun smartCast(x: Any): Boolean {
    if (x is Int) {
        return x // x is now an Int
    }
    else if (x is String) {
        return x.isNotEmpty() // x is a String 
    }
    else {
        return false
    }
}
println(smartCast("ballin"))
// => true
println(smartCast(""))
// => false
println(1) // => true
println(0) // => false
```

And with short function syntax and a `when` block:

```
fun smartCast(x: Any) = when (x) {
    is Boolean -> x
    is Int -> x > 0
    is String -> x.isNotEmpty()
    else -> false 
}
```

Did you want to extend the native objects like you can do in JavaScript? Go right ahead!

```
fun String.remove(c: Char): String {
    return this.filter {it != c}
}
println("011100110".remove('1'))
// => "0000"
```

Oh yeah, `Char`s are denoted by single quotes. 

Speaking of `Char`s, strings can both have the usual escape sequences like `\n`, `\t`, etc. but also can be like Python's docstrings where declaring them """like this""" instead of "like this" puts formatting into them!

Now I'm not very much more knowledgeable about the language than this, but already I can see myself being quite comfortable in this environment, and the language will only get better with time and more users! It is easily a much more impressive language than Java already, so if you're one of the many modern programmers who are disgusted with Java, this might be your avenue into app development. It's definitely becoming mine!

Come join me on this adventure!

