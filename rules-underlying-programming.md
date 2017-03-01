# Rules Underlying the Writing of Programs

Question: "Are there any rules as to how programs are supposed to be written?"

Sorry this comment will be fairly long, but I don't think you realize just how deep a question you're asking. I'll answer it because I desire that you have the fundamental understanding needed to become a great programmer with actual knowledge of what's going on behind those weird symbols you'll be writing. Trust me, you'll be all the better for it, all I'm asking is a few minutes of your time, if you will. 

A program is a set of instructions for the computer to do. Those instructions come in the form of "code", a language meant to communicate information in an unambiguous way. The rules one must follow when writing these codes depend entirely on what the computer itself has the ability to do. 

Computers are comprised of a [CPU and memory](https://en.wikipedia.org/wiki/Von_Neumann_architecture) in the form of RAM and disk memory. 

The CPU executes the [instructions](https://en.wikipedia.org/wiki/Machine_code) given it by the programmer (the instructions themselves reside in memory). 

So what can the hardware (CPU and memory) do?

Computers operate by small [electric circuits](https://en.wikipedia.org/wiki/Electrical_network) that [direct](https://en.wikipedia.org/wiki/Logic_gate) electrical flow in certain ways, governed by the laws of [formal mathematical logic](https://en.wikipedia.org/wiki/Boolean_algebra). 

Memory consists of conglomerations of thousands or millions of interconnected circuits (each individually numbered in order, like your locker at school) that can store electrical charges (or magnets that are flipped certain ways for long-term storage). This means you have the ability to store information in each individual circuit and change the information the circuits hold. This alteration is done with `move` or `load` instructions that change the pattern of electrical excitation in some specific memory circuit (identified with its number, or "address").

```
move 5, 0x2650
```

is an instruction that "moves" the value 5 into the 9808th memory circuit (memory addresses are commonly referenced in base 16 numbers for reasons I won't get into). I'll be using decimal numbers for memory addresses instead of hexadecimal numbers for ease-of-understanding.

As well as changing the electrical flow through memory, you can reference parts of memory that have specific values already stored into them and do math with those values. The `add` instruction, for example, adds up two numbers in two memory addresses. 

```
move 2, 1000
move 2, 1004
add 1000, 1004
```

This more complex set of instructions moves the value 2 into both the memory addresses 1000 and 1004 and stores the result in address 1000. 

Subtraction, multiplication, and division work the same way, and if you know arithmetic, you already know there's really nothing but addition in the first place. Edit: division needs a remainder and so does not work exactly the same. It stores the remainder in a separate memory location.

As well as math, you can also do comparisons and logical instructions, although I won't be touching on logical instructions here. `compare` instructions compare two values for equality. 

```
compare 8600, 1000
```

This takes the value at address 8600 and *subtracts* the value in 1000, and if the result is zero, the comparison succeeds. 

Why is this useful?

The set of instructions you give the computer is read one-at-a-time by the CPU, and the address of the current instruction to be read is stored in a [special circuit](https://en.wikipedia.org/wiki/Processor_register) on the CPU called the *instruction pointer* or *program counter*.

The value of the instruction pointer can be changed by special instructions called "jump" or "branch" instructions that change the order in which the instructions are read. This is useful because you can jump to different parts of code and back, or read the same instructions over and over again in a loop, allowing your programs to be dynamic, compact, and interactive. 

```
move 5, 2228
move 5, 2232
compare 2228, 2232
jumpg 65316
```

This moves a 5 into both 2228 and 2232, compares the two values (returning a zero and thus succeeding), and then jumping the reading of the code to address 65316. I typed `jumpg` here to mean "jump only if the comparison yields a positive value", or "jump if greater than."

In actual code, you're not going to be jumping to specific, numbered memory addresses, but addresses that you can give understandable names to. 

```
start:
move 10, 204
subtract 1, 204
compare 204, 0
jumpne start
```

This code gives the name `start` to the first memory address, loads a 10 into the 204th memory address, subtracts one from the value in the 204th address, and compares that value with the literal value zero. 

The reading jumps back to the label `start` afterward, but only if the comparison succeeds. If it doesn't, the jump is ignored, and the instruction pointer simply reads the next instruction in memory (thus jump**ne** would mean "jump only if **n**ot **e**qual", as opposed to "greater than" or "less than"). This code loops around and around, subtracting 1 from the 204th memory address every time until the value in it is reduced to zero. (Reasoning seems incorrect. May need revision.)

Memory addresses can also be given names when you want to keep track of important values. If you want to calculate the value of a car after x amount of years after it's manufactured, you'd make a program that looks something like this, assuming you start at address 2 and go up 4 addresses for every new value (giving yourself some space to store values):

```
newCarPrice equ 45000
yearlyDecrease equ 800
carAge equ 6
multiply yearlyDecrease, carAge
subtract newCarPrice, yearlyDecrease
```

The `equ` instruction gives an address a name, and gives it the value of the number on the right, advancing the reading of memory afterward, giving you three memory addresses named `newCarPrice`, `yearlyDecrease`, and `carAge`, with the respective memory locations of 2, 6, and 10. 

Next, we multiply the value at the address labeled `yearlyDecrease` by the value at the address labeled `carAge`, yielding 800 * 6 = 4800, which is then stored in `yearlyDecrease`. We then subtract that new value 4800 from the value in `newCarPrice` to get 45000 - 4800 = 40800, which is the final price of your car after 6 years, deprecating $800 every year. 

This process of manipulating values in named memory locations is behind the use of "variables" in programming languages. 

There's a lot more to it than this, but this is basically how CPU instructions operate deep down in the computer's bare circuitry. 

Every programming language you will ever learn builds off this basic set of instructions. The rules for writing code are built off this base. Understand this instruction set, and you will understand your computer, and thus programming languages in general. 

For more information, please read the first 150 pages or so of [The Art of x86 Assembly Language](http://www.ic.unicamp.br/~pannain/mc404/aulas/pdfs/Art%20Of%20Intel%20x86%20Assembly.pdf) without skipping over anything. It is an absolutely indispensable book on the subject.
