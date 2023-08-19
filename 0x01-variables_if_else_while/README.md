# PROJECT: 0x01. C - Variables, if, else, while

## Project By: Jordan Crossley  

## Course: ALX SOFTWARE ENGINEERING

## Overview

![image](https://media.geeksforgeeks.org/wp-content/uploads/20230424101456/Conditional-Statements-in-c.webp)

This project covers foundational concepts in C programming that are essential for beginning C developers to understand:

### Variables
- Variables hold data in a program and must be declared before use
- C has basic data types like int, char, float, double
- Variable names follow rules and conventions 

### Arithmetic Operators 
- C provides operators for mathematical operations like +, -, *, /, %
- These allow calculations on numeric variables

### If/Else Statements
- If/else allows conditional execution based on a boolean expression
- If evaluates the expression and executes code if true
- Else executes code when the expression is false

### While Loops
- While loops repeat a block of code as long as a condition is true
- Condition is evaluated before each iteration
- Loop continues until condition becomes false

### Printing Output
- printf() and putchar() are standard library functions to print output
- printf() formats strings with variables interpolated  
- putchar() prints single characters

### Code Structure
- C code is organized into functions like main()
- Code blocks use { } braces to group statements 
- Proper indentation and spacing is required

This project uses these concepts to print numbers, letters, and combinations of them. The tasks build an understanding of variables, operators, conditional logic, loops, and printing output in C.

## Resources

- [Everything you need to know to start with C.pdf](https://s3.amazonaws.com/alx-intranet.hbtn.io/uploads/misc/2022/4/e0ccf91eec6b977a9e00ed384dc285df9c2772e3.pdf?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIARDDGGGOUSBVO6H7D%2F20230819%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20230819T131407Z&X-Amz-Expires=86400&X-Amz-SignedHeaders=host&X-Amz-Signature=821083c053b58b55111604746efe30350cf11451a41d6993e17919d2d75db155) - Covers C basics like comments, data types, declarations, operators, if/else, while loops
- [Keywords and identifiers](https://publications.gbdirect.co.uk//c_book/chapter2/keywords_and_identifiers.html) - C reserved words and rules for naming variables/functions
- [integers](https://publications.gbdirect.co.uk//c_book/chapter2/integral_types.html) - Integer types like int, short, long 
- [Arithmetic Operators in C](https://www.tutorialspoint.com/cprogramming/c_arithmetic_operators.htm) - Operators for arithmetic in C like +, -, *, /, %
- [If statements in C](https://www.cprogramming.com/tutorial/c/lesson2.html) - If and if/else statements
- [while loop in C](https://www.tutorialspoint.com/cprogramming/c_while_loop.htm) - While and do/while loop syntax 

## man or help:

`ascii` - Prints ASCII table showing character encodings 

## Tasks answers and explainations

### 0-positive_or_negative.c

```c
#include <stdlib.h>
#include <time.h>
#include <stdio.h>

/**
 * main - Determines if a number is positive, negative or zero.
 * Return: Always 0 (Success)
*/
int main(void)
{
  int n;

  srand(time(0)); // seed random number generator
  n = rand() - RAND_MAX / 2; // get random number
  
  if (n > 0) // check if n is greater than 0
  {
    printf("%d is positive\n", n); // print positive if true
  }
  else if (n == 0) // check if n is equal to 0
  {
    printf("%d is zero\n", n); // print zero if true
  }
  else // if none of the above cases
  { 
    printf("%d is negative\n", n); // print negative
  }
  
  return (0);
}
```

This program generates a random number using srand() and rand() and stores it in the integer variable n. It then checks if n is greater than 0, equal to 0, or less than 0 using if/else statements to print whether the number is positive, zero, or negative.

### 1-last_digit.c

```c
#include <stdlib.h>
#include <time.h>
#include <stdio.h>

/**
 * main - Prints the last digit of a randomly generated number
 *        and whether it is greater than 5, less than 6, or 0.
 * Return: Always 0.
*/
int main(void)
{
  int n;

  srand(time(0)); // seed random number generator
  n = rand() - RAND_MAX / 2; // get random number

  if ((n % 10) > 5) // check last digit
  {
    printf("Last digit of %d is %d and is greater than 5\n", n, n % 10);
  }
  else if ((n % 10) < 6 && (n % 10) != 0) // check last digit
  {
    printf("Last digit of %d is %d and is less than 6 and not 0\n", n, n % 10);
  }
  else // last digit is 0
  {
    printf("Last digit of %d is %d and is 0\n", n, n % 10);
  }

  return (0);

}
```

This program generates a random number n. It prints the last digit of n which is obtained by n % 10. Using if/else, it compares the last digit to 5 and 6 to print messages indicating if it is greater than 5, less than 6, or equal to 0.

### 2-print_alphabet.c

```c
#include <stdio.h>

/**
 * main - Prints the alphabet in lowercase.
 * Return: Always 0 (Success)
*/
int main(void)
{
  char alp[26] = "abcdefghijklmnopqrstuvwxyz";
  int i;

  for (i = 0; i < 26; i++) // loop through alphabet
  {
    putchar(alp[i]); // print current letter
  }
  
  putchar('\n'); // print newline after loop
  return (0);
}
```

This program stores the alphabet in a character array alp. It loops through the array using a for loop and index i, calling putchar() to print each letter. After the loop, it prints a newline.

### 3-print_alphabets.c

```c  
#include <stdio.h>

/**
 * main - Prints the alphabet in lowercase and uppercase.
 * Return: Always 0 (Success)
*/
int main(void)
{
  char alp[52] = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";
  int i;

  for (i = 0; i < 52; i++) // loop through lowercase and uppercase alphabet
  {
    putchar(alp[i]); // print current letter
  }
  
  putchar('\n'); // print newline after loop
  return (0); 
}
```

This is similar to the previous task, but uses a longer string containing both cases of the alphabet. It loops through 52 characters and prints each one with putchar().

### 4-print_alphabt.c

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

/**  
 * main - Prints the alphabet except for q and e.
 * Return: Always 0 (Success)
*/
int main(void)
{
  int i;

  for (i = 97; i < 123; i++) // ascii codes for lowercase letters
  {
    if (i != 101 && i != 113) // skip e and q
    {
      putchar(i); 
    }
  }
  
  putchar('\n');
  return (0);
}
```

This loops through lowercase ascii codes, printing each letter unless it is e or q by using an if statement inside the loop.

### 5-print_numbers.c

```c  
#include <stdio.h>

/**
 * main - Prints numbers from 0 to 9. 
 * Return: Always 0 (Success)
*/  
int main(void)
{
  int i;
  
  for (i = 0; i < 10; i++)
  {
    printf("%d", i); // print current number 
  }

  putchar('\n');
  return (0);
} 
```

Simple for loop from 0 to 9, printing each number with printf().

### 6-print_numberz.c

```c
#include <stdio.h>

/**
 * main - Print 0 to 9 using putchar.
 * Return: Always 0 (Success)  
*/
int main(void)
{
  int i;

  for (i = 48; i < 58; i++) // ascii codes for 0-9
  {
    putchar(i);
  }

  putchar('\n');
  return (0);
}
```

Same as previous task but uses putchar() and ascii codes instead of printf().

Here are the full code examples and explanations for tasks 7 through 102:

### 7-print_tebahpla.c

```c
#include <stdio.h>

/**
 * main - Prints the lowercase alphabet in reverse.
 * Return: Always 0 (Success)
*/
int main(void) 
{
  char ch;

  for (ch = 'z'; ch >= 'a'; ch--) // start at 'z', end at 'a'
  {
    putchar(ch); // print current letter
  }

  putchar('\n'); // print newline after loop
  return (0);
}
```

This loops backwards from 'z' to 'a' using the decrement operator. Each letter is printed with putchar().

### 8-print_base16.c

```c
#include <stdio.h>

/**
 * main - Prints hex digits 0-9 and a-f in lowercase.
 * Return: Always 0 (Success)
*/
int main(void)
{
  int i;

  for (i = 48; i < 58; i++) // ascii codes for 0-9
  {
    putchar(i); 
  }

  for (i = 97; i < 103; i++) // ascii codes for a-f
  {
    putchar(i);
  }

  putchar('\n');
  return (0);
} 
```

Two loops print the hex digit characters using their ascii values - 0-9 from 48 to 57, and a-f from 97 to 102. 

### 9-print_comb.c

```c
#include <stdio.h>

/**
 * main - Prints digits 0 to 9 with commas.
 * Return: Always 0 (Success)
*/
int main(void)
{
  int i;
  
  for (i = 48; i < 58; i++)
  {
    putchar(i);
    
    if (i != 57) // no comma after last digit
    {
      putchar(',');
      putchar(' '); 
    }
  }

  putchar('\n');
  return (0);
}
```

This loop prints each digit, then a comma and space, except after the last digit 9.

### 100-print_comb3.c

```c
#include <stdio.h>

/**
 * main - Prints combinations of two different digits. 
 * Return: Always 0 (Success)
*/
int main(void)
{
  int i, j;

  for (i = 48; i < 58; i++) 
  {
    for (j = 49; j < 58; j++)
    {
      if (j > i) // print only increasing combinations
      {
        putchar(i);
        putchar(j);
        
        if (i != 56 || j != 57) // no comma after last combo
        {
          putchar(',');
          putchar(' ');
        }
      }
    }
  }

  putchar('\n');
  return (0);
}
```

Nested loops generate all combinations of two increasing digits. Comma and space are printed between combinations.

### 101-print_comb4.c

```c
#include <stdio.h>

/**  
 * main - Prints combinations of three digits.
 * Return: Always 0 (Success)
*/
int main(void)
{
  int i, j, k;

  for (i = 48; i < 58; i++)
  {
    for (j = 49; j < 58; j++) 
    {
      for (k = 50; k < 58; k++)
      {
        if (k > j && j > i) // increasing order
        {
          putchar(i);
          putchar(j);
          putchar(k);
          
          if (i != 55 || j != 56) // comma except after last
          {
            putchar(',');
            putchar(' ');
          }
        }
      }
    }
  }

  putchar('\n'); 
  return (0);
}
```

Three nested loops generate increasing combinations of three digits. Commas separate combinations.

### 102-print_comb5.c

```c
#include <stdio.h>

/**
 * main - Prints combinations of two two-digit numbers.
 * Return: Always 0 (Success)
*/
int main(void)
{
  int i, j;
  
  for (i = 0; i < 100; i++)
  {
    for (j = 0; j < 100; j++) 
    {
      if (i < j)
      {
        putchar((i / 10) + 48); // tens digit as ascii
        putchar((i % 10) + 48); // ones digit as ascii
        putchar(' ');
        putchar((j / 10) + 48);
        putchar((j % 10) + 48);
        
        if (i != 98 || j != 99)
        {
          putchar(',');
          putchar(' ');
        }
      }
    }
  }

  putchar('\n');
  return (0);
}
```

Loops count from 0 to 99 for variables i and j. Each digit of i and j is printed by converting to ascii. Comma separates combinations.

## Additional info

- Variables, arithmetic operators, if/else statements and while loops form the basic building blocks of C programs
- Functions like printf() and putchar() from the standard library are used for output
- Code is structured using functions like main() and code blocks surrounded by { } braces
- Proper code styling and formatting must be followed for readability
