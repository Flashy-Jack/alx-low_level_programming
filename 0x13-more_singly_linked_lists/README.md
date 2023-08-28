# Project: 0x13. C - More singly linked lists

## Project By: Jordan Crossley

## Course: ALX Low Level Programming

## Overview

### Visual Example of a Singly Linked List

![image](https://media.geeksforgeeks.org/wp-content/uploads/singly-linkedlist.png)

### Visual Example of Inserting a Node at the beginning of a linked list

![image](https://www.log2base2.com/images/ds/linked-list-add-front-10.png)

### Visual Example of Inserting a Node at the end of a linked list

![image](https://www.log2base2.com/images/ds/linked-list-add-back-20.png)

This project covers how to use singly linked lists in C. Singly linked lists contain nodes that store data and a pointer to the next node in the list. This allows efficient insertion and removal of elements.

The key functions implemented in this project include:

- **Printing** the entire linked list 
- **Getting length** of the linked list
- **Adding nodes** at the beginning or end
- **Freeing** the entire linked list
- **Popping** nodes from the head
- **Getting nodes** at a certain index  
- **Summing** data across all nodes
- **Inserting** nodes at an index
- **Deleting** nodes at an index
- **Reversing** the order of the linked list
- **Printing safely** with potential loops
- **Freeing safely** with potential loops

### Sample Code Snippets 

**Printing a Linked List**

```c
size_t print_listint(const listint_t *h) {
  size_t num = 0;

  while (h) {
    // Print current node's data
    printf("%d\n", h->n); 
    num++; // Increment count
    
    // Advance to next node
    h = h->next;
  }

  return (num);
}
```

This loops through the list printing each node's data and counting the number of nodes.

**Inserting a Node at End**

```c
listint_t *add_nodeint_end(listint_t **head, const int n) {

  // Allocate and set new node
  listint_t *new = malloc(sizeof(listint_t));
  new->n = n;
  new->next = NULL;

  // If empty list, set as head
  if (*head == NULL) {
    *head = new;
    return new;
  }

  // Find last node
  listint_t *temp = *head;
  while (temp->next) {
    temp = temp->next;
  }

  // Insert new node after last
  temp->next = new;
  
  return new;
}
```

This first allocates the new node and sets its data. It checks if empty list to insert as head. Otherwise it traverses to the last node and inserts new after.

**Reversing a Linked List**

```c
listint_t *reverse_listint(listint_t **head) {
  
  listint_t *prev = NULL;
  listint_t *next = NULL;

  while (*head) {
    // Store next node
    next = (*head)->next;
    
    // Reverse current node's pointer
    (*head)->next = prev;
    
    // Advance prev and head pointers    
    prev = *head;
    *head = next;
  }

  // Update head to final node
  *head = prev;
  return *head;
}
```

This uses prev and next pointers to reverse the pointers of each node while traversing. It updates head to point to the final node.

The other files contain similar detailed explanations of how each linked list function operates on the nodes.

## Tasks Answers and Explanations

### 0-print_listint.c

```c
#include "lists.h"

/**
 * print_listint - prints all the elements of a linked list
 * @h: linked list of type listint_t to print
 *
 * Return: number of nodes
 */
size_t print_listint(const listint_t *h)
{
	size_t num = 0;

	while (h) 
	{
		printf("%d\n", h->n);
		num++;
		h = h->next; 
	}

	return (num);
}
```

This function prints all elements in a linked list. It takes a constant pointer to the head node as input. It loops through each node printing the integer data. It also counts the number of nodes and returns that value.

### 1-listint_len.c

```c  
#include "lists.h"

/**
 * listint_len - returns the number of elements in a linked lists
 * @h: linked list of type listint_t to traverse
 *
 * Return: number of nodes
 */
size_t listint_len(const listint_t *h)
{
	size_t num = 0;

	while (h)
	{
		num++;
		h = h->next;
	}

	return (num);
}
```

This function counts the number of nodes in a linked list. It takes a constant pointer to the head node as input. It loops through the list incrementing the count each iteration. It returns the total number of nodes.

### 2-add_nodeint.c

```c
#include "lists.h"

/**
 * add_nodeint - adds a new node at the beginning of a linked list
 * @head: pointer to the first node in the list
 * @n: data to insert in that new node
 *
 * Return: pointer to the new node, or NULL if it fails
*/
listint_t *add_nodeint(listint_t **head, const int n)
{
	listint_t *new;

	new = malloc(sizeof(listint_t));
	if (!new)
		return (NULL);

	new->n = n;
	new->next = *head;  
	*head = new;

	return (new);
}
```

This function inserts a new node at the beginning of a linked list. It takes a double pointer to the head node and integer data. It dynamically allocates memory for the new node and sets its data value. It links the new node's next pointer to the current head node. It updates the head pointer to point to the new node. It returns a pointer to the inserted node.

### 3-add_nodeint_end.c

```c
#include "lists.h"

/**
 * add_nodeint_end - adds a node at the end of a linked list
 * @head: pointer to the first element in the list
 * @n: data to insert in the new element  
 *
 * Return: pointer to the new node, or NULL if it fails
*/
listint_t *add_nodeint_end(listint_t **head, const int n)
{
	listint_t *new;
	listint_t *temp = *head;

	new = malloc(sizeof(listint_t));
	if (!new)
		return (NULL);

	new->n = n;
	new->next = NULL;

	if (*head == NULL) {
		*head = new;
		return (new);
	}

	while (temp->next)
		temp = temp->next;

	temp->next = new;

	return (new);
}
```

This function inserts a new node at the end of a linked list. It takes a double pointer to the head node and data. It allocates memory for the new node and sets its data value and next pointer. It checks if the list is empty and sets the new node as the head if so. Otherwise, it traverses to the last node and links the new node to it. It returns a pointer to the inserted node.

### 4-free_listint.c

```c
#include "lists.h"

/**
 * free_listint - frees a linked list
 * @head: listint_t list to be freed
*/
void free_listint(listint_t *head)
{
	listint_t *temp;

	while (head)
	{
		temp = head->next;
		free(head);
		head = temp;
	}
}
```

This function frees an entire linked list. It takes the head node as input. It loops through the list, storing the next node in temp each iteration. It frees the current node then advances head to the next node in temp. This continues until the end, freeing the whole list.

### 5-free_listint2.c

```c
#include "lists.h"

/**
 * free_listint2 - frees a linked list
 * @head: pointer to the listint_t list to be freed
*/
void free_listint2(listint_t **head)  
{
	listint_t *temp;

	if (head == NULL)
		return;

	while (*head)
	{
		temp = (*head)->next;
		free(*head);
		*head = temp;
	}

	*head = NULL;
}
```

This function frees a linked list similar to the previous task. The difference is it takes a double pointer to the head node as parameter. It loops through the list freeing each node. Then it sets the head pointer itself to NULL after freeing the whole list.

### 6-pop_listint.c

```c  
#include "lists.h"

/**
 * pop_listint - deletes the head node of a linked list
 * @head: pointer to the first element in the linked list
 *
 * Return: the data inside the elements that was deleted, 
 * or 0 if the list is empty
*/
int pop_listint(listint_t **head)
{
	listint_t *temp;
	int num;

	if (!head || !*head)
		return (0);

	num = (*head)->n;
	temp = (*head)->next;
	free(*head);
	*head = temp;

	return (num);
}
```

This function deletes the head node in a linked list. It takes a double pointer to the head node. It stores the head node's data value. It points temp to the next node, frees the head, then updates the head pointer to temp (the next node). It returns the value of the removed node.

### 7-get_nodeint.c

```c
#include "lists.h"

/**
 * get_nodeint_at_index - returns the node at a certain index in a linked list
 * @head: first node in the linked list
 * @index: index of the node to return 
 *
 * Return: pointer to the node we're looking for, or NULL
*/
listint_t *get_nodeint_at_index(listint_t *head, unsigned int index) 
{
	unsigned int i = 0;
	listint_t *temp = head;

	while (temp && i < index)
	{
		temp = temp->next;
		i++;
	}

	return (temp ? temp : NULL);
}
```

This function locates and returns a node at a specific index in a linked list. It takes the head node and index as parameters. It initializes a counter variable and temp pointer to traverse the list. It loops through the list incrementing i until it reaches the given index. It returns temp which will be pointing to the node at that index, or NULL if not found.

### 8-sum_listint.c

```c
#include "lists.h"

/**
 * sum_listint - calculates the sum of all the data in a listint_t list
 * @head: first node in the linked list
 *
 * Return: resulting sum
*/ 
int sum_listint(listint_t *head)
{
	int sum = 0;
	listint_t *temp = head;

	while (temp)
	{
		sum += temp->n;
		temp = temp->next;
	}

	return (sum);
}
```

This function calculates the sum of all node data in a linked list. It takes the head node as input. It initializes a sum variable and temp pointer to traverse. It loops through adding each node's data to the sum. It returns the final sum value after reaching the end.

### 10-delete_nodeint.c

```c
#include "lists.h"

/**
 * delete_nodeint_at_index - deletes a node in a linked list at a certain index
 * @head: pointer to the first element in the list
 * @index: index of the node to delete
 *
 * Return: 1 (Success), or -1 (Fail)
*/
int delete_nodeint_at_index(listint_t **head, unsigned int index)
{
	listint_t *temp = *head;
	listint_t *current = NULL;
	unsigned int i = 0;

	if (*head == NULL)
		return (-1);
	
	if (index == 0) {
		*head = (*head)->next;
		free(temp);
		return (1);
	}

	while (i < index - 1) {
		if (!temp || !(temp->next))
			return (-1);
			
		temp = temp->next;
		i++;
	}


	current = temp->next;
	temp->next = current->next;
	free(current);

	return (1);
}
```

This function deletes a node at a specified index in a linked list. It takes a double pointer to the head node and index. It handles deleting the head node if index is 0. Otherwise, it traverses to the node before the target index. It stores the next node (to delete) in current. It updates the previous node's next pointer to skip over current. Then it frees current to delete it. It returns 1 for success or -1 if invalid.

### 100-reverse_listint.c

```c
#include "lists.h"

/**
 * reverse_listint - reverses a linked list
 * @head: pointer to the first node in the list
 *
 * Return: pointer to the first node in the new list
*/
listint_t *reverse_listint(listint_t **head)
{
	listint_t *prev = NULL;
	listint_t *next = NULL;

	while (*head)
	{
		next = (*head)->next;
		(*head)->next = prev;
		prev = *head;
		*head = next;
	}

	*head = prev;

	return (*head);
}
```

This function reverses the order of nodes in a linked list. It takes a double pointer to the head node. It initializes prev and next pointers. In the loop, it sets next to the head's next node, points the head's next to prev, sets prev to head, and advances head to next. This reverses the links. It sets the original head pointer to the last node prev. It returns the new head.

### 101-print_listint_safe.c

```c 
#include "lists.h"
/**
 * print_listint_safe - function that prints a linked list with a loop safely.
 * @head: pointer to the 1st node of the linked list
 * Return: new_node
*/
size_t print_listint_safe(const listint_t *head)
{
	const listint_t *tmp_n = NULL;
	const listint_t *l_n = NULL;
	size_t counter = 0;
	size_t new_n;

	tmp_n = head;
	while (tmp_n) {
		printf("[%p] %d\n", (void *)tmp_n, tmp_n->n);
		counter++;
		tmp_n = tmp_n->next;
		l_n = head;
		new_n = 0;
		while (new_n < counter) {
			if (tmp_n == l_n) {
				printf("-> [%p] %d\n", (void *)tmp_n, tmp_n->n);
				return (counter);
			}
			l_n = l_n->next;
			new_n++;
		}
		if (!head)
			exit(98);
	}
	return (counter);
}
```

This function safely prints a linked list that contains loops. It takes the head node as input. It uses two pointers, tmp_n traverses the list while l_n starts from the beginning each iteration. It checks if tmp_n equals l_n at any point, which means a loop. If so, it prints the node and returns the count. If not, it prints the whole list. It also checks for empty lists.

### 102-free_listint_safe.c

```c
#include "lists.h"

/**
 * free_listint_safe - frees a linked list
 * @h: pointer to the first node in the linked list
 *
 * Return: number of elements in the freed list
*/
size_t free_listint_safe(listint_t **h)
{
	size_t len = 0;
	int diff;
	listint_t *temp;

	if (!h || !*h)
		return (0);

	while (*h)
	{
		diff = *h - (*h)->next;
		if (diff > 0)
		{
			temp = (*h)->next;
			free(*h);
			*h = temp;
			len++;
		}
		else
		{
			free(*h);
			*h = NULL;
			len++;
			break;
		}
	}

	*h = NULL;

	return (len); 
}
```

This function safely frees a potentially circular linked list. It takes a double pointer to the head node. It calculates the difference between the head and next pointers. If greater than 0, it frees the node and advances. If 0, it means a loop so it frees the head, sets it to NULL and stops. It returns the count of freed nodes.

## Additional Info

The key concepts covered in this project include:

- Using linked lists data structures in C
- Dynamically allocating and freeing memory for nodes
- Inserting and deleting nodes in different positions
- Traversing linked lists iteratively
- Safely handling potential issues like loops and empty lists
- Understanding memory management and pointers
- Structuring code across header and source files
- Using helper functions and clean coding style
