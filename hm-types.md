What if I could tell you that I know the general pattern your function takes just by asking you what its arguments and return type are?

Turns out there's an entire formalism for determining this. It's called Hinley-Milner type theory.

You're used to thinking that values have types, but Hinley-Milner type theory gives functions types too. These types are captured with type signatures.

HM type theory has a basic set of syntax to understand the whole thing.

If the function returns something, no matter the type, we'll call the type `a`. Another type, `b`, might have the same type as `a`, but doesn't necessarily have to.

A function that takes 1 argument and returns a value looks like

```
functionName :: a -> a
```

The `::` reads as "has type of", and since functions relate two values, that is said with the arrow. It's a function FROM some type TO some type.

For example, a function that takes an int and doubles its value has a type signature like

```
double :: Int -> Int
```

So, `double 2 = 4`

If you have a function that accepts a function as a parameter, or returns a function as an argument, the types of the functions are said within grouping symbols.

For example, the function `compose`, defined as

```
compose f g = f (g)
```

in point-free style, awaits an argument to `g`, then passes its returned value to `f`, which returns its value.

Therefore, the HM type signature of compose is

```
compose :: (a -> b) -> (b -> c) -> (a -> c)
```

Let's say you have a list of values of some type. The type would be `a`, but that it's a list is communicated by putting the `a` in brackets: `[a]`.

The "head" function takes a list and gives you the first element of that list. You may already be able to guess its HM type:

```
head :: [a] -> a
```

It goes from a "list of `a`" to an `a`. Notice that the type has to stay the same because they're both `a`s. If the type could change, it would be a `b` or `c` or etc. Simple logic will tell you that this list is a list of data all of the same type.

Transforming a list or filtering a list, simple logic will dictate, will have the type signature of `[a] -> [a]`, since you take in a list, and get back another list.

The `filter` function, which returns a list of only the elements of the list it takes in that fall into a set of criteria also passed in, 

```
filter (isEven) [1..10]
```

gives back a list of all the even numbers between 1 and 10: [2, 4, 6, 8], which has the type `[Int]`, a list of `Int`s. So we went from a `[Int]` to a `[Int]`, so this behavior lines up with this function's HM type signature: `[a] -> [a]`.

You can go the other way, too. For example, ECMAScript 6's `Array.prototype.fill()` function takes a type and returns an array of that type: `a -> [a]`, the first `a` being what to fill the array with, and the `[a]` being the filled array.

Types have variants. This seems weird when I say it, but you all already know this. `2` is not equal to `2.0`. That would be a type mismatch, yet they're both numbers?

There's another layer of abstraction here, and this is determined by a name attached to the type name. For example, any number type can be captured with `Num`, such that the type signature for a function that takes something in that class of types and returns something within the same class of types would be

```
Num a => a -> a
```

reading as "a type `a` of the class `Num` that we happen to call `a` TO another `a` of the same class of types".

What if the number is an ordinal number instead of a cardinal number? That would be of the `Ord` class:

```
Ord a => a -> a
```

This notation gives us fine-grained control of what we're talking about in relation to our functions.

Let's say we're trying to make a comparison function that returns the larger of two numbers. Just being able to compare two numbers in this way requires both numbers to be of the `Ord` type class. Thus, a function taking two numbers and returning the larger of the two would look like:

```
largerOf :: Ord a => a -> a -> a
```

We don't need to say `Ord` more than once because all `a`s are of the same type just by being called `a`.

As you have probably picked up by now, an arrow separates each function argument as well as its return value.

What if a function doesn't return anything? That non-existent return value is denoted by an empty set of parentheses: `()`.

```
a -> ()
```

called "unit". It's the same the other way around when the function doesn't take a value, but does return something: its type is "unit TO a":

```
() -> a
```

There can be classes applied to unit as well. For example, a function that takes a value, doesn't return a value, but does print something onto the screen, has the type of

```
a -> IO ()
```

"an `a` TO an IO action that itself doesn't return a value".

If you have a function that takes a value and updates some outside program state, that can be generically captured with a type signature like

```
a -> State a
```

A function that takes a value and returns an error condition?

```
a -> Error a
```

Those of you venturing out into the world of programming using languages like Python or JavaScript will not necessarily be thinking of types first, but behavior first. These are the people this post will be benefiting most, as how types line up affects your program's composability and thus reusability and embeddability in larger codebases.

Those of you using strongly-typed languages like C# or Rust know very well how important keeping track of your types is, and this system will give you a formal way of thinking about how the pieces of your program behave and fit together.

Lining your types up correctly is a great way to tell if things will work right with each other, but it's only the tip of the iceberg for how to make your compositions more bulletproof, backed by an entire branch of mathematics! Maybe that will be the subject of a future post? Let me know how interested you actually are.
