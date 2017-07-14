# Functional and Declarative JavaScript

### By densedever, 2015

## Intro

This doc is going to introduce you to functional programming in JavaScript. Functional programming (FP) is undoubtedly a growing trend in the development world, even outside of the web, and learning it can only help you as you start to get exposed to it, if only to understand other people's code. 

I'm assuming you already know the trifecta of web languages, so I won't spend time on the syntax and everything. There are plenty of excellent resources for that already. I do not assume you know what "imperative", "functional" or "declarative" means, and that will be the subject of this text.


## What is Functional Programming?

FP uses [mathematical functions](https://en.wikipedia.org/wiki/Function_(mathematics)) to return values and pass/accept data, and does not use any mutable (changeable) state at all. Functions rule this world of programming. There are no loops, no statements, no procedures, no class/object hierarchies, no exception handling, and *no need for them either*! There's nothing but functions that take values and return values. Yes, you can actually program productively this way!

It's a style of declarative programming, telling the computer **what** results you want, rather than telling the computer **how** to calculate the results and give them to you. Instead of laying out a series of **steps**, you're declaring a series of **facts**. It's a terse and expressive coding style that's easy on the mind and does more with less code. 


## Why JavaScript?

JavaScript has many built-in features that play very nicely with a functional style of coding, and it is a language that is ubiquitous and easily accessible to everyone. You just need a web browser. 

It's not a perfect language, and there are a bunch of things that operate very different than many other languages, but I will be pointing them out as they come. When coded the way it was meant to be coded, JavaScript is a very fun language rich with features to suit many types of programmers. I will be using as many ES6 features as are supported by the latest version of Chrome (version 59 at the time of writing).


## A Tale of Two Brothers

Here I will explain a little bit about each of the two paradigms I'll be covering in this text: imperative and functional (and, through it, declarative).

*Imperative* code can be captured with the idea of telling your computer how to do a task or calculate a result. Do this step, then this one, then if this happens, go to this step, then call this set of steps... It's highly dependent on what values variables have (*program state*), on iterative structures to accomplish repetition (such as loops), on branching structures to control program flow (such as `if` or `switch`), and on procedures to organize and modularize code.

*Declarative* code is written by stating axioms and facts about those axioms. "Declaring" what *is* about your program. Functional programming often takes this paradigm, and can fit this style of computation amazingly well, which is why I'm holding the two paradigms close. However, they are still different.

*Functional* code is written solely around *function applications* (aka "function calls") on passed-in data, directing it down a pipeline where it is transformed along the way, much like an assembly line. Your computer is not told how to do things, that's taken care of. It's simply told what data to fetch for you and how that data is supposed to look at the other end.

The most difficult part about learning functional programming is the shift in thinking required to write programs in it, so throughout the book you'll be shown many examples of the same code written both in an imperative and functional style. The programs will be broken down, showing the upsides and downsides of each programming paradigm. We will first start with the simplest building blocks of programming: statements, expressions, and functions.

## Statements and Expressions

An *expression* is an unsimplified term that is able to be reduced down into a single value. `2+(5*3)` is an expression because it can be evaluated into one value: `17`. Functional coding emphasizes the use of expressions to get things done rather than statements. 

A *statement* is a piece of code meant to do I/O, or to store, retrieve, or mutate data. JavaScript's name lookup scheme works in a way that lets variables stick around in the namespace longer than your off-the-rack C programmer might expect, so statements (assignment operator) should be used as little as possible in declarative programs to ensure predictability in them. 

How can you program with just expressions? Surely programs need loops, mutable state, and what-have-you? I'll go through everything that you think a program needs, and show you how to do it in a way that doesn't require any of these things. You'll find that your programs will even start to be more reasonable and predictable. It all starts with one of the most powerful concepts in JavaScript (and programming in general): the function.



## Variables and Names

FP is a lot different than imperative, and there are a few things that need to be reconceptualized for the style to be learned naturally, and this rethinking starts with variables. The imperative programmer's notion of variables is that they are named storage boxes for values. The functional programmer views them a little differently.

FP disallows mutable state, so every variable is a constant whose value stays the same throughout the lifetime of the program. This ensures that you know what you're getting. 

In imperative coding, making variables is called "variable assignment", assigning a value to a variable, and resetting it later on if need be. Variable assignment is perfectly possible in functional programming, but once the value is set, that's it! This is no longer deemed to be variable assignment then, and such an action has a special title to set it apart: *name binding*. 

Instead of using `var` or `let`, name binding is going to be done with `const`. This keyword prevents the variable from being reassigned.


## Functions Fly First-Class!

In FP, functions are thrown around just as much as variables are in other languages. They're considered values just as much as numbers are, and are treated the same. Functions-as-values are called *first-class functions* - functions acting like normal data: able to be bound to a name, passed to a function, or returned from a function.

Imperative coding treats functions as named blocks of code that sometimes return data back to their caller. In FP, they are instead treated as mathematical functions are: lookup tables that match one value to another based on a calculation. Put the same stuff in, get the same stuff out. 

For example, here's a function that adds two inputs:

```javascript
function add (a, b) {
  return a + b
}

> add (6, 4)
10
> add (2, 2)
4
```

A shorter way of saying roughly the same thing is:

```javascript
const add = (a, b) => a + b
```

The variable `add` has the value of a function (remember: functions are first-class data). If this function gets the same inputs, it will, by nature, give you the same outputs every time, and it does nothing else with its inputs. This property is called "purity." 

A function that is not pure is a function that does something other than returning a value. Logging something to the console, retrieving things from a database, updating program state, these are things that are not simply accepting and returning data. They instead invoke *side-effects*, breaking function purity. This is what we're trying to minimize. Being so fundamental to imperative style, you'll be surprised how few side effects your software actually needs.



## Some Examples of Both Paradigms

Here I'm going to show you a few small imperative programs and then refactor them into declarative programs by maximizing the amount of expressions and minimizing the amount of statements they employ.

Here is a program that defines some basic arithmetic operations:

```javascript
<body>
<form method="get" action="">
    <input id="id1" type="number"><br>
    <input id="id2" type="number"><br>
    <button onclick="add()">ADD</button>
    <button onclick="sub()">SUBTRACT </button>
    <button onclick="div()">DIVIDE</button>
    <button onclick="mul()">MULTIPLY</button>
    <button onclick="equ()">  ||  </button>
    <button onclick="rem()">REMAINDER</button>
    <input type="reset" value="CLEAR">
</form>
<script>
var x,y,z;

function add(){
    x=document.getElementById("id1").value;
    y=document.getElementById("id2").value;
    var z=parseInt(x,10)+parseInt(y,10);
    window.alert("Sum is: "+z);
}

function sub(){
    x=document.getElementById("id1").value;
    y=document.getElementById("id2").value;
    z=x-y;
    window.alert("Difference is: "+z);
}

function div(){
    x=document.getElementById("id1").value;
    y=document.getElementById("id2").value;
    z=x/y;
    window.alert("Quotient is: "+z);
}

function mul(){
    x=document.getElementById("id1").value;
    y=document.getElementById("id2").value;
    z=x*y;
    window.alert("Product is: "+z);
}

function equ(){
    x=document.getElementById("id1").value;
    y=document.getElementById("id2").value;
    if(x>y){
        window.alert(x+" is greater than "+y);
    } else if(x<y){
        window.alert(x+ " is less than "+y);
    }
    else{
        window.alert(x+" is equal to "+y);
    }
}

function rem(){
    x=document.getElementById("id1").value;
    y=document.getElementById("id2").value;
    z=x%y;
    window.alert("Remainder is: "+z);
}
</script>
</body>
```

Looks like average, elementary JS code. However it can be greatly simplified, especially with some of the new features of ES6. Looking over the functions, you'll immediately see a pattern. There are three pieces of state defined: two to hold the terms in the final expression, and a third to hold the result. The amount of state can effectively be reduced to zero.

The first step in doing this is to notice that getting the values of the input boxes is a source of repeated code. One of the most important principles in good software design is minimizing repeat code - the **DRY** rule: **d**on't **r**epeat **y**ourself!

These repeated actions can be captured with a single function which I'll call `idval()` that queries an element with its selector and returns its value. I'll throw in another one that gets only the element:

```javascript
const idval = elem =>
    document
    .getElementById(elem)
    .value

const id = elem =>
    document
    .getElementById(elem)
```

(The same thing can be done with a light version of jQuery.)

The second step is to realize that the values can be substituted for the variables and nothing is wrong with that. 

Take the `add()` function above. Basically the only important thing this function does is alert a value, so let's make the `alert()` our focus. `window` is a top level value, and thus doesn't need to be referenced explicitly.

```javascript
alert("Sum is:"+ z)
```

Now for `z`. `x` and `y` are the values for the two textboxes, so they can be substituted for `idval("id1")` and `idval("id2")`. `z` also must be casted as a number.

Now, to completely eliminate every bit of state, substitute that expression for `z`. I put it in a string template instead of a normal string:

```javascript
alert(`Sum is: ${parseInt(idval("id1")) + parseInt(idval("id2"))}`)
```

As a final step, put that into the `add()` function:

```javascript
const add = () => 
    alert(`Sum is: ${
        parseInt(idval("id1")) + parseInt(idval("id2"))
    }`)
```

**Hint:** *any function taking empty parentheses is an impure function.*

The same can be done with the other arithmetic functions that follow that same pattern:

```javascript
const sub = () =>
    alert(`Difference is: ${idval("id1") - idval("id2")}`)

// a ternary checks for division by zero
const div = () =>
    alert(`Quotient is: ${
        idval("id1") / (
        idval("id2") != 0?
            idval("id2"): 1)}`)

const mul = () =>
    alert(`Product is: ${idval("id1") * idval("id2")}`)

const rem = () =>
    alert(`Remainder is: ${idval("id1") % idval("id2")}`)
```

This last function can be done in two ways: one that involves `if` statements, and another that uses ternaries. Since some developers have an irrational hatred for ternaries, I will show both ways and you can pick which one you like better:

```javascript
const equ = () => {
    const x = parseInt(idval("id1"))
          y = parseInt(idval("id2"))
    if(x > y) {
        alert(`${x} is greater than ${y}`)
    } else if(x < y) {
        alert(`${x} is less than ${y}`)
    } else {
        alert(`${x} is equal to ${y}`)
    }
}

const equ = () => {
    const x = parseInt(idval("id1"))
          y = parseInt(idval("id2"))
    alert(x == y?
        `${x} equal to ${y}`:
        x < y?
            `${x} less than ${y}`:
            `${x} greater than ${y}`)
}
```

Many coders find the second way much less readable, but I personally don't, I think it's pretty clean when properly indented.

Putting this all together, the whole program now looks like this:

```javascript
<body>
<form method="get" action="">
<input id="id1" type="number"><br>
<input id="id2" type="number"><br>
<button onclick="add()">ADD</button>
<button onclick="sub()">SUBTRACT </button>
<button onclick="div()">DIVIDE</button>
<button onclick="mul()">MULTIPLY</button>
<button onclick="equ()">EQUAL</button>
<button onclick="rem()">REMAINDER</button>
<input type="reset" value="CLEAR">
</form>
<script>
const idval = elem =>
    document.getElementById(elem).value

const add = () =>
    alert(`Sum is: ${(idval("id1") + idval("id2"))}`)
 
const sub = () =>
    alert(`Difference is: ${idval("id1") - idval("id2")}`)
 
// a ternary checks for division by zero
const div = () =>
    alert(`Quotient is: ${
        idval("id1") / (
        idval("id2") != 0?
            idval("id2"): 1)}`)

const mul = () =>
    alert(`Product is: ${idval("id1") * idval("id2")}`)
 
const rem = () =>
    alert(`Remainder is: ${idval("id1") % idval("id2")}`)

const equ = () => {
    const x = parseInt(idval("id1"))
          y = parseInt(idval("id2"))
    alert(x == y?
        `${x} equal to ${y}`:
        x < y?
            `${x} less than ${y}`:
            `${x} greater than ${y}`)
}

</script>
</body>
```

This is much cleaner, nicer, and more compact. 

Let's look at another example: finding the average of some numbers.

```javascript
<body><script>
var a=parseInt(prompt("Enter 1st score!"));
var b=parseInt(prompt("Enter 2nd score!"));
var c=parseInt(prompt("Enter 3rd score!"));

document.write(
    "1st score: "+a+"<br>"+
    "2nd score: "+b+"<br>"+
    "3rd score: "+c+"<br>");

var total=a+b+c;
document.write(
    "Total score: "+total+
    "<br><br>");

var average=total/3;
document.write(
    "Average score: "+
    average+"<br><br>");

if(average<=50){
    document.write("Poor score!");}
if(average>=51 && average<75){
    document.write("Still not enough!");}
if(average>=75 && average<90){
    document.write("Ohh not bad!");}
if(average>=90){
    document.write("Wow, am proud!");}
</script></body>
```

There are largely the same symptoms we saw in the last program. Now that we have an idea how to clean it up, let's start. 

The program starts with three pieces of state for each piece of info, `a`, `b`, and `c`. First question to ask: "How are these being used in the rest of the program?"

This particular program is simple I/O, displaying five pieces of data:
1. The user prompt
2. The data items' values
3. The total score 
4. The average score 
5. An ending message 

A trick that my friends and I have used in this very situation is not annoying the user with three separate prompts, but instead use one and split the input:

```javascript
const scores = prompt("Enter the scores (separated by spaces):")
    .split(" ")
    .map(score => parseInt(score))
```

This is a little bit different than the above code, and there are some new concepts here. The user is prompted to type in all three numbers and the input is split into an array of three strings with the `split()` function. Since this returns an array of strings, we need to change these into numbers. 

First, I apply the `map()` function (docs [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)) on the array, which applies a specified function to each element and gives you back the new list. I passed into `map()` a function from `score` to `parseInt(score)`, which changes all the strings to numbers.

This is a quick and clean pipeline from one data transformation to another that's very readable and minimizes mutable state. 

Next is to substitute `a`, `b`, and `c` for the values in the `scores` array:

```javascript
document.write([
    `1st score: ${scores[0]}`,
    `2nd score: ${scores[1]}`,
    `3rd score: ${scores[2]}`
    ].join('<br>'));
```

I do this by exchanging the string literals for template literals for readability, and joining them together with `<br>`s.

The next piece of state (and its output) is the sum of all the elements in the array. 

To perform an operation on an array to get a single value back is called a [fold](https://en.wikipedia.org/wiki/Fold_(higher-order_function)), or in JavaScript: `reduce()` (documentation [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)). This takes a function of two arguments (a *2-ary*, or *binary* function) and combines the entire array, starting with the first two elements and going until the original array has been gone through. 

```javascript
const add = (a, b) => a + b
const total = scores.reduce(add)

document.write(
    "Total score: "+total+
    "<br><br>");
```

This is actually too long! We can shorten this up even more with more substitution (something you'll be doing a lot of). The above three lines of code declared two pieces of state and did one thing. We can do better. 

`add` was put in purely for readability and doesn't need to be there. Taking it out, you get the arguably equally as readable

```javascript
const total = scores
    .reduce((a, b) => a + b)
```

Noting that we're still writing two lines of code for one operation, we can cut out the remaining piece of state and simply print the result we wanted in the first place:

```javascript
document.write(
    "Total score: "+
    scores
        .reduce((a, b) => a + b)+
        "<br><br>")
```

Going off this theme, the same thing can be done to the next piece of output, the average:

```javascript
var average = scores
    .reduce((a, b) => a + b) / 3
document.write(
    "Average score: "+
    average+"<br><br>");
```

And then substituting again:

```javascript
document.write(
    "Average score: "+
    scores.reduce((a, b) => a + b) / 3+
    "<br><br>");
```

Now it's one clean statement.

Since we're using the total in more than one place, it's smart to put the output in a variable, so the only change we really needed to make was to change `total` to the call to `reduce()`.

There's a bit of a limit to exactly how much it's sensible to substitute everything, and the next bit of code is a prime example. If/else ladders are pretty much unavoidable when programming in imperative languages. Conditional constructs like guards in Haskell or match expressions in F# don't exist in JavaScript, so what we're left with is this set of conditions:

```javascript
if (average<=50){
    document.write("Poor score!");}
if (average>=51 && average<75){
    document.write("Still not enough!");}
if (average>=75 && average<90){
    document.write("Ohh not bad!");}
if (average>=90){
    document.write("Wow, am proud!");}
```

One thing you could do to reduce repeat code is to make a `between` function that tells whether a number is between two values, because we're comparing the score between an upper and lower bound. 

```javascript
// compares a value x to a left and right bound (l and r)
const between = (x, l, r) => x >= l && x < r
```

The function to do the comparing is simple, however it's not really necessary, so I won't be including it in the final program, but why not stick it here for future use anyway?

The whole program, then, looks like this:

```javascript
<body><script>
const scores = prompt("Enter the scores (separated by spaces):")
    .split(" ")
    .map(score => parseInt(score))

document.write([
    `1st score: ${scores[0]}`,
    `2nd score: ${scores[1]}`,
    `3rd score: ${scores[2]}`
    ].join('<br>'))

const total   = scores.reduce((a, b) => a + b),
      average = total/3

document.write(
    `<br>Total score: ${total}<br><br>`+
    `Average score: ${average}<br><br>`)

if (average <= 50) {
    document.write("Poor score!")}
if (average >= 51 && average < 75) {
    document.write("Still not enough!")}
if (average >= 75 && average < 90) {
    document.write("Ohh not bad!")}
if (average >= 90) {
    document.write("Wow, am proud!")}
</script></body>
```



TODO: These programs

```
<head>
<title>Compound Interest</title>
<style>
button {
  width: 250px;
  height: 40px;
  color: white;
  border: 1px solid blue;}
input {width: 250px;
  height: 35px;
  border: 1px solid blue;}
p {color: white;}
</style>
<script>
var principal, time, rate;
function solve(){
 principal=document.getElementById('id1').value;
 time=document.getElementById('id2').value;
 rate=document.getElementById('id3').value;
 income=(principal*time*rate)/100;
 window.alert("Your income is: "+income);
}</script></head>
<body style="background-color: blue;">
<h2 style="text-align:center; color: white;"><b>COMPOUND INTEREST</b></h2>
<form method="get" action="a.html"/>
<p style="text-align:center;"><b>PRINCIPAL</b><br>
<input id="id1" type="number"/><br><b>TIME</b><br>
<input id="id2" type="number"/><br><b>RATE</b><br>
<input id="id3" type="number"/><br><br><br>
<button style="background-color: red; color: white;" onclick="solve()">
<b>SOLVE</b></button><br>
<input style="background-color: red; color: white;" type="reset" value="CLEAR"/></p>
</form></body>
```



```
<head><title>find average</title>
<script>
var arr=[];
var i, x, y;
x=prompt("how many elements:");
for(y=1; y<=x; y++){
 arr[i]=prompt("Enter element "+y);
}
alert("Elements: "+arr.valueOf());
function add(prev, current, index, array){
 return parseFloat(prev)+parseFloat(current);
}
arr=arr.valueOf().reduce(add);
alert("sum is: "+arr);
var avg=arr/x;
alert("average is:"+avg);
</script></head>
```




```
function add(a,b){
 return parseInt(a)+parseInt(b);
}
function sum(){
 arr=document.getElementById("id").value;
 alert(arr.split(' ').reduce(add));
}
```






```
<script language="javascript" type="text/javascript"> 
answer1="London"

function test(form){
for (i=0;i< 3 ;i++){
if(form.elements[i].checked) {
if (form.elements[i].value==answer1){
alert("correct"); }
else{
alert("incorrect,the correct answer is" + answer1);
}
}
}
}

if (form.elements[1].checked){
alert("correct");
else {("incorrect");
}
}
</script>
```

```
<body>
<form>
whqhwnwncnwnwnw nsndjwn<br>
<input name="radio1" type="radio" value="rome">Rome<br>
<input name="radio1" type="radio" value="London">London<br>
<input name="radio1" type="radio" value="Beijing">Beijing

<br>

<input name="submit1" type="submit" value="submit" Onclick="test(this.form)">

</form>
</body>
</html>
```
Do this instead of the input. <button name="submit_1" onclick="test(this.form)">Submit</button>

*Imperative code contributed by:*
 * Hannah Han 
 * Jim-Chriss Charles 
 * Mahubele Ronald Seoka 

