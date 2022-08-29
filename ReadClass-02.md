# State and Props
## Reading
----------------
### 1. Based off the diagram, what happens first, the ‘render’ or the ‘componentDidMount’?

* ####  Render happens first, then componentDidMount
-----

### 2. What is the very first thing to happen in the lifecycle of React?

* ####  Mounting.
---------

### 3. Put the following things in the order that they happen: componentDidMount, render, constructor, componentWillUnmount, React Updates

* ####  constructor -> render -> componentDidMount -> react update -> componentWillUnmount
-----

### 4. What does componentDidMount do?

* ####  To set up any subscriptions, we are used to connect to the YouTube API and get videos when viewing components.
------

### 5. What types of things can you pass in the props?
* ####  any JavaScript data type from strings to functions, objects, etc. ...etc.
----

### 6. What is the big difference between props and state?
* ####  The difference is that the state is the props you pass to a component, the state is handled, and the state is different within that component. The props are handled outside the component.
-----

### 7. When do we re-render our application?
* ####  re-render is used when the state change in the parent component, or when the props get changed.
-------

### 8. What are some examples of things that we could store in state?
* ####  strings mostly, and integer or other objects can be stored too.
