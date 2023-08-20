# PROJECT: 0x06. C - More pointers, arrays and strings

## Project By: Jordan Crossley

## Course: ALX SOFTWARE ENGINEERING

## Overview

![image](https://media.geeksforgeeks.org/wp-content/uploads/20230302091959/Arrays-in-C.png)

This project covers functions in C that manipulate pointers, arrays, and strings. Pointers provide direct access to memory to efficiently work with data. Arrays allow storing collections of data contiguously in memory. Strings represent sequences of characters terminated by a null byte. 

### Resources

The following resources are provided for the project:

- [_putchar.c](https://github.com/holbertonschool/_putchar.c/blob/master/_putchar.c) - writes a character to stdout
- [main.h](https://github.com/jordanrossiter/alx-low_level_programming/blob/master/0x06-pointers_arrays_strings/main.h) - header file with prototypes for all functions

### man or help:

The man page for putchar covers how it writes a character to stdout and returns success/error codes.

## Tasks answers and explanations

### TASK 0: 0-strcat.c

```c
char *_strcat(char *dest, char *src)
{
  int i; // initialize index for dest
  int j; // initialize index for src

  i = 0; 
  // start i at beginning of dest

  while (dest[i] != '\0') 
  {
    i++;
    // increment i to find end of dest string
  }

  j = 0;
  // initialize j at beginning of src

  while (src[j] != '\0')
  {
    dest[i] = src[j]; 
    // copy char from src to end of dest

    i++; 
    // increment dest index

    j++;
    // increment src index
  }

  dest[i] = '\0'; 
  // add null byte at end of new concatenated string

  return (dest);
  // return pointer to dest
}
```

_strcat concatenates two strings. It appends the src string to the dest string, overwriting the terminating null byte (\0) at the end of dest, and then adds a new terminating null byte.

### TASK 1: 1-strncat.c

```c
char *_strncat(char *dest, char *src, int n)
{
  int i; // initialize index for dest
  int j; // initialize index for src

  i = 0;
  // start i at beginning of dest

  while (dest[i] != '\0')  
  {
    i++;
    // find end of dest
  }

  j = 0; 
  // initialize j at beginning of src

  while (j < n && src[j] != '\0') 
  {
    dest[i] = src[j];
    // copy char from src to end of dest

    i++;
    // increment dest index 

    j++; 
    // increment src index
  }

  dest[i] = '\0';
  // add null byte at end

  return (dest);
  // return pointer to dest
}
```

_strncat concatenates two strings similar to _strcat, but only uses at most n bytes from src. It doesn't require src to be null-terminated if it has n or more bytes.

### TASK 2: 2-strncpy.c

```c
char *_strncpy(char *dest, char *src, int n) 
{
  int j;

  j = 0;
  // initialize index at start

  while (j < n && src[j] != '\0')
  {
    dest[j] = src[j];
    // copy chars from src to dest

    j++;
    // increment index
  }

  while (j < n) 
  {
    dest[j] = '\0';
    // pad remaining with null bytes

    j++;
  }

  return (dest);
  // return pointer to dest
}
```

_strncpy copies a string from src to dest up to n bytes. If src is less than n chars, dest is padded with null bytes.

### TASK 3: 3-strcmp.c

```c
int _strcmp(char *s1, char *s2)
{
  int i; // initialize index

  i = 0;

  while (s1[i] != '\0' && s2[i] != '\0')
  {
    if (s1[i] != s2[i]) 
    {
      return (s1[i] - s2[i]);
      // if chars differ, return ascii diff
    }

    i++;
    // increment index
  }

  return (0);
  // if end of both strings, they are equal
}
```

_strcmp compares two strings lexicographically. It iterates through both strings until chars differ or null byte. If chars differ, it returns the difference of the ascii values. If strings are equal, it returns 0.

### TASK 4: 4-rev_array.c

```c
void reverse_array(int *a, int n)
{
  int i; // index
  int t; // temp var

  for (i = 0; i < n--; i++) 
  {
    t = a[i]; 
    // save current element

    a[i] = a[n];
    // overwrite current with last element

    a[n] = t;
    // overwrite last element with current
  }
}
```

reverse_array reverses the order of elements in an array of ints.

It iterates through half the array swapping the first and last elements, then second and second last, etc. until middle reached. Temp variable t stores element to swap. Loop runs n-- times to cover half array.

### TASK 5: 5-string_toupper.c

```c
char *string_toupper(char *n)
{
  int i; // initialize index

  i = 0;

  while (n[i] != '\0')
  {
    if (n[i] >= 'a' && n[i] <= 'z')  
      n[i] = n[i] - 32; 
      // if lowercase, subtract 32 to uppercase

    i++;
    // increment index
  }

  return (n);
  // return modified string
}
```

string_toupper changes lowercase chars in a string to uppercase.

It loops through each char in the string. If between 'a' and 'z' in ascii, it subtracts 32 to convert to uppercase. Then it returns pointer to the modified string.

### TASK 6: 6-cap_string.c

```c
char *cap_string(char *str)
{
  int index = 0; // initialize index

  while (str[index]) 
  {
    if (str[index - 1] == ' ' ||
        str[index - 1] == '\t' ||
        str[index - 1] == '\n' ||
        str[index - 1] == ',' ||
        str[index - 1] == ';' ||
        str[index - 1] == '.' ||
        str[index - 1] == '!' ||
        str[index - 1] == '?' ||
        str[index - 1] == '"' ||
        str[index - 1] == '(' ||
        str[index - 1] == ')' ||
        str[index - 1] == '{' ||
        str[index - 1] == '}' || 
        index == 0)
    {
      if (str[index] >= 'a' && str[index] <= 'z')
        str[index] -= 32; 
        // uppercase current char if previous separator
    }

    index++;
    // increment index
  }

  return (str);
  // return modified string
}
```

cap_string capitalizes first char of each word in a string.

It loops through each char, checking if previous char is a separator or beginning of string. If so and current char is lowercase, it uppercases it by subtracting 32. Then it returns the modified string.

### TASK 7: 7-leet.c

```c
char *leet(char *n)
{
  int i, j; // indexes
  char s1[] = "aAeEoOtTlL";
  char s2[] = "4433007711";

  for (i = 0; n[i] != '\0'; i++)
  {
    for (j = 0; j < 10; j++) 
    {
      if (n[i] == s1[j])
      {
        n[i] = s2[j];
        // replace char
      }
    }
  }

  return (n);
  // return modified string
}
```

leet encodes a string into "leet speak". Letters a,A,e,E,o,O,t,T,l,L are replaced by 4,3,0,7,1 respectively.

It loops through each char in string n. For each char, it loops through s1 and s2 arrays searching for a match. If found, the char is replaced by the leet equivalent. This continues until end of string is reached.

### TASK 8: 100-rot13.c

```c
char *rot13(char *s)
{
  int i; // index for s
  int j; // index for alphabet

  char data1[] = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz";
  char datarot[] = "NOPQRSTUVWXYZABCDEFGHIJKLMnopqrstuvwxyzabcdefghijklm";

  for (i = 0; s[i] != '\0'; i++)
  {
    for (j = 0; j < 52; j++)
    {
      if (s[i] == data1[j]) 
      {
        s[i] = datarot[j];
        // replace char with ROT13 equivalent
      }
    }
  }

  return (s);
} 
```

rot13 performs the ROT13 cipher on a string. Each letter is rotated 13 places in the alphabet.

It loops through each char in string s. For each char, it loops through data1 and datarot mapping equivalent ROT13 chars. If a match, s[i] is replaced. This continues until end of string is reached.


### TASK 9: 101-print_number.c

```c
void print_number(int n)
{
  unsigned int n1; // absolute value of n
  
  if (n < 0) 
  {
    _putchar('-');
    // print minus if negative

    n1 = -n;
    // take absolute value
  }
  else
  {  
    n1 = n;
  }

  if (n1 / 10 != 0)
  {
    print_number(n1 / 10);
    // recursive call for next left digit
  }
  
  _putchar((n1 % 10) + '0');
  // print last digit
}
```

print_number prints an integer. It recursively prints each digit starting with the leftmost.

It handles negative numbers by printing a - and passing positive value to recursive call. Base case is n1<10 so it prints the last digit. Recursive case divides by 10 and passes quotient to new call to print next left digit.

### TASK 10: 102-magic.c

```c
  /*
   * write your line of code here...
   */
  *(p + 5) = 98;
```

This line sets the value at index p+5 to 98. p is a pointer to integer n. By offsetting 5 int positions (5 * sizeof(int) bytes), it reaches array a and sets the 6th element to 98.

### TASK 11: 103-infinite_add.c

```c  
char *infinite_add(char *n1, char *n2, char *r, int size_r)
{
  int i = 0, j = 0, k = 0, l = 0, m = 0, n = 0;

  while (n1[i] != '\0')
    i++; 
  // find length of n1

  while (n2[j] != '\0')
    j++;
  // find length of n2

  if (i + 2 > size_r || j + 2 > size_r)
    return (0);
  // validate size of r

  r[k] = '0'; 
  // initialize result string

  for (; k < size_r - 1; k++)
  {
    if (i >= 0)  
      m = n1[i--] - '0';
    // get digit from n1

    if (j >=0)
      n = n2[j--] - '0';
    // get digit from n2

    r[k] = (m + n + l) % 10 + '0'; 
    // sum with carry

    l = (m + n + l) / 10;
    // update carry
  }

  if (l == 1)
    r[k++] = '1'; 
  // handle last carry

  r[k] = '\0';
  // null terminate result

  return (r);
}
```

infinite_add adds two numbers stored in strings n1 and n2, saving result in r.

It initializes index variables to iterate through n1, n2, r. Checks size of r is big enough. Initializes r to '0'. 

Loops through r size - 1, tracking carries in l. Gets each char from n1,n2 as ints m,n. Sums m+n+l and modulo 10 is right digit. Carry is sum/10. Stores right digit in r.

After loop, if last carry, store '1' in next r index. Null terminate r. Return pointer to r.

### TASK 12: 104-print_buffer.c

```c
void print_buffer(char *b, int size)
{
  int i, j, k; // loop indexes

  for (i = 0; i < size; i += 10)
  {
    printf("%08x: ", i); 
    // print offset

    for (j = i; j < i + 10; j++)
    {
      if (j % 2 == 0)
        printf(" ");
      // space between hex chars

      if (j < size)
        printf("%02x", b[j]); 
      // print hex char

      else
        printf("  ");
    }

    printf(" ");

    for (k = i; k < i + 10; k++) 
    {
      if (k >= size)
        break;
      
      if (b[k] < 32 || b[k] > 126)
        printf("%c", '.');
      // nonprintable as .

      else
        printf("%c", b[k]);
      // print ascii char
    }

    printf("\n");
  }
}
```

print_buffer prints a buffer 10 bytes per line in hex and ascii.

Outer loop iterates buffer in chunks of 10 bytes by incrementing i. Inner loop prints hex value of each byte followed by a space. Second inner loop prints ascii char or '.' if non-printable. Null byte included in size terminates.

## Additional info

This project covers core memory manipulation concepts in C. Pointers provide direct access to read/write data. Arrays are blocks of contiguous memory to store collections of data. Strings are arrays of chars terminated by a null byte. These building blocks allow creating complex data structures and algorithms to solve problems in C. The tasks demonstrate basic usage that serve as the foundation for higher level programming.
