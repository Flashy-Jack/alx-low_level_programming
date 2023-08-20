# PROJECT: 0x08. C - Recursion

## Project By: Jordan Crossley

## Course: ALX SOFTWARE ENGINEERING

## Overview

![image](https://media.geeksforgeeks.org/wp-content/cdn-uploads/Recursive-Functions-in-c.png)

This project focuses on implementing recursion in C. Recursion is when a function calls itself repeatedly to solve a problem. The key is having a base case that will end the recursion.

**Recursion** is a technique where a function calls itself repeatedly to solve a problem. Any problem that can be solved recursively can also be solved iteratively, but sometimes recursion provides an elegant and simple solution.

Some examples of problems that can be solved recursively:

- Factorial - calculating n!
- Fibonacci sequence - f(n) = f(n-1) + f(n-2)
- Reversing a string or linked list by reversing the rest of the list first
- Tree traversal - traversing child nodes recursively

The key is to ensure there is a **base case** that does not make a recursive call, to end the recursion. Otherwise it will keep calling itself forever, causing a stack overflow.

![Recursion Diagram](https://www.researchgate.net/profile/Wei-Chiang-Hong/publication/220942631/figure/fig3/AS:305851638976515@1449899174801/An-example-of-the-recursive-function-calls-of-the-factorial-function.png)

## Resources

- [Recursion in C](https://www.programiz.com/c-programming/recursion) - Tutorial on recursion concepts and examples in C.
- [C Programming Recursion](https://www.tutorialspoint.com/cprogramming/c_recursion.htm) - Recursion tutorial with C code examples.
- [Recursion in Wikipedia](https://en.wikipedia.org/wiki/Recursion_(computer_science)) - General overview of recursion concepts.

## man or help 

The C standard library provides functions like `puts()`, `strlen()`, `factorial()` etc. The man pages for these explain the function prototypes, parameters, return values and purpose.

Before implementing these functions recursively, study their man pages to understand how they work.

For example, `man puts` shows that `puts()` writes a string to stdout up to the null terminator, and appends a newline.

## Tasks Code Explanations

### 0-puts_recursion.c

```c
void _puts_recursion(char *s)
{
  if (*s) { // check if current char is not null
    _putchar(*s); // print current char
    _puts_recursion(s + 1); // call recursively on next char
  } else {
    _putchar('\n'); // print newline when reach null terminator
  }
}
```

This implements a recursive version of the `puts()` function.

- It prints each character in the string `s` by recursively calling itself on the next character. 
- Once we reach the null terminator (`*s == '\0'`), it prints a newline and returns.

### 1-print_rev_recursion.c

```c
void _print_rev_recursion(char *s) 
{
  if (*s) {
    _print_rev_recursion(s + 1); // call recursively on next char first
    _putchar(*s); // print current char after return
  }
}
```

This prints a string in reverse by recursively calling itself on each next character first before printing the current one.

- First it recursively calls itself on the next character `s+1`. 
- When that recursive call returns, it prints the current character `*s`.
- This has the effect of printing each character only after printing all subsequent characters first.

### 2-strlen_recursion.c

```c  
int _strlen_recursion(char *s)
{
  int length = 0;

  if (*s) {
    length++; // increase length
    length += _strlen_recursion(s + 1); // add returned recursive length 
  }
  
  return length;
}
```

This recursively calculates the length of the string `s`:

- Initialize a `length` variable to track length.
- If `*s` is not null, increase `length` by 1.
- Recursively call `_strlen_recursion` on `s+1` to get length of rest of string, and add it to `length`. 
- When we reach null terminator, `length` contains total length.

### 3-factorial.c

```c
int factorial(int n) 
{
  if (n < 0) // invalid input
    return -1; 
  if (n == 0) // base case
    return 1;

  return (n * factorial(n - 1)); // recursive call
}
```

This calculates the factorial recursively:

- Base cases - return 1 if `n == 0`, return -1 for invalid input 
- Otherwise, recursively call `factorial(n-1)` to calculate `(n-1)!`
- Multiply `(n-1)!` by `n` to calculate `n!`

### 4-pow_recursion.c

```c
int _pow_recursion(int x, int y)
{
  if (y < 0) // invalid
    return -1;

  if (y == 0) // base case    
    return 1;

  return x * _pow_recursion(x, y - 1); // recursively call
} 
```

This raises a number `x` to power `y` recursively:

- Base cases - return 1 if `y == 0`, return -1 if `y` is negative
- Recursively call `_pow_recursion(x, y-1)` to calculate `x^(y-1)`  
- Multiply `x^(y-1)` by `x` to get `x^y`

### 5-sqrt_recursion.c

```c
int _sqrt_recursion(int n)
{
  return actual_sqrt_recursion(n, 0); 
}

int actual_sqrt_recursion(int n, int i) 
{
  if (i*i > n) // exceeded 
    return -1; 
  
  if (i*i == n) // found square root
    return i;

  return actual_sqrt_recursion(n, i + 1); // try next number
}
```

This uses recursion to calculate the square root of a number:

- Start `i` at 0, increment it each recursive call until `i*i > n`
- When `i*i == n`, we've found the square root, so return `i` 
- Return -1 if `i*i` exceeds `n` without finding square root

### 100-is_palindrome.c  

```c
int is_palindrome(char *s)
{
  int len = _strlen_recursion(s);
  return check_pal(s, 0, len - 1);
}

int check_pal(char *s, int i, int j) {

  if (i >= j) // finished checking
    return 1;
  
  if (s[i] != s[j]) // not palindrome
    return 0;

  return check_pal(s, i + 1, j - 1); // check next chars
} 
```

This checks if a string is a palindrome recursively:

- Get the length of string using `_strlen_recursion()`
- Call `check_pal()` on indexes `i=0` to `j=len-1` 
- Compare chars at indexes `i` and `j`
  - If different, return 0 (not palindrome)
  - If same, recursively check next chars by incrementing `i` and decrementing `j`
- When `i >= j`, we've checked all chars, so string is palindrome.

Here are the line-by-line explanations for 101-wildcmp.c:

### 101-wildcmp.c

```c
int wildcmp(char *s1, char *s2) {

  if (*s1 == '\0') { // if s1 is empty

    if (*s2 != '\0' && *s2 == '*') // if s2 has a *
      return wildcmp(s1, s2 + 1); // skip the * and recurse

    return (*s2 == '\0'); // if s2 is also empty, match

  }

  if (*s2 == '*') // if s2 has a *

    return wildcmp(s1 + 1, s2) || wildcmp(s1, s2 + 1); 
    // try skipping 1 char in s1 or skipping the * in s2

  if (*s1 == *s2) // if current chars match

    return wildcmp(s1 + 1, s2 + 1); // compare next chars

  return 0; // strings don't match

}
```
This compares two strings allowing a wildcard `*` character:

- If `s1` is empty:
  - If `s2` has a `*`, recursively call on `s2+1` to skip it
  - If `s2` is also empty, the strings match.
- If `s2` has a `*`:
  - Try matching `s1+1` to `s2` (skipping 1 char in `s1`) 
  - Or try matching `s1` to `s2+1` (skipping the `*` in `s2`)
- If current chars of `s1` and `s2` match, recursively compare next chars.
- If none of above, the strings don't match.

## Additional Info

- Recursion allows elegant solutions, but can have high memory cost due to function calls.
- Limit recursion depth to avoid stack overflow.
- Iterative solutions have lower overhead but can be more complex.
- Use recursion for intrinsically recursive problems like tree traversal, combinatorics.
