# PROJECT: 0x04. C - More functions, more nested loops

## Project By: Jordan Crossley

## Course: ALX SOFTWARE ENGINEERING 

## Overview

![image](https://runestone.academy/ns/books/published/csawesome/_images/nestedloops.png)

This project covers writing custom functions and using nested loops in C programming. Functions allow code to be reused easily, while loops provide a way to repeat operations efficiently. 

The tasks involve writing C functions that perform basic operations like [checking uppercase/lowercase](https://www.tutorialspoint.com/cprogramming/c_functions.htm), [multiplying integers](https://beginnersbook.com/2014/01/c-multiply-two-numbers/), printing numbers/characters, and drawing shapes with repeated characters. [Nested loops](https://www.programiz.com/c-programming/nested-loops) are used to repeat inner loop operations multiple times.

Functions encapsulate reusable logic with inputs and return values. Loops and conditionals enable iterating through ranges of values and selecting which to print/process. Combining functions, loops, conditional checks, character printing allows creating reusable logic blocks.

### Resources

- [C Functions Tutorial](http://www.tutorialspoint.com/cprogramming/c_functions.htm) - Covers function syntax, prototypes, passing arguments etc
- [Nested Loops in C](https://www.programiz.com/c-programming/nested-loops) - Examples of nested for and while loops
- [C Header Files](https://www.tutorialspoint.com/cprogramming/c_header_files.htm) - How header files work and link with source code

## Tasks answers and explanations

### 0-isupper.c

```c
int _isupper(int c) 
{
  if (c >= 'A' && c <= 'Z') // Compare c to uppercase ASCII values
    return (1);  
  else
    return (0); 
}
```

This function checks if the int input `c` is uppercase. It compares `c` to the ASCII values between `A` and `Z` using the AND `&&` operator. If true, it returns 1, otherwise 0. This allows reuse to check uppercase.

### 1-isdigit.c

```c
int _isdigit(int c)
{
  if (c >= '0' && c <= '9') // Compare c to digit ASCII values
    return (1);
  else
    return (0);  
}
```

Similar to 0-isupper.c, this function checks if the `int c` input is a digit between 0-9 by comparing to the ASCII values with AND. Returns 1 if true, 0 if false. Reusable for checking digits.

### 2-mul.c

```c
int mul(int a, int b) 
{
  return (a * b); // Multiply a and b then return
}
```

This multiplies the two `int` inputs `a` and `b` using the * operator. The result is returned, allowing reuse for multiplying integers.

### 3-print_numbers.c

```c
void print_numbers(void)
{
  char c;

  for (c = '0'; c <= '9'; c++) // Loop '0' to '9' ASCII values
  {
    _putchar(c); // Print char c 
  }
  _putchar('\n'); // Newline after loop
}
```

This prints the numbers 0 to 9 using a `for` loop incrementing `char c` from `'0'` to `'9'`. Each ASCII char value is passed to `_putchar()` to print. `\n` prints a newline after the loop ends.

### 4-print_most_numbers.c

```c  
void print_most_numbers(void)
{
  char c;
  
  for (c = '0'; c <= '9'; c++) // Loop 0-9
  {
    if (!(c == '2' || c == '4')) // Skip 2 and 4
      _putchar(c);
  }
  _putchar('\n');
}
```

Similar to the previous function, but excludes printing 2 and 4 using an `if` check for `c != '2'` AND `c != '4'`. The `!` flips the logic to skip those ASCII values.

### 5-more_numbers.c

```c
void more_numbers(void)
{
  int i, j;

  for (i = 0; i < 10; i++) // Outside loop 
  {
    for (j = 0; j <= 14; j++) // Inside loop
    {
      if (j >= 10)
        _putchar('1'); 
      _putchar(j % 10 + '0'); // Print ones digit  
    }
    _putchar('\n');
  }
}
```

This demonstrates nested loops by printing 0 to 14 ten times. The outer `for` loop runs 10 times based on `int i`. The inner loop prints 0 to 14 by modulus math (`j % 10`) to extract each ones digit and print as a char. This nesting repeats the inner printing loop 10 times total.

### 6-print_line.c

```c
void print_line(int n) 
{
  int i;

  for (i = 0; i < n; i++) // Loop n times
  {
    _putchar('_'); // Print '_' char 
  }
  _putchar('\n');
}
```

This prints a horizontal line of `_` characters based on the `int n` size input. It loops from 0 to `n`, calling `_putchar('_')` each time, then prints a newline after the loop ends.

### 7-print_diagonal.c

```c
void print_diagonal(int n)
{
  int i, j;

  for (i = 0; i < n; i++) // Loop n times 
  {
    for (j = 0; j < n; j++) // Inner loop
    {
      if (j == i) // Print slash on diagonal
        _putchar('\\');  
      else if (j < i)
        _putchar(' ');
    }
    _putchar('\n');
  }
}
```

This prints a diagonal line of `\` characters. The outer loop goes through each row `i`. The inner goes through each column `j`. An `if` checks if `j == i` to print `\` on the diagonal. Else spaces print. This builds the diagonal by printing the slash when the row and column match.

### 8-print_square.c  

```c
void print_square(int size) 
{
  int i, j;

  if (size <= 0) 
  {
    _putchar('\n');
  } else {

    for (i = 0; i < size; i++) // Row loop
    {
      for (j = 0; j < size; j++) // Column loop
      {
        _putchar('#');
      }
      _putchar('\n'); 
    }
  }
}
```

This prints a square of `#` characters based on `int size`. It checks if `size > 0` first. Then nested loops print rows and columns calling `_putchar('#')`. `\n` goes after each row. The loops print `size` rows and columns to form the full square.

### 9-fizz_buzz.c

```c
int main(void)
{
  int i;

  for (i = 1; i <= 100; i++) 
  {
    if (i % 3 == 0 && i % 5 != 0) // Divisible by 3
      printf(" Fizz");

    else if (i % 5 == 0 && i % 3 != 0) // Divisible by 5
      printf(" Buzz");
    
    else if (i % 3 == 0 && i % 5 == 0) // Divisible by 3 and 5  
      printf(" FizzBuzz");

    else if (i == 1) 
      printf("%d", i);

    else
      printf(" %d", i);
  }

  printf("\n");

  return (0);
}
```

This prints the FizzBuzz game by checking each number's divisors. It loops 1 to 100 with `int i`. For multiples of 3 it prints "Fizz", of 5 it prints "Buzz", and both prints "FizzBuzz". Else it prints the number. This demonstrates using conditionals inside loops.

### 10-print_triangle.c

```c
void print_triangle(int size)
{
  int i, j;

  if (size <= 0) {
    _putchar('\n'); 
  } else {

    for (i = 1; i <= size; i++) // Rows
    {
      for (j = i; j < size; j++) // Columns
      {
        _putchar(' '); // Print spaces
      }

      for (j = 1; j <= i; j++) // Print hashes
      {
        _putchar('#');  
      }

      _putchar('\n');
    }
  }
}
```

This prints a triangle of `#` characters based on `int size`. The outer loop increments each row `i`. The first inner loop prints leading spaces by looping from `i` to `size`. Then the second inner prints `i` `#` characters for that row. This builds each new row of the triangle shape.

### 100-prime_factor.c

```c
long int n = 612852475143; // Number to find largest prime factor
long int max = -1; 

for (i = 2; i <= sqrt(n); i = i + 2) { // Test factors up to square root

  while (n % i == 0) { // If factor divides n evenly
    max = i; // Track largest factor in max
    n = n / i; // Divide n to find smaller factors
  }

}

if (n > 2) // If n reduced to a prime number
  max = n; // That number is largest prime factor

printf("%ld\n", max);
```

This finds the largest prime factor by dividing `n` by increasing potential factors `i`. It checks for remainder 0 to find factors, which become the new `max`. Dividing `n` by that factor produces smaller factors. The largest `i` that evenly divides `n` is the maximum prime factor.

### 101-print_number.c

```c  
void print_number(int n)
{
  unsigned int n1; // Temporary positive value

  if (n < 0) { // Handle negative input
    n1 = -n;  
    _putchar('-'); // Print minus sign
  } else {
    n1 = n;
  }

  if (n1 / 10) { 
    print_number(n1 / 10); // Recursive call for left digits
  }

  _putchar((n1 % 10) + '0'); // Print rightmost digit   
}
```

This recursively prints the `int n` number. For negative `n`, it makes the value positive temporarily in `n1` and prints the `-` sign. It calls `print_number` recursively on `n1 / 10` to print left digits. After returning from recursion, it prints the rightmost digit using `% 10` modulus to isolate it. This builds the full number from left to right.

### Additional info

- Functions allow reusable logic blocks
- Loops enable iterating over ranges of values 
- Conditionals select which values to print
- Character printing can draw shapes/patterns
- Nesting combines loops for efficient repetition
- Loops, conditions, and recursion enable processing sequences
- Printing characters/strings can create visual outputs
- Functions allow reusable logic blocks to be invoked
- Nested loops repeat inner loops efficiently
- Modulus `%` finds remainder digits  
- Header files centralize prototypes

