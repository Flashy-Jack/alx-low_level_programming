# Project: 0x0F. C - Function pointers

## Project By: Jordan Crossley  

## Course: ALX Software Engineering

## Overview

![image](https://media.geeksforgeeks.org/wp-content/uploads/20221221122225/Function-Pointer-768.png)

Function pointers allow you to pass around and call functions as if they were values or variables in C. This enables powerful techniques like callbacks, dynamic dispatch, and polymorphism.

### Declaring Function Pointers

To declare a function pointer variable that points to a function with a given signature, you use this syntax:

```c
returnType (*variableName)(paramType1, paramType2, ...);
```

For example:

```c
int (*addFunc)(int, int); // pointer to function that adds two ints
```

This declares `addFunc` as a pointer to a function that takes two int parameters and returns an int.

You can also declare function pointers as part of structs or arrays.

### Assigning Function Pointers

To assign a function to a function pointer, you simply use the function name without parentheses:

```c 
int add(int x, int y) {
  return x + y;
}

addFunc = &add; // Assign function add to the pointer
```

The function name evaluates to the memory address of the function code, so it can be assigned to a pointer.

You can also assign function pointers directly:

```c
addFunc = &add;
subtractFunc = &subtract; 
```

### Calling Function Pointers

To call a function through a pointer, you dereference the pointer using the `*` operator:

```c
int result = (*addFunc)(2, 3); // Calls add using the pointer
```

As a shortcut, you can also call function pointers using the pointer name as if it was the function:

```c  
int result = addFunc(2, 3); 
```

This makes usage simpler in most cases.

### Why Use Function Pointers?

Key reasons to use function pointers:

- **Callbacks** - Pass functions to be called at later time
- **Polymorphism** - Abstract away implementation details
- **Dynamic dispatch** - Choose implementation dynamically
- **Data organization** - Store function pointers in structs or arrays

They allow a very flexible and modular programming style in C.

## Resources
- Function Pointer in C: https://www.geeksforgeeks.org/function-pointer-in-c/
- Pointers to functions: https://publications.gbdirect.co.uk//c_book/chapter5/function_pointers.html  
- Function Pointers in C / C++: https://www.youtube.com/watch?v=ynYtgGUNelE
- Everything you need to know about pointers in C: https://www.youtube.com/watch?v=sxTFSDAZM8s

## Tasks, Answers and Explanations

### 0. What's my name

**Task:** Write a function `print_name` that prints a name using a function pointer parameter to print the name.

### 0-print_name.c

```c
#include <stdlib.h>
#include "function_pointers.h"

/**
 * print_name - prints a name 
 * @name: name to print
 * @f: pointer to the printing function
 */
void print_name(char *name, void (*f)(char *))
{
  // Check if name or function pointer are NULL
  if (!name || !f) 
    return;
  
  // Call function f passed in, passing the name 
  f(name);
}
```

This function takes a name and function pointer. It checks they are not NULL, then calls the function passed in, giving it the name to print.

This takes a character pointer `name` and a function pointer `f`. It checks they are not NULL, then calls the function `f` passed, passing the name to print.

To call it:

```c
print_name("John", print_name_function);
```

Where `print_name_function` is defined elsewhere. This allows passing different print functions to customize printing.

### 1. If you spend too much time thinking about a thing, you'll never get it done

**Task:** Write a function `array_iterator` that executes a callback function on each element of an array.

### 1-array_iterator.c

```c  
#include <stdlib.h>
#include "function_pointers.h"

/**
 * array_iterator - executes a function given on array elements
 * @array: array to iterate over
 * @size: size of the array 
 * @action: function pointer to use
*/
void array_iterator(int *array, size_t size, void (*action)(int))
{
  unsigned int i;
  
  // Loop through array
  for (i = 0; i < size; i++) { 
    // Call action function on each element
    action(array[i]);
  }
}
```
Iterates an array of given size, calling the passed action function on each element.

This takes an integer array, size, and a callback function pointer. It loops through the array, calling the callback on each element.

To use:

```c  
array_iterator(array, 100, print_element);
```

This calls `print_element` on each of the 100 elements. The callback can do anything, like print or modify array elements.

### 2. To hell with circumstances; I create opportunities  

**Task:** Write `int_index` that searches an array for a value based on a comparator function.

### 2-int_index.c

```c
#include "function_pointers.h"

/**
 * int_index - search array for int using cmp function
 * @array: array to search
 * @size: size of array
 * @cmp: function pointer to compare values
 *
 * Return: index of match or -1 if not found
*/  
int int_index(int *array, int size, int (*cmp)(int))
{
  // Loop through array
  for (int i = 0; i < size; i++) {

    // Call compare function on element
    if (cmp(array[i]) != 0) {
      
      // Return index if cmp finds match
      return i; 
    }
  }

  // Not found
  return -1; 
}
```

Searches an array by calling a compare function on each element. Returns index where compare matches or -1 if not found.

This takes an array, size, and comparator function pointer. It loops through calling cmp on each element. If cmp returns non-zero (found match), the index is returned. Otherwise -1 (not found).

To use: 

```c  
index = int_index(array, 100, find_42); 
```

Calls `find_42` on each element, returning index where 42 is found or -1.

### 3. A goal is not always meant to be reached, it often serves simply as something to aim at

**Task:** Write a simple calculator program using operator function pointers.

**Answer:**

`3-calc.h` - Header file with function prototypes and op struct.

`3-op_functions.c` - Contains the operator functions for +, -, *, /, %.

### 3-op_functions.c

Contains the 5 math operator functions:

```c
op_add - addition
op_sub - subtraction 
op_mul - multiplication
op_div - division
op_mod - modulo
```

`3-get_op_func.c` - Returns a pointer to the math operator function corresponding to the operator string passed in.

### 3-get_op_func.c

```c
#include "3-calc.h"

/**
 * get_op_func - returns operator function pointer
 * @s: operator string 
 *
 * Return: function pointer for operator
*/
int (*get_op_func(char *s))(int, int) {

  // Array of operators and function pointers
  op_t ops[] = {
      {"+", add},
      {"-", subtract},
      ...
  };

  // Loop through ops array
  for (int i = 0; ops[i].op; i++) {

    // Compare operator string
    if (strcmp(ops[i].op, s) == 0) {
  
      // Return matching function pointer
      return ops[i].f; 
    }
  }

  // No match found
  return NULL;
}
```

`3-main.c` - Main program that uses operator functions via pointer.

### 3-main.c

Main program that uses operator functions via pointers.

Key parts:

```c
// Get function pointer for operator  
op_func = get_op_func(argv[2]);

// Call function pointer  
result = op_func(arg1, arg2);
```

### 4. Most hackers are young because young people tend to be adaptable. As long as you remain adaptable, you can always be a good hacker

**Task:** Write a program that prints the opcodes of its own `main` function.

**FILENAME:** 100-main_opcodes.c

```c
#include <stdio.h>

/**
 * main - prints opcodes of main function
 * @argc: number of arguments
 * @argv: argument array
 *
 * Return: 0 on success
*/
int main(int argc, char *argv[]) {

  // Convert arg to number of bytes
  int bytes = atoi(argv[1]);

  // Get pointer to start of main 
  char *arr = (char *)main;

  // Loop through bytes
  for (int i = 0; i < bytes; i++) {
    
    // Print byte in hex
    printf("%02hhx", arr[i]);  
    
    // Add space between
    if (i != bytes - 1) {
      printf(" "); 
    }
  }

  // Newline 
  printf("\n");

  return 0; 
}
```

This takes the number of bytes as an argument, gets a char pointer `arr` to the start of the `main` function code using typecasting. 

It loops through the requested number of bytes, printing the opcode hexadecimal values, with spaces between.

This directly prints the machine code opcodes that make up the `main` function by treating the function as data.

## Additional Info

This covers the basics of declaring, assigning, and using function pointers in C. Function pointers are powerful for implementing callbacks, polymorphism, and other techniques.
