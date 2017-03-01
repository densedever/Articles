# Why Java Sucks

Java programmers, I'm asking for criticism and also open-mindedness from anyone who uses Java as their primary language and especially its die-hard fans!

**TL;DR:** Java sucks and shouldn't be used or recommended to anyone, especially beginner programmers! 

Just to give you a bit of background so you know where I'm coming from: I program in Haskell, JavaScript, and Python. These are the languages I prefer, and I could write entire books explaining why. I started with OOP in C++, Java, and Python. I programmed in Java for two years, making GUI applications, games, graphics, and command-line utilities. This is my takeaway from that. 

A disclaimer is that my qualm is equally with Java and OOP (I am very vocally anti-OOP), and as you'll hear fairly quickly from Java's detractors, the two complaints often overlap. However, Java as a language leaves a lot to be desired, and I'll try to cover both bases throughout the article. 

Put aside its popularity and ubiquity for a second, take off your rose-tinted glasses, and consider a new point of view. 

Java, as a language, brought pretty much *nothing* to the programming world. The idea of a language running atop a universal interpreter wasn't even new. That was preceded by ~30 years by an O-code process virtual machine running a BCPL language front-end in the late 60s. Many people like Java because of its VM, chanting the phrase "write once, run anywhere", but there are many problems with this point. 

First, the idea that Java is a write-once language is *demonstrably* false, and any sufficiently-practiced Java programmer will have already seen this first-hand. Not all JVMs are created equal, and Java is actually rather unportable between JVM versions (even within different versions of the same JVM) without having to modify code, rebuild libraries, or recompile stuff. 

An important point to note is that it does not follow that having a VM implies binary portability. To the surprise of many new programmers, such a goal isn't always something you really *need*, especially considering a majority of your users will be using one popular platform such as Windows or Android. In the end, on the job, what matters is immediate availability to the largest chunk of the market share. 

An *oft*-repeated point I hear all the time from fans is that Java was the first OOP language, or at least the first influential one. I even got this claim in my previous Java post! Java did not invent object-oriented programming. Simula '67 was a fully OOP language long before 1995. Smalltalk was another. C++ even preceded it. OOP wasn't even on the minds of software engineers until Nygaard, Dahl, Sutherland, and Kay came into the picture in the early 60s. 

But ignoring the lack of unique contributions to computer science, there is plenty to dislike about the language syntax, semantics, library layout, and programming/execution model. 

For example, C# can do file I/O in a line or two as opposed to Java's 40+ lines for the same operation despite the structure and model of Java and C# being actually quite similar. 

It's not just about the JVM, but the language itself. Java's method and object names are extremely and gratuitously verbose, forcing you to write more code than you have to just because of the naming. Example:

```
BufferedReader br = new BufferedReader("foo.txt"); 
```

You have to type `BufferedReader` twice in the same line. This is unnecessary code repetition (repeated for every new object instantiation, this quickly becomes an annoyance) and ultimately makes more work for the programmer. At the end of the day, it comes down to how much functionality is implemented, not how much code is written. If you retort with "but that's just how the language works with its use of class instantiation because it's a data abstraction and..." I contend that makes the situation *worse*. If you need code completion to write your project, there's a problem here. You should ask yourself why you're fine with this. 

At this point, the more experienced Java programmers have already thought "but that point is crap because Java has an `auto` keyword that abstracts out the explicit naming of variable types." Not many constructs besides maybe the `auto` keyword do very much for the verbosity of code at the end of the day. If I have to write another line like
`private static final unsigned int blah = 2;`
inside a class...
branching from a parent class....
contained in an abstract base class.....
inside of a namespace......
inside of a package.......
I will drink myself to sleep. 

Python's `blah=2` will always do it better and while you're still writing your classes and interfaces and jars and packages and bags and suitcases, I'm on to the next project.

OOP, Java's main programming model, not only does not do Java any favors, but it doesn't do programming in general any favors either. It's extremely verbose code for even the simplest operations. Abstract data types can do most everything classes can accomplish and if you don't believe me, learn Lua and how it uses tables. 

This is a very contrived point, I'll admit, however I believe it's still relevant. The structure of languages like Python and Lua does away with the need to create boilerplate code. In Java, you *have* to create a package to hold your application. You *have* to have a main class. You *have* to have a main method. If you spit back with "oh but that's because languages like C and Java have to have those constructs because they're compiled", check out FreeBasic, a compiled language that couldn't care less whether you have a main function or not. 

If your retort is "oh but that's because all those classes and methods mean things and have larger uses in the program", let me introduce you to Ruby, a language where everything is an object, no exceptions (unlike Java), keeping itself comfortably consistent. It has no need for packages, a main class, a main method, etc. and no requirement that anything in your program needs to be a class.

The choice to implement an explicit program entry point, as well as other cruft, comes down to the compiler. Whatever happened to KISS?

Another very popular point brought up by fans of OOP is that it's great for large projects because it keeps related data and logic in their own self-contained playpens. This is a train of logic that *completely* ignores how the real world actually works, which is where your programs are ultimately going to be used. Everything is an interconnected whole, with its parts constantly interacting with other parts. Caging them up to try to curb complexity is an exercise in madness. Do this with ANY discipline, and, careful as you might be, you *will* eventually run into problems. 

This is why interdisciplinary approaches to many fields of science, even ones previously thought to be specializations such as psychiatry, are becoming more popular in the last five or six decades. You can't have a boxed-in world. 

Another important thing to note is that there are different types of OOP; it's not just one paradigm. *Class-based* OOP such as what Java features, creates unnecessarily bloated code, making entire copies of potentially huge data structures (whose members have to be pointer-accessed, there's more CPU cycles down the drain), and eating up memory like nothing else. 

There's another type of OOP that JavaScript and Rust use called *prototype-based* OOP that's far faster and more memory-efficient than Java and C#'s class-based OOP, using "delegation linkages" to connect objects. This means instead of deep copying entire data structures, it simply references previously-created ones, shadowing their methods if need be (there's encapsulation, polymorphism, AND inheritance accounted for in one elegant mechanism!), reducing the program's total memory footprint. 

Java's language, libraries, and execution model are, on the whole, clunky, messy, overly verbose, and not even unique. 

Yet Java, C#, and OOP are what are used by the giants in the computing industry and are consequently what are taught to everyone in college. You quite literally cannot take a computer science course and not run into classes based around it. It's the saddest part of modern programming. 

The reasons for liking Java are sentimental, not based on any kind of logic. This is nothing but demonstrable on every level. 

I could go on. I didn't even mention Java's many buggy and deprecated libraries such as awt or swing, its liberal use of try/catch when Just/Maybe/Either monads would suffice, or its overly-complex, wasteful, "hey let's bundle up even our smallest sets of related data and create APIs so they can still interact with the rest of the code" programming model. I'm sure I don't even need to mention the bulk and sluggishness of its more popular workplace IDEs like Visual Age, Eclipse, and NetBeans, especially when Vim + Ctags will do the same work, but instantly.
