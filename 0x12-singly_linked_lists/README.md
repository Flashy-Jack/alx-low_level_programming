# PROJECT: 0x12. C - Singly linked lists

## Authors: Jordan Crossley

## Course: ALX Software Engineering

## Overview

Singly linked lists are a fundamental data structure used extensively in software development. Unlike arrays which have static predetermined size, linked lists provide dynamic memory allocation allowing them to grow and shrink as needed. 

Linked lists consist of nodes where each node contains some data and a pointer to the next node in the list. The first node is called the head while the last node points to NULL to denote the end. This structure allows efficient insertion and removal of nodes by simply updating the pointers rather than shifting elements like arrays require.

![image](https://media.geeksforgeeks.org/wp-content/uploads/20220816144425/LLdrawio.png)

Some key advantages of linked lists:

- Dynamic size - No need to preallocate a fixed amount of memory, nodes can be added as needed
- Efficient insertion and deletion - Adding and removing nodes is O(1) by updating pointers rather than shifting elements
- Flexible memory allocation - Nodes can be scattered through memory and don't need contiguous blocks like arrays

The tradeoff is linked lists lack random access since nodes must be traversed sequentially rather than accessed directly by index like arrays.

This project covers core functions for working with singly linked lists in C:

- Printing the list 
- Getting number of nodes
- Adding nodes at the head or tail
- Freeing the entire list

Two visual examples of operations on a simple linked list:

**Adding node at head**

![image](https://www.alphacodingskills.com/imgfiles/linked-list-add-node-at-start.PNG)

**Removing node from middle** 

![image](https://www.w3resource.com/w3r_images/c-linked_list-exercise-20-image.png)

### Resources
- Linked Lists video: https://www.youtube.com/watch?v=udapt4FGY20&t=130s 
- Google for linked list info: https://www.google.com/#q=linked+lists
- YouTube for linked list videos: https://www.youtube.com/results?search_query=linked+lists

These resources explain the theory and usage of linked lists in programming. The video gives a visual overview, Google provides general info, and YouTube has coding tutorials.

### Concepts
- Data Structures

This project focuses specifically on linked lists as a fundamental data structure in computer science. Linked lists allow efficient insertion and removal of elements with dynamic memory allocation.

### man or help:

The man pages cover the standard C library functions allowed and used in this project like malloc, free, exit.

## Tasks answers and explanations

### 0-print_list.c

```C
#include <stdio.h> // Includes standard I/O library
#include "lists.h" // Includes header defining list_t struct

/**
 * print_list - prints all elements of a linked list
 * @h: pointer to the list_t list to print  
 *
 * Return: number of nodes printed
*/
size_t print_list(const list_t *h) 
{
  size_t s = 0; // Initialize counter to 0

  while (h) { // Loop until reaching NULL
    if (!h->str) 
      printf("[0] (nil)\n"); // If node string is NULL, print (nil)
    else
      printf("[%u] %s\n", h->len, h->str); // Else print string  
   
    h = h->next; // Move to next node
    s++; // Increment counter
  }

  return (s); // Return number of nodes printed
}
```

This function prints the entire linked list. It loops through each node while `h` is not NULL. It prints the string if it exists, or prints (nil) if the string is NULL. It returns the count of nodes.

### 1-list_len.c

```C
#include <stdlib.h> // Includes standard library
#include "lists.h" // Includes header defining list_t

/**
 * list_len - returns number of elements in linked list
 * @h: pointer to the list_t list
 *
 * Return: number of elements in h  
*/
size_t list_len(const list_t *h)
{
  size_t n = 0; // Initialize counter to 0

  while (h) { // Loop through list
    n++; // Increment counter
    h = h->next; // Move to next node
  }

  return (n); // Return final count
}
```

This function counts the number of nodes in the linked list. It initializes a counter `n` to 0, then loops through each node incrementing `n` at each one. It returns the final count.

### 2-add_node.c

```C  
#include <stdlib.h> // Standard library
#include <string.h> // String functions 
#include "lists.h" // List header

/**
 * add_node - adds new node at beginning of linked list
 * @head: double pointer to the list_t list
 * @str: new string to add in node
 *
 * Return: address of new element or NULL if fail  
*/
list_t *add_node(list_t **head, const char *str)  
{
  list_t *new;
  unsigned int len = 0;

  while (str[len]) // Get length of new string
    len++;
  
  new = malloc(sizeof(list_t)); // Allocate memory for new node
  if (!new) 
    return (NULL); // Return NULL if malloc fails

  new->str = strdup(str); // Copy new string
  new->len = len; // Set length
  new->next = (*head); // Link to old head
  (*head) = new; // Update head to new node

  return (*head); // Return pointer to new head
}
```

This function adds a new node at the beginning of the linked list. It allocates memory for the new node, copies the string value, sets the other fields, and links the new node's next pointer to the old head. It then updates the head to point to the new node.

### 3-add_node_end.c

```C
#include <stdlib.h> // Standard library
#include <string.h> // String functions
#include "lists.h" // List header  

/**
 * add_node_end - adds new node at end of linked list
 * @head: double pointer to the list_t list 
 * @str: string to put in new node
 *
 * Return: address of new element or NULL if fail
*/
list_t *add_node_end(list_t **head, const char *str) 
{
  list_t *new;
  list_t *temp = *head; // Temporary pointer to head
  unsigned int len = 0;

  while (str[len]) // Get length of new string
    len++;

  new = malloc(sizeof(list_t)); // Allocate memory for new node
  if (!new)
    return (NULL); // Return NULL if malloc fails

  new->str = strdup(str); // Copy new string
  new->len = len; 
  new->next = NULL; // Set next pointer to NULL

  if (*head == NULL) { // If empty list, new node is head
    *head = new;
    return (new);
  }

  while (temp->next) // Traverse to end of list
    temp = temp->next; 

  temp->next = new; // Link current tail to new node

  return (new); // Return pointer to new node
}
```

This function adds a new node at the end (tail) of the linked list. It allocates the new node, sets its values, and links it to the current tail node. If the list is empty, it sets head to the new node. Otherwise it traverses to the tail and updates its next pointer.

### 4-free_list.c

```C
#include <stdlib.h> // Standard library
#include "lists.h" // List header

/**
 * free_list - frees a linked list
 * @head: list_t list to be freed
*/
void free_list(list_t *head) 
{
  list_t *temp;

  while (head) { // Loop until head is NULL
    temp = head->next; // Store next node

    free(head->str); // Free current node string
    free(head); // Free current node
    
    head = temp; // Advance to next node
  }
}
```

This function frees the memory allocated for the linked list. It loops through each node, storing the next pointer, then frees the string value, frees the node, and moves to the next node until head is NULL.

## Additional info
- Singly linked lists provide dynamic memory allocation and efficient insertion/removal compared to arrays
- Nodes store data and a pointer connecting to the next node 
- Linked lists must be traversed sequentially rather than accessed randoml
