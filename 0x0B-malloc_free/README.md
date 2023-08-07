# PROJECT: 0x0B. C - malloc, free

## Project By: Jordan Crossley

## Course: ALX SOFTWARE ENGINEERING 

![image](https://techalmirah.com/wp-content/uploads/2021/09/dynamic-memory-allocation-in-c-1024x415.png)

## Overview

Dynamic memory allocation in C allows manually allocating and freeing blocks of memory at runtime. This provides more control over memory usage compared to static allocation. The malloc and free functions are used to allocate and free memory dynamically.

### Resources

Read or watch:

- [0x0a - malloc & free - quick overview.pdf](https://s3.amazonaws.com/alx-intranet.hbtn.io/uploads/misc/2021/1/a094c90e7f466bbeaa49cb24c8f04e7f27aaad41.pdf?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIARDDGGGOUSBVO6H7D%2F20230807%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20230807T135319Z&X-Amz-Expires=86400&X-Amz-SignedHeaders=host&X-Amz-Signature=7159c59c9267822a97ea48466d16f75a5567797f779cd5e3564416113f75e9b5).

- [Dynamic memory allocation in C - malloc calloc realloc "free (stop at 6:50)"](https://www.youtube.com/watch?v=xDVC3wKjS64).

### man or help:

`malloc`

`free`
 

## Tasks

### 0. Float like a butterfly, sting like a bee

Write a function `create_array` that creates an array of chars initialized with a specific char.

**Summary:**

- Allocates memory for array of given size
- Initializes array with specified char  
- Null terminates array
- Returns NULL if size is 0

**Corrected Pseudo Code:**

```c
char *create_array(unsigned int size, char c) {
  
  // Allocate memory
  char *array = malloc(size * sizeof(char));
  if (array == NULL)
    return NULL;
    
  // Initialize array  
  for (unsigned int i = 0; i < size; i++) {
    array[i] = c;
  }
  
  // Null terminate
  array[size] = '\0';

  return array;
}
```

### 1. The woman who has no imagination has no wings

Write a function `_strdup` that returns a pointer to a newly allocated space in memory containing a copy of a given string.

**Summary:**

- Allocates memory for duplicate of string  
- Copies string to new memory space
- Returns NULL if string is NULL

**Corrected Pseudo Code:**

```c
char *_strdup(char *str) {
  
  // Check string is not NULL
  if (str == NULL)
    return NULL;
    
  // Allocate memory
  unsigned int len = 0;
  while (str[len])
    len++;
  char *dup = malloc(len + 1);
  
  // Copy string
  unsigned int i;
  for (i = 0; str[i]; i++) {
    dup[i] = str[i];
  }
  dup[i] = '\0';

  return dup;
}
```

### 2. He who is not courageous enough to take risks will accomplish nothing in life

Write a function `str_concat` that concatenates two strings.

**Summary:**

- Allocates memory for concatenated string
- Copies strings into new space  
- Adds null terminator
- Handles NULL strings

**Corrected Pseudo Code:**

```c
char *str_concat(char *s1, char *s2) {

  unsigned int len1 = 0, len2 = 0;
  char *concat;

  // Check strings are not NULL
  if (s1 == NULL) 
    s1 = "";
  if (s2 == NULL)
    s2 = "";

  // Get lengths
  while (s1[len1])
    len1++;
  while (s2[len2])
    len2++;
  
  // Allocate memory
  concat = malloc(len1 + len2 + 1);
  if (concat == NULL)
    return NULL;

  // Copy s1
  unsigned int i;
  for (i = 0; i < len1; i++)
    concat[i] = s1[i];

  // Copy s2
  for (i = 0; i < len2; i++)
    concat[len1 + i] = s2[i];

  // Null terminate
  concat[len1 + len2] = '\0';

  return concat;
}
```

### 3. If you even dream of beating me you'd better wake up and apologize

Write a function `alloc_grid` that returns a pointer to a 2D array of integers.

**Summary:**

- Dynamically allocates memory for 2D array
- Sets each element to 0
- Handles invalid inputs 

**Corrected Pseudo Code:** 

```c  
int **alloc_grid(int width, int height) {

  int **grid;
  int i;

  if (width <= 0 || height <= 0)
    return NULL;

  // Allocate grid
  grid = malloc(sizeof(int *) * height);
  if (grid == NULL)
    return NULL;

  // Allocate rows 
  for (i = 0; i < height; i++) {
    grid[i] = malloc(sizeof(int) * width);
    if (grid[i] == NULL) {
      free_grid(grid, i);
      return NULL;
    }
  }

  // Initialize to 0
  for (i = 0; i < height; i++) {
    for (int j = 0; j < width; j++) {
      grid[i][j] = 0;
    }
  }

  return grid;
}
```

### 4. It's not bragging if you can back it up

Write a function `free_grid` to free a 2D grid previously created by `alloc_grid`.

**Summary:** 

- Frees memory allocated for each row
- Frees main grid pointer
- Handles NULL grid

**Corrected Pseudo Code:**

```c
void free_grid(int **grid, int height) {

  if (grid == NULL || height <= 0)
    return;

  for (int i = 0; i < height; i++) 
    free(grid[i]);

  free(grid);
}
```

### 5. It isn't the mountains ahead to climb that wear you out; it's the pebble in your shoe

Write a function `argstostr` that concatenates all arguments of a program into a string.

**Summary:**

- Concatenates program arguments with newlines
- Handles NULL arguments 
- Allocates memory for concatenated string

**Corrected Pseudo Code:**

```c
char *argstostr(int ac, char **av) {

  char *str;
  int i, j, idx, size = 0;

  if (ac == 0 || av == NULL)
    return NULL;

  // Calculate total size
  for (i = 0; i < ac; i++) {
    for (j = 0; av[i][j]; j++)
      size++;
    size++; // newline
  }

  // Allocate memory
  str = malloc(size + 1);
  if (str == NULL)
    return NULL;

  // Concatenate arguments and newlines
  idx = 0;
  for (i = 0; i < ac; i++) {
    for (j = 0; av[i][j]; j++) {
      str[idx] = av[i][j];
      idx++;
    }
    str[idx] = '\n';
    idx++;
  }
  str[idx] = '\0';

  return str;
}
```

### 6. I will show you how great I am 

Write a function `strtow` that splits a string into words.

**Summary:**

- Splits string into array of words
- Allocates memory for array and each word  
- Adds null terminator to each word
- Handles empty string

**Corrected Pseudo Code:**

```c
char **strtow(char *str) {
  
  char **words;
  int i, j, word_cnt;

  if (str == NULL || str[0] == '\0')
    return NULL;

  // Count words
  word_cnt = 0;
  for (i = 0; str[i]; i++)
    if (str[i] == ' ' && (str[i + 1] != ' ' && str[i + 1] != '\0'))
      word_cnt++;

  // Allocate memory for words array
  words = malloc((word_cnt + 1) * sizeof(char *));
  if (words == NULL)
    return NULL;

  j = 0;
  while (*str) {

    // Extract word if found
    if (*str != ' ') {
      char *word = malloc(i + 1); 
      int idx = 0;

      while (*str != ' ' && *str != '\0') {
        word[idx] = *str;
        idx++;
        str++;  
      }
      word[idx] = '\0';

      // Add to array
      words[j++] = word;
    }
    str++;
  }  
  words[j] = NULL;

  return words;
}
```

