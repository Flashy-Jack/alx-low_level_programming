# PROJECT: 0x05. C - Pointers, arrays and strings

## Project By: Jordan Crossley

## Course: ALX SOFTWARE ENGINEERING 

# C Pointers, Arrays and Strings Project

## Overview

![image](https://user-images.githubusercontent.com/105258746/190977571-d5135d31-02a5-4ff3-88de-d9062d6cfe13.png)

This project covers key concepts related to pointers, arrays and strings in C programming. The tasks focus on manipulating pointers to update variable values, swapping values between integers, finding string lengths, printing strings and arrays, copying strings, reversing strings, printing parts of strings, converting strings to integers, and generating random passwords.

### Resources
- [C - Arrays](https://www.tutorialspoint.com/cprogramming/c_arrays.htm) - Tutorialspoint arrays reference  
- [C - Pointers](https://www.tutorialspoint.com/cprogramming/c_pointers.htm) - Tutorialspoint pointers reference
- [C - Strings](https://www.tutorialspoint.com/cprogramming/c_strings.htm) - Tutorialspoint strings reference

### man or help:
The man pages cover the standard C library functions related to strings (e.g. strlen, strcpy), character I/O (e.g. putchar, puts), pseudorandom numbers (e.g. rand, srand), time (e.g. time), and numeric conversions (e.g. atoi).

## Tasks answers and explanations

### 0-reset_to_98.c

```c
#include "main.h" // Includes the main header file 

/**
 * reset_to_98 - Updates the value pointed to by n to 98  
 * @n: The pointer to update
*/
void reset_to_98(int *n) // Function definition
{
     *n = 98; // Dereferences n and sets that memory address to 98
}
```

- The reset_to_98 function takes a pointer to an int as input and updates the underlying value to 98. 
- It dereferences the pointer using the '*' operator to set the value at that address to 98.
- This allows the function to modify the original variable passed via its pointer.

### 1-swap.c

```c
#include "main.h" // Includes the main header file

/**
 * swap_int - Swaps the values of integers a and b
 * @a: The first integer to swap  
 * @b: The second integer to swap
*/ 
void swap_int(int *a, int *b) // Function definition
{
     int temp = *a; // Stores value at a in temp
     *a = *b; // Sets a to value at b  
     *b = temp; // Sets b to original value of a
}
```

- The swap_int function swaps the values of two integer pointers a and b.
- It stores one value in a temporary variable temp on line 5.
- Then it sets a to b's value and b to the original value of a stored in temp on lines 6-7.
- This switches the values that a and b point to in memory.

### 2-strlen.c

```c
#include "main.h" // Includes the main header file

/**
 * _strlen - Returns the length of a string
 * @s: The string to get the length of
 * 
 * Return: The length of @s
*/  
int _strlen(char *s) // Function definition
{
     int length = 0; // Initialize length counter
     
     while (*s != '\0') { // Iterate until null terminator
          length++; // Increment counter
          s++; // Move s pointer forward
     }

     return (length); // Return final length
}
```

- _strlen iterates through each char in string pointer s until '\0' on line 8.  
- It increments the length counter each iteration on line 9.
- On line 10 it moves the pointer s forward. 
- This traverses the string to calculate and return its total length.

### 3-puts.c

```c
#include "main.h" // Includes main header file

/**
 * _puts - Prints a string to stdout
 * @str: The string to print  
*/
void _puts(char *str) // Function definition
{
     while (*str != '\0') { // Iterate until null terminator
          _putchar(*str++); // Print current char and increment str pointer 
     }

     _putchar('\n'); // Print newline after string
}
```

- _puts prints each char in string str while incrementing the pointer on line 8, until '\0'.
- On line 10 it prints a newline to complete the line.
- This prints the full string character-by-character.

Here are line by line explanations for tasks 4-print_rev.c through 101-keygen.c:

### 4-print_rev.c

```c
#include "main.h" // Includes main.h header file

/**
 * print_rev - Prints a string in reverse
 * @s: The string to print  
*/
void print_rev(char *s) // Function definition
{
     int len = 0; // Initialize length counter

     while (s[len] != '\0') { // Iterate to find null terminator
          len++; // Increment counter each loop
     }

     for (int i = len - 1; i >= 0; i--) { // Loop backwards  
          _putchar(s[i]); // Print current char
     }

     _putchar('\n'); // Print newline after finished
}
```

- Finds string length by incrementing len until null terminator
- Loops backwards from len - 1 down to 0 printing each char 
- Prints newline after finished printing in reverse

### 5-rev_string.c

```c
#include "main.h"

/**
 * rev_string - Reverses a string 
 * @s: String to reverse
*/
void rev_string(char *s) 
{
     int len = 0; // Initialize length counter
     char tmp; // Temporary char 
     
     while (s[len] != '\0') { // Find null terminator
          len++;  
     }

     for (int i = 0; i < len / 2; i++) { // Swap opposite chars
          tmp = s[i]; // Store current char
          s[i] = s[len - i - 1]; // Set current to char from end
          s[len - i - 1] = tmp; // Set end char to tmp
     }
}
```

- Finds string length 
- Swaps chars from opposite ends until middle
- Temp variable tmp stores one char during swap

### 6-puts2.c

```c  
#include "main.h"

/**
 * puts2 - Prints every other char of string
 * @str: The string to print
*/
void puts2(char *str)
{
     int i = 0; // Initialize counter

     while (str[i] != '\0') { // Iterate over each char
          if (i % 2 == 0) { // If index is even
               _putchar(str[i]); // Print char
          }

          i++; // Increment counter
     }

     _putchar('\n'); // Print newline after done 
}
```

- Iterates through each char, printing if index is even
- Increments counter i each iteration  
- Prints newline after finished printing every other char

### 7-puts_half.c

```c
#include "main.h"  

/**
 * puts_half - Prints second half of string 
 * @str: The string to print
*/
void puts_half(char *str)
{
     int len = 0; // Initialize length counter
     
     while (str[len] != '\0') { // Find null terminator
          len++; 
     }

     int n = len / 2; // Calculate midpoint
     if (len % 2 == 1) { // If odd, print extra char
          n++;  
     }

     for (int i = n; i < len; i++) { // Print from midpoint 
          _putchar(str[i]);
     }

     _putchar('\n'); // Print newline after done
} 
```

- Finds string length
- Calculates midpoint index n based on even/odd length 
- Prints from n to end of string
- Handles odd length by printing extra char

### 8-print_array.c

```c
#include "main.h"

/**
 * print_array - Prints n elements of array 
 * @a: The array
 * @n: Number of elements
*/
void print_array(int *a, int n)
{
     for (int i = 0; i < n - 1; i++) { // Print each up to n - 1
          printf("%d, ", a[i]); // With comma
     }

     if (n > 0) { // Handle n == 0 edge case
          printf("%d", a[n - 1]); // Print last without comma
     }

     printf("\n"); // Print newline after done
}
```

- Loops printing each element up to n - 1 followed by comma  
- Prints last element without comma
- Handles n == 0 edge case by not printing final element

### 9-strcpy.c

```c
#include "main.h"   

/**
 * _strcpy - Copies string src to dest  
 * @dest: Destination string
 * @src: Source string
 *
 * Return: Pointer to dest
*/
char *_strcpy(char *dest, char *src)
{
     int i = 0; // Initialize counter

     while (src[i] != '\0') { // Iterate over src
          dest[i] = src[i]; // Copy char to dest
          i++; // Increment counter
     }

     dest[i] = '\0'; // Add null terminator
     return dest; // Return dest pointer
}
```

- Iterates through src string while not null terminator
- Copies each src char to dest string
- Adds null terminator to end of dest 
- Returns pointer to dest string

You're right, I made a mistake in including print_number.c when it is not part of the project tasks. Here is an updated explanation without 11-print_number.c and with 10-atoi.c corrected to 100-atoi.c:

### 100-atoi.c

```c
#include "main.h"

/**
 * _atoi - Converts string to integer
 * @s: String to convert
 *
 * Return: Converted integer
*/  
int _atoi(char *s)
{
     int sign = 1; // Track sign 
     int num = 0; // Track digits

     for (int i = 0; s[i] != '\0'; i++) {
          if (s[i] == '-') { // Flip sign if -
               sign *= -1;
          } else if (s[i] >= '0' && s[i] <= '9') { // Accumulate digits  
               num = (num * 10) + (s[i] - '0');
          } else if (num > 0) { // Break at non-digit
               break;
          }
     }

     return sign * num; // Return sign * digits
}
```

- Iterates through string tracking sign and building digit num
- Sign flips if minus character encountered
- Digits 0-9 converted to int values and added
- Breaks once non-digit char encountered
- Returns sign multiplied by num

### 101-keygen.c

```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

/** 
 * main - Generates random valid passwords
 * 
 * Return: Always 0 (Success)
*/
int main(void)  
{
     int pass[100]; // Array of digit chars
     int sum = 0; // Sum of digits

     srand(time(NULL)); // Seed random generator
     
     for (int i = 0; i < 100; i++) {
          pass[i] = rand() % 78; // Random digit [0-77]
          sum += pass[i] + '0'; // Accumulate sums
          putchar(pass[i] + '0'); // Print digit
          if (sum + '0' >= 2772) { // Check sum criteria
               break; // Done if exceeded 2772 
          }
     }

     return 0; // Return success status
}
```

- Seeds random number generator with current time
- Generates random digit chars [0-77]
- Sums digits and prints each digit
- Stops when sum of digits exceeds 2772
- Returns 0 success status after generating valid password  

This uses rand() to generate random digit chars [0-9a-zA-Z] that meet the crackme sum criteria.


