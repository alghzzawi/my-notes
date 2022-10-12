# OOP Part02

## __design style__

#### It is just a description or template of how to solve a problem! They can be used in many different situations. So each design pattern provides a solution to common software design problems. Patterns are global best practices that a software developer can use to solve common problems when designing an application. In the case of the object-oriented programming paradigm, design patterns are generally aimed at solving object creation and communication problems, rather than larger problems in program architecture in general.

#### At a higher level, there are larger architectural patterns in the range of design patterns, usually describing an overall pattern that an entire system follows.

### The difference between programming paradigms, architectural patterns, design patterns, and design principles:

#### __Programming paradigms:__ A method of classifying programming languages ​​based on their coding patterns and properties.

#### __Architectural patterns:__ a reusable solution to a common problem in software engineering within a given context.

#### __Design patterns:__ A reusable solution to a common software design problem within a given context, it is a description or template for how to solve a problem.

#### __Design Principles:__ A set of guidelines that help developers avoid bad design.

---

<br>

## There are 3 main types of design patterns:

<br>

### __Creational Patterns__

#### Creational Patterns allow the programmer ways to create a single instance or group of objects. Facilitate creating things in a way that fits the situation.

<br>

#### __Some Creational Patterns:__

* #### *Factory method*. The factory model is used to replace class constructors, which abstracts the object creation process so that the type of instantiated object can be determined at run time.

* #### *Singleton*. Single pattern ensures that only one object of a given class is created. All other references to single class objects refer to the same basic example.

* #### *Abstract Factory*. The abstract factory pattern is used to provide the client with a set of related or dependent objects. The 'group' of factory-generated objects is determined at run time.

<br>

<br>

### __structural patterns:__
#### Structural patterns provide a way to define relationships between classes or objects.

<br>

#### __Some structural patterns:__
* #### *fake appearance* The interface pattern is used to define a simplified interface for a more complex subsystem.
* #### *Designer* The decorator pattern is used to extend or change the functionality of objects at run time by wrapping them in an object of the decorator class.

<br>

<br>

### __behavioral patterns:__
#### Behavioral patterns determine the methods of communication between categories and objects.

<br>

#### __Some behavioral patterns:__
* #### *observer* The observer pattern is used to allow the object to propagate changes to its state.
* #### *mediator* The median pattern is used to reduce coupling between classes that communicate with each other.
* #### *chain of responsibility* The chain of responsibility pattern is used to process various requests, each of which can be handled by a different processor.

----
---

## __Risk Analysis__

### What is risk analysis used for?
#### Use of risk analysis at the beginning of the project highlights potential problem areas. After identifying areas of risk, it helps developers and managers to mitigate risks. When a test plan is created, the risks involved in product testing must be taken into account along with the potential for harm it may cause to your software as well as the solutions.

### __Define risk__
### There are different groups of risks in the risk identification process:
* #### Business risk: It is the risk that may come from your company or customer, not from your project.
* #### Testing risks: You should be well versed in the platform you are working on, along with the software testing tools used.
* #### Early Release Risks: A fair amount of knowledge is required to analyze the risks associated with releasing unsatisfactory or untested software.
* #### Software Risks: You should be well aware of the risks associated with the software development process.

### __risk assessment__
### This is one of the most important steps. This step is said to be quite complex and should be handled very carefully. After the risks have been identified, the assessment should be approached programmatically. There are a few perspectives on risk assessment.

### __risk assessment perspective__
### There are three perspectives of risk assessment:
* #### Effect - to assess risk through impact.
* #### Cause - Assessing risk by cause is the opposite of effect.
* #### Likelihood - to evaluate risk by probability.

### __How is a risk analysis performed?__
### There are three steps:

* #### Searching for risks

* #### Analyze the impact of each risk individually

* #### Risk measures have been identified

----
---

## **dependency injection**

### There are three basic types of dependency injection:
* #### **Constructor injection:** Dependencies are provided by a class constructor.
* #### **Injector injection:** The client discloses a tuning method that the injector uses to inject dependency.
* #### **Interface injection:** A dependency provides an injector method that will inject the dependency into any client it is passed to. Clients must implement an interface that displays a method of mapping that accepts the dependency.

### So now the responsibility for dependency injection is on:
* Create objects
* Find out which classes require those objects
* and provide them with all those objects

<br>

| Benefits of using DI | Disadvantages of DI |
|:---------|:---------|
|Helps with unit testing.|Learning is a bit complicated, and if overused it can lead to management issues.|
|Boiler plate code is reduced.|Many compile-time errors are pushed to runtime.|
|Extending the application becomes easier.|Dependency injection frameworks are implemented with reflection or dynamic programming. This can hinder the use of IDE automation|
|It helps to enable loose coupling, which is important in application programming.||


<br>