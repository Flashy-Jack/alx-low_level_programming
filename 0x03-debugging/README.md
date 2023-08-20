# PROJECT: 0x03. C - Debugging

## Project By: Jordan Crossley  

## Course: ALX SOFTWARE ENGINEERING

## Overview

![image](https://res.cloudinary.com/practicaldev/image/fetch/s--u050vX7V--/c_imagga_scale,f_auto,fl_progressive,h_900,q_auto,w_1600/https://dev-to-uploads.s3.amazonaws.com/i/jpoha21x1m8mr9xsz4y1.jpg)

This project covers debugging in C and reading error messages. The project aims to solve issues in C code examples using techniques like adding print statements and fixing logical errors. It covers key concepts such as using print statements to debug code, fixing infinite loops and logical errors, reading compiler warnings and error messages, testing code with different inputs, and ensuring code handles all cases.

The project is divided into 4 tasks:

Task 0: Multiple mains
Task 1: Like, comment, subscribe
Task 2: 0 > 972?
Task 3: Leap year

### Resources

- [Debugging Wikipedia article](https://en.wikipedia.org/wiki/Debugging)
- [Rubber Duck Debugging article](https://www.thoughtfulcode.com/rubber-duck-debugging-psychology/)

### man or help:

- debug
- gdb

## Tasks answers and explanations

### 0-main.c

```c
#include "main.h" // Includes header file with function prototype

/**
* main - tests function that prints if integer is positive or negative
* Return: 0
*/

int main(void) // Main function
{
        int i; // Declare integer variable

        i = 0; // Initialize i to 0
        positive_or_negative(i); // Call function with i = 0

        return (0); // Return 0 for success
}
```

This implements the main function to test the positive_or_negative() function. It passes 0 to test the case of 0 input.

### 1-main.c

```c  
#include <stdio.h> // Include stdio.h for printf

/**
* main - causes an infinite loop
* Return: 0  
*/

int main(void) // Main function
{
        int i; // Declare loop counter

        printf("Infinite loop incoming :(\n"); // Print message

        i = 0; // Initialize i to 0

        /*while (i < 10) // Original while loop
        {
                putchar(i); // Print each iteration
        }*/

        printf("Infinite loop avoided! \\o/\n"); // Success message

        return (0); // Return 0 for success
}
```

The while loop is commented out to avoid an infinite loop.

### 2-largest_number.c

```c
#include "main.h" // Includes header file

/**
 * largest_number - returns the largest of 3 numbers
 * @a: first integer
 * @b: second integer
 * @c: third integer
 * Return: largest number
*/

int largest_number(int a, int b, int c) // Function definition
{
  int largest; // Variable to store largest

  if (a >= b && a >= c) // Check if a is largest
  { 
    largest = a; 
  }
  else if (b >= a && b >= c) // Check if b is largest
  {
    largest = b;
  }
  else // Otherwise c must be largest
  {
    largest = c; 
  }

  return (largest); // Return the largest number
}
```

This checks every case to find the largest number instead of assuming order.

### 3-print_remaining_days.c

```c  
#include <stdio.h> // Include stdio.h
#include "main.h" // Include header file

/**
 * print_remaining_days - takes a date and prints how many days are 
 * left in the year, taking leap years into account
 * @month: month in number format
 * @day: day of month
 * @year: year
 * Return: void
*/

void print_remaining_days(int month, int day, int year) // Function definition
{
  if ((year % 400 == 0) || (year % 4 == 0 && year % 100 != 0)) // Check for leap year
  {
    if (month > 2 && day >= 60) // After Feb, increment if >= 60 days
    {
      day++; 
    }
    
    printf("Day of the year: %d\n", day); // Print day of year
    printf("Remaining days: %d\n", 366 - day); // Print remaining days
  }
  else // Not a leap year
  {
    if (month == 2 && day == 60) // Check for invalid Feb 29
    {
      printf("Invalid date: %02d/%02d/%04d\n", month, day - 31, year);
    }
    else 
    {
      printf("Day of the year: %d\n", day); // Print day of year
      printf("Remaining days: %d\n", 365 - day); // Print remaining days
    }
  }
}
```

The leap year logic is fixed to check >= 60 days in February instead of just 60.

## Additional info

Key concepts covered include:

- Using print statements to debug code
- Fixing infinite loops and logical errors
- Reading compiler warnings and error messages  
- Testing code with different inputs
- Ensuring code handles all cases
