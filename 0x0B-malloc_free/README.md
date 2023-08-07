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
- Returns NULL if size is 0

**Pseudo Code:**

```c
char* create_array(unsigned int size, char c) {
  // Allocate memory 
  char* array = malloc(size * sizeof(char)); 
  
  // Initialize array
  for(int i = 0; i < size; i++) {
    array[i] = c;
  }

  return array;
}
```

### 1. The woman who has no imagination has no wings

Write a function `_strdup` that returns a pointer to a newly allocated space in memory containing a copy of a given string.

**Summary:**

- Allocates memory for duplicate of string
- Copies string to new memory space
- Returns NULL if string is NULL

**Pseudo Code:**

```c  
char*_strdup(char* str) {

  // Allocate memory
  char* dup = malloc(strlen(str) + 1);

  // Copy string 
  strcpy(dup, str);

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

**Pseudo Code:**

```c
char* str_concat(char* s1, char* s2) {

  // Handle NULLs
  if (s1 == NULL) {
    s1 = "";
  }
  if (s2 == NULL) {
    s2 = "";
  }
  
  // Allocate memory
  int len = strlen(s1) + strlen(s2);
  char* concat = malloc(len + 1);

  // Concatenate strings
  strcpy(concat, s1);
  strcat(concat, s2);

  // Add null terminator
  concat[len] = '\0';

  return concat;
}
```

### 3. If you even dream of beating me you'd better wake up and apologize

Write a function `alloc_grid` that returns a pointer to a 2D array of integers.

**Summary:** 

- Dynamically allocates memory for 2D array
- Sets each element to 0  
- Handles invalid inputs

**Pseudo Code:**

```c
int** alloc_grid(int width, int height) {

  // Handle invalid inputs
  if (width <= 0 || height <= 0) {
    return NULL;
  }

  // Allocate memory 
  int** grid = malloc(height * sizeof(int*));
  for (int i = 0; i < height; i++) {
    grid[i] = malloc(width * sizeof(int)); 
  }

  // Initialize to 0
  for (int i = 0; i < height; i++) {
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

**Pseudo Code:**

```c
void free_grid(int** grid, int height) {

  // Free each row
  for (int i = 0; i < height; i++) {
    free(grid[i]);
  }

  // Free grid pointer
  free(grid);
}
```

### 5. It isn't the mountains ahead to climb that wear you out; it's the pebble in your shoe 

Write a function `argstostr` that concatenates all arguments of a program into a string.

**Summary:**

- Concatenates program arguments with newlines 
- Handles NULL arguments
- Allocates memory for concatenated string

**Pseudo Code:**

```c
char* argstostr(int ac, char** av) {

  // Handle NULL args
  if (ac == 0 || av == NULL) {
    return NULL;
  }

  // Calculate total length
  int len = 0;
  for (int i = 0; i < ac; i++) {
    len += strlen(av[i]) + 1; // +1 for newline
  }

  // Allocate memory
  char* str = malloc(len + 1); // +1 for null term

  // Concatenate arguments
  int idx = 0;
  for (int i = 0; i < ac; i++) {
    strcpy(str + idx, av[i]); 
    idx += strlen(av[i]);
    str[idx++] = '\n';
  }

  return str;
}
```

### 6. I will show you how great I am

Write a function `strtow` that splits a string into words.

**Summary:**

- Splits string into array of words  
- Allocates memory for array and each word
- Handles empty string
- Adds null terminator after each word

**Pseudo Code:**

```c
char** strtow(char* str) {

  // Handle empty string
  if (str == NULL || str[0] == '\0') {
    return NULL; 
  }

  // Allocate memory for array of words
  char** words = malloc(num_words * sizeof(char*));

  // Extract and allocate each word
  int idx = 0;
  int start = 0;
  for (int i = 0; str[i]; i++) {
    if (str[i] == ' ') {
      int word_len = i - start;
      words[idx] = malloc(word_len + 1);
      strncpy(words[idx++], str + start, word_len);
      words[idx][word_len] = '\0';
      start = i + 1; 
    }
  }

  // Null terminate array
  words[idx] = NULL;

  return words;
}
```

