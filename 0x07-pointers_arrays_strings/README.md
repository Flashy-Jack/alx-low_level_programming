# PROJECT: 0x07. C - Even more pointers, arrays and strings

## Project By: Jordan Crossley  

## Course: ALX SOFTWARE ENGINEERING

![image](https://media.geeksforgeeks.org/wp-content/uploads/20230412184146/Strings-in-C.webp)

## Overview

This project covers concepts like pointers to pointers, multidimensional arrays, and common C standard library functions for string manipulation. The tasks involve implementing functions that make use of these concepts.

Here is an expanded overview section explaining the key concepts and tasks in more detail:

## Overview

This project covers important concepts related to pointers, arrays, and strings in C programming:

### Pointers to pointers

- A pointer variable that stores the address of another pointer variable.
- Allows creating multiple levels of indirection i.e. a pointer to a pointer points to a pointer that points to data.
- Used when you need to modify the pointer's address from a function.
- Operations like addition/subtraction on double pointers move them by the size of the datatype they point to.

### Multidimensional arrays

- Arrays containing elements that are also arrays. 
- Commonly used to represent matrices or tables of data with multiple indices like rows and columns.
- Elements are stored contiguously row by row in memory.
- Can be accessed using nested index expressions like a[i][j].
- Useful for problems that require matrix or tabular operations.

### C strings  

- Array of characters terminated with a null '\0' byte.
- Allows storing sequences of characters like text.
- String manipulate functions expect null terminated strings.
- Strings can be declared statically or dynamically allocated.
- Handled using character pointers that point to first char.

### C standard library string functions

- Functions defined in string.h like strlen, strcpy, strcat etc.
- Used to operate on null terminated string arguments.
- Implement common string tasks like copy, concatenate, compare, search.
- Avoid reimplementing basic string utilities.

The tasks in this project involve:

- Filling a block of memory using a loop and pointer arithmetic.
- Copying a fixed number of bytes from one memory area to another. 
- Locating a character in a null terminated string using pointer traversal.
- Finding the length of a matching substring at start using nested loops.
- Searching for any occurrence of a set of bytes inside a string.
- Finding a substring within a larger string by comparing char by char.  
- Printing a 2D array (like a chess board) by traversing rows and columns.
- Calculating sum of diagonals in a 2D array using pointer offsets.
- Setting one pointer variable to point to another via a function.

This provides hands-on experience with memory management, data structures, string handling and other key aspects of C programming.

## Resources

- Pointers and arrays concept: https://intranet.alxswe.com/concepts/60 
- C - Pointer to Pointer: https://www.tutorialspoint.com/cprogramming/c_pointer_to_pointer.htm
- C – Pointer to Pointer with example: https://beginnersbook.com/2014/01/c-pointer-to-pointer/
- Multi-dimensional Arrays in C: https://www.tutorialspoint.com/cprogramming/c_multi_dimensional_arrays.htm 
- Two dimensional (2D) arrays in C: https://beginnersbook.com/2014/01/2d-arrays-in-c-example/

These resources explain the key concepts of pointers to pointers, multidimensional arrays, and working with strings in C.

## man or help:

The man pages cover the standard C library functions like memset, memcpy, strchr, strspn etc. These explain the purpose, syntax and usage of the functions.

## Tasks answers and explanations

### 0-memset.c

```c
#include "main.h"

/**
 * _memset - fills memory with a constant byte
 * @s: memory area to fill
 * @b: constant byte
 * @n: number of bytes to fill
 *
 * Return: changed array with new value for n bytes
*/

char *_memset(char *s, char b, unsigned int n) {

  int i = 0; // initialize counter to 0

  for (; n > 0; i++) {
    
    s[i] = b; // set current byte s[i] to value of b

    n--; // decrement n to move through memory
  }

  return (s); // return pointer to filled memory s
}
```

This initializes a counter `i`, then loops through the memory `s` until `n` reaches 0, setting each element to the value of `b`. It returns a pointer to the filled memory area `s`.

### 1-memcpy.c

```c
#include "main.h"

/**
 * _memcpy - copies n bytes from memory area src to dest
 * @dest: memory area to copy to 
 * @src: memory area to copy from
 * @n: number of bytes to copy
 *
 * Return: pointer to dest
*/

char *_memcpy(char *dest, char *src, unsigned int n) {

  int r = 0; // counter for loop

  for (; r < n; r++) {
    
    dest[r] = src[r]; // copy byte from src to dest
    
  }

  return (dest); // return pointer to copied memory dest
}
```

This iterates a counter `r` from 0 to `n-1`, copying bytes from `src` to `dest` one by one. It returns a pointer to `dest`.

### 2-strchr.c

```c
#include "main.h"

/**
 * _strchr - locates first occurrence of c in s
 * @s: string to search
 * @c: character to find
 * 
 * Return: pointer to located character or NULL
*/

char *_strchr(char *s, char c) {
  
  int i = 0; // initialize index to 0
  
  for (; s[i] >= '\0'; i++) {
    
    if (s[i] == c) // check current char s[i] matches c
      return (&s[i]); // return pointer if match is found
    
  }
  
  return (0); // no match found, return NULL
}
```

This loops through each character in `s` starting from index 0 until a null terminator is reached. It returns a pointer to the first occurrence of `c`, or NULL if no match is found.

### 3-strspn.c

```c
#include "main.h"

/**
 * _strspn - gets length of prefix substring
 * @s: main string to search
 * @accept: string containing bytes to match
 * 
 * Return: number of initial bytes in s from accept 
*/

unsigned int _strspn(char *s, char *accept) {

  unsigned int n = 0; // counter for bytes matched
  
  while (*s) {

    for (int r = 0; accept[r]; r++) {
    
      if (*s == accept[r]) { 
      
        n++; // increment counter if byte matches
        break;
        
      } else if (accept[r + 1] == '\0') {
      
        return (n); // return count when end of accept is reached
        
      }
    }
    
    s++; // move through strings 
  }

  return (n);
}
```

This iterates through `s`, checking if each byte is present in `accept` and increasing counter `n` if a match is found. It returns `n` when end of `accept` is reached.

### 4-strpbrk.c

```c  
#include "main.h"

/**
 * _strpbrk - searches string for any bytes from accept
 * @s: string to search
 * @accept: bytes to look for
 *
 * Return: pointer to byte in s matching accept or NULL
*/

char *_strpbrk(char *s, char *accept) {

  while (*s) {
  
    for (int k = 0; accept[k]; k++) {
    
      if (*s == accept[k]) // check for match
        return (s); // return pointer if found
      
    }
    
    s++; // move to next byte in s 
  }

  return ('\0'); // no match, return NULL
}
```

This loops through each byte of `s`, checking if it matches any byte in `accept`. It returns a pointer to the first match or NULL if no match.

### 5-strstr.c

```c
#include "main.h"

/** 
 * _strstr - locates substring needle in haystack
 * @haystack: string to search in
 * @needle: substring to find
 *
 * Return: pointer to located substring or NULL
*/

char *_strstr(char *haystack, char *needle) {

  for (; *haystack != '\0'; haystack++) {
  
    char *l = haystack; // set pointer l to current
    char *p = needle; // set p to start of needle
  
    while (*l == *p && *p != '\0') {
    
      l++; // increment pointers if chars match
      p++;
    
    }
    
    if (*p == '\0') // if reached end of needle
      return (haystack); // return pointer to start of match

  }

  return (0); // no match found  
}
```

This loops through `haystack`, comparing substring `needle` and returning a pointer if the full `needle` is matched.

### 7-print_chessboard.c

```c  
#include "main.h"

/**
 * print_chessboard - prints a chessboard 
 * @a: chessboard array
*/

void print_chessboard(char (*a)[8]) {

  for (int i = 0; i < 8; i++) {
  
    for (int j = 0; j < 8; j++) {
    
      _putchar(a[i][j]); // print each element
      
    }
    
    _putchar('\n'); // print new line after row
    
  }

}
```

This uses nested loops to iterate through the 2D chessboard array, printing each element followed by a new line after each row.

### 8-print_diagsums.c

```c
#include "main.h"  

/**
 * print_diagsums - prints sum of diagonals
 * @a: square matrix
 * @size: size of matrix
*/

void print_diagsums(int *a, int size) {

  int sum1 = 0; 
  int sum2 = 0;

  for (int i = 0; i < size; i++) {

    sum1 += a[i * size + i]; // sum top-left to bottom-right
    
    sum2 += a[i * size + size - i - 1]; // sum bottom-right to top-left
  }

  printf("%d, %d\n", sum1, sum2); // print sums  
}
```

This calculates the two diagonal sums by traversing the array from opposite ends, then prints them.

### 100-set_string.c

```c
#include "main.h"

/**
 * set_string - sets value of pointer to char
 * @s: pointer to pointer
 * @to: pointer
*/

void set_string(char **s, char *to) {

  *s = to; // set s to point to address stored in to
  
}
```

This sets the pointer `s` to point to the address stored in the pointer `to`.

### 101-crackme_password

This file contains the password for the crackme2 executable.

 101-crackme_password contains the password for the [crackme2](https://github.com/holbertonschool/0x06.c) executable.
- You may need to install the `openssl` library to run the crakme2 program: `sudo apt install libssl-dev`
- Edit the source list `sudo vim /etc/apt/sources.list` to add the following line: `deb http://security.ubuntu.com/ubuntu xenial-security main` Then `sudo apt update` and `sudo apt install libssl1.0.0`

OR 

## The Advanced task no. 9
1. open the file using `vi -b 101-crackme_password`
2. when you see the vi window, don't use the insert mode, just type `:set binary` and hit enter
3. type `:set noeol` and hit enter
4. use the insert mode(i) and type abc123
5. esc `:wq` hit enter

==> Then do the github steps on Git add . , Git Commit -m "latest", git push
