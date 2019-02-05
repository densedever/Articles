# Understanding Programming Through Math

I've seen countless many posts in forums and social media telling people they don't need much math in most areas of programming, yet so few of the people saying this don't realize how much math they actually use in their daily coding.

Knowing how much is the key to writing programs that are composable and self-documenting, because you'll just know how they behave and fit together from the mathematical laws they follow.

Code has many patterns in it and these can be (or already have been) modeled by certain concepts in mathematics. Here are some examples.

Anything you can smush together into a bigger version of the same thing obeys the laws of [semigroups](https://en.wikipedia.org/wiki/Semigroup). String concatenation is one example.

Any two things you can combine into another of the same thing (along with a do-nothing operation) obeys the laws of [monoids](https://en.wikipedia.org/wiki/Monoid). Anything made up entirely of monoids is itself a monoid.

Classes, along with their fields and methods, are captured purely with [comonads](http://www.haskellforall.com/2013/02/you-could-have-invented-comonads.html).

Lists of data are [sets](https://en.wikipedia.org/wiki/Set_(mathematics)) and can be manipulated with set operations, unless they contain two or more of the same value, then they're [multisets](https://en.wikipedia.org/wiki/Multiset). If you can order them, they're [posets](https://en.wikipedia.org/wiki/Partially_ordered_set) (or [chains](https://en.wikipedia.org/wiki/Total_order#Chains) if the list has total ordering).

Expression parsing requires a set of data and a set of operations on that data, collectively called an [algebra](https://en.wikipedia.org/wiki/Algebraic_structure).

Changing the value of a piece of data is done with a [morphism](https://en.wikipedia.org/wiki/Morphism). A data type is effectively a [category](https://en.wikipedia.org/wiki/Category_(mathematics)), assuming it obeys commutative laws, and thus the value change is described as an [endomorphism](https://en.wikipedia.org/wiki/Endomorphism) within that category. You can also think of going from one value of a type to another value of the same type as an endomorphism in the category of that type.

Changing the value of anything inside a structure (without changing their type) is done with [functors](https://en.wikipedia.org/wiki/Functor). We're not talking about values with types anymore, we're talking about values with types *inside* a structure such as a list, `Promise()`, or `IEnumerable<T>`. Running a function on a value inside a structure requires an [applicative functor](https://en.wikipedia.org/wiki/Applicative_functor), so does running a (first-class) function stored inside that structure.

Looping constructs can be captured with [recursive functions](https://en.wikipedia.org/wiki/Recursion_(computer_science)) (no, they're *not* always more inefficient and difficult to understand than loops; this is an oft-repeated trope). These include [maps](https://en.wikipedia.org/wiki/Map_(higher-order_function)) (list transformations), [filters](https://en.wikipedia.org/wiki/Filter_(higher-order_function)) (operating on parts of lists), and [folds](https://en.wikipedia.org/wiki/Fold_(higher-order_function)) (turning a list into a single value). Lists stand in for iterators and indexes.

Changing each value in a list is done with [list comprehensions](https://en.wikipedia.org/wiki/List_comprehension) (from set theory). These can combine the uses of maps and filters.

Input and output of data to and from the user and the program in a pure manner can be done with [monads](https://en.wikipedia.org/wiki/Monad_(functional_programming)), which are structures that take in data to be worked with and perform operations on them away from the rest of the code (obeying the laws of monads). This works because the values are preserved and the changes are passed around (monads "are" [endofunctors](https://en.wikipedia.org/wiki/Functor#Examples)).

Structures themselves can be built up with various morphisms and [F-algebras](https://en.wikipedia.org/wiki/F-algebra)/[coalgebras](https://en.wikipedia.org/wiki/F-coalgebra).

Sequential statements can be performed in a pure way with monads as well. "Do" monads perform these operations in functional languages. Monads also handle error checks and null checks, replacing try/catch blocks.

Data encapsulation without classes is done with [lexical closures](https://en.wikipedia.org/wiki/Closure_(computer_programming)) involving returning [higher-order functions](https://en.wikipedia.org/wiki/Higher-order_function) from normal functions.

(to be continued? Please send pull requests!)
