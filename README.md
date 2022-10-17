# Linked List Homework

Linked lists are useful for maintaining list that can be dynamically resized at runtime according to user input. They are used quite a bit by operating systems to keep track of system resources. For example, when you start a new program, the operating system creates a new data structure to track your program's execution state, memory usage, etc. This data structure is stored in a linked list. When your program finishes, the data structure is removed from the list.

## Overview

In this homework assignment, you are going to implement a linked list in C. This program will run in Linux (not in `qemu`), so you can use standard C library functions like `printf`, `malloc`, etc. Your program should provide functionality to add a new element to the list by calling `listAdd` function and remove an element from the list by calling `listRemove`. In your `main` function, you should call `listAdd` and `listRemove` several times, printing out the structure of the list after each call. Don't hard-code a series of `listAdd`s and `listRemove`s in your program. Instead, either (1) ask for user input to decide if a new element should be inserted or removed or (2) choose a random number and base the decision on its value.

## Detailed Instructions

To-do items for this homework:
1. Define a data structure to store linked list elements. Include linkage pointers (`next` and `prev`) and at least one payload.
2. Create a `head` pointer to point to the beginning of your list
3. Write a `listAdd` function that adds new elements to your list **in ascending order according to the value of the element's payload.**
4. Write a `listRemove` function that removes elements from your list
5. Call `listAdd` and `listRemove` from `main` to demonstrate that they work

### Defining the Data Structure

First, you're going to want to define a data structure for elements in your linked list. Do this in a header file. Your data structure should have `next` and `prev` pointers and some payload. For the payload, you can create a single integer.

    struct linkedListElement {
        struct linkedListElement *next; // Ptr to next element in list
        // More elements here...
    };

This `struct` definition doesn't actually create any variables, it just tells the compiler what the structure of each linked list element should be.

Each element in the linked list contains a pointer to the next element in the list. This is just the address in memory of the next element. You may also want to add a pointer to the previous element in the list, which makes it easier to remove elements from the list.

### Creating Objects from your Data Structure

In your `main` function, you can create new `linkedListElement` objects by calling `malloc`:

    struct linkedListElement *newElement = malloc(sizeof(struct linkedListElement);

This allocates a block of memory that is large enough to fit your data structure and puts the address of the memory block into `newElement`.

### Creating a List Head

The beginning of a linked list is defined by a list head pointer. This is usually a global variable that points to the first element of the list. The first element then points to the second, the second to the third, and so on:

    struct linkedListElement *listHead = NULL;

We initialize this pointer to NULL, which indicates to our program that there are no elements in the list. 

### Adding New Elements to the List

Write a function called `listAdd` that adds a new element to the list. The function prototype is below:

    void listAdd(struct linkedListElement *newListElement);

This function takes a pointer to the new list element. When you call `listAdd`, the argument `newListElement` should point to a block of memory that has been allocated with `malloc`.


### Removing an Element from the List

Write a function called `listRemove` that removes an element from the list:

    void listRemove(struct linkedListElement *element);


The argument to this function is an element that should be removed from the list. `listRemove` should unlink it from the list, connecting the element before `element` to the element after it.

## Grading

| Task                                                                   | Points |
|------------------------------------------------------------------------|--------|
| Working Makefile                                                       | 5      |
| Data structure defined correctly                                       | 3      |
| List head defined correctly                                            | 2      |
| `listAdd` function works                                               | 10     |
| `listAdd` adds elements in order according to the value of the payload | 10     |
| `listRemove` function works                                            | 15     |
| Demo `listAdd` and `listRemove` by calling them from `main`            | 5      |

