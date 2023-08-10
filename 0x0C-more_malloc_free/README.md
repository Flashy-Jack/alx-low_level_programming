# PROJECT: 0x0C. C - More_malloc_free  

## Project By: Jordan Crossley

## Course: ALX SOFTWARE ENGINEERING

![image](https://media.geeksforgeeks.org/wp-content/cdn-uploads/Malloc-function-in-c.png)

![image](https://media.geeksforgeeks.org/wp-content/cdn-uploads/Free-function-in-c.png)

![image](https://media.geeksforgeeks.org/wp-content/cdn-uploads/realloc-function-in-c.png)

![image](https://media.geeksforgeeks.org/wp-content/cdn-uploads/calloc-function-in-c.png)

## Overview

Dynamic memory allocation in C allows manually allocating and freeing blocks of memory at runtime. This provides more control over memory usage compared to static allocation. 

The `malloc` function is used to allocate a block of memory dynamically. It takes a size as parameter and returns a pointer to the allocated block. This memory can be accessed via the returned pointer.

The `free` function is used to de-allocate a block of memory that was previously allocated with `malloc`. It takes the pointer to the block as parameter, freeing up that memory. 

Using `malloc` and `free` allows allocating memory as needed and freeing it when no longer required. This approach helps optimize memory usage as compared to static allocation which allocates fixed blocks upfront.

The manual allocation also puts the responsibility on the programmer to track allocated blocks and correctly free them after use. Failing to free memory causes memory leaks.

So in summary, `malloc` and `free` give fine-grained control over dynamic memory allocation and de-allocation in C programs.

### Resources

Read or watch:

- Do I cast the result of malloc? https://stackoverflow.com/questions/605845/do-i-cast-the-result-of-malloc

### man or help:

`malloc`

`free`

`exit (3)`

`calloc`

`realloc`

## 0-malloc_checked.c

```c
void *malloc_checked(unsigned int b)
{
  void *ptr;

  ptr = malloc(b); // Call malloc to allocate memory

  if (ptr == NULL) // Check if malloc failed
    exit(98);      // If failed, exit with error

  return (ptr);    // Return the pointer
}
```

This implements `malloc_checked()` which checks the return value from `malloc()` before using the allocated memory.

- `malloc(b)` allocates `b` bytes and returns a pointer to the memory.

- We store the returned pointer in `ptr`.

- `if (ptr == NULL)` checks if the pointer is `NULL` which means `malloc` failed.

- If failed, we call `exit(98)` to exit the program with status 98.

- If `malloc` succeeded, we return the pointer `ptr` to the caller.

## 1-string_nconcat.c

```c
char *string_nconcat(char *s1, char *s2, unsigned int n)
{
  char *s;
  unsigned int len1 = 0, len2 = 0;

  while (s1 && s1[len1]) // Get length of s1
    len1++;

  while (s2 && s2[len2]) // Get length of s2 
    len2++;

  if (n < len2) // If n < len2, allocate len1 + n + 1 bytes
    s = malloc(len1 + n + 1);
  else // Else allocate len1 + len2 + 1 bytes
    s = malloc(len1 + len2 + 1);

  // Copy s1 
  int i = 0;
  while (i < len1) {
    s[i] = s1[i];
    i++; 
  }

  // Copy first n bytes of s2
  int j = 0;
  while (n < len2 && i < len1 + n) {
    s[i++] = s2[j++];
  }

  // Copy remaining bytes of s2
  while (n >= len2 && i < len1 + len2) {
    s[i++] = s2[j++];
  }

  s[i] = '\0'; // Add null terminator

  return s;
}
```

This dynamically allocates memory for concatenating two strings s1 and s2, copying up to n bytes of s2.

- `len1` and `len2` store lengths of the strings computed using `while` loops.

- `malloc` allocates memory for result string based on `n`, `len1` and `len2`.

- `s1` is copied byte-by-byte using a `while` loop. 

- Next, `n` bytes of `s2` are copied using another `while` loop. 

- If `n` > `len2`, the remaining bytes of `s2` are copied.

- A null terminator is added at the end.

- The pointer to the concatenated string is returned.

## 2-calloc.c

```c
void *_calloc(unsigned int nmemb, unsigned int size)
{
  char *ptr;

  ptr = malloc(size * nmemb); // Allocate memory for array

  if (ptr == NULL) // Check for malloc failure
    return NULL; 

  _memset(ptr, 0, nmemb * size); // Initialize array to 0

  return ptr;
}
```

This implements `_calloc()` to allocate and initialize array memory:

- `malloc(size * nmemb)` allocates a block for an array of `nmemb` elements, each of `size` bytes.

- Return `NULL` if `malloc` fails.

- `_memset(ptr, 0, nmemb * size)` sets the allocated memory to zero to initialize it. 

- Finally return the pointer to caller.

## 3-array_range.c

```c  
int *array_range(int min, int max)
{
  int *ptr;
  int size = max - min + 1;

  ptr = malloc(sizeof(int) * size); // Allocate array

  if (ptr == NULL) 
    return NULL;

  for (int i = 0; min <= max; i++) {
    ptr[i] = min++; // Populate array
  }

  return ptr;
}
```

This creates an array of integers between min and max:

- `size` calculates the number of elements needed.

- `malloc` allocates memory for an array of `size` elements.

- Return `NULL` if `malloc` fails. 

- The `for` loop fills the array with values from `min` to `max`.

- `min` is incremented each iteration to fill next element.

- Finally the pointer to the created array is returned.

## 100-realloc.c

```c
void *_realloc(void *ptr, unsigned int old_size, unsigned int new_size)
{
  char *ptr1;

  if (new_size == old_size)
    return ptr;

  if (new_size == 0 && ptr) {
    free(ptr);
    return NULL;
  }

  if (!ptr)
    return malloc(new_size);

  ptr1 = malloc(new_size); // Allocate new block

  if (!ptr1)
    return NULL;

  // Copy old data to new block
  if (new_size < old_size) {
    memcpy(ptr1, ptr, new_size); 
  } else {
    memcpy(ptr1, ptr, old_size);
  }

  free(ptr); // Free old block
  return ptr1;
}
```

This implements `_realloc()` to reallocate memory:

- If `new_size == old_size`, return same pointer.

- If `ptr` is `NULL`, equivalent to `malloc`.

- If `new_size` is 0, free pointer and return `NULL`.

- `malloc` new block and copy old data based on size.

- `memcpy` handles copying from old to new block.

- Free the old block once copied. 

- Return pointer to new block.

So it reallocates memory dynamically based on the new size requested.
