# PROJECT: 0x0D. C - Preprocessor

## Project By: Jordan Crossley

## Course: ALX SOFTWARE ENGINEERING

## Overview

![image](https://media.geeksforgeeks.org/wp-content/cdn-uploads/Preprocessor-In-C.png)

The C preprocessor is the first step in the compilation process for C programs. It handles directives that begin with '#' like #include and #define. 

The preprocessor expands macros, resolves #include directives, and processes other pre-compiler instructions before passing the code to the compiler.

Some key responsibilities of the C preprocessor:

- Expanding macro definitions
- Including header files specified with #include
- Handling conditional compilation directives like #if, #ifdef, #ifndef
- Removing comments 
- Concatenating adjacent string literals
- Expanding predefined macros like __FILE__ and __LINE__

The preprocessor allows writing code that can adapt easily across platforms and systems by using macros rather than hardcoding values.

This project covers writing macros, including header guards, understanding predefined macros, and learning how to inspect preprocessor output.

### Resources

- [Understanding C program Compilation Process](https://www.youtube.com/watch?v=eW5he5uFBNM) 
- [Object-like Macros](https://gcc.gnu.org/onlinedocs/gcc-5.1.0/cpp/Object-like-Macros.html#Object-like-Macros)
- [Macro Arguments](https://gcc.gnu.org/onlinedocs/gcc-5.1.0/cpp/Macro-Arguments.html#Macro-Arguments)
- [Pre Processor Directives in C](https://www.youtube.com/watch?v=X6HiYbY3Uak) 
- [The C Preprocessor](https://www.cprogramming.com/tutorial/cpreprocessor.html)
- [Standard Predefined Macros](https://gcc.gnu.org/onlinedocs/gcc-5.1.0/cpp/Standard-Predefined-Macros.html#Standard-Predefined-Macros)
- [include guard](https://en.wikipedia.org/wiki/Include_guard)
- [Common Predefined Macros](https://gcc.gnu.org/onlinedocs/gcc-5.1.0/cpp/Common-Predefined-Macros.html#Common-Predefined-Macros)

### Tasks, Answers and Explanations

**0. Object-like Macro**

Create a header file `0-object_like_macro.h` that defines a macro named `SIZE` as an abbreviation for the token `1024`.

**Answer:**

```c
#ifndef OBJECT_LIKE_MACRO_H // include guard 
#define OBJECT_LIKE_MACRO_H

#define SIZE 1024 // macro definition

#endif
```

// This defines the macro `SIZE` with the value `1024`. The `#ifndef` and `#define` ensure this is only defined once.

**1. Pi**

Create a header file `1-pi.h` that defines a macro named `PI` as an abbreviation for the token `3.14159265359`.

**Answer:**

```c
#ifndef PI_H // include guard
#define PI_H 

#define PI 3.14159265359 // macro definition 

#endif
``` 

// This defines the macro `PI` with the value `3.14159265359`. The `#ifndef` and `#define` ensure this is only defined once.

**2. File name**

Write a program that prints the name of the file it was compiled from, followed by a new line.

**Answer:** 

```c
#include <stdio.h> // include stdio.h

/** 
 * main - prints the name of the file
 *
 * Return: Always 0 (Success)
 */
int main(void) 
{
	printf("%s\n", __FILE__); // use __FILE__ macro
	return (0);
}
```

// This uses the predefined `__FILE__` macro to print the current file name.

**3. Function-like macro**  

Write a function-like macro `ABS(x)` that computes the absolute value of a number `x`.

**Answer:**

```c  
#ifndef FUNCTION_LIKE_MACRO_H // include guard
#define FUNCTION_LIKE_MACRO_H

#define ABS(x) ((x) < 0 ? -(x) : (x)) // macro definition

#endif
```

// This defines a macro `ABS(x)` that uses a ternary operator to return either the negative or positive version of `x`, implementing the absolute value function.

**4. SUM**

Write a function-like macro `SUM(x, y)` that computes the sum of the numbers `x` and `y`.

**Answer:** 

```c
#ifndef SUM_H // include guard
#define SUM_H

#define SUM(x, y) ((x) + (y)) // macro definition 

#endif
```

// This defines a simple macro `SUM(x, y)` that adds `x` and `y` together to compute the sum.
