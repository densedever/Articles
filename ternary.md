
# Ternary ?:

This operator is hated a lot, yet it is such a beautiful and useful construct in code. 

The ternary operator (`?:`) is a conditional in the form of an expression as opposed to a statement. It asks a question and evaluates to one of two different values depending on whether its predicate is true. 

A ternary expression is able to be assigned, used in a larger expression, compared to another value, passed to a function, or returned from a function. 

This has so many uses! You can put ternaries inside ternaries to make expressions in the form of binary trees arbitrarily deep - good for complex expressions!

You can even use it for conditional application of functions:

```
void doThis() {puts("Yum");}
void doThat() {puts("Blah!");}
main() {
  char *s = "Pizza";
  (strcmp(s, "Pizza")==0)?
    doThis():
    doThat();
}
```

This is the syntax:

```
(predicate)? 
    ifTrueExpression:
    ifFalseExpression;
```

(The parentheses are optional for only one term)

It's also extremely useful for shortening otherwise lengthy pieces of code:

```
if(age<18) {
  puts("You can't enter.");
else
  puts("Come in.");
```

Reduced to one expression:

```
puts((age<18)?
  "You can't enter.":
  "Come in.");
```

```
int max(int l, int r) {
  if(l<r) 
    return r;
  else
    return l;
}
```

Reduced to one line:

```
int max(int l, int r) {
    return (l>r)? l: r;
}
```

```
int abs(int x) {
  if(x>=0)
    return x;
  else
    return x*(-1);
}
```

Reduced to one line:

```
int abs(int x) {
    return (x>=0)? x: x*(-1);
}
```

Nested ternaries are often bashed for being "unreadable", but are really not hard to read if you're sufficiently familiar with seeing them. 

```
char* testNumber(int n) {
  return(n>0)?
    "Positive":
    (n<0)?
      "Negative":
      "Zero";
}
```

Just check the indentation level, and the flow of logic will be immediately apparent.

And if you're a Python programmer, you don't have to miss out! Python has an if expression as well. Its syntax is:

```
var = trueExpr if predicate else falseExpr
```

```
doThis() if predicate else doThat()
```

```
print("Come in" if age>21 else "Go away!")
```

C, C++, Java, JavaScript, Python, Go, and a bunch of other languages have if expressions. Check your favorite language and see if it does, and go forth and refactor your code!
