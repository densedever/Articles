"Are there any rules as to how programs are supposed to be written?"

Sorry this comment will be fairly long, but I don't think you realize just how deep a question you're asking. I'll answer it because I desire that you have the fundamental understanding needed to become a great programmer with actual knowledge of what's going on behind those weird symbols you'll be writing. Trust me, you'll be all the better for it, all I'm asking is a few minutes of your time, if you will. 

Ok so a program is a set of instructions for the computer to do. Those instructions come in the form of "code", a language meant to communicate information in an unambiguous way. The rules one must follow when writing these codes depend entirely on what the computer itself has the ability to do. 

Computers are comprised of a CPU and memory in the form of RAM and disk memory (Google "von Neumann architecture"). 

The CPU executes the instructions given it by the programmer (the instructions themselves reside in memory, Google "machine operation codes"). 

So what can the hardware (CPU and memory) do?

Computers operate by small electric circuits that direct electrical flow in certain ways (Google "circuit diagrams", "logic gates"), governed by the laws of formal ("Boolean") mathematical logic. 

Memory consists of conglomerations of thousands or millions of interconnected circuits (each individually numbered in order, like your locker at school) that can store electrical charges (or magnets that are flipped certain ways for long-term storage). This means you have the ability to store information in each individual circuit and change the information the circuits hold. This alteration is done with "move" or "load" instructions that change the pattern of electrical excitation in some specific memory circuit (identified with its number, or "address").

move 5, 0x2650

is an instruction that "moves" the value 5 into the 9808th memory circuit (memory addresses are commonly referenced in base 16 numbers for reasons I won't get into). 

As well as changing the electrical flow through memory, you can reference parts of memory that have specific values already stored into them and do math with those values. The "add" instruction, for example, adds up two numbers in two memory addresses. 

move 2, 0xAA20
move 2, 0xAA24
add 0xAA20, 0xAA24

This more complex set of instructions moves the value 2 into both the memory addresses 43552 and 43556 (in base 10) and stores the result in address 43552. 

Subtraction, multiplication, and division work the same way, and if you know arithmetic, you already know there's really nothing but addition in the first place. 

As well as math, you can also do comparisons and logical instructions, although I won't be touching on logical instructions here. "Compare" instructions compare two values for equality. 

compare 0x2250, 0x4411

This takes the value at address 8784 and SUBTRACTS the value in 17425, and if the result is zero, the comparison succeeds. 

Why is this useful?

The set of instructions you give the computer is read one at a time by the CPU, and the address of the current instruction to be read is stored in a special circuit on the CPU (Google "memory register") called the "instruction pointer" or "program counter."

The value of the instruction pointer can be changed by special instructions called "jump" or "branch" instructions that change the order in which the instructions are read. This is useful because you can jump to different parts of code and back, or read the same instructions over and over again in a loop, allowing your programs to be dynamic, compact, and interactive. 

move 5, 0x1110
move 5, 0x1114
compare 0x1110, 0x1114
jumpg 0xFF25

This moves a 5 into both 4368 and 4372, compares the two values (returning a zero and thus succeeding), and then jumping the reading of the code to address FF25 (65317 in base 10). I typed "jumpg" here to mean "jump only if the comparison yields a positive value", or "jump if greater than."

In actual code, you're not going to be jumping to specific, numbered memory addresses, but addresses that you can give understandable names to. 

start:
move 10, 0x0002
subtract 1, 0x0002
compare 0x0002, 0
jumpne start

This code gives the name "start" to the first memory address, loads a 10 into the second memory address, subtracts one from the value in the second address, and compares that value with the literal value zero. 

The reading jumps back to the label "start" afterward, but only if the comparison succeeds. If it doesn't, the jump is ignored, and the instruction pointer simply reads the next instruction in memory (thus "jumpne" would mean "jump only if Not Equal", as opposed to "greater than" or "less than"). This code loops around and around, subtracting 1 from the second memory address every time until the value in it is reduced to zero. 

Memory addresses can also be given names when you want to keep track of important values. If you want to calculate the value of a car after x amount of years after it's manufactured, you'd make a program that looks something like this, assuming you start at address 0x0001 and go up 4 addresses for every new value:

newCarPrice equ 45000
yearlyDecrease equ 800
carAge equ 6
multiply yearlyDecrease, carAge
subtract newCarPrice, yearlyDecrease

The "equ" instruction gives an address a name, and gives it the value of the number on the right, advancing the reading of memory afterward, giving you three memory addresses named newCarPrice, yearlyDecrease, and carAge, with the respective memory locations of 0x0001, 0x0004, and 0x0008. 

Next, we multiply the value at the address labeled yearlyDecrease by the value at the address labeled carAge, yielding 800 * 6 = 4800, which is then stored in yearlyDecrease. We then subtract that new value 4800 from the value in newCarPrice to get 45000 - 4800 = 40800, which is the final price of your car after 6 years, deprecating $800 every year. 

This process of manipulating values in named memory locations is behind the use of "variables" in programming languages. 

There's more to it than this, but this is basically how CPU instructions operate deep down in the computer's bare circuitry. 

Every programming language you will ever learn builds off this basic set of instructions. The rules for writing code are built off this base. Understand this instruction set, and you will understand your computer, and thus programming languages in general. 

For more information, please read the first 150 pages or so of "The Art of x86 Assembly Language" (found here: http://www.ic.unicamp.br/~pannain/mc404/aulas/pdfs/Art%20Of%20Intel%20x86%20Assembly.pdf). 