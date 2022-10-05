# Passing Functions as Props
---------
### 1. What does .map() return?

* ####  it is return a new array
-----------

### 2. If I want to loop through an array and display each value in JSX, how do I do that in React?

* ####  new addition to the set of operators, copying an array using map() or the regular for loop. we attach it to an array we've created and pass a callback function that'll be called each iteration.

----

### 3. Each list item needs a unique ____.

* #### Each list item needs a unique key. 
------

### 4. What is the purpose of a key?

* #### The keys in the map are arranged in a simple and straightforward manner. The keys tell the reaction of changes to the elements. The map object repeats entries, keys, and values in the order of the entry insertion.

---------

### 5. What is the spread operator?

* ####  spread operator: Takes in a recursive and adds elements to an array and expands it to individual elements.
-------

### 6. List 4 things that the spread operator can do.

* ####  Copy all or part of an existing array or object to an array or other object and spreading the array
---------
### 7. Give an example of using the spread operator to combine two arrays.

#### const firstWord = ['Hello', 'World'];
##### sicWord = ['python', 'JavaScript'];

#### const combine = [firstWord, sicWord];

#### output ['World', 'Hello', 'python', 'JavaScript']

-------
### 8. Give an example of using the spread operator to add a new item to an array.

#### const word = ['Hello', 'World'];

#### const newWord = [word, 'python', 'JavaScript'];

#### output ['World', 'Hello', 'python', 'JavaScript']
------

### 9. Give an example of using the spread operator to combine two objects into one.

#### let employee1 = {name : 'sam', age : '29'};
##### let location = {age : '30', city : 'England'};

#### let combine = {employee1, location}

#### output [name : 'sam', age : '30', city : 'England']
---
### 10. In the video, what is the first step that the developer does to pass functions between components?

* ####  Define the function  where the state exists in the parent component.
--------
### 11. In your own words, what does the increment function do?
* ####  The Increment : is to increment the next node at the same level
-------
### 12. How can you pass a method from a parent component into a child component?

* ####  define then pass value using "this" then invoke.
---
### 13. How does the child component invoke a method that was passed to it from a parent component?

* ####  by calling it using props