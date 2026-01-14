# Introduction to Rust

Hello. 

I would like to explain and introduce you to Rust programming language as I would like to have it explained to me when I was learning it.

# Who am I

I'm Rafał Draws, SWE at Nordea Bank. I'm a Rust Poland co-founder, a music and car nerd.

# Pre-word

Most of the examples I'll be giving will be comparing Python and Rust, as they differ the most. 

My belief is that if you're familiar with syntax of C#/Java, Scala, Kotlin, C, Go or TypeScript. you shouldn't have an issue learning Rust. If Python is your only programming languages, there might be bumps in the road.


# Structure of this presentation

- 5 minutes of general principles
- 10 minutes of what
- 10 minutes of why 
- 10 minutes of how
- 10 minutes of possibilities

as little async as possible, since async Rust is it's own language

# What is Rust? pt.1

Rust is a general-purpose programming language. It is noted for its emphasis on performance, type safety, concurrency, and memory safety. 


# What is Rust? pt.2

Rust supports multiple programming paradigms. 

It was influenced by ideas from functional programming, including immutability, higher-order functions, algebraic data types, and pattern matching.


# How Rust puts emphasis on type safety?

1. Functions must take in typed parameters and return type. 
2. Ownership and Borrowing System
3. No nulls
4. Immutability by default
5. Exhaustive pattern matching
6. Zero-Cost abstractions


# 1. Functions must take in typed parameters and return type. 

```rust
enum Pizzeria {
    KUBRYK,
    PIRATTO,
    SOPRANO,
}

enum Sauce {
    Garlic,
    Spicy,
    Bbq
}


enum Ingridient {
    Meat {
        type: String,
        double: bool
    }, // struct
    Rocket, // single enum
    Cheese(String), // tuple struct
}

struct PizzaBox {
    source: Pizzeria,
    ingridients: Vec<Ingridient>,
    sauces: [Option<Sauce>; 2],
}

fn eat_pizza(box: PizzaBox) -> Result<Satisfaction, SatisfactionError> {

    match pizza_box.source {
        Pizzeria::PIRATTO => return Err(SatisfactionError::BadPizzeria),
        Pizzeria::SOPRANO => {
            println!("NICE!")
        }
        _ => {} 
    }

    let has_sauce: bool = pizza_box.sauces
                    .iter()
                    .any(|sauce| sauce.is_some());


    let mut has_sauce: bool = false;
    for sauce_option in &pizza_box.sauces {
        match sauce_option {
            Some(Sauce::Spicy) => has_sauce = true,
            Some(Sauce::Garlic) => has_sauce = true,
            Some(Sauce::Bbq) => has_sauce = true,
            None => {}
        }
    }


    let mut hapiness = 0;
    
    for item in pizza_box.ingridients {
        match item {

            Ingridient::Meat { type: meat_kind, double } => {
                if meat_kind == "Pineapple" {
                    return Err(SatisfactionError::AllergicTo("Pineapple on Meat".to_string()));
                }
                happiness += if double { 5 } else { 2 };
            },
            
            Ingridient::Cheese(cheese_name) => {
                if cheese_name == "Gorgonzola" {
                    happiness -= 2; // Too zesty!
                } else {
                    happiness += 3;
                }
            },

            Ingridient::Rocket => {
                happiness += 1;
            }
        }
    }

    // finally
    Ok(Satisfaction {
        level: happiness,
        comment: String::from("Delicious and type-safe!"),
    })
}


#[derive(Debug)]
enum SatisfactionError {
    TooSpicy,
    AllergicTo(String),
    NotEnoughSauce,
    BadPizzeria,
}

#[derive(Debug)]
struct Satisfaction {
    level: u32,
    comment: String,
}

```


# Ownership and Borrowing System

Ownership and borrowing systems are tough to comprehend at first, but there are many great resources explaining these systems.

In languages like Python or Java, you rarely think about where a variable lives. The "price" for this convenience is paid by your computer: a Garbage Collector runs in the background, consuming CPU and RAM to clean up after you.

In systems languages like C++, you manage memory manually. The "price" is paid by the developer: one mistake leads to crashes or security vulnerabilities.

Rust offers a third way. The compiler refuses to build your code unless it can prove—at compile time—that you haven't made any memory mistakes. You pay the price upfront by satisfying the compiler, but in exchange, your program runs with the speed of C++ and the safety of Java.

(Hence some call Rust development as CDD, Compiler Driven Development)


# Immutability by default

Variables in Rust are read-only by default, ensuring that once a value is assigned to a name, it cannot be accidentally overwritten. (Also checked by the compiler)

This design eliminates unexpected side effects and makes concurrency safer, as immutable data can be shared across threads without fear of data races.

To modify a value, you must explicitly "opt-in" using the mut keyword, which signals to the compiler and other developers that state changes are intentional.

```rust
fn main() {
    let price = 99;      
    // price = 100; // Compiler Error: cannot assign to immutable variable

    let mut stock = 10;  // "mut" makes it mutable
    stock -= 1;          
}
```

# No nulls!

Sir Charles Antony Richard Hoare, a british computer scientist, inventor of Quicksort algorithm and grandfather of "design by contract" famously said:
"I call it my billion-dollar mistake. It was the invention of the null reference in 1965. At that time, I was designing the first comprehensive type system for references in an object oriented language (ALGOL W). My goal was to ensure that all use of references should be absolutely safe, with checking performed automatically by the compiler. But I couldn't resist the temptation to put in a null reference, simply because it was so easy to implement. This has led to innumerable errors, vulnerabilities, and system crashes, which have probably caused a billion dollars of pain and damage in the last forty years."

# So how do we omit nulls?

```rust
Option<T>;
Result<Ok, Err>;
```

# Ok, so how did the Cloudflare famously crashed?

```


```

# 1. Why write in Rust when you can achieve the same in Python?

1. Resources matter
2. Upfront best practices enforced by compiler
3. Community


# 1a. Resources matter

![RustvsCPPmergesortMatrixMul](image.png)


Performance evaluation for choosing
between Rust and C++ - Patrik Karlsson, p.16 2023

https://www.diva-portal.org/smash/get/diva2:1761754/FULLTEXT01.pdf


# 1b. Resources matter

![RvCPP-I/Otask](image-1.png)

Performance evaluation for choosing
between Rust and C++ - Patrik Karlsson, p.17 2023

https://www.diva-portal.org/smash/get/diva2:1761754/FULLTEXT01.pdf




# 2. Why write in Rust when you can achieve the same in C?

1. Compiler support
2. Upfront best practices enforced by compiler
3. Cargo


# 3. You mentioned upfront best practices enforced by compiler, what exactly do you mean bud?

- Structs and enums are first class citizens of Rust
- Explicit type checks
- Ownership model
- RAII
- data-race-free concurrency
- Option<T>, Result<T, E>


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

