# PROJECT: 0x0E. C - Structures, typedef

## Project By: Jordan Crossley  

## Course: ALX SOFTWARE ENGINEERING

## Overview

![image](https://media.geeksforgeeks.org/wp-content/cdn-uploads/Structure-In-C.png)
![image](https://fastbitlab.com/wp-content/uploads/2022/12/Figure-1-15-1024x530.png)

This project covers structures and typedefs in C programming. Structures allow grouping related data into a single composite type. This allows encapsulating different pieces of data into an organized structure. For example, a `struct dog` can store a dog's name, age, and owner together. Typedefs allow creating alias names for existing types. This is useful for giving cleaner names to struct types like `dog_t` for `struct dog`. 

Key topics include:

- Declaring and defining structures with different member types
- Initializing struct variables and accessing members 
- Learning dot syntax for accessing members of a struct
- Typedef'ing a struct to create a new named type
- Dynamically allocating memory for new struct instances
- Properly handling null pointers and failures
- Freeing memory allocated for structs when no longer needed

This project provides hands-on experience working with these important concepts in C. The tasks cover declaring, accessing, allocating, and freeing structures to master these essential skills.

### Resources

- [0x0d. Structures.pdf](https://intranet.alxswe.com/rltoken/giS4eNQT2BQ9RLK0PMhgJQ) 
- [Struct (C programming language)](https://intranet.alxswe.com/rltoken/MinJEDOHpeZs31qaXU8v1w)
- [Documentation: structures](https://github.com/alx-tools/Betty/wiki/Documentation:-Data-structures)
- [0x0d. Typedef and structures.pdf](https://s3.amazonaws.com/alx-intranet.hbtn.io/uploads/misc/2021/1/c8ff3e6f7202be7fa489a584e41d005504a07c23.pdf?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIARDDGGGOUSBVO6H7D%2F20230814%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20230814T172231Z&X-Amz-Expires=86400&X-Amz-SignedHeaders=host&X-Amz-Signature=e90607529b290c548bb4b5107c6321c29e1356cab46f2d5013b0053c5a3aaba9)
- [Typedef](https://publications.gbdirect.co.uk//c_book/chapter8/typedef.html)
- [Programming in C by Stephen Kochan - Chapter 8, Working with Structures p163-189](https://lshoshia.science.tsu.ge/C/Stephen%20G%20Kochan%20Programming%20in%20C%20%202005.pdf) 
- [The Lost Art of C Structure Packing (Advanced - not mandatory)](http://www.catb.org/esr/structure-packing/)

### Tasks, Answers and Explanations

**Question #0, File: dog.h**

```c
/* Declares a struct 'dog' with required members */
struct dog {
  char *name; 
  float age;
  char *owner;
};
```
- Declares struct dog with required members

**Question #1, File: 1-init_dog.c**

```c
/* Handles NULL pointer and initializes members from parameters */
void init_dog(struct dog *d, char *name, float age, char *owner) 
{
  /* Check for NULL and malloc if needed */
  if (d == NULL)
    d = malloc(sizeof(struct dog));

  /* Use dot syntax to access members */
  d->name = name;
  d->age = age;
  d->owner = owner;
}
```
- Handles NULL pointer 
- Uses dot syntax to access members
- Initializes members from parameters

**Question #2, File: 2-print_dog.c**

```c
/* Checks for NULL, prints placeholders, and prints members properly */  
void print_dog(struct dog *d)
{
  /* Check for NULL dog */
  if (d == NULL)
    return;

  /* Print placeholder strings for NULL members */
  if (d->name == NULL)
    d->name = "(nil)";
  if (d->owner == NULL)
    d->owner = "(nil)";   

  /* Print each member with proper format specifier */
  printf("Name: %s\n", d->name);
  printf("Age: %f\n", d->age);
  printf("Owner: %s\n", d->owner);
}
```

- Checks for NULL dog and members
- Prints placeholders for NULL members  
- Prints members with proper format specifiers

**Question #3, File: dog.h**

```c
/* Typedefs struct dog as dog_t */
typedef struct dog dog_t;
```
- Typedefs struct dog as dog_t

**Question #4, File: 4-new_dog.c** 

```c  
/* Dynamically allocates memory, copies strings, handles errors */
dog_t *new_dog(char *name, float age, char *owner)
{
  dog_t *dog = malloc(sizeof(dog_t));
  if (dog == NULL)
    return NULL;

  dog->name = strcpy(dog->name, name);
  dog->owner = strcpy(dog->owner, owner);  
  dog->age = age;

  return dog;
}
```

- Dynamically allocates memory for struct
- Handles malloc failure 
- Copies name and owner strings
- Sets age member
- Returns new dog or NULL

**Question #5, File: 5-free_dog.c**

```c
/* Frees members and struct, handles NULL pointer */
void free_dog(dog_t *d) {
  if (d == NULL)
    return;
  
  free(d->name);
  free(d->owner);
  free(d);
}
``` 

- Handles NULL pointer
- Frees each member pointer
- Frees struct pointer


