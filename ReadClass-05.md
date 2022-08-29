# Putting it all toegher
---
### 1. What is the single responsibility principle and how does it apply to components?

* #### This means that one component that states that every module, class or function should have responsibility over a single part of that program's functionality.
----
### 2. What does it mean to build a ‘static’ version of your application?

* #### makes an application displays without the need for server side processing.
---
### 3. Once you have a static application, what do you need to add?

* #### application for deploy like netlify
---

### 4. What are the three questions you can ask to determine if something is state?

* #### Does it remain changed over time, if they can be defined in the component itself, if it's set and can be updated by an object, If so, it is state.
---

### 5. How can you identify where state needs to live?

* #### identify every component that renders something based on that state.
---

### 6. What is a “higher-order function”?
* #### Is a function that accepts functions as parameters and returns a function.
---
### 7. Explore the greaterThan function as defined in the reading. In your own words, what is line 2 of this function doing?
* #### if m is greater than n then return m

---
### 8. Explain how either map or reduce operates, with regards to higher-order functions.
* #### reduse: constructs a value by recursively taking a single element of an array and combining it
* #### Map: A map method transforms an array by a function of all its elements