# PROJECT: 0x02. C - Functions, nested loops

## Project By: Jordan Crossley

## Course: ALX SOFTWARE ENGINEERING 

## Overview

![image](https://user-images.githubusercontent.com/105258746/189934273-f596e713-d5a1-4ab2-b623-75094e5c9b0e.png)

Here is an updated overview section summarizing the key concepts:

## Overview

This project focuses on writing reusable functions, looping through iterations, printing output, and evaluating conditions in C programming. The main concepts covered are:

- Modular programming with functions 
- Iteration with for and while loops
- Printing formatted text output
- Controlling program flow based on logic

Writing modular functions allows code to be reused. Loops perform repeated execution. Printing output allows results to be displayed. Evaluating conditions with logic controls code flow.

Mastering these core programming concepts of functions, loops, print, and logic in C is essential for being able to properly structure code, automate repetitive tasks, display results, and make decisions programmatically.

**Key concepts**:

- Writing functions with arguments and return values
- Understanding scope and lifetime of variables  
- Utilizing for and while loops and nesting loops
- Printing characters and strings with putchar
- Formatting output using techniques like padding
- Evaluating logic with if/else statements and comparisons
- Calling functions from within other functions
- Defining function prototypes
- Performing mathematical and string operations

Mastering these foundational concepts will enable creating robust programs in C.

## Resources

- [Nested while loops video](https://www.youtube.com/watch?v=Z3iGeQ1gIss) - Explains nested while loops in C with examples

- [C functions reference](http://www.tutorialspoint.com/cprogramming/c_functions.htm) - Covers function syntax, return values, scope, passing arguments, prototypes

- [Learning C video](https://www.youtube.com/watch?v=qMlnFwYdqIw) - Video tutorial on writing C functions

- [Function prototype reference](https://www.geeksforgeeks.org/what-is-the-purpose-of-a-function-prototype/) - Explains purpose and syntax of prototypes

- [C header files reference](https://www.tutorialspoint.com/cprogramming/c_header_files.htm) - Covers including and declaring headers

## Task Code Explanations

### 0-putchar.c

```c
#include "main.h" // Includes header file with _putchar prototype

/**
 * main - Entry point function
 *
 * Return: Always 0 (Success)
*/

int main(void) // Main function definition
{
  char str[] = "_putchar"; // Initialize string variable
  int ch; // Counter variable
  
  for (ch = 0; ch < 8; ++ch) // Loop through string
    _putchar(str[ch]); // Call _putchar to print each char
  
  _putchar('\n'); // Print new line

  return (0); // Return 0 for success
}
```

This program prints the string `_putchar` by looping through each character and passing it to the `_putchar` function to print.

### 1-alphabet.c

```c  
#include "main.h"

/**
 * print_alphabet - Print alphabet a-z
*/

void print_alphabet(void) // Function definition
{
  int ch; // Counter variable

  for (ch = 'a'; ch <= 'z'; ++ch) // Loop 'a' to 'z'
    _putchar(ch); // Print each character
  
  _putchar('\n'); // Print new line
}
```

This function prints the lowercase alphabet a-z by looping from `a` to `z` and calling `_putchar` on each character.

### 2-print_alphabet_x10.c

```c
#include "main.h"

/**  
 * print_alphabet_x10 - Prints alphabet 10 times 
*/

void print_alphabet_x10(void) // Function definition
{
  char ch; // Inner loop counter
  int i; // Outer loop counter

  i = 0; 

  while (i < 10) { // Outer loop iterates 10 times
    
    ch = 'a';
    while (ch <= 'z') { // Inner loop prints a-z
      _putchar(ch);
      ch++; 
    }
    
    _putchar('\n'); // New line after inner loop
    i++; // Increment outer counter
  }

}
```

This function utilizes nested `while` loops to print the alphabet 10 times. The outer loop controls the number of iterations, while the inner loop prints `a-z`.

### 3-islower.c

```c
#include "main.h"  

/**
 * _islower - Check if c is lowercase
 * @c: Character to check
 *
 * Return: 1 if lowercase, 0 if not
*/

int _islower(int c) // Function definition
{
  if (c >= 'a' && c <= 'z') // Compare to a-z range
    return (1); 
  
  return (0); // Default return 0
}
```

This function checks if a character is lowercase by comparing `c` to the lowercase alphabet range `a-z`. It returns `1` if true, `0` if false.

### 4-isalpha.c

```c
#include "main.h"

/**
 * _isalpha - Check if alphabetic character
 * @c: Character to check
 *
 * Return: 1 if alphabetic, 0 if not 
*/

int _isalpha(int c)
{
  // Check both lowercase and uppercase ranges
  return ((c >= 'a' && c <= 'z') || (c >= 'A' && c <= 'Z')); 
}
```

This function checks if `c` is alphabetical by comparing it to both the lowercase `a-z` and uppercase `A-Z` ranges. It returns `1` if true, `0` if false.

### 5-sign.c

```c
#include "main.h"

/**
 * print_sign - Prints sign of number
 * @n: Number to check
 *
 * Return: 1 for positive, 0 for zero, -1 for negative
*/

int print_sign(int n) 
{
  if (n > 0) {
    _putchar('+');
    return (1);
  }
  else if (n == 0) {
    _putchar('0');
    return (0);
  }
  else {
    _putchar('-');
    return (-1);
  }
}
```

This prints the sign of `n` as `+` if positive, `0` if zero, `-` if negative. It returns `1`, `0`, or `-1` based on the sign.

### 6-abs.c

```c
#include "main.h"

/**
 * _abs - Computes absolute value of integer
 * @n: Number to take absolute value of
 *
 * Return: Absolute value of n
*/

int _abs(int n)
{
  if (n < 0) // If n is negative
    n = (-1) * n; // Make positive
  
  return (n);
} 
```

This function computes the absolute value of `n`. If `n` is negative, it makes it positive by multiplying by -1.

### 7-print_last_digit.c


```c
/*
Extracts, prints, and returns last digit of a number
Demonstrates modulo operation and printing digits
*/

int print_last_digit(int n) {

  int lastDigit = n % 10; // Isolate last digit

  _putchar(lastDigit + '0'); // Print as char

  return lastDigit;

}
```

This function extracts the last digit of a number using modulo, prints it, and returns the value. It demonstrates isolating a digit and printing it.

- Takes in an int
- Isolates last digit using modulo
- Prints and returns last digit

### 8-24_hours.c

```c  
/* 
Prints hours:minutes 00:00-23:59
Shows nested loops and printing time values
*/

void jack_bauer(void) {

  int hour, min; // Loop counters

  for (hour = 0; hour < 24; hour++) {
    for (min = 0; min < 60; min++) {
      
      _putchar((hour / 10) + '0'); // Print hours
      _putchar((hour % 10) + '0');
      
      _putchar(':'); // Print separator

      _putchar((min / 10) + '0'); // Print minutes
      _putchar((min % 10) + '0');

      _putchar('\n'); // New line
    }
  }

}
```

This function uses nested loops to iterate hours 0-23 and minutes 0-59, printing each complete time. It demonstrates printing formatted time values.

- Uses nested loops for hours and minutes
- Prints formatted time string for each iteration
- Demonstrates printing time/date values

### 9-times_table.c

```c
#include "main.h"

/**
 * times_table - Prints 9 times table 0-9
*/

void times_table(void)
{
  int num, mult, prod;

  for (num = 0; num <= 9; ++num) {
    _putchar('0');
    
    for (mult = 1; mult <= 9; ++mult) {
      _putchar(',');
      _putchar(' ');

      prod = num * mult;

      if (prod <= 9) 
        _putchar(' ');
      
      else
        _putchar((prod / 10) + '0');

      _putchar((prod % 10) + '0');
    }
    _putchar('\n');
  }
}
```

This prints the 9 times table by nesting two `for` loops. The outer loop iterates each number 0-9. The inner loops prints the multiple for each 1-9 and formats it.

Here are detailed explanations for 10-add.c and 11-print_to_98.c:

### 10-add.c

```c
int add(int a, int b) {

  int sum;
  
  // Declares variable to store sum

  sum = a + b; 
  
  // Adds input parameters a and b

  return (sum);

  // Returns the sum

}
```

This function takes two `int` inputs, stores their sum in `sum`, and returns it.

- `a` and `b` are the input parameters
- `sum` holds the result of `a + b` 
- The sum is calculated then returned

It allows summing two numbers by calling the function and passing arguments.

### 11-print_to_98.c

```c
void print_to_98(int n) {

  if (n <= 98) {

    // If n is less than or equal to 98

    for (int i = n; i <= 98; i++) {
    
      // Loop from n to 98

      printf("%d", i); 

      // Print current number

      if (i != 98) {
      
        // Add comma except last number
      
        printf(", "); 

      }

    }

  } else {

    // If n is greater than 98

    for (int i = n; i >= 98; i--) {
    
      // Loop down from n to 98

      printf("%d", i);

      if(i != 98) {
      
        printf(", ");
      
      }

    }

  }

  printf("\n");

}
```

This function prints all numbers between `n` and 98:

- Checks if `n` is less than or greater than 98
- Uses appropriate loop to increment or decrement
- Prints each number, adding comma separator
- Prints new line after loop finishes

It handles both ascending and descending sequences from `n`.

### 100-times_table.c

```c  
#include "main.h"

/**
 * print_times_table - Prints input time table
 * @n: Number input
*/

void print_times_table(int n)
{
  // Nested loops print rows and columns  
  for (int row = 0; row <= n; row++) {
    for (int col = 0; col <= n; col++) {
      int prod = row * col;
      
      if (col != 0) 
        _putchar(',');

      if (prod < 10) 
        _putchar(' ');
      else 
        _putchar((prod / 10) + '0');

      _putchar((prod % 10) + '0');
    }
    _putchar('\n');
  }
}
```

This function prints the input `n` times table by nesting two `for` loops to iterate the rows and columns. It formats each number to handle 1 or 2 digits.

### 101-natural.c

```c
int main(void) {

  int sum = 0;

  for (int i = 0; i < 1024; i++) {

    // Loops 0 to 1023

    if (i % 3 == 0 || i % 5 == 0) {
    
      // Checks if divisible by 3 or 5

      sum += i; // Adds to sum if true

    }

  }

  printf("%d\n", sum); // Prints total sum
  
}
``` 

Sums multiples of 3 and 5 below 1024.

### 102-fibonacci.c

```c
int main(void) {
  
  int n1 = 0, n2 = 1, next;

  for (int i = 0; i < 50; i++) {

    // Loop 50 times

    if (i > 1) {
    
      // Skips printing first 2
     
      printf(", ");

    }

    printf("%d", n1); // Prints current

    next = n1 + n2; // Calculates next term

    n1 = n2; // Shifts sequence down
    n2 = next;

  }

}
```

Prints first 50 Fibonacci sequence terms.
### 103-fibonacci.c

Here is a detailed explanation of the 103-fibonacci.c code:

```c
int main(void) {

  int i;
  
  // Declares loop counter variable i

  unsigned long int j = 1;
  unsigned long int k = 2;
  
  // Initializes first two Fibonacci numbers

  unsigned long int sum = 0;
  
  // Sum variable to keep track of total

  unsigned long int next;

  // Temporary variable to store next number

  for (i = 1; i <= 33; i++) {

    // Loop 33 times 

    if (j < 4000000 && j % 2 == 0) {
    
      // Check if j is even and < 4 million
      
      sum += j; // Add to sum if true
  
    }

    next = j + k; // Calculate next Fibonacci number

    j = k; // Shift j to next number
    k = next; // Shift k to next number

  }

  printf("%lu\n", sum); // Print final sum 

}
```

Key points:

- Uses unsigned long ints to allow large numbers
- Initializes starting Fibonacci numbers 
- Calculates next number each iteration 
- Sums even numbers below 4 million
- Prints total sum after loop ends

This calculates even Fibonacci numbers and sums those below 4 million.

### 104-fibonacci.c

```c
#include <stdio.h>

/**
 * main - Print first 98 Fib nums
 *
 * Return: Always 0
*/

int main(void)
{
  // Initialize variables
  unsigned long int i; 
  unsigned long int bef1 = 1;
  unsigned long int bef2 = 2;

  // Print first two pre-defined numbers
  printf("%lu", bef1);
  printf(", %lu", bef2);

  // Loop and print 96 more
  for (i = 2; i < 98; i++) {
    unsigned long int cur = bef1 + bef2;
    printf(", %lu", cur);
    bef1 = bef2;
    bef2 = cur;
  }
  
  printf("\n");
  return (0);
}
```

This prints the first 98 Fibonacci sequence numbers. It initializes the first two numbers then uses a loop to print each subsequent number by adding the previous two.
