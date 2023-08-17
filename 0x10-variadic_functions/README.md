# PROJECT: 0x10. C - Variadic functions

## Project By: Jordan Crossley

## Course: ALX SOFTWARE ENGINEERING 

## Overview

![image](https://slideplayer.com/slide/12182675/71/images/3/Variadic+Functions+in+C.jpg)

![image](https://qph.cf2.quoracdn.net/main-qimg-e411b04ad11b1390dbae4caec08e6381-pjlq)

Variadic functions are functions that can take a variable number of arguments. They are useful when you want a function to be flexible and work with different numbers and types of parameters. 

In C, variadic functions use a set of macros defined in `stdarg.h` to access their arguments:

- `va_start` - Initializes access to the list of arguments.
- `va_arg` - Accesses the next argument in the list.
- `va_end` - Cleans up the list when done.

To create a variadic function in C, you declare it with an ellipsis (...) instead of a fixed list of parameters. Inside the function, `va_start` is used to initialize a `va_list` that points to the first variable argument. `va_arg` is then used in a loop to access each argument and do something with it. Finally, `va_end` cleans up the `va_list`.

Key points:

- Variadic functions have a variable number of arguments.
- `stdarg.h` defines macros to access the arguments.
- Use `va_start`, `va_arg`, and `va_end` to process arguments.
- Declare variadic functions with an ellipsis instead of fixed parameters.
- Can pass different numbers and types of arguments each call.

This project covers creating variadic functions, passing them arguments, and printing out those arguments in different ways.
## Resources
- [stdarg.h](https://en.wikipedia.org/wiki/Stdarg.h) - Header file that defines macros for accessing arguments in variadic functions
- [Variadic Functions](https://www.gnu.org/software/libc/manual/html_node/Variadic-Functions.html) - Documentation on variadic functions in C
- [Const Keyword](https://www.youtube.com/watch?v=1W4oyuOdXv8) - Video explaining the const keyword in C

## man or help
- `stdarg` - Manual page for stdarg macros

## Tasks, Answers and Explanations

### 0. Beauty is variable, ugliness is constant (0-sum_them_all.c)

```c
int sum_them_all(const unsigned int n, ...) {
  // Initialize variable argument list
  va_list list;
  va_start(list, n);
  
  // Sum all arguments in the list
  int sum = 0;
  for (unsigned int i = 0; i < n; i++) {
    sum += va_arg(list, int);
  }
  
  // Clean up list
  va_end(list);

  return sum;
}
```

This function calculates the sum of all the arguments passed to it. 

- va_start initializes `list` to point to the first variable argument after `n`.
- The `for` loop iterates `n` times, using `va_arg` to get each argument and add it to `sum`. 
- `va_arg` takes the `list` and the type to cast the argument to.
- `va_end` cleans up the list.
- The sum is returned.

### 1. To be is to be the value of a variable (1-print_numbers.c)

```c
void print_numbers(const char *separator, const unsigned int n, ...) {

  // Initialize list
  va_list list;
  va_start(list, n);

  // Print each argument
  for (unsigned int i = 0; i < n; i++) {
    // Print number
    printf("%d", va_arg(list, int));
    
    // Print separator  
    if (separator != NULL && i != 0) {
      printf("%s", separator);
    }
  }

  // Clean up list
  va_end(list);

  printf("\n");
}
```

This function prints numbers passed as arguments, separating them with a string if given.

- `va_start` and `va_end` initialize and clean up the list.
- The `for` loop prints each argument.
- If no separator is passed, just print the number.
- For the first number, don't print the separator.
- Otherwise, print the separator between numbers.
- A newline is printed at the end.

### 2. One woman's constant is another woman's variable (2-print_strings.c)

```c
void print_strings(const char *separator, const unsigned int n, ...) {

  // Initialize list
  va_list list;
  va_start(list, n);

  // Print each string
  for (unsigned int i = 0; i < n; i++) {

    // Get the string pointer
    char *str = va_arg(list, char *);

    // Print string or (nil) if NULL
    if (str == NULL) {
      printf("(nil)");
    } else {
      printf("%s", str);
    }

    // Print separator
    if (separator != NULL && i != 0) {
      printf("%s", separator);
    }
  }

  // Clean up list
  va_end(list);

  printf("\n");
}
```

This prints strings passed as arguments, separating them with a string if given.

- `va_start` and `va_end` initialize and clean up. 
- Loop through the arguments.
- Get the string pointer from `va_arg` and check if NULL.
- Print the string like the previous task, handling separators.
- `(nil)` is printed if a NULL string is passed.
- A newline is printed at the end.

### 3. To be is a to be the value of a variable (3-print_all.c)

```c
void print_all(const char *format, ...) {

  // Initialize list
  va_list list;
  va_start(list, format);

  // Print arguments based on format
  for (int i = 0; format[i] != '\0'; i++) {
    switch(format[i]) {
      case 'c':
        printf("%c", va_arg(list, int));
        break;
      case 'i':
        printf("%d", va_arg(list, int));
        break;
      case 'f':
        printf("%f", va_arg(list, double));
        break;
      case 's':
        char *str = va_arg(list, char *);
        if (str == NULL) {
          printf("(nil)");
        } else {
          printf("%s", str);
        }
        break;
    }

    // Print separator
    if (format[i + 1] != '\0') {
      printf(", "); 
    }
  }

  // Clean up list
  va_end(list);

  printf("\n");

}
```

This prints anything based on a format string listing the types.

- `format` contains the types of the arguments - 'c' for char, 'i' for int, 'f' for float, 's' for string.
- Loop through `format`, printing each argument based on its type. 
- `va_arg` is used to get the next argument from the list based on the type.
- Strings are checked for NULL.
- A separator is printed between each argument.
- Anything not in the format string is skipped.
- `va_end` cleans up the list.

## Additional Info
This covers the basics of variadic functions in C - how to access the variable arguments, iterate through them, and print them. The stdarg.h macros `va_start`, `va_arg`, and `va_end` are critical to working with these kinds of functions.
