# Linkedlist


### This chapter explains the basic terms related to data structure.

## Data Definition
### Data Definition defines a particular data with the following characteristics.

* #### Atomic − Definition should define a single concept.

* #### Traceable − Definition should be able to be mapped to some data element.

* #### Accurate − Definition should be unambiguous.

* #### Clear and Concise − Definition should be understandable.

## Data Object

### Data Object represents an object having a data.

## Data Type

### Data type is a way to classify various types of data such as integer, string, etc. which determines the values that can be used with the corresponding type of data, the type of operations that can be performed on the corresponding type of data. There are two data types −

* #### Built-in Data Type

* #### Derived Data Type

## Built-in Data Type

### Those data types for which a language has built-in support are known as Built-in Data types. For example, most of the languages provide the following built-in data types.

* #### Integers

* #### Boolean (true, false)

* #### Floating (Decimal numbers)

* #### Character and Strings

## Derived Data Type

### Those data types which are implementation independent as they can be implemented in one or the other way are known as derived data types. These data types are normally built by the combination of primary or built-in data types and associated operations on them. For example −

* #### List

* #### Array

* #### Stack

* #### Queue

## Basic Operations

### The data in the data structures are processed by certain operations. The particular data structure chosen largely depends on the frequency of the operation that needs to be performed on the data structure.

* #### Traversing

* #### Searching

* #### Insertion

* #### Deletion

* #### Sorting

* #### Merging

---

# Data Structure and Algorithms - Linked List

### A linked list is a sequence of data structures, which are connected together via links.

### Linked List is a sequence of links which contains items. Each link contains a connection to another link. Linked list is the second most-used data structure after array. Following are the important terms to understand the concept of Linked List.

* #### __Link__ − Each link of a linked list can store a data called an element.

* #### __Next__ − Each link of a linked list contains a link to the next link called Next.

* #### __LinkedList__ − A Linked List contains the connection link to the first link called First.

## Linked List Representation

### Linked list can be visualized as a chain of nodes, where every node points to the next node.

![nothing](./img/Linked_List.png)

### As per the above illustration, following are the important points to be considered.

* #### Linked List contains a link element called first.

* #### Each link carries a data field(s) and a link field called next.

* #### Each link is linked with its next link using its next link.

* #### Last link carries a link as null to mark the end of the list.

## Types of Linked List
### Following are the various types of linked list.

* #### __Simple Linked List__ − Item navigation is forward only.

* #### __Doubly Linked List__ − Items can be navigated forward and backward.

* #### __Circular Linked List__ − Last item contains link of the first element as next and the first element has a link to the last element as previous.