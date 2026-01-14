# Introduction to Rust

Hello. 

I would like to explain and introduce you to Rust programming language as I would like to have it explained to me when I was learning it.

// There are many great resources that will explain the insights and mechanisms within Rust programming language.



Five years ago I had no to little academic knowledge of computer science. 

Even if something rang a bell, I wasn't able to comprehend this or understand the reason behind specific mechanisms or algorithms.


I was focused solely on two ideas:

1. If it does what it's supposed to, I am happy
2. If it works fast, I'm happy

Back then I was, what would be considered an junior tech enthusiast, lazy enough to utilise python and ambitious enough to pick up scala to tangle with Apache Spark SDK.

I was still trying to find passion in software engineering, tangled with machine learning a bit, tried this and that. 

So this lecture is for beginners like me, a little favor to my past self.

We'll ask ourselves some questions and I'll try my best to provide an answer.


# 0. Why there are so many programming languages in the world?

1. Because people have preferences
2. Because different tools serve different purposes
3. Because we advance

# 1. Why write in Rust when you can achieve the same in Python?

1. Resources matter
2. Upfront best practices enforced by compiler
3. Equal tooling

# 2. Why write in Rust when you can achieve the same in C?

1. Compiler support
2. Upfront best practices enforced by compiler
3. Cargo


#3. You mentioned upfront best practices enforced by compiler, what exactly do you mean bud?

Let's go back to Rust vs Python example


#4. Let's compare both!

Rust | Python
Compiled | Interpreted (can be compiled)
Strong typing | Implicit typing (but can be strongly typed)
No Object Oriented Programming | Everything is an Object
No Garbage Collection | Garbage Collection present (but can be disabled :))
Hella tough learning curve | plug and play


#5. Why compiling is worth it and why Rust is superb at it?

1. compiled software is faster - It's just binary code ready for your computer to interpret, and in rust example - you can set optimization levels from 0 to 3.
2. When you run .py script - you just execute it using python interepreter, and if you were to run this script on another device, you would have to make sure that the other device has the same or higher version of python with the same requirements
3. Operating systems have different ways to acquire memory, play a sound, or print something on screen. These instructions are SYSCALLs, and if you ever wondered how can you use software specific for Windows - "wine" translates Windows Syscalss to Linux/Unix ones.

Therefore, if you compile executable for linux, you won't be able to run it on Windows machine!


#6. Enter cargo

1. It is package manager, toolchain manager, compiler CLI, documentation tool and testing suite.
2. Imagine requirements.txt but with project metadata and workspace manager.
3. Cargo also allows you to run, check (compilation without running the code), test and much, much more. There's a whole book about cargo.
4. Cargo let's you install toolchains - If you're on linux, you can specify windows with an ARM processor as compilation target. You can copy/send the executable and it will run smoothly on specified machine, as long as it's exact toolchain for the system.
5. Wonderful compiler errors.


#7. Enough with the yapping, explain the ownership please.

Rust started of after one of Mozilla employees had it enough with broken elevator, which was crashing due to memory allocation bug. The idea of memory-safe language was born.

Your computer has two ways to store variables.

Stack and Heap.

Stack is a "plate-like structure" that allows for Last-In First-Out access, while
Heap has "just put it somewhere idc" structure. 

Languages like Python doesn't bother the developers with deciding where to store the variables, but if you were to develop something in C - you would. 

