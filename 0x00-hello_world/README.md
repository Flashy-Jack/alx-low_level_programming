# PROJECT: 0x00. C - Hello, World

## Project By: Jordan Crossley

## Course: ALX SOFTWARE ENGINEERING

## Overview

## Overview

![image](https://i.pinimg.com/736x/2a/55/1a/2a551a79059e2338775e8598e77dcaae--programming.jpg)

This project covers the basics of compiling and running C programs using the gcc compiler.

The `gcc` command compiles C source code files into executable binaries. The basic usage is:

```
gcc [options] <source files>
```

Some common gcc options:

- `-E`: Only run the preprocessor
- `-S`: Only run the preprocessor and compiler, output assembly code
- `-c`: Only run the preprocessor, compiler, no linking
- `-o`: Specify output executable filename
- `-Wall`: Enable common warnings 
- `-std=`: Specify C language standard

The `printf` function prints formatted output to stdout. It takes a format string and arguments:

```c
printf("format string", arguments); 
```

Common format specifiers:
- `%d` - integer
- `%c` - character
- `%s` - string
- `%f` - float

The `puts` function prints a string to stdout followed by a newline. 

The `putchar` function prints a character to stdout.

The `sizeof` operator returns the size in bytes of a type or variable.

The `main` function is the entry point of a C program. It has an integer return type that serves as the program's exit status.

Header files like `<stdio.h>` contain declarations for standard library functions.

The man pages provide more detail on these and other functions.

NOTE: For this project we have used `chmod u+x` to compile all files. The first line of all SSH scripts must start with `#!/bin/bash` 

## Resources

- [Everything you need to know to start with C](https://intranet.alxswe.com/rltoken/fY96UFVTZ-oN6hL85E6L4w)
- [Dennis Ritchie](https://en.wikipedia.org/wiki/Dennis_Ritchie)
- [“C” Programming Language: Brian Kernighan](https://www.youtube.com/watch?v=de2Hsvxaf8M)  
- [Why C Programming Is Awesome](https://www.youtube.com/watch?v=smGalmxPVYc)
- [Learning to program in C part 1](https://www.youtube.com/watch?v=rk2fK2IIiiQ) 
- [Learning to program in C part 2](https://www.youtube.com/watch?v=FwpP_MsZWnU)
- [Understanding C program Compilation Process](https://www.youtube.com/watch?v=VDslRumKvRA)
- [Betty Coding Style](https://github.com/holbertonschool/Betty/wiki)
- [Hash-bang under the hood](https://twitter.com/unix_byte/status/1024147947393495040?s=21) 
- [Linus Torvalds on C vs. C++](http://harmful.cat-v.org/software/c++/linus)

## man or help:

- `gcc`
- `printf` 
- `puts`
- `putchar`

### Tasks, Answers and Explanations

#### 0. Preprocessor

```bash
#!/bin/bash
gcc -E $CFILE -o c
```

This runs the C source code (`$CFILE`) through the preprocessor only and saves the preprocessed output to the file `c`. The `-E` flag tells gcc to only run the preprocessor step.

#### 1. Compiler 

```bash
#!/bin/bash
gcc -c $CFILE
```

This compiles the C source code (`$CFILE`) into an object file without linking. The `-c` flag tells gcc to only run the compilation step, which generates a `.o` object file with the same name as the source (except for the `.c` extension changed to `.o`).

#### 2. Assembler

```bash
#!/bin/bash
gcc -S $CFILE
```

This generates assembly code from the C source code (`$CFILE`). The `-S` flag tells gcc to only run the compilation step and generate assembly code output. The assembly file will have the same name as the C file but with a `.s` extension.

#### 3. Name

```bash
#!/bin/bash
gcc $CFILE -o cisfun
```

This compiles the C source code (`$CFILE`) into an executable called `cisfun`. By default, gcc compiles and links the source code into an executable called `a.out`, but the `-o` flag lets us specify the output file name.

#### 4. Hello, puts

```c
#include <stdio.h>

/**
 * main - Prints "Programming is like building a multilingual puzzle"
 *
 * Return: Always 0.
 */
int main(void)
{
        puts("\"Programming is like building a multilingual puzzle");
        return (0);
}
```

This uses the `puts()` function to print a string to stdout. `puts()` prints the string followed by a newline character. The `\"` escapes the double quote so it is printed.

#### 5. Hello, printf

```c
#include <stdio.h>

/**
 * main - Prints "with proper grammar, but the outcome is a piece of art,"
 *
 * Return: Always 0.
 */
int main(void)
{
        printf("with proper grammar, but the outcome is a piece of art,\n");
        return (0);
}
```

This uses `printf()` to print a formatted string. `\n` prints a newline character.

#### 6. Size is not grandeur

```c
#include <stdio.h>

/**
 * main - Prints the sizes of various types
 *
 * Return: Always 0.
 */
int main(void)
{
    printf("Size of a char: %d byte(s)\n", sizeof(char));
    printf("Size of an int: %d byte(s)\n", sizeof(int));
    printf("Size of a long int: %d byte(s)\n", sizeof(long int));
    printf("Size of a long long int: %d byte(s)\n", sizeof(long long int));
    printf("Size of a float: %d byte(s)\n", sizeof(float));
    return (0);
}
```

This uses `sizeof` to print out the sizes in bytes of various data types.

#### 100. Intel

```bash
#!/bin/bash
gcc -S -masm=intel $CFILE
```

This generates assembly code from the C source code (`$CFILE`) using Intel syntax. The `-S` flag outputs assembly and `-masm=intel` sets the syntax to Intel.

#### 101. UNIX is basically a simple operating system

```c
#include <unistd.h>

/**
 * main - Prints a string to stderr
 *
 * Return: Always 1.
 */
int main(void)
{
  write(2, "and that piece of art is useful\" - Dora Korpar, 2015-10-19\n", 59);
  return (1);
}
```

This uses the `write()` system call to print a string to stderr (file descriptor 2). It returns 1 to represent an error.

## Additional Info

The `Betty` linter can be installed for checking coding style.
