# Category Theory Notes - Bartosz Milewski

## Lecture 1.1: [Motivation and Philosophy](https://www.youtube.com/watch?v=I8LbkfSSR58&list=PLbgaMIhjbmEnaH_LTkxLI7FMa2HsnawM_)

An important question to ask is "What helps us in programming?"

Composability helps to create complexity from simple parts and to break down complex problems into simple sub-problems.

Abstraction decreases mental effort by hiding details. For two similar-yet-distinct objects, abstraction allows you to regard them as the same. It doesn't care about minute details. Objects and abstract data types are meant to hide details.

Abstracting and composing things lead the way to reusability of generalized, small parts.

There's something wrong with the OO approach. It doesn't mix with concurrency well because of the wrong implementation details being abstracted. Two important things: 
1. mutation
2. sharing (pointers, data)

Mixing sharing and mutation results in data-races. Locks don't compose, and so won't fix the problem.

When raising the level of abstraction, be careful what you're abstracting. Non-mutable languages like Haskell don't have data-race problems because nothing is changed.

What are the limits of a new language? What's hard to do in it? Even simple ideas can be clumsily implemented in a language.

Library writers deliberately explore and push the limits of languages in their abstractions.

Disregarding details oftentimes gives you new tools to use to solve new problems or old problems in a new way.

Haskell even has limits to its abstraction. Some things are awkwardly-expressed in this language too. Some things in [Edward](https://www.schoolofhaskell.com/user/edwardk) [Kmett's](https://github.com/ekmett) libraries are very difficult to understand what his thought processes were.

The secret to understanding these concepts is category theory. He translates category theory to Haskell. Since category theory is the most general math you can get so far, of course you're gonna lose some abstraction upon translation, it becomes more concrete. For example, Haskell has one category built in, and in doing category theory, you're restricting yourself to that one category. 

Making other categories is possible in Haskell, but suffers the same clumsiness as template metaprogramming in C++ in terms of modeling complex structures.

Category theory is more abstract than Haskell or programming in general. In chopping away unnecessary details, you start to see mathematical constructs and programming languages as more similar and connected. Category theory attempts to unify many branches by providing a formal, abstract interface for the most common mathematical patterns. 

Those categories can even be put into bigger categories and given types, and then you have type theory. These are all based on logic, invented by the Greeks a long time ago, giving rise to all modern math. These areas of math are all the same. This is called the Curry-Howard lambda isomorphism - what you do in logic translates to what you do in type theory; they're the same, they're defined in terms of each other.

The lambda part says there are types of categories that describe the same thing. All human activity is described by one thing, independently discovered by different people at different times in history. This points to a greater truth.

But what if there's a simpler explanation? It goes back to how we do math or discover things.

How are problems solved? They're broken down into smaller problems, easier to solve, and then combine the solutions. This is how we do everything, even if we don't know it. But this only works if we have a recognizable structure for solving the problem. If we don't see that structure, we have to solve other problems first and build a structure up that we can hope to use for the first problem.

Maybe everything in the universe works like this and our brains are just reflecting it. But at the smallest levels, it seems that's not the case. If so, then maybe this destructuring is a result of how our brains work. If we can't see a pattern or structure, we have no way of solving the problem. In this way, category theory isn't about math, it's about thinking. It's semological rather than ontological. 

## Lecture 1.2: [What is a category?](https://youtu.be/p54Hd7AmVFU)








